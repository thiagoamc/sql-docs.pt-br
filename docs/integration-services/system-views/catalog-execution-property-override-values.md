---
title: catalog.execution_property_override_values | Microsoft Docs
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 83cbdd6f-ddde-47bf-abde-36bd24272621
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f7a126110bfeca6f3822e47f9f7c0e31f3f89952
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2018
---
# <a name="catalogexecutionpropertyoverridevalues"></a>catalog.execution_property_override_values
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Exibe os valores de substituição de propriedade que foram definidos durante a execução do pacote.  
  
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|property_id|**bigint**|ID exclusiva do valor de substituição de propriedade.|  
|execution_id|**bigint**|ID exclusivo da instância de execução.|  
|property_path|**nvarchar(4000)**|O caminho para a propriedade no pacote.|  
|property_value|**nvarchar(max)**|O valor de substituição da propriedade.|  
|sensitive|**bit**|Quando o valor for 1, a propriedade será confidencial e criptografada quando for armazenada. Quando o valor for 0, a propriedade não será confidencial e o valor será armazenado em texto não criptografado.|  
  
## <a name="remarks"></a>Remarks  
 Essa exibição mostra uma linha para cada execução em que os valores de propriedade foram substituídos usando a seção **Substituições de propriedade** na guia **Avançado** da caixa de diálogo **Executar Pacote**. O caminho para a propriedade é derivado da propriedade **Caminho do Pacote** da tarefa de pacote.  
  
## <a name="permissions"></a>Permissões  
 Esta exibição requer uma das seguintes permissões:  
  
-   Permissão READ na instância de execução  
  
-   Associação à função de banco de dados **ssis_admin**  
  
-   Associação à função de servidor **sysadmin**  
  
> [!NOTE]  
>  Quando você tem permissão para executar uma operação no servidor, também tem permissão para exibir informações sobre a operação. A segurança em nível de linha é imposta; somente as linhas para as quais você tem permissão de exibição são exibidas.  
  
  
