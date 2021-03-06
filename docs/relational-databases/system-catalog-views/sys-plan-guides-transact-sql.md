---
title: plan_guides (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.planguides_TSQL
- plan_guides
- sys.planguides
- plan_guides_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.plan_guides catalog view
ms.assetid: 3dde0397-ef6f-4b3f-8250-3f25584eb62b
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 591bc781d6c156320dffcb06e6e541aeb5b669a3
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="sysplanguides-transact-sql"></a>sys.plan_guides (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Contém uma linha para cada guia de plano no banco de dados.  
  
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|**plan_guide_id**|**int**|Identificador exclusivo do guia de plano no banco de dados.|  
|**name**|**sysname**|Nome do guia de plano.|  
|**create_date**|**datetime**|Date e hora de criação do guia de plano.|  
|**modify_date**|**Datetime**|Data da última modificação do guia de plano.|  
|**is_disabled**|**bit**|1 = Guia de plano desabilitado.<br /><br /> 0 = Guia de plano habilitado.|  
|**query_text**|**nvarchar(max)**|Texto da consulta na qual o guia de plano é criado.|  
|**scope_type**|**tinyint**|Identifica o escopo do guia de plano.<br /><br /> 1 = OBJECT<br /><br /> 2 = SQL<br /><br /> 3 = TEMPLATE|  
|**scope_type_desc**|**nvarchar (60)**|Descrição do escopo do guia de plano.<br /><br /> OBJECT<br /><br /> SQL<br /><br /> TEMPLATE|  
|**scope_object_id**|**Int**|object_id do objeto que definirá o escopo do guia de plano se o escopo for OBJECT.<br /><br /> NULL se o guia de plano não tiver nenhum escopo para OBJECT.|  
|**scope_batch**|**nvarchar(max)**|Texto em lotes, se **scope_type** é SQL.<br /><br /> NULL se tipo de lote não for SQL.<br /><br /> Se for NULL e **scope_type** SQL, o valor de **query_text** se aplica.|  
|**parâmetros**|**nvarchar(max)**|A cadeia de caracteres que define a lista de parâmetros associada ao guia de plano.<br /><br /> NULL = Nenhuma lista de parâmetros está associada ao guia de plano.|  
|**dicas**|**nvarchar(max)**|Dicas da cláusula OPTION associadas ao guia de plano.|  
  
## <a name="permissions"></a>Permissões  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Para obter mais informações, consulte [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Consulte também  
 [Exibições de catálogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sp_create_plan_guide &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
  
