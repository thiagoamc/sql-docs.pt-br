---
title: managed_backup.fn_get_current_xevent_settings (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- fn_get_current_xevent_settings
- smart_admin.fn_get_current_xevent_settings_TSQL
- fn_get_current_xevent_settings_TSQL
- smart_admin.fn_get_current_xevent_settings
dev_langs:
- TSQL
helpviewer_keywords:
- smart_admin.fn_get_current_xevent_settings
- fn_get_current_xevent_settings
ms.assetid: 95d3adaa-bb9d-4833-b8b4-3d9fd4f9c82a
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4884f807d77ded37acc60ef6a6591420efe8af34
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2018
---
# <a name="managedbackupfngetcurrentxeventsettings-transact-sql"></a>managed_backup.fn_get_current_xevent_settings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Retorna 1 linha para cada tipo de Evento Estendido com suporte no Administrador Inteligente.  
  
 Use esta função para retornar ou examinar as configurações atuais do Evento Estendido para identificar o tipo de eventos que são configuráveis e as configurações atuais.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Convenções da sintaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```sql  
smart_admin.fn_get_current_xevent_settings ()   
```  
  
##  <a name="Arguments"></a> Argumentos  
 Essa função não tem nenhum argumento.  
  
## <a name="table-returned"></a>Tabela retornada  
 A administração, as análises e os canais operacionais dos Eventos Estendidos são necessários, habilitados por padrão e não são configuráveis.  
  
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|Event_name|NVARCHAR(128)|Tipo de eventos estendidos|  
|is_configurable|NVARCHAR(128)|Isso é definido como **True** se o evento for configurável, caso contrário ele definido como **False**.|  
|is_enabled|NVARCHAR(128)|Isso será definido como True se o evento estiver habilitado; defina como False se não estiver habilitado. Use o smart_admin.sp_set_parameter para habilitar eventos de depuração.|  
  
## <a name="security"></a>Segurança  
  
### <a name="permissions"></a>Permissões  
 Requer **selecione** permissões na função.  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir retorna todos os Eventos Estendidos com seu status atual.  
  
```  
SELECT *   
FROM smart_admin.fn_get_current_xevent_settings ()  
  
```  
  
  
