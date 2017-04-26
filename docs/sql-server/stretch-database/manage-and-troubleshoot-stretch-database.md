---
title: "Gerenciar e solucionar problemas no Stretch Database | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "06/27/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.service: "sql-server-stretch-database"
ms.suite: ""
ms.technology: 
  - "dbe-stretch"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Stretch Database, gerenciando"
  - "Stretch Database, solucionando problemas"
  - "gerenciando o Stretch Database"
  - "solucionando problemas no Stretch Database"
ms.assetid: 6334db3e-9297-44df-8d53-211187a95520
caps.latest.revision: 42
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 41
---
# Gerenciar e solucionar problemas no Stretch Database
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Para gerenciar e solucionar problemas do Stretch Database, use as ferramentas e os métodos descritos neste tópico.  
## Gerenciar dados locais  
  
###  <a name="LocalInfo"></a> Obter informações sobre tabelas e bancos de dados locais habilitados para o Stretch Database  
 Abra as exibições de catálogo **sys.databases** e **sys.tables** para ver informações sobre tabelas e bancos de dados do SQL Server habilitados para Stretch. Para obter mais informações, veja [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) e [sys.tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md).  
 
 Para ver quanto espaço uma tabela habilitada para Stretch está usando no SQL Server, execute a instrução a seguir.
 
 ```tsql
USE <Stretch-enabled database name>;
GO
EXEC sp_spaceused '<Stretch-enabled table name>', 'true', 'LOCAL_ONLY';
GO
 ```
   
## Gerenciar a migração de dados  
  
