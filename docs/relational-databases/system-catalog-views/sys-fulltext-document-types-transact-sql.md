---
title: sys.fulltext_document_types (Transact-SQL) | Microsoft Docs
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
- sys.fulltext_document_types_TSQL
- fulltext_document_types
- fulltext_document_types_TSQL
- sys.fulltext_document_types
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fulltext_document_types catalog view
ms.assetid: 156fcfa4-7304-4a5c-b96f-1c3e061e5df0
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 26a1729aac9094d0b0f150d64772229d7f89c20a
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2018
---
# <a name="sysfulltextdocumenttypes-transact-sql"></a>sys.fulltext_document_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retorna uma linha para cada tipo de documento disponível para operações de indexação de texto completo. Cada linha representa a interface IFilter registrada na instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|**document_type**|**sysname**|A extensão de arquivo do tipo de documento com suporte.<br /><br /> Esse valor pode ser usado para identificar o filtro que será usado durante a indexação de texto completo de colunas do tipo **varbinary (max)** ou **imagem**.|  
|**class_id**|**uniqueidentifier**|GUID da classe IFilter que oferece suporte à extensão de arquivo.|  
|**path**|**nvarchar(260)**|O caminho da DLL de IFilter. O caminho está visível somente para membros da função de servidor fixa **serveradmin** .|  
|**version**|**sysname**|Versão da DLL do IFilter.|  
|**manufacturer**|**sysname**|Nome do fabricante do IFilter.<br /><br /> Observação: Apenas documentos com fabricante como [!INCLUDE[msCoName](../../includes/msconame-md.md)] têm suporte em [!INCLUDE[ssSDS](../../includes/sssds-md.md)].|  
  
## <a name="permissions"></a>Permissões  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Exibições de catálogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
