---
title: "Replica&#231;&#227;o de monitoramento | Microsoft Docs"
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
  - "monitorando o desempenho [replicação do SQL Server], Replication Monitor"
  - "Replication Monitor, sobre o Replication Monitor"
ms.assetid: 81f596d2-27a5-489d-bf8d-0f4361decd02
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 37
---
# Replica&#231;&#227;o de monitoramento
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Monitor de replicação é uma ferramenta gráfica que permite que você monitore a integridade geral de uma topologia de replicação. O Replication Monitor fornece informações detalhadas sobre o status e o desempenho das publicações e das assinaturas, permitindo responder a perguntas comuns tais como:  
  
-   Meu sistema de replicação está íntegro?  
  
-   Quais assinaturas estão lentas?  
  
-   A minha assinatura transacional está muito atrás na fila?  
  
-   Quanto tempo uma transação confirmada agora, levará para alcançar um Assinante em replicação transacional?  
  
-   Por que minha assinatura de mesclagem está lenta?  
  
-   Por que um agente não está executando?  
  
 Para monitorar a replicação o usuário deve ser membro da função de servidor fixa **sysadmin** no Distribuidor ou membro da função de banco de dados fixa **replmonitor** no banco de dados de distribuição. Um administrador de sistema pode adicionar qualquer usuário à função **replmonitor** , o que permite que o usuário exiba a atividade de replicação no Replication Monitor. No entanto, o usuário não pode administrar a replicação.  
  
## Nesta seção  
 Os tópicos a seguir fornecem mais informações sobre os recursos do Replication Monitor.  
  
 [Visão geral da interface do Replication Monitor](../../../relational-databases/replication/monitor/overview-of-the-replication-monitor-interface.md)  
 Descreve cada janela e guia no Replication Monitor e fornece informações sobre como responder às perguntas listadas anteriormente.  
  
 [Iniciar o Replication Monitor](../../../relational-databases/replication/monitor/start-the-replication-monitor.md)  
 Descreve como iniciar o Replication Monitor.  
  
 [Allow Non-Administrators to Use Replication Monitor](../../../relational-databases/replication/monitor/allow-non-administrators-to-use-replication-monitor.md)  
 Descreve como atribuir permissões a não administradores de forma que eles possam usar o Replication Monitor.  
  
 [Adicionar e remover Publicadores do Replication Monitor](../../../relational-databases/replication/monitor/add-and-remove-publishers-from-replication-monitor.md)  
 Descreve como adicionar ou remover Publicadores do Replication Monitor.  
  
 [Atualizar dados no Replication Monitor](../../../relational-databases/replication/monitor/refresh-data-in-replication-monitor.md)  
 Descreve como atualizar dados no Replication Monitor.  
  
 [Monitorar o desempenho com o Replication Monitor](../../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md)  
 Descreve como monitorar o desempenho no Replication Monitor, inclusive as informações em como definir limiares de desempenho. Inclui informações sobre as estatísticas em nível de artigo para a replicação de mesclagem, as quais fornecem uma visão detalhada do processamento.  
  
 [Measure Latency and Validate Connections for Transactional Replication](../../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
 Descreve os tokens de rastreamento que permitem medir o desempenho de uma topologia de replicação transacional.  
  
 [Monitorar agentes de replicação](../../../relational-databases/replication/monitor/monitor-replication-agents.md)  
 Descreve como localizar informações sobre cada agente de replicação.  
  
 [Set Thresholds and Warnings in Replication Monitor](../../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md)  
 Descreve os avisos, limiares e alertas que você pode definir no Replication Monitor. Recomendamos habilitar os avisos para a sua topologia, para que esteja informado sobre o status e o desempenho de maneira oportuna.  
  
 [Cache, atualização e desempenho do Replication Monitor ](../../../relational-databases/replication/monitor/caching-refresh-and-replication-monitor-performance.md)  
 Descreve como o Replication Monitor armazena os dados em cache para melhorar o desempenho; explica como a atualização da interface de usuário se relaciona à atualização do cache.  
  
 [Exibir o status da publicação e da assinatura no Replication Monitor](../../../relational-databases/replication/monitor/view-publication-and-subscription-status-in-replication-monitor.md)  
 Descreve como exibir informações de status em uma Publicação ou Assinatura usando o Replication Monitor.  
  
 [Exibir informações e executar tarefas para um publicador & #40. Monitor de replicação e 41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publisher-replication-monitor.md)  
 Descreve como exibir informações e executar tarefas para um Publicador usando o Replication Monitor.  
  
 [Exibir informações e executar tarefas para uma publicação e 40; Monitor de replicação e 41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publication-replication-monitor.md)  
 Descreve como exibir informações e executar tarefas para uma publicação usando o Replication Monitor.  
  
 [Exibir informações e executar tarefas para os agentes associados com uma publicação e 40; Monitor de replicação e 41;](../../../relational-databases/replication/monitor/view information and perform tasks for publication agents.md)  
 Descreve como exibir informações e executar tarefas para os agentes associados com uma publicação usando o Replication Monitor.  
  
 [Exibir informações e executar tarefas para uma assinatura & #40. Monitor de replicação e 41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-subscription-replication-monitor.md)  
 Descreve como exibir informações e executar tarefas para uma assinatura usando o Replication Monitor.  
  
 [Exibir informações e executar tarefas para os agentes associados com uma assinatura & #40. Monitor de replicação e 41;](../../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md)  
 Descreve como exibir informações e executar tarefas para os agentes associados com uma assinatura usando o Replication Monitor.  
  
  