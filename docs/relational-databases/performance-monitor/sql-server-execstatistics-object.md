---
title: "SQL Server, objeto ExecStatistics | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SQLServer:ExecStatistics"
  - "objeto ExecStatistics"
ms.assetid: 4f8557a8-345f-4622-a8a5-763a0388ad94
caps.latest.revision: 14
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 14
---
# SQL Server, objeto ExecStatistics
  O objeto **SQLServer:ExecStatistics** do Microsoft SQL Server oferece contadores para o monitoramento de diversas execuções.  
  
 Esta tabela descreve os contadores **Exec Statistics** do SQL Server.  
  
|Contadores Exec Statistics do SQL Server|Descrição|  
|-----------------------------------------|-----------------|  
|**Consulta Distribuída**|Estatísticas referentes à execução de consultas distribuídas.|  
|**Chamadas DTC**|Estatísticas referentes à execução de chamadas DTC.|  
|**Procedimentos Estendidos**|Estatísticas referentes à execução de procedimentos estendidos.|  
|**Chamadas OLEDB**|Estatísticas referentes à execução de chamadas OLEDB.|  
  
 Cada contador no objeto contém as seguintes instâncias:  
  
|Item|Descrição|  
|----------|-----------------|  
|**Tempo médio de execução (ms)**|Tempo médio de execução do tipo de execução selecionado.|  
|**Tempo de execução cumulativo (ms) por segundo**|Tempo de execução agregado, por segundo, do tipo de execução selecionado.|  
|**Execuções em andamento**|Número de execuções em andamento do tipo de execução selecionado.|  
|**Execuções iniciadas por segundo**|Número de execuções iniciadas por segundo, do tipo de execução selecionado.|  
  
## Consulte também  
 [Monitorar o uso de recursos &#40;Monitor do Sistema&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  