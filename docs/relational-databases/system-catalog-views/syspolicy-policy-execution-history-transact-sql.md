---
title: syspolicy_policy_execution_history (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- syspolicy_policy_execution_history_TSQL
- syspolicy_policy_execution_history
dev_langs:
- TSQL
helpviewer_keywords:
- syspolicy_policy_execution_history view
ms.assetid: b13c44a7-6d49-4d50-abe1-e657fc52bb05
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8751e694bb4b1e3eed619827930356f0bca66d9f
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2018
---
# <a name="syspolicypolicyexecutionhistory-transact-sql"></a>syspolicy_policy_execution_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Exibe a hora quando foram executadas as políticas, o resultado de cada execução e os detalhes sobre erros, se houver. A tabela a seguir descreve as colunas na exibição syspolicy_policy_execution_history.  
  
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|history_id|**bigint**|Identificador deste registro. Cada registro indica uma política e uma vez que ela foi iniciada.|  
|policy_id|**Int**|Identificador da política.|  
|start_date|**datetime**|Data e hora em que esta política tentou executar.|  
|end_date|**datetime**|Hora em que esta política parou de executar.|  
|result|**bit**|Êxito ou falha da política. 0 = Falha, 1 = Êxito.|  
|exception_message|**nvarchar(max)**|Mensagem gerada pela exceção, se houver.|  
|exception|**nvarchar(max)**|Descrição da exceção, se houver.|  
  
## <a name="remarks"></a>Remarks  
 O [syspolicy_policy_execution_history_details](../../relational-databases/system-catalog-views/syspolicy-policy-execution-history-details-transact-sql.md) exibição contém os detalhes relacionados sobre os destinos da política e as expressões de condição testadas.  
  
## <a name="permissions"></a>Permissões  
 Requer a associação à função PolicyAdministratorRole no banco de dados msdb.  
  
## <a name="see-also"></a>Consulte também  
 [Administrar servidores com Gerenciamento Baseado em Políticas](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [Exibições de Gerenciamento Baseado em Políticas &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
