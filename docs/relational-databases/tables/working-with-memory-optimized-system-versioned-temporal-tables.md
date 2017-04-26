---
title: "Trabalho com tabelas temporais com controle da vers&#227;o do sistema com otimiza&#231;&#227;o de mem&#243;ria | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "05/05/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-tables"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 691d4f80-6754-43f5-8b43-d4facf08f6fc
caps.latest.revision: 12
author: "CarlRabeler"
ms.author: "carlrab"
manager: "jhubbard"
caps.handback.revision: 12
---
# Trabalho com tabelas temporais com controle da vers&#227;o do sistema com otimiza&#231;&#227;o de mem&#243;ria
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Este tópico discute como o trabalho com uma tabela temporal com controle da versão do sistema com otimização de memória é diferente do trabalho com uma tabela temporal com versão do sistema baseada em disco.  
  
> [!NOTE]  
>  O uso de tabelas temporais com otimização de memória só se aplica ao [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], não ao [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  
  
## Descoberta de Metadados  
 Para descobrir os metadados referentes a uma tabela temporal com controle de versão do sistema e otimização de memória, você precisa combinar as informações de [sys.tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md) e [sys.internal_tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-internal-tables-transact-sql.md). Uma tabela temporal com controle da versão do sistema é apresentada como parent_object_id da tabela de histórico na memória interna  
  
 Este exemplo mostra como consultar e unir essas tabelas.  
  
```  
SELECT SCHEMA_NAME (T1.schema_id) as TemporalTableSchema  
   , OBJECT_NAME(IT.parent_object_id) as TemporalTableName  
   , T1.object_id as TemporalTableObjectId  
   , IT.Name as InternalHistoryStagingName   
   , SCHEMA_NAME (T2.schema_id) as HistoryTableSchema  
   , OBJECT_NAME (T1.history_table_id) as HistoryTableName   
FROM sys.internal_tables IT    
JOIN sys.tables T1   
   ON IT.parent_object_id = T1.object_id   
JOIN sys.tables T2   
   ON T1.history_table_id = T2.object_id   
WHERE T1.is_memory_optimized  = 1 AND T1.temporal_type = 2  
  
```  
  
## Modificando dados  
 As tabelas temporais com controle da versão do sistema com otimização de memória podem ser modificadas por meio de procedimentos armazenados compilados nativamente que permitem converter tabelas não temporais com otimização de memória para versão do sistema e manter procedimentos existentes armazenados nativamente.  
  
 Este exemplo mostra como uma tabela criada anteriormente pode ser modificada no módulo compilado nativamente.  
  
```  
CREATE PROCEDURE dbo.UpdateFXCurrencyPair  
   (   
       @ProviderID int  
     , @CurrencyID1 int  
     , @CurrencyID2 int  
     , @BidRate decimal(8,4)  
     , @AskRate decimal(8,4)   
   )   
WITH NATIVE_COMPILATION, SCHEMABINDING  
   , EXECUTE AS OWNER   
AS    
   BEGIN ATOMIC WITH   
   (TRANSACTION ISOLATION LEVEL = SNAPSHOT  , LANGUAGE = N'English')   
      UPDATE dbo.FXCurrencyPairs SET AskRate = @AskRate, BidRate  = @BidRate   
     WHERE ProviderID = @ProviderID AND CurrencyID1 = @CurrencyID1 AND CurrencyID2 = @CurrencyID2   
END   
GO ;  
  
```  
  
## Este artigo foi útil para você? Estamos atentos  
 Quais são as informações que você está procurando? Você as localizou? Estamos atentos aos seus comentários para aprimorar o conteúdo. Envie seus comentários a [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Working%20with%20Memory-Optimized%20System-Versioned%20Temporal%20Tables%20page)  
  
## Consulte também  
 [Tabelas temporais com controle da versão do sistema com tabelas com otimização de memória](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)   
 [Criação de uma tabela temporal com controle da versão do sistema com otimização de memória](../../relational-databases/tables/creating-a-memory-optimized-system-versioned-temporal-table.md)   
 [Monitorando tabelas temporais com controle da versão do sistema com otimização de memória](../../relational-databases/tables/monitoring-memory-optimized-system-versioned-temporal-tables.md)   
 [Considerações sobre desempenho com tabelas temporais com versão do sistema e otimização de memória](../../relational-databases/tables/memory-optimized-system-versioned-temporal-tables-performance.md)   
 [Tabelas temporais](../../relational-databases/tables/temporal-tables.md)   
 [Verificações de consistência do sistema de tabela temporal](../../relational-databases/tables/temporal-table-system-consistency-checks.md)   
 [Gerenciar a Retenção de Dados Históricos em Tabelas Temporais com Versão do Sistema](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)   
 [Funções e exibições de metadados de tabela temporal](../../relational-databases/tables/temporal-table-metadata-views-and-functions.md)  
  
  