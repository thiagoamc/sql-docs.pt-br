---
title: SQL Server Agent, objeto Trabalhos | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLAgent:Jobs
- Jobs object
ms.assetid: 225b5e2d-4a78-4178-b2b6-b419df83c4aa
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f372eced96ca17d4fd547a11a56cfefd732394b9
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/18/2018
---
# <a name="sql-server-agent-jobs-object"></a>SQL Server Agent, objeto Jobs
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] O objeto de desempenho **Jobs** do SQL Server Agent contém contadores de desempenho que relatam informações sobre trabalhos do SQL Server Agent. A tabela a seguir lista os contadores contidos nesse objeto.  
  
 A tabela abaixo contém os contadores **SQLAgent:Jobs** .  
  
|Nome|Description|  
|----------|-----------------|  
|**Trabalhos Ativos**|Este contador informa o número de trabalhos atualmente em execução.|  
|**Trabalhos com falha**|Este contador informa o número de trabalhos que falharam.|  
|**Taxa de êxito de trabalhos**|Este contador informa a porcentagem de trabalhos executados que foram concluídos com êxito.|  
|**Trabalhos ativados/minuto**|Este contador informa o número de trabalhos iniciados no último minuto.|  
|**Trabalhos em fila**|Este contador informa o número de trabalhos prontos para execução pelo SQL Server Agent, mas que ainda não foram iniciados.|  
|**Trabalhos bem-sucedidos**|Este contador informa o número de trabalhos que obtiveram êxito.|  
  
 Cada contador no objeto contém as seguintes instâncias:  
  
|Instância|Description|  
|--------------|-----------------|  
|**_Total**|Informações referentes a todos os trabalhos.|  
|**Alertas**|Informações sobre trabalhos iniciados por alertas.|  
|**Others**|Informações sobre trabalhos que não foram iniciados nem por alertas, nem por agendas. Normalmente, trata-se de trabalhos iniciados manualmente usando **sp_start_job**.|  
|**Agendas**|Informações sobre trabalhos iniciados por agendas.|  
  
## <a name="see-also"></a>Consulte Também  
 [Implementar trabalhos](http://msdn.microsoft.com/library/69e06724-25c7-4fb3-8a5b-3d4596f21756)   
 [Usar objetos de desempenho](http://msdn.microsoft.com/library/830b843a-6b2a-4620-a51b-98358e9fc54b)   
 [Monitorar o uso de recursos &#40;Monitor do Sistema&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
