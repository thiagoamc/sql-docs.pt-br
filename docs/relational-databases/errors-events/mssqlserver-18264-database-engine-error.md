---
title: MSSQLSERVER_18264 | Microsoft Docs
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
helpviewer_keywords:
- 18264 (Database Engine error)
ms.assetid: 3050fc56-2be5-43cf-916b-50a3ac5f89aa
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5bcae15f84f9bdc33de072f2df2d5acb0cc9b59a
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver18264"></a>MSSQLSERVER_18264
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Detalhes  
  
|||  
|-|-|  
|Nome do produto|Microsoft SQL Server|  
|ID do evento|18264|  
|Origem do evento|MSSQLENGINE|  
|Componente|SQLEngine|  
|Nome simbólico|STRMIO_DBDUMP|  
|Texto da mensagem|Backup do banco de dados efetuado. Banco de dados: %s, data (hora) da criação: %s(%s), páginas despejadas: %d, primeiro LSN: %s, último LSN: %s, número de dispositivos de despejo: %d, informações sobre o dispositivo: (%s). Essa mensagem é apenas informativa. Não é necessária nenhuma ação do usuário.|  
  
## <a name="explanation"></a>Explicação  
Por padrão, todo backup bem-sucedido adiciona essa mensagem informativa ao log de erros do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e ao log de eventos do sistema. Se você faz backup do log de transações com muita frequência, essas mensagens podem se acumular muito rapidamente, resultando em logs de erros imensos que podem dificultar a localização de outras mensagens.  
  
## <a name="user-action"></a>Ação do usuário  
Você pode suprimir essas entradas de log usando o sinalizador de rastreamento [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **3226**. Habilitar o sinalizador de rastreamento é útil quando você executa backups de logs com frequência e se nenhum dos seus scripts depende dessas entradas.  
  
Para obter informações sobre como usar sinalizadores de rastreamento, consulte os Manuais Online do SQL Server.  
  
## <a name="see-also"></a>Consulte também  
[Sinalizadores de rastreamento &#40;Transact-SQL&#41;](~/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)  
  
