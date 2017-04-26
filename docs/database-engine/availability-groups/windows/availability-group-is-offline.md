---
title: "O grupo de disponibilidade est&#225; offline | Microsoft Docs"
ms.custom: ""
ms.date: "05/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.agdashboard.agp2online.issues.f1"
helpviewer_keywords: 
  - "Grupos de disponibilidade [SQL Server], políticas"
ms.assetid: 093c5208-bf7a-49f4-a546-72b48197cadf
caps.latest.revision: 14
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 14
---
# O grupo de disponibilidade est&#225; offline
    
## Introdução  
  
|||  
|-|-|  
|**Nome da Política**|Estado Online do Grupo de Disponibilidade|  
|**Problema**|O grupo de disponibilidade está offline.|  
|**Categoria**|**Crítico**|  
|**Faceta**|Grupo de disponibilidade|  
  
## Descrição  
 Esta política verifica o estado online ou offline do grupo de disponibilidade. A política estará em estado não íntegro e um alerta será emitido quando o recurso de cluster do grupo de disponibilidade estiver offline ou o grupo de disponibilidade não tiver uma réplica primária.  
  
 O estado da política será íntegro quando o recurso de cluster do grupo de disponibilidade estiver online e o grupo de disponibilidade tiver uma réplica primária.  
  
> [!NOTE]  
>  Para esta versão do [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], as informações sobre possíveis causas e soluções estão localizadas em [O grupo de disponibilidade está offline](http://go.microsoft.com/fwlink/p/?LinkId=220850) no TechNet Wiki.  
  
## Causas possíveis  
 Esse problema pode ser causado por uma falha na instância de servidor que hospeda a réplica primária ou pelo recurso de grupo de disponibilidade WSFC (Windows Server Failover Cluster) que entra offline. Estas são as possíveis causas do grupo de disponibilidade estar offline:  
  
-   O grupo de disponibilidade não está configurado com o modo de failover automático. A réplica primária torna-se indisponível e a função de todas as réplicas do grupo de disponibilidade torna-se RESOLVING.  
  
    -   O serviço de instância de réplica primária está inativo ou não respondendo.  
  
    -   O grupo de disponibilidade tem um problema de conectividade com o cluster.  
  
-   O grupo de disponibilidade está configurado com o modo de failover automático e não é concluído com êxito.  
  
    -   Durante o failover automático, a verificação de prontidão primária na réplica de destino falha e não há réplica disponível para se tornar a nova primária.  
  
-   O recurso de grupo de disponibilidade no cluster fica offline.  
  
    -   Qualquer recurso de cluster dependente encontra um problema crítico e se torna offline. O recurso de grupo de disponibilidade também permanece offline até que o recurso dependente ficar online.  
  
    -   Um problema crítico no cluster desativa o recurso de grupo de disponibilidade.  
  
-   Há um failover automático, manual ou forçado em andamento para o grupo de disponibilidade.  
  
## Soluções possíveis  
 Estas são as possíveis soluções para este problema:  
  
-   Se a instância do SQL Server da réplica primária estiver inativa, reinicie o servidor e verifique se o grupo de disponibilidade recupera o estado íntegro.  
  
-   Se o failover automático parece ter falhado, verifique se os bancos de dados da réplica estão sincronizados com a réplica primária previamente conhecida, e execute o failover da réplica primária. Se os bancos de dados não estiverem sincronizados, selecione uma réplica com perda mínima de dados e recupere no modo de failover.  
  
-   Se o recurso no cluster estiver offline enquanto as instâncias do SQL Server parecerem íntegras, use o Gerenciador de Cluster de Failover para verificar a integridade do cluster ou outros problemas no cluster do servidor. Você também pode usar o Gerenciador de Cluster de Failover para tentar colocar o recurso de grupo de disponibilidade online.  
  
-   Se houver um failover em andamento, aguarde a conclusão do failover.  
  
## Consulte também  
 [Visão geral dos grupos de disponibilidade AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Usar o Painel AlwaysOn &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  