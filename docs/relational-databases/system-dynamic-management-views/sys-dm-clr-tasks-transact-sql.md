---
title: sys.dm_clr_tasks (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_clr_tasks
- sys.dm_clr_tasks_TSQL
- dm_clr_tasks
- dm_clr_tasks_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_clr_tasks dynamic management view
ms.assetid: 462b9061-09fa-4858-9707-03d6cc19c769
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2a3c99ffd172c97c5738ed2dd19bc8b07f303470
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmclrtasks-transact-sql"></a>sys.dm_clr_tasks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retorna uma linha para todas as tarefas de CLR (Common Language Runtime) que estão atualmente em execução. Um lote [!INCLUDE[tsql](../../includes/tsql-md.md)] que contém uma referência a uma rotina CLR cria uma tarefa separada para execução de todo o código gerenciado nesse lote. Várias instruções no lote que requerem o uso de execução de código gerenciado usam a mesma tarefa de CLR. A tarefa de CLR é responsável por manter objetos e estado que pertencem à execução de código gerenciado, bem como as transições entre a instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e o CLR.  
  
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|**task_address**|**varbinary(8)**|Endereço da tarefa de CLR.|  
|**sos_task_address**|**varbinary(8)**|Endereço da tarefa de lote [!INCLUDE[tsql](../../includes/tsql-md.md)] subjacente.|  
|**appdomain_address**|**varbinary(8)**|Endereço do domínio de aplicativo no qual esta tarefa está em execução.|  
|**state**|**nvarchar(128)**|O estado atual da tarefa.|  
|**abort_state**|**nvarchar(128)**|Define se a anulação está atualmente ativada (se a tarefa tiver sido cancelada). Há vários estados envolvidos ao anular tarefas.|  
|**type**|**nvarchar(128)**|Tipo de tarefa.|  
|**affinity_count**|**Int**|Afinidade da tarefa.|  
|**forced_yield_count**|**Int**|Número de horas que a tarefa foi forçada a produzir.|  
  
## <a name="permissions"></a>Permissões  
 Em [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] requer a permissão VIEW SERVER STATE no servidor.  
  
 Em [!INCLUDE[ssSDS](../../includes/sssds-md.md)] camadas Premium requer a permissão VIEW DATABASE STATE no banco de dados. Em [!INCLUDE[ssSDS](../../includes/sssds-md.md)] camadas Standard e Basic requer o [!INCLUDE[ssSDS](../../includes/sssds-md.md)] conta de administrador.  
  
## <a name="see-also"></a>Consulte também  
 [Exibições e funções de gerenciamento dinâmico &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Common Language Runtime relacionados exibições de gerenciamento dinâmico &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/common-language-runtime-related-dynamic-management-views-transact-sql.md)  
  
  

