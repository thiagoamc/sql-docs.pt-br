---
title: dbo.syssessions (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dbo.syssessions_TSQL
- dbo.syssessions
- syssessions_TSQL
- syssessions
dev_langs:
- TSQL
helpviewer_keywords:
- syssessions system table
ms.assetid: 187819b6-c7f4-4a26-b74c-0a89e96695cf
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3099413685b594404a577d71011bb1738b756ac1
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2018
---
# <a name="dbosyssessions-transact-sql"></a>dbo.syssessions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Sempre que é iniciado, o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent cria uma nova sessão. O [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent usa sessões para preservar o status de trabalhos quando serviço do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent é reinicializado ou para inesperadamente. Cada linha do **syssessions** tabela contém informações sobre uma sessão. Use o **sysjobactivity** tabela para exibir o estado do trabalho no final de cada sessão.  
  
 Essa tabela é armazenada no **msdb** banco de dados.  
  
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|**session_id**|**Int**|ID de uma sessão do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.|  
|**agent_start_date**|**datetime**|Data e hora em que o serviço do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent foi iniciado para essa sessão.|  
  
## <a name="remarks"></a>Remarks  
 Somente os usuários que são membros do **sysadmin** função de servidor fixa pode acessar essa tabela.  
  
## <a name="see-also"></a>Consulte também  
 [dbo.sysjobactivity &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysjobactivity-transact-sql.md)  
  
  
