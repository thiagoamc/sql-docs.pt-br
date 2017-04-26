---
title: "Índices columnstore – desfragmentação | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 01/27/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d3efda1a-7bdb-47f5-80bf-f075329edee5
caps.latest.revision: 17
author: barbkess
ms.author: barbkess
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: eea1da9c6a3c9dd30b89c72488570ae98737eaa5
ms.lasthandoff: 04/11/2017

---
# <a name="columnstore-indexes---defragmentation"></a>Índices columnstore – desfragmentação
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Tarefas para desfragmentação de índices columnstore.  
  
## <a name="use-alter-index-reorganize-to-defragment-a-columnstore-index-online"></a>Usar ALTER INDEX REORGANIZE para desfragmentar um índice columnstore online  
 APLICA-SE A: SQL Server (a partir do 2016), Banco de Dados SQL do Azure  
  
  Depois de executar os carregamentos de todos os tipos, você poderá ter vários rowgroups pequenos no deltastore. Você pode usar ALTER INDEX REORGANIZE para forçar todos os rowgroups no índice columnstore e combinar os rowgroups em rowgroups menores com mais linhas.  A operação de reorganização removerá também as linhas que foram excluídas do columnstore.  
  
 Para saber mais, confira as postagens do blog de Sunil Agarwal no blog da equipe do Mecanismo de Banco de Dados do SQL.  
  
-   [Minimizing index fragmentation in columnstore indexes (Minimizando a fragmentação de índice nos índices columnstore)](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/07/columnstore-index-defragmentation-using-reorganize-command/)  
  
-   [Columnstore indexes and the merge policy for rowgroups (Índices columnstore e a política de mesclagem para rowgroups)](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/08/columnstore-index-merge-policy-for-reorganize/)  
  
### <a name="recommendations-for-reorganizing"></a>Recomendações para reorganização  
 Reorganize um índice columnstore o mais rapidamente possível, depois que um ou mais carregamentos de dados atingir os benefícios de desempenho de consulta. Inicialmente, a reorganização exigirá recursos de CPU adicionais para compactar os dados, o que pode reduzir o desempenho geral do sistema. No entanto, assim que os dados forem compactados, o desempenho de consulta poderá aumentar.  
  
 Use o exemplo em [sys.dm_db_column_store_row_group_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-column-store-row-group-physical-stats-transact-sql.md) para calcular a fragmentação. Isso vai ajudar você a determinar se vale a pena executar uma operação REORGANIZE.  
  
### <a name="example-how-reorganizing-works"></a>Exemplo: Funcionamento da reorganização  
 Este exemplo mostra como ALTER INDEX REORGANIZE pode forçar todos os rowgroups do deltastore no índice columnstore e combinar os rowgroups.  
  
1.  Execute este Transact-SQL para criar uma tabela de preparo que contenha 300.000 linhas. Usaremos isso para o carregamento de linhas em massa em um índice columnstore.  
  
    ```  
    USE master;  
    GO  
  
    IF EXISTS (SELECT name FROM sys.databases  
        WHERE name = N'[columnstore]')  
        DROP DATABASE [columnstore];  
    GO  
  
    CREATE DATABASE [columnstore];  
    GO  
  
    IF EXISTS (SELECT name FROM sys.tables  
        WHERE name = N'staging'  
        AND object_id = OBJECT_ID (N'staging'))  
    DROP TABLE dbo.staging;  
    GO  
  
    CREATE TABLE [staging] (  
         AccountKey int NOT NULL,  
         AccountDescription nvarchar (50),  
         AccountType nvarchar(50),  
         AccountCodeAlternateKey int  
    );  
    GO  
  
    -- Load data  
    DECLARE @loop int;  
    DECLARE @AccountDescription varchar(50);  
    DECLARE @AccountKey int;  
    DECLARE @AccountType varchar(50);  
    DECLARE @AccountCode int;  
  
    SELECT @loop = 0;  
    BEGIN TRAN  
        WHILE (@loop < 300000)   
          BEGIN  
            SELECT @AccountKey = CAST (RAND()*10000000 AS int);  
            SELECT @AccountDescription = 'accountdesc ' + CONVERT(varchar(20), @AccountKey);  
            SELECT @AccountType = 'AccountType ' + CONVERT(varchar(20), @AccountKey);  
            SELECT @AccountCode =  CAST (RAND()*10000000 AS int);  
  
            INSERT INTO staging VALUES (  
               @AccountKey,   
               @AccountDescription,   
               @AccountType,   
               @AccountCode  
            );  
  
            SELECT @loop = @loop + 1;  
          END  
    COMMIT  
  
    ```  
  