### Verificar a função de filtro aplicada a uma tabela  
 Abra a exibição de catálogo **sys.remote_data_archive_tables** e verifique o valor da coluna **filter_predicate** para identificar a função que o Stretch Database está usando para selecionar linhas para migração. Se o valor for nulo, a tabela inteira será qualificada para ser migrada. Para obter mais informações, veja [sys.remote_data_archive_tables &#40;Transact-SQL&#41;](../Topic/sys.remote_data_archive_tables%20\(Transact-SQL\).md) e [Selecione linhas para migrar usando uma função de filtro](../../sql-server/stretch-database/select-rows-to-migrate-by-using-a-filter-function-stretch-database.md).  
  
###  <a name="Migration"></a> Verificar o status da migração dos dados  
 Para monitorar a migração de dados no Monitor do Stretch Database, selecione **Tarefas | Stretch | Monitorar** para um banco de dados no SQL Server Management Studio. Para obter mais informações, veja [Monitorar e solucionar problemas de migração de dados &#40;Stretch Database&#41;](../../sql-server/stretch-database/monitor-and-troubleshoot-data-migration-stretch-database.md).  
  
 Ou então, abra a exibição de gerenciamento dinâmico **sys.dm_db_rda_migration_status** para ver quantos lotes e linhas de dados foram migradas.  
  
###  <a name="Firewall"></a> Solucionar problemas de migração de dados  
 Para obter sugestões de solução de problemas, veja [Monitorar e solucionar problemas de migração de dados &#40;Stretch Database&#41;](../../sql-server/stretch-database/monitor-and-troubleshoot-data-migration-stretch-database.md).  
  
## Gerenciar dados remotos  
  
###  <a name="RemoteInfo"></a> Obter informações sobre tabelas e bancos de dados remotos usados pelo Stretch Database  
 Abra as exibições de catálogo **sys.remote_data_archive_databases** e **sys.remote_data_archive_tables** para ver informações sobre as tabelas e os bancos de dados remotos em que os dados migrados são armazenados. Para obter mais informações, veja [sys.remote_data_archive_databases &#40;Transact-SQL&#41;](../Topic/sys.remote_data_archive_databases%20\(Transact-SQL\).md) e [sys.remote_data_archive_tables &#40;Transact-SQL&#41;](../Topic/sys.remote_data_archive_tables%20\(Transact-SQL\).md).  
 
Para ver quanto espaço uma tabela habilitada para Stretch está usando no Azure, execute a instrução a seguir.
 
 ```tsql
USE <Stretch-enabled database name>;
GO
EXEC sp_spaceused '<Stretch-enabled table name>', 'true', 'REMOTE_ONLY';
GO
 ```

### Excluir os dados migrados  
Se você quiser excluir dados que já foram migrados para o Azure, siga as etapas descritas em [sys.sp_rda_reconcile_batch](../../relational-databases/system-stored-procedures/sys-sp-rda-reconcile-batch-transact-sql.md).  
  
## Gerenciar o esquema de tabela

### Não altere o esquema da tabela remota  
 Não altere o esquema da tabela remota do Azure associada a uma tabela do SQL Server configurada para o Stretch Database. Em particular, não modifique o nome ou o tipo de dados de uma coluna. O recurso Stretch Database faz várias suposições sobre o esquema da tabela remota em relação ao esquema de tabela do SQL Server. Se você alterar o esquema remoto, o Stretch Database deixará de funcionar para a tabela alterada.  

### Reconciliar as colunas da tabela  
Se, acidentalmente, você excluiu colunas da tabela remota, execute **sp_rda_reconcile_columns** para adicionar colunas à tabela remota existentes na tabela do SQL Server habilitada para Stretch, mas que não existem na tabela remota. Para obter mais informações, veja [sys.sp_rda_reconcile_columns](../../relational-databases/system-stored-procedures/sys-sp-rda-reconcile-columns-transact-sql.md).  
  
  > [!IMPORTANT] Quando **sp_rda_reconcile_columns** recria colunas que foram acidentalmente excluídas da tabela remota, ele não restaura os dados que estavam anteriormente nas colunas excluídas.
  
**sp_rda_reconcile_columns** não exclui colunas da tabela remota existentes na tabela remota, mas que não existem na tabela do SQL Server habilitado para Stretch. Se houver colunas na tabela remota do Azure que não existem mais na tabela do SQL Server habilitada para Stretch, essas colunas extras não impedirão o funcionamento normal do Stretch Database. Opcionalmente, é possível remover as colunas extras manualmente.  
 
## Gerenciar o desempenho e os custos  
  
### Solucionar problemas de desempenho de consulta  
  Espera-se que consultas incluindo tabelas habilitadas para o Stretch executem mais lentamente do que executavam antes da habilitação dessas tabelas para o Stretch. Se o desempenho da consulta diminuir significativamente, examine os problemas possíveis a seguir.  
  
-   O servidor do Azure está em uma região geográfica diferente do SQL Server? Configure o servidor do Azure para que esteja na mesma região geográfica que o SQL Server, para reduzir a latência de rede.  
  
-   As condições de rede podem ter se degradado. Contate o administrador de rede para obter informações sobre problemas recentes ou interrupções.  
  
### Aumentar o nível de desempenho do Azure para operações com uso intensivo de recursos, como a indexação  
 Quando você cria, recria ou reorganiza um índice em uma tabela grande que está configurada para o Stretch Database e prevê uma carga pesada de consultas dos dados migrados no Azure durante esse período, considere aumentar o nível de desempenho do banco de dados do Azure remoto correspondente em relação à duração da operação. Para obter mais informações sobre níveis de desempenho e preços, veja [Preços do SQL Server Stretch Database](https://azure.microsoft.com/pricing/details/sql-server-stretch-database/).  
  
### Não é possível pausar o serviço SQL Server Stretch Database no Azure  
 Lembre-se de selecionar o nível adequado de desempenho e de preço. Se você aumentar o nível de desempenho temporariamente para uma operação de uso intensivo de recursos, restaure-a para o nível anterior após a conclusão da operação. Para obter mais informações sobre níveis de desempenho e preços, veja [Preços do SQL Server Stretch Database](https://azure.microsoft.com/pricing/details/sql-server-stretch-database/).  
   
 ## Alterar o escopo de consultas  
 Consultas em tabelas habilitadas para Stretch retornam dados locais e remotos por padrão. Você pode alterar o escopo de consultas de todas as consultas por todos os usuários ou de apenas uma única consulta por administrador.  
   
 ### Alterar o escopo de consultas para todas as consultas por todos os usuários  
 Para alterar o escopo de todas as consultas por todos os usuários, execute o procedimento armazenado **sys.sp_rda_set_query_mode**. Você pode reduzir o escopo para consultar apenas os dados locais, desabilitar todas as consultas ou restaurar a configuração padrão. Para obter mais informações, veja [sys.sp_rda_set_query_mode](../../relational-databases/system-stored-procedures/sys-sp-rda-set-query-mode-transact-sql.md).  
   
 ### <a name="queryHints"></a>Alterar o escopo de consultas para uma única consulta por um administrador  
 Para alterar o escopo de uma única consulta por um membro da função db_owner, adicione a dica de consulta **WITH ( REMOTE_DATA_ARCHIVE_OVERRIDE = *value* )** à instrução SELECT. A dica de consulta REMOTE_DATA_ARCHIVE_OVERRIDE pode ter os valores a seguir.  
 -   **LOCAL_ONLY**. Consultar apenas dados locais.  
   
 -   **REMOTE_ONLY**. Consultar apenas dados remotos.  
   
 -   **STAGE_ONLY**. Consulte somente os dados na tabela em que o Stretch Database prepara linhas qualificadas para migração e retém as linhas migradas durante o período especificado após a migração. Essa dica de consulta é a única maneira de consultar a tabela de preparo.  
  
Por exemplo, a consulta a seguir retorna apenas resultados locais.  
  
 ```tsql  
USE <Stretch-enabled database name>;
GO
SELECT * FROM <Stretch_enabled table name> WITH (REMOTE_DATA_ARCHIVE_OVERRIDE = LOCAL_ONLY) WHERE ... ;
GO
```  
   
 ## <a name="adminHints"></a>Realizar exclusões e atualizações administrativas  
 Por padrão, não é possível atualizar ou excluir linhas qualificadas para migração ou linhas que já foram migradas, em uma tabela habilitada para Stretch. Quando você precisa corrigir um problema, um membro da função db_owner pode executar uma operação UPDATE ou DELETE adicionando a dica de consulta **WITH ( REMOTE_DATA_ARCHIVE_OVERRIDE = *value* )** à instrução. A dica de consulta REMOTE_DATA_ARCHIVE_OVERRIDE pode ter os valores a seguir.  
 -   **LOCAL_ONLY**. Atualizar ou excluir apenas os dados locais.  
   
 -   **REMOTE_ONLY**. Atualize ou exclua apenas os dados remotos.  
   
 -   **STAGE_ONLY**. Atualize ou exclua somente os dados na tabela em que o Stretch Database prepara linhas qualificadas para migração e retém as linhas migradas durante o período especificado após a migração.  
  
## Consulte também  
 [Monitorar e solucionar problemas de migração de dados &#40;Stretch Database&#41;](../../sql-server/stretch-database/monitor-and-troubleshoot-data-migration-stretch-database.md)   
[Fazer backup de bancos de dados habilitados para Stretch (Stretch Database)](../../sql-server/stretch-database/backup-stretch-enabled-databases-stretch-database.md)  
[Restaurar bancos de dados habilitados para Stretch (Stretch Database)](../../sql-server/stretch-database/restore-stretch-enabled-databases-stretch-database.md)  
  
  