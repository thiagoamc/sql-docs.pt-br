---
title: Configurations (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
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
- sys.configurations_TSQL
- configurations
- sys.configurations
- configurations_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.configurations catalog view
ms.assetid: c4709ed1-bf88-4458-9e98-8e9b78150441
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 38f44fb8d174d3fa32bea9d97e079fce0c3d1afc
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="sysconfigurations-transact-sql"></a>sys.configurations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contém uma linha para cada valor de opção de configuração em todo o servidor no sistema.  
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|**configuration_id**|**int**|Identificação exclusivo do valor de configuração.|  
|**name**|**nvarchar(35)**|O nome da opção de configuração.|  
|**valor**|**sql_variant**|Valor configurado dessa opção.|  
|**minimum**|**sql_variant**|Valor mínimo para a opção de configuração.|  
|**maximum**|**sql_variant**|Valor máximo para a opção de configuração.|  
|**value_in_use**|**sql_variant**|Valor de execução atualmente em efeito dessa opção.|  
|**Descrição**|**nvarchar(255)**|Descrição da opção de configuração.|  
|**is_dynamic**|**bit**|1 = A variável é implementada quando a instrução RECONFIGURE é executada.|  
|**is_advanced**|**bit**|1 = a variável é exibida somente quando o **Mostrar advancedoption** está definido.|  
  
 Para obter uma lista de todas as opções de configuração de servidor, consulte [opções de configuração do servidor &#40; SQL Server &#41; ](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
> [!NOTE]  
>  Opções de configuração de nível de banco de dados, consulte [ALTER DATABASE SCOPED CONFIGURATION &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md). Para configurar o NUMA, consulte [Soft-NUMA &#40; SQL Server &#41; ](../../database-engine/configure-windows/soft-numa-sql-server.md).  
  
## <a name="permissions"></a>Permissões  
 Requer associação à função **pública** . Para obter mais informações, consulte [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Consulte também  
 [Exibições de catálogo de configuração do servidor &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/server-wide-configuration-catalog-views-transact-sql.md)   
 [Exibições de catálogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