2.  Crie uma tabela armazenada como um índice columnstore.  
  
    ```  
    IF EXISTS (SELECT name FROM sys.tables  
        WHERE name = N'cci_target'  
        AND object_id = OBJECT_ID (N'cci_target'))  
    DROP TABLE dbo.cci_target;  
    GO  
  
    -- Create a table with a clustered columnstore index  
    -- and the same columns as the rowstore staging table.  
    CREATE TABLE cci_target (  
         AccountKey int NOT NULL,  
         AccountDescription nvarchar (50),  
         AccountType nvarchar(50),  
         AccountCodeAlternateKey int,  
         INDEX idx_cci_target CLUSTERED COLUMNSTORE  
    )  
    GO  
  
    ```  
  
3.  Faça uma inserção em massa das linhas da tabela de preparo na tabela do índice columnstore. INSERT INTO... SELECT executa uma inserção em massa.   A opção TABLOCK executa a inserção em paralelo.  
  
    ```  
    -- Insert rows in parallel  
    INSERT INTO cci_target WITH (TABLOCK)  
    SELECT TOP (300000) * FROM staging;  
    GO  
  
    ```  
  
4.  Para exibir os rowgroups, use a DMV (exibição de gerenciamento dinâmico) sys.dm_db_column_store_row_group_physical_stats.  
  
    ```  
    -- Run this dynamic management view (DMV) to see the OPEN rowgroups.   
    -- The number of rowgroups depends on the degree of parallelism.   
    -- You will see multiple OPEN rowgroups depending on the degree of parallelism.   
    -- This is because insert operation can run in parallel in SQL server 2016.  
  
    SELECT *   
    FROM sys.dm_db_column_store_row_group_physical_stats   
    WHERE object_id  = object_id('cci_target')  
    ORDER BY row_group_id;  
  
    ```  
  
     Neste exemplo, os resultados mostram oito rowgroups ABERTOS com 37.500 linhas cada. A quantidade de rowgroups ABERTOS depende da configuração max_degree_of_parallelism.  
  
     ![Rowgroups OPEN](../../relational-databases/indexes/media/cci-openrowgroups.png "Rowgroups OPEN")  
  
5.  Use ALTER INDEX REORGANIZE com a opção COMPRESS_ALL_ROW_GROUPS para forçar a compactação de todos os rowgroups no índice columnstore.  
  
    ```  
    -- This command will force all CLOSED and OPEN rowgroups into the columnstore.  
    ALTER INDEX idx_cci_target ON cci_target   
    REORGANIZE WITH (COMPRESS_ALL_ROW_GROUPS = ON);  
  
    SELECT *   
    FROM sys.dm_db_column_store_row_group_physical_stats   
    WHERE object_id  = object_id('cci_target')  
    ORDER BY row_group_id;  
  
    ```  
  
     Os resultados mostram oito rowgroups COMPACTADOS e oito rowgroups MARCAS DE EXCLUSÃO. Todos os rowgroups são compactados no índice columnstore, independentemente do respectivo tamanho. Os rowgroups TOMBSTONE serão removidos pelo sistema.  
  
     ![Rowgroups TOMBSTONE e COMPRESSED](../../relational-databases/indexes/media/cci-tombstone-compressed-rowgroups.png "Rowgroups TOMBSTONE e COMPRESSED")  
  
