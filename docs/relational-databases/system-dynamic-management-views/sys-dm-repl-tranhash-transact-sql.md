---
title: sys.dm_repl_tranhash (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_repl_tranhash
- sys.dm_repl_tranhash_TSQL
- dm_repl_tranhash_TSQL
- dm_repl_tranhash
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_repl_tranhash dynamic management view
ms.assetid: 0cc52338-e805-4ed4-9835-b19bbf72448e
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 34de8de4ffeb2e9cc6d2ce84ae5df81570ea9911
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmrepltranhash-transact-sql"></a>sys.dm_repl_tranhash (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retorna informações sobre transações sendo replicadas em uma publicação transacional.  
  
|column_name|data_type|descrição|  
|------------------|----------------|-----------------|  
|**buckets**|**bigint**|Número de partições de memória na tabela hash.|  
|**hashed_trans**|**bigint**|Número de transações confirmadas replicadas no lote atual.|  
|**completed_trans**|**bigint**|Número de transações disputadas até o momento.|  
|**compensated_trans**|**bigint**|Número de transações que contêm reversões parciais.|  
|**first_begin_lsn**|**nvarchar(64)**|Número de sequência de log de início mais antigo (LSN) no lote atual.|  
|**last_commit_lsn**|**nvarchar(64)**|Último LSN de confirmação no lote atual.|  
  
## <a name="permissions"></a>Permissões  
 Requer permissão VIEW DATABASE STATE no banco de dados de publicação para chamar **dm_repl_tranhash**.  
  
## <a name="remarks"></a>Remarks  
 As informações só serão retornadas para objetos de banco de dados replicados atualmente armazenados no cache de artigo de replicação.  
  
## <a name="see-also"></a>Consulte também  
 [Exibições e funções de gerenciamento dinâmico &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Exibições de gerenciamento dinâmico &#40; relacionadas à replicação Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/replication-related-dynamic-management-views-transact-sql.md)  
  
  
