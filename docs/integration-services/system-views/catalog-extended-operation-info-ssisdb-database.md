---
title: catalog.extended_operation_info (Banco de Dados SSISDB) | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
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
ms.assetid: db299b45-557d-4c62-8e14-355cdb051f63
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: afe4af0fc87a44786e879d1fc86706f30c2e691f
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2018
---
# <a name="catalogextendedoperationinfo-ssisdb-database"></a>catalog.extended_operation_info (Banco de Dados SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Exibe informações estendidas de todas as operações no catálogo do [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|info_id|**bigint**|O identificador exclusivo (ID) da informação estendida.|  
|operation_id|**bigint**|A ID exclusiva da operação que corresponde à informação estendida.|  
|object_name|**nvarchar(260)**|O nome do objeto.|  
|object_type|**smallint**|O tipo de objeto afetado pela operação. O objeto pode ser uma pasta (`10`), um projeto (`20`), um pacote (`30`), um ambiente (`40`) ou uma instância de execução (`50`).|  
|reference_id|**bigint**|A ID exclusiva da referência usada na operação.|  
|status|**int**|O status da operação. Os possíveis valores são criado (`1`), em execução (`2`), cancelado (`3`), com falha (`4`), pendente (`5`), encerrado inesperadamente (`6`), êxito (`7`), parando (`8`) e concluído (`9`).|  
|start_time|**datetimeoffset(7)**|A data e a hora de início da operação.|  
|end_time|**datetimeoffset(7)**|A data e a hora de término da operação.|  
  
## <a name="remarks"></a>Remarks  
 Uma única operação pode ter várias linhas de informações estendidas.  
  
## <a name="permissions"></a>Permissões  
 Esta exibição requer uma das seguintes permissões:  
  
-   Permissão READ na operação  
  
-   Associação à função de banco de dados **ssis_admin**  
  
-   Associação à função de servidor **sysadmin**  
  
> [!NOTE]  
>  Quando você tem permissão para executar uma operação no servidor, também tem permissão para exibir informações sobre a operação. A segurança em nível de linha é imposta; somente as linhas para as quais você tem permissão de exibição são exibidas.  
  
  
