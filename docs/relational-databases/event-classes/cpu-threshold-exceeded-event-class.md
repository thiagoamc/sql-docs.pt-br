---
title: "Classe de evento CPU Threshold Exceeded | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Classe de evento CPU Threshold Exceeded"
ms.assetid: eb106f7d-baa3-4a2b-96b2-f9fe0844057d
caps.latest.revision: 15
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 15
---
# Classe de evento CPU Threshold Exceeded
  A classe de evento CPU Threshold Exceeded indica que o Administrador de Recursos detecta uma consulta que excede o limite da CPU especificado para REQUEST_MAX_CPU_TIME_SEC.  
  
> [!NOTE]  
>  O intervalo de detecção para esse evento é cinco segundos. Há garantia de que um evento será gerado se uma consulta exceder o limite especificado em pelo menos cinco segundos. Contudo, se uma consulta exceder o limite especificado em menos de cinco segundos, sua detecção poderá ser perdida, dependendo do controle de tempo da consulta e da hora da última varredura de detecção.  
  
## Colunas de dados de CPU Threshold Exceeded  
  
|Nome da coluna de dados|Tipo de dados|Descrição|ID da coluna|Filtrável|  
|----------------------|---------------|-----------------|---------------|----------------|  
|CPU|**int**|Uso de CPU em milissegundos.|18|Sim|  
|EventClass|**int**|214|27|Não|  
|EventSubClass|**int**|Violação de limite da CPU.|21|Sim|  
|GroupID|**int**|ID do grupo onde a violação ocorreu.|66|Sim|  
|OwnerID|**int**|SPID do processo que causou a violação.|58|Sim|  
|SPID|**int**|ID do processo de servidor que dispara este evento.<br /><br /> Observação: poderá ser diferente do verdadeiro SPID do usuário se um thread de sistema validar o uso da CPU como uma tarefa em segundo plano.|12|Sim|  
|StartTime|**datetime**|A hora em que esse evento foi disparado.|14|Sim|  
  
## Consulte também  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  