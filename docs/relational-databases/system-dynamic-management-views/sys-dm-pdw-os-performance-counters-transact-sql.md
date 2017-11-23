---
title: sys.dm_pdw_os_performance_counters (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 0673a8f8-8bed-41eb-8959-a9e3e9e03a65
caps.latest.revision: "8"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0b4b346df5211f91519accf3c81374d0ab7302ec
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmpdwosperformancecounters-transact-sql"></a>sys.dm_pdw_os_performance_counters (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Contém informações sobre contadores de desempenho do Windows para os nós no [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
|Nome da coluna|Tipo de dados|Description|Intervalo|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|A ID do nó que contém o contador.<br /><br /> pdw_node_id e counter_name formam a chave para este modo de exibição.|Consulte node_id em [sys.dm_pdw_nodes &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|counter_name|**nvarchar(255)**|Nome do contador de desempenho do Windows.||  
|counter_category|**nvarchar(255)**|Nome da categoria de contador de desempenho do Windows.||  
|instance_name|**nvarchar(255)**|Nome da instância específica do contador.||  
|counter_value|**Decimal(38,10)**|Valor atual do contador.||  
|last_update_time|**Datetime2(3)**|Carimbo de hora da última vez que o valor foi atualizado.||  
  
## <a name="see-also"></a>Consulte também  
 [SQL Data Warehouse e exibições de gerenciamento dinâmico do Parallel Data Warehouse &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  