---
title: sys.dm_exec_function_stats (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- sys.dm_exec_function_stats
- sys.dm_exec_function_stats_tsql
- dm_exec_function_stats
- dm_exec_function_stats_tsql
helpviewer_keywords:
- sys.dm_exec_function_stats dynamic management view
ms.assetid: 4c3d6a02-08e4-414b-90be-36b89a0e5a3a
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c9071315f8adebb6a889840b919f4bd50d4a8bde
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmexecfunctionstats-transact-sql"></a>sys.dm_exec_function_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Retorna estatísticas de desempenho para as funções em cache de agregação. A exibição retorna uma linha para cada plano de função em cache, e o tempo de vida da linha é como a função permanece em cache. Quando uma função é removida do cache, a linha correspondente é eliminada desta exibição. Nesse momento, um evento de rastreamento de SQL de estatísticas de desempenho é gerado como **sys.DM exec_query_stats**. Retorna informações sobre funções escalares, incluindo funções na memória e funções escalares CLR. Retorna informações sobre funções com valor de tabela.  
  
 No [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], as exibições de gerenciamento dinâmico não podem expor informações que afetarão a contenção do banco de dados ou informações sobre outros bancos de dados aos quais o usuário tem acesso. Para evitar a exposição dessas informações, cada linha que contém os dados que não pertencem ao locatário conectado será filtrada.  
  
> [!NOTE]
> Uma consulta inicial de **sys.DM exec_function_stats** pode produzir resultados inexatos se houver uma carga de trabalho atualmente em execução no servidor. Mais resultados precisos podem ser determinados pela reexecução da consulta.  
  
  
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**Int**|ID de banco de dados no qual a função reside.|  
|**object_id**|**Int**|Número de identificação de objeto da função.|  
|**type**|**char(2)**|Tipo de objeto: FN = funções com valor escalar|  
|**type_desc**|**nvarchar(60)**|Descrição do tipo de objeto: SQL_SCALAR_FUNCTION|  
|**sql_handle**|**varbinary(64)**|Isso pode ser usado para correlacionar com as consultas de **sys.DM exec_query_stats** que foram executados nessa função.|  
|**plan_handle**|**varbinary(64)**|Identificador do plano na memória. Esse identificador é transitório e permanece constante somente enquanto o plano permanece no cache. Esse valor pode ser usado com o **exec_cached_plans** exibição de gerenciamento dinâmico.<br /><br /> Sempre será 0x000 quando uma tabela de consultas, uma otimização de memória da função compilada nativamente.|  
|**cached_time**|**datetime**|Hora em que a função foi adicionada ao cache.|  
|**last_execution_time**|**datetime**|Última vez em que a função foi executada.|  
|**execution_count**|**bigint**|Número de vezes que a função foi executada desde sua última compilação.|  
|**total_worker_time**|**bigint**|Tempo total de tempo de CPU, em microssegundos, consumido por execuções desta função desde sua compilação.<br /><br /> Para funções compiladas nativamente, **total_worker_time** pode não ser preciso se várias execuções levarem menos de 1 milissegundo.|  
|**last_worker_time**|**bigint**|Tempo de CPU, em microssegundos, consumido na última vez em que a função foi executada. <sup>1</sup>|  
|**min_worker_time**|**bigint**|Tempo mínimo de CPU, em microssegundos, que essa função consumiu durante uma única execução. <sup>1</sup>|  
|**max_worker_time**|**bigint**|Tempo máximo de CPU, em microssegundos, que essa função consumiu durante uma única execução. <sup>1</sup>|  
|**total_physical_reads**|**bigint**|Número total de leituras físicas efetuadas por execuções desta função desde sua compilação.<br /><br /> Sempre será 0 ao consultar uma tabela com otimização de memória.|  
|**last_physical_reads**|**bigint**|Número de leituras físicas efetuadas na última vez em que a função foi executada.<br /><br /> Sempre será 0 ao consultar uma tabela com otimização de memória.|  
|**min_physical_reads**|**bigint**|Número mínimo de leituras físicas que essa função efetuou durante uma única execução.<br /><br /> Sempre será 0 ao consultar uma tabela com otimização de memória.|  
|**max_physical_reads**|**bigint**|Número máximo de leituras físicas que essa função efetuou durante uma única execução.<br /><br /> Sempre será 0 ao consultar uma tabela com otimização de memória.|  
|**total_logical_writes**|**bigint**|Número total de gravações lógicas efetuadas por execuções desta função desde sua compilação.<br /><br /> Sempre será 0 ao consultar uma tabela com otimização de memória.|  
|**last_logical_writes**|**bigint**|O número de páginas do pool de buffers que foram sujas na última vez em que o plano foi executado. Se uma página já estiver suja (modificada), nenhuma gravação será contabilizada.<br /><br /> Sempre será 0 ao consultar uma tabela com otimização de memória.|  
|**min_logical_writes**|**bigint**|Número mínimo de gravações lógicas que essa função efetuou durante uma única execução.<br /><br /> Sempre será 0 ao consultar uma tabela com otimização de memória.|  
|**max_logical_writes**|**bigint**|Número máximo de gravações lógicas que essa função efetuou durante uma única execução.<br /><br /> Sempre será 0 ao consultar uma tabela com otimização de memória.|  
|**total_logical_reads**|**bigint**|Número total de leituras lógicas efetuadas por execuções desta função desde sua compilação.<br /><br /> Sempre será 0 ao consultar uma tabela com otimização de memória.|  
|**last_logical_reads**|**bigint**|Número de leituras lógicas efetuadas na última vez em que a função foi executada.<br /><br /> Sempre será 0 ao consultar uma tabela com otimização de memória.|  
|**min_logical_reads**|**bigint**|Número mínimo de leituras lógicas que essa função efetuou durante uma única execução.<br /><br /> Sempre será 0 ao consultar uma tabela com otimização de memória.|  
|**max_logical_reads**|**bigint**|Número máximo de leituras lógicas que essa função efetuou durante uma única execução.<br /><br /> Sempre será 0 ao consultar uma tabela com otimização de memória.|  
|**total_elapsed_time**|**bigint**|Total de tempo decorrido, em microssegundos, de execuções concluídas dessa função.|  
|**last_elapsed_time**|**bigint**|Tempo decorrido, em microssegundos, da execução concluída mais recente desta função.|  
|**min_elapsed_time**|**bigint**|Tempo mínimo decorrido, em microssegundos, de qualquer execução concluída dessa função.|  
|**max_elapsed_time**|**bigint**|Tempo máximo decorrido, em microssegundos, de qualquer execução concluída dessa função.|  
  
## <a name="permissions"></a>Permissões  
Em [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], requer `VIEW SERVER STATE` permissão.   
Em [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] camadas Premium, requer o `VIEW DATABASE STATE` no banco de dados. Em [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] camadas Standard e Basic, requer o **administrador do servidor** ou um **administrador do Active Directory do Azure** conta.  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir retorna informações sobre as funções de dez principais identificados por tempo médio decorrido.  
  
```  
SELECT TOP 10 d.object_id, d.database_id, OBJECT_NAME(object_id, database_id) 'function name',   
    d.cached_time, d.last_execution_time, d.total_elapsed_time,  
    d.total_elapsed_time/d.execution_count AS [avg_elapsed_time],  
    d.last_elapsed_time, d.execution_count  
FROM sys.dm_exec_function_stats AS d  
ORDER BY [total_worker_time] DESC;  
```  
  
## <a name="see-also"></a>Consulte também  
 [Funções e exibições de gerenciamento dinâmico &#40; relacionadas à execução Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_exec_sql_text &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)   
 [sys.dm_exec_query_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)   
 
 [sys.dm_exec_trigger_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-trigger-stats-transact-sql.md)   
 [sys.dm_exec_procedure_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md)  
  
  