6.  Para aprimorar o desempenho da consulta, é muito melhor combinar pequenos rowgroups.  ALTER INDEX REORGANIZE combinará rowgroups COMPRESSED. Agora que os rowgroups delta estão compactados no columnstore, execute ALTER INDEX REORGANIZE novamente para combinar os pequenos rowgroups COMPRESSED. Nesse momento, você não precisa da opção COMPRESS_ALL_ROW_GROUPS.  
  
    ```  
    -- Run this again and you will see that smaller rowgroups   
    -- combined into one compressed rowgroup with 300,000 rows  
    ALTER INDEX idx_cci_target ON cci_target REORGANIZE;  
  
    SELECT *   
    FROM sys.dm_db_column_store_row_group_physical_stats   
    WHERE object_id  = object_id('cci_target')  
    ORDER BY row_group_id;  
    ```  
  
     Os resultados mostram que os oito rowgroups COMPRESSED foram combinados em um único rowgroup COMPRESSED.  
  
     ![Rowgroups combinados](../../relational-databases/indexes/media/cci-compressed-rowgroups.png "Rowgroups combinados")  
  
##  <a name="rebuild"></a> Usar ALTER INDEX REBUILD para desfragmentar o índice columnstore offline  
 Para o SQL Server 2016 e posterior, normalmente não é necessário recompilar o índice columnstore, pois REORGANIZE executa os dados básicos de uma recompilação em segundo plano como uma operação online.  
  
 A recompilação de um índice columnstore remove a fragmentação e transfere todas as linhas para o columnstore. Use [CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-columnstore-index-transact-sql.md) ou [ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md) para executar uma recriação completa de um índice columnstore clusterizado existente. Além disso, você pode usar ALTER INDEX ... REBUILD para recompilar uma partição específica.  
  
### <a name="rebuild-process"></a>Processo de recriação  
 Para recompilar um índice columnstore, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
1.  Obtenha um bloqueio exclusivo na tabela ou na partição durante a recompilação.  Os dados estão "offline" e indisponíveis durante a recompilação, mesmo se você usar NOLOCK, RCSI ou SI.  
  
2.  Compacta novamente todos os dados do columnstore. Há duas cópias do índice columnstore durante a recompilação. Quando a recompilação é concluída, o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] exclui o índice columnstore original.  
  
### <a name="recommendations-for-rebuilding-a-columnstore-index"></a>Recomendações para recompilação de um índice columnstore  
 A recompilação de um índice columnstore é útil para remover a fragmentação e para transferir todas as linhas para o columnstore. Nossas recomendações:  
  
1.  Recriar uma partição em vez de toda a tabela.  
  
    -   Recriar a tabela inteira é uma tarefa demorada se o índice é grande, e isso exige espaço em disco suficiente para armazenar uma cópia adicional do índice durante a recriação. Geralmente, é necessário recriar apenas a partição mais recentemente usada.  
  
    -   Em tabelas particionadas, não é necessário recriar todo o índice columnstore, pois é provável que a fragmentação ocorra apenas nas partições que foram modificadas recentemente. As tabelas de fatos e de dimensões grandes geralmente são particionadas para executar operações de backup e gerenciamento em partes da tabela.  
  
2.  Recriar uma partição após operações DML pesadas.  
  
    -   Recriar uma partição desfragmentará a partição e reduzirá o armazenamento em disco. Essa recriação excluirá todas as linhas do columnstore marcadas para exclusão e moverá todos os rowgroups do deltastore para o columnstore. Observe que pode haver várias rowgroups no deltastore, que possuem menos de um milhão de linhas cada um.  
  
3.  Recriar uma partição após carregar dados.  
  
    -   Isso garante que todos dados sejam armazenados no columnstore. Quando os processos atuais carregam menos de 100 mil linhas cada um na mesma partição em simultâneo, a partição pode acabar com vários deltastores. A recriação moverá todas as linhas do deltastore para o columnstore.  
  
## <a name="see-also"></a>Consulte também        
[Índices columnstore – novidades](../../relational-databases/indexes/columnstore-indexes-what-s-new.md)

[Índices columnstore – desempenho da consulta](../../relational-databases/indexes/columnstore-indexes-query-performance.md)   
[Introdução ao Columnstore para análise operacional em tempo real](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)   
 [Índices columnstore – data warehouse](../../relational-databases/indexes/columnstore-indexes-data-warehouse.md)   
   
  
  
