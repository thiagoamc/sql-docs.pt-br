---
title: MSSQLSERVER_125 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- "125"
helpviewer_keywords:
- 125 (Database Engine error)
ms.assetid: 0f58338d-2ea0-48b8-8a20-c438b0940433
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a13add2226c9a54b0b888d1f292ffb2f7b43c27b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver125"></a>MSSQLSERVER_125
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Detalhes  
  
|||  
|-|-|  
|Nome do produto|SQL Server|  
|ID do evento|125|  
|Origem do evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbólico||  
|Texto da mensagem|As expressões Case só podem ser aninhadas no nível %d.|  
  
## <a name="explanation"></a>Explicação  
O [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] permite apenas 10 níveis de aninhamento em expressões CASE.  
  
## <a name="user-action"></a>Ação do usuário  
Reduza o nível de instruções CASE instruções para 10 ou menos.  
  
## <a name="see-also"></a>Consulte também  
[CASE &#40;Transact-SQL&#41;](~/t-sql/language-elements/case-transact-sql.md)  
  
