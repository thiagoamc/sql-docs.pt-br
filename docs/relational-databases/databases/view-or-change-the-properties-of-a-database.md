---
title: "Exibir ou alterar as propriedades de um banco de dados | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "08/25/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "exibindo bancos de dados"
  - "exibindo banco de dados [SQL Server]"
  - "bancos de dados [SQL Server], exibição"
  - "exibindo bancos de dados"
ms.assetid: 9e8ac097-84b7-46c7-85e3-c1e79f94d747
caps.latest.revision: 42
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 40
---
# Exibir ou alterar as propriedades de um banco de dados
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Este tópico descreve como exibir ou alterar os propriedades de um banco de dados no [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] usando o [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou o [!INCLUDE[tsql](../../includes/tsql-md.md)]. Depois de alterar uma propriedade de banco de dados, a modificação entra em vigor imediatamente.  
  
 **Neste tópico**  
  
-   **Antes de começar:**  
  
     [Recomendações](#Recommendations)  
  
     [Segurança](#Security)  
  
-   **Para exibir ou alterar as propriedades de um banco de dados usando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Antes de começar  
  
###  <a name="Recommendations"></a> Recomendações  
  
-   Quando AUTO_CLOSE for ON, algumas colunas da exibição de catálogo [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) e da função DATABASEPROPERTYEX retornarão NULL, pois o banco de dados não está disponível para recuperar os dados. Para resolver esse problema, abra o banco de dados.  
  
###  <a name="Security"></a> Segurança  
  
####  <a name="Permissions"></a> Permissões  
 Requer a permissão ALTER no banco de dados para alterar as propriedades de um banco de dados. Requer pelo menos uma associação na função de banco de dados Público para exibir as propriedades de um banco de dados.  
  
##  <a name="SSMSProcedure"></a> Usando o SQL Server Management Studio  
  
#### Para exibir ou alterar as propriedades de um banco de dados  
  
1.  No **Pesquisador de Objetos**, conecte-se a uma instância do [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]e expanda-a.  
  
2.  Expanda **Banco de Dados**, clique com o botão direito do mouse no banco de dados para exibi-lo e clique em **Propriedades**.  
  
3.  Na caixa de diálogo **Propriedades do Banco de Dados** , selecione uma página para exibir as informações correspondentes. Por exemplo, selecione a página **Arquivos** para exibir os dados e as informações do arquivo de log.  
  
##  <a name="TsqlProcedure"></a> Usando Transact-SQL  
 O Transact-SQL fornece vários métodos diferentes para exibir as propriedades de um banco de dados e para alterar essas propriedades. Para exibir as propriedades de um banco de dados, é possível usar a função [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/databasepropertyex-transact-sql.md) e a exibição do catálogo [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md). Para alterar as propriedades de um banco de dados, você pode usar a versão da instrução ALTER DATABASE para seu ambiente: [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md) ou [ALTER DATABASE &#40;Banco de Dados SQL do Azure&#41;](../../t-sql/statements/alter-database-azure-sql-database.md). Para exibir as propriedades de banco de dados com escopo, use a exibição de catálogo [sys.database_scoped_configurations &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-scoped-configurations-transact-sql.md), e para alterá-las, use a instrução [ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).  
  
#### Para exibir uma propriedade de um banco de dados usando a função DATABASEPROPERTYEX  
  
1.  Conecte-se ao [!INCLUDE[ssDE](../../includes/ssde-md.md)] e, em seguida, conecte-se ao banco de dados para o qual você deseja exibir suas propriedades.  
  
2.  Na barra Padrão, clique em **Nova Consulta**.  
  
3.  Copie e cole o exemplo a seguir na janela de consulta e clique em **Executar**. Este exemplo usa a função do sistema [DATABASEPROPERTYEX](../../t-sql/functions/databasepropertyex-transact-sql.md) para retornar o status da opção de banco de dados AUTO_SHRINK no banco de dados [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]. Um valor de retorno 1 significa que a opção está definida como ON e um valor de retorno 0 significa que a opção está definida como OFF.  
  
    ```tsql  
    SELECT DATABASEPROPERTYEX('AdventureWorks2012', 'IsAutoShrink');  
    ```  
  
#### Para exibir as propriedades de um banco de dados consultando sys.databases  
  
1.  Conecte-se ao [!INCLUDE[ssDE](../../includes/ssde-md.md)] e, em seguida, conecte-se ao banco de dados para o qual você deseja exibir suas propriedades.  
  
2.  Na barra Padrão, clique em **Nova Consulta**.  
  
3.  Copie e cole o exemplo a seguir na janela de consulta e clique em **Executar**. Este exemplo consulta a exibição de catálogo [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) para exibir várias propriedades do banco de dados [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . Este exemplo retorna o número de identificação de banco de dados (`database_id`), se o banco de dados for somente leitura ou de leitura/gravação (`is_read_only`), o agrupamento do banco de dados (`collation_name`) e o nível de compatibilidade do banco de dados (`compatibility_level`).  
  
    ```tsql  
    SELECT database_id, is_read_only, collation_name, compatibility_level  
    FROM sys.databases WHERE name = 'AdventureWorks2012';  
    ```  
  
#### Para exibir as propriedades de uma configuração de escopo do banco de dados consultando sys.databases_scoped_configuration  
  
1.  Conecte-se ao [!INCLUDE[ssDE](../../includes/ssde-md.md)] e, em seguida, conecte-se ao banco de dados para o qual você deseja exibir suas propriedades.  
  
2.  Na barra Padrão, clique em **Nova Consulta**.  
  
3.  Copie e cole o exemplo a seguir na janela de consulta e clique em **Executar**. Este exemplo consulta a exibição de catálogo [sys.database_scoped_configurations &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-scoped-configurations-transact-sql.md) para exibir várias propriedades do banco de dados atual.  
  
    ```tsql  
    SELECT configuration_id, name, value, value_for_secondary  
    FROM sys.database_scoped_configurations;  
    ```  
  
     Para obter mais exemplos, veja [sys.database_scoped_configurations &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-scoped-configurations-transact-sql.md)  
  
#### Para alterar as propriedades de um banco de dados do SQL Server 2016 usando ALTER DATABASE  
  
1.  Conecte-se ao [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Na barra Padrão, clique em **Nova Consulta**.  
  
3.  Copie e cole o exemplo a seguir na janela de consulta. O exemplo determina o estado de isolamento de instantâneo no banco de dados [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] , altera o estado da propriedade e verifique a alteração.  
  
     Para determinar o estado de isolamento de instantâneo, selecione a primeira instrução `SELECT` e clique em **Executar**.  
  
     Para alterar o estado de isolamento de instantâneo, selecione a primeira instrução `ALTER DATABASE` e clique em **Executar**.  
  
     Para verificar a alteração, selecione a segunda instrução `SELECT` e clique em **Executar**.  
  
     [!code-sql[DatabaseDDL#AlterDatabase9](../../relational-databases/databases/codesnippet/tsql/view-or-change-the-prope_1.sql)]  
  
#### Para alterar as propriedades de escopo do banco de dados usando ALTER DATABASE SCOPED CONFIGURATION  
  
1.  Conecte-se ao banco de dados na instância do SQL Server.  
  
2.  Na barra Padrão, clique em **Nova Consulta**.  
  
3.  Copie e cole o exemplo a seguir na janela de consulta. O exemplo a seguir define MAXDOP para um banco de dados secundário com o valor do banco de dados primário.  
  
    ```  
    ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET MAXDOP=PRIMARY   
    ```  
  
## Consulte também  
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/databasepropertyex-transact-sql.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [ALTER DATABASE &#40;Banco de Dados SQL do Azure&#41;](../../t-sql/statements/alter-database-azure-sql-database.md)   
 [ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)   
 [sys.database_scoped_configurations &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-scoped-configurations-transact-sql.md)  

  
  