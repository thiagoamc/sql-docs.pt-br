---
title: syspolicy_policy_execution_history_details (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 08/09/2016
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
- syspolicy_policy_execution_history_details
- syspolicy_policy_execution_history_details_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- syspolicy_policy_execution_history_details view
ms.assetid: 97ef6573-5e8b-4ba5-8ae0-7901e79a9683
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f560563cb2f558a55d9aeafd1e8a9d6071dfffb6
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2018
---
# <a name="syspolicypolicyexecutionhistorydetails-transact-sql"></a>syspolicy_policy_execution_history_details (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Exibe as expressões de condição que foram executadas as políticas, os destinos das expressões, o resultado de cada execução e os detalhes sobre erros, se houver. A tabela a seguir descreve as colunas na exibição  syspolicy_execution_history_details.  
  
  
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|detail_id|**bigint**|Identificador deste registro. Cada registro representa a tentativa para avaliar ou obrigar uma expressão de condição em uma política. Se aplicado a vários destinos, cada condição terá um registro de detalhe para cada destino.|  
|history_id|**bigint**|Identificador do evento de histórico. Cada evento de histórico representa um tentativa para executar uma política. Como uma condição pode ter várias expressões de condição e vários destinos, um history_id pode criar vários registros de detalhe. Use a coluna history_id para unir esta exibição para o [syspolicy_policy_execution_history](../../relational-databases/system-catalog-views/syspolicy-policy-execution-history-transact-sql.md) exibição.|  
|target_query_expression|**nvarchar(max)**|Destino da política e da exibição syspolicy_policy_execution_history.|  
|execution_date|**datetime**|Data e hora em que este registro de detalhe foi criado.|  
|result|**bit**|Êxito ou falha deste destino e a avaliação de expressão de condição:<br /><br /> 0 (êxito) ou 1 (falha).|  
|result_detail|**nvarchar(max)**|Mensagem resultante. Só disponível se fornecido pela faceta.|  
|exception_message|**nvarchar(max)**|Mensagem gerada pela exceção, se houver.|  
|exception|**nvarchar(max)**|Descrição da exceção, se houver.|  
  
## <a name="remarks"></a>Remarks  
 Quando você estiver solucionando problemas de Gerenciamento Baseado em Políticas, consulte a exibição syspolicy_policy_execution_history_details para determinar qual destino e quais combinações de expressão de condição falharam, quando a falha ocorreu e para revisar os erros relatados.  
  
 A consulta a seguir combina a exibição `syspolicy_policy_execution_history_details` com as exibições `syspolicy_policy_execution_history_details` e `syspolicy_policies` para exibir o nome da política, o nome da condição e os detalhes das falhas.  
  
```  
SELECT Pol.name AS Policy,   
Cond.name AS Condition,   
PolHistDet.target_query_expression,   
PolHistDet.execution_date,   
PolHistDet.result,   
PolHistDet.result_detail,   
PolHistDet.exception_message,   
PolHistDet.exception   
FROM msdb.dbo.syspolicy_policies AS Pol  
JOIN msdb.dbo.syspolicy_conditions AS Cond  
    ON Pol.condition_id = Cond.condition_id  
JOIN msdb.dbo.syspolicy_policy_execution_history AS PolHist  
    ON Pol.policy_id = PolHist.policy_id  
JOIN msdb.dbo.syspolicy_policy_execution_history_details AS PolHistDet  
    ON PolHist.history_id = PolHistDet.history_id  
WHERE PolHistDet.result = 0 ;  
```  
  
## <a name="permissions"></a>Permissões  
 Requer a associação à função PolicyAdministratorRole no banco de dados msdb.  
  
## <a name="see-also"></a>Consulte também  
 [Administrar servidores com Gerenciamento Baseado em Políticas](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [Exibições de Gerenciamento Baseado em Políticas &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
