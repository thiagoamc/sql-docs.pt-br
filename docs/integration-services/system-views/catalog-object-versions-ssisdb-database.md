---
title: Catalog. object_versions (banco de dados SSISDB) | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 2fd8c020-1c77-4702-8e6b-efa6a348daab
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 3ea7c5ae054a002b9bb4f150e60f323ae03d702a
ms.contentlocale: pt-br
ms.lasthandoff: 09/26/2017

---
# <a name="catalogobjectversions-ssisdb-database"></a>catalog.object_versions (Banco de Dados SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Exibe as versões dos objetos do catálogo do [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Nesta versão, apenas versões de projetos têm suporte nesta exibição.  
  
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|object_version_lsn|**bigint**|O ID (identificador exclusivo) da versão do objeto. Não há garantia de que este número seja sequencial.|  
|object_id|**bigint**|A ID exclusiva do objeto.|  
|object_type|**smallint**|O tipo do objeto. Um valor `20` será exibido para projetos.|  
|object_name|**sysname(nvarchar(128))**|O nome do objeto.|  
|descrição|**nvarchar (1024)**|A descrição do projeto.|  
|created_by|**nvarchar (128)**|O nome do usuário que adicionou o objeto ao catálogo.|  
|created_time|**datetimeoffset**|A data e a hora nas quais o objeto foi adicionado ao catálogo.|  
|restored_by|**nvarchar (128)**|O nome do usuário que restaurou o objeto.|  
|last_restored_time|**datetimeoffset**|A data e a hora na qual o objeto foi restaurado pela última vez.|  
  
## <a name="remarks"></a>Comentários  
 Esta exibição mostra uma linha para cada versão de um objeto no catálogo.  
  
## <a name="permissions"></a>Permissões  
 Para consultar linhas nesta exibição, você deve ter uma das permissões a seguir:  
  
-   Permissão READ no objeto  
  
-   Associação de **ssis_admin** função de banco de dados  
  
-   Associação de **sysadmin** função de servidor.  
  
> [!NOTE]  
>  A segurança em nível de linha é imposta; somente as linhas para as quais você tem permissão de exibição são exibidas.  
  
  