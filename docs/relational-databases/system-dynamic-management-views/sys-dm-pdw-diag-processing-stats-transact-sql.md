---
title: sys.dm_pdw_diag_processing_stats (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: df659c55-4f63-45f8-8afe-ce300031bc5b
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3ab28a8e13851642b11a5f465365ab2b48b51bd9
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmpdwdiagprocessingstats-transact-sql"></a>sys.dm_pdw_diag_processing_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Exibe informações relacionadas a todos os eventos de diagnósticos internos que podem ser incorporados em sessões de diagnóstico definidas pelo administrador. Consulte essa exibição para entender as estatísticas por trás os subsistemas de eventos e de diagnóstico que a população de todos os outros DMVs de unidade. Há um grupo de filas para cada processo em cada nó.  
  
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|**pdw_node_id**|**Int**|Esse log é de um nó de dispositivo.|  
|**process_id**|**Int**|Identificador do processo em execução enviar essa estatística.|  
|**target_name**|**nvarchar(255)**|O nome da fila.|  
|**queue_size**|**Int**|O número de itens na fila de processo. Geralmente, o tamanho da fila é 0. Um número positivo indica que o sistema está sob carga excessiva e está criando a lista de pendências de eventos. Uma contagem positiva nas outras colunas significa sistema está corrompido para essa fila determinada e DMVs relacionados.|  
|**lost_events_count**|**bigint**|O número de eventos perdidos.|  
  
## <a name="see-also"></a>Consulte também  
 [SQL Data Warehouse e exibições de gerenciamento dinâmico do Parallel Data Warehouse &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
