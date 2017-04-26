---
title: "Iniciar e interromper um Agente de Replica&#231;&#227;o (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "agentes [replicação do SQL Server], parando"
  - "agentes [replicação do SQL Server], iniciando"
ms.assetid: 97977c4a-8c7c-4a22-9480-69aa812bd1e5
caps.latest.revision: 42
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 42
---
# Iniciar e interromper um Agente de Replica&#231;&#227;o (SQL Server Management Studio)
  Iniciar e parar os agentes de **trabalhos** pasta e o **replicação** pasta [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] e do Replication Monitor. Inicie e pare os seguintes agentes e trabalhos:  
  
-   O Agente de Instantâneo, que é usado por todas as publicações.  
  
-   O Agente de Leitor de Log, que é usado por todas as publicações transacionais.  
  
-   O Agente de Leitor de Fila, que é usado pelas publicações transacionais habilitadas para atualização de assinaturas em fila.  
  
-   O Agente de Distribuição que sincroniza as assinaturas para publicações transacionais e de instantâneo.  
  
-   O Agente de Mesclagem que sincroniza as assinaturas para publicações de mesclagem.  
  
-   Trabalhos de manutenção de replicação.  
  
 Para obter mais informações sobre como iniciar o Merge Agent e o agente de distribuição, consulte [sincronizar uma assinatura Push](../../../relational-databases/replication/synchronize-a-push-subscription.md) e [sincronizar uma assinatura Pull](../../../relational-databases/replication/synchronize-a-pull-subscription.md). Para obter mais informações sobre trabalhos de manutenção, consulte [Executar trabalhos de manutenção de replicação e 40; SQL Server Management Studio e 41;](../../../relational-databases/replication/administration/run-replication-maintenance-jobs-sql-server-management-studio.md).  
  
 Para obter informações sobre como iniciar o Monitor de replicação, consulte [Iniciar o Replication Monitor](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
### Para iniciar e parar um Agente de Instantâneo ou Agente de Leitor de Log a partir do Management Studio  
  
1.  Conectar-se ao publicador no [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], e, em seguida, expanda o nó do servidor e o **replicação** pasta.  
  
2.  Expanda o **publicações locais** pasta e, em seguida, clique com botão direito uma publicação.  
  
3.  Clique em **Exibir o Status do Snapshot Agent** ou **Exibir o Status do Log Reader Agent**.  
  
4.  Clique em **Iniciar** ou **Parar**.  
  
### Para iniciar e parar um Agente de Leitor de Fila a partir do Management Studio  
  
1.  Conecte-se ao Distribuidor no [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]e, em seguida, expanda o nó do servidor.  
  
2.  Expanda a pasta **SQL Server Agent** e, em seguida, a pasta **Trabalhos** .  
  
3.  Clique no trabalho para o agente e, em seguida, clique em **Iniciar trabalho** ou **Parar trabalho**. O nome do trabalho para o Queue Reader Agent está na forma **[\< distribuidor>]. \< inteiro>**.  
  
### Para iniciar e parar um Agente de Instantâneo, Agente de Leitor de Log ou Agente de Leitor de Fila a partir do Replication Monitor  
  
1.  Expanda um Grupo do publicador no painel esquerdo, expanda um Publicador e clique em uma publicação.  
  
2.  Clique na guia **Agentes** .  
  
3.  Clique com botão direito um agente e, em seguida, clique em **Iniciar agente** ou **Parar agente**.  
  
## Consulte também  
 [Replicação de monitoramento](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)   
 [Conceitos dos executáveis do Replication Agent](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)   
 [Visão geral dos agentes de replicação.](../../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  