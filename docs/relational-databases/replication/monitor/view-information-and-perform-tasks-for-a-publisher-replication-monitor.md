---
title: "Exibir informações e executar tarefas para um Publicador (Replication Monitor) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Publishers [SQL Server replication], Replication Monitor tasks
- viewing Publisher information
- Publishers [SQL Server replication], viewing information
ms.assetid: 1e777e95-377a-4de3-b965-867464aadaaf
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6d82b24e92b90f7e4688b9f97746dc40ad94dd1b
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2018
---
# <a name="view-information-and-perform-tasks-for-a-publisher-replication-monitor"></a>Exibir informações e executar tarefas para um Publicador (Replication Monitor)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  O Replication Monitor fornece as seguintes guias que exibem informações sobre o Publicador selecionado:  
  
-   **Publicações**  
  
     Essa guia exibe informações sobre todas as publicações no Publicador selecionado.  
  
-   **Lista de Observação da Assinatura**  
  
     Essa guia destina-se a exibir informações sobre as assinaturas de todas as publicações disponíveis no Publicador selecionado que tenham erros, avisos ou o pior desempenho. Essa guia não é exibida para Distribuidores que executam as versões anteriores do [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
-   Guia**Agentes**   
  
     Essa guia exibe informações detalhadas sobre os agentes e trabalhos usados por todos os tipos de replicação. A guia também permite que você inicie e interrompa cada agente e trabalho.  
  
 Para exibir mais informações sobre as opções de cada guia, clique na guia no painel direito e clique em **Ajuda** na barra de menus. Para obter informações sobre como iniciar o Replication Monitor, consulte [Start the Replication Monitor](../../../relational-databases/replication/monitor/start-the-replication-monitor.md) (Iniciar o Replication Monitor).  
  
### <a name="to-view-information-and-perform-tasks-for-a-publisher"></a>Para exibir informações e executar tarefas para um Publicador  
  
1.  Expanda um Grupo do publicador no painel esquerdo e clique em um Publicador.  
  
2.  Para exibir informações sobre todas as publicações, clique na guia **Publicações** .  
  
3.  Para exibir informações sobre assinaturas, clique na guia **Lista de Observação da Assinatura** . Você também pode acessar informações mais detalhadas e realizar tarefas a partir dessa guia:  
  
    -   Para exibir informações detalhadas sobre o agente associado a uma assinatura, clique com o botão direito do mouse na assinatura e então clique em **Exibir Detalhes**.  
  
    -   Para exibir as propriedades de uma assinatura, clique com o botão direito do mouse na assinatura e então clique em **Propriedades**.  
  
    -   Para sincronizar uma assinatura push, clique com o botão direito do mouse na assinatura, e, depois, clique em **Iniciar Sincronização**.  
  
    -   Para reinicializar uma assinatura, clique com o botão direito do mouse na assinatura, e, depois, clique em **Reinicializar Assinatura**.  
  
4.  Para exibir informações sobre agentes, clique na guia **Agentes** . Você também pode acessar informações mais detalhadas e realizar tarefas nesta guia:  
  
    -   Para exibir informações detalhadas sobre o agente (como mensagens informativas e qualquer mensagem de erro), clique com o botão direito do mouse no agente e então clique em **Exibir Detalhes**.  
  
    -   Para exibir informações detalhadas sobre o trabalho que executa o agente (como o cronograma, detalhes da etapa de trabalho e outras), clique com o botão direito do mouse no agente e então clique em **Propriedades**.  
  
    -   Para gerenciar os perfis do agente, clique com o botão direito do mouse no agente e então clique em **Perfil do Agente**. Para obter mais informações, consulte [Trabalhar com perfis do agente de replicação](../../../relational-databases/replication/agents/work-with-replication-agent-profiles.md).  
  
    -   Para iniciar um agente que não está sendo executado, clique com o botão direito do mouse no agente e então clique em **Iniciar Agente**.  
  
    -   Para interromper um agente que está sendo executado, clique com o botão direito do mouse no agente e então clique em **Interromper Agente**.  
  
## <a name="see-also"></a>Consulte Também  
 [Exibir e modificar propriedades de Publicador e Distribuidor](../../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [Monitorando a Replicação](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  
