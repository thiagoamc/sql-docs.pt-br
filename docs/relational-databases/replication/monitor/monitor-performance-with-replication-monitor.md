---
title: "Monitorar o desempenho com o Replication Monitor | Microsoft Docs"
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
  - "Agente de Leitor de Log, monitorando"
  - "Replication Monitor, desempenho"
  - "Agente de Mesclagem, monitorando"
  - "Queue Reader Agent, monitorando"
  - "Agente de Instantâneo, monitorando"
  - "Agente de Distribuição, monitorando"
  - "monitorando o desempenho [replicação do SQL Server]"
ms.assetid: f212397d-1bfd-496b-a246-668952891d09
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 36
---
# Monitorar o desempenho com o Replication Monitor
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] O Replication Monitor permite monitorar o desempenho da replicação transacional e da replicação de mesclagem das seguintes maneiras:  
  
-   Definindo as advertências e os limites  
  
-   Exibindo as medições de desempenho  
  
-   Determinando a latência com os tokens de rastreamento (replicação transacional)  
  
-   Exibindo as estatísticas de sincronização detalhadas (replicação de mesclagem)  
  
-   Exibindo as transações e a hora de entrega (replicação transacional)  
  
## Definir avisos e limites  
 O Replication Monitor permite ativar avisos para várias condições de desempenho. Ao habilitar um aviso, você especifica um limite. Quando esse limite é atingido ou excedido, um aviso é exibido no **Status** coluna para a assinatura e a publicação com a qual ele é sincronizado (a menos que um problema com uma prioridade mais alta precise ser exibido). Além de exibir de um aviso no Replication Monitor, atingir um limite também pode disparar um alerta. Você pode habilitar avisos para as seguintes condições de desempenho:  
  
-   Exceder a latência especificada (o período decorrido entre a confirmação de uma transação no Publicador e a confirmação da transação correspondente no Assinante).  
  
     Isso se aplica à replicação transacional. Se o limite especificado for atingido ou excedido, o status será exibido como **Desempenho crítico**.  
  
-   Excedendo o tempo de sincronização especificado.  
  
     Isso se aplica à replicação de mesclagem. Se o limite especificado for atingido ou excedido, o status é exibido como **mesclagem de execução longa**. Você pode especificar limites diferentes para conexões discadas e Rede local (LAN).  
  
-   Falha no processamento do número especificado de linhas em um determinado período.  
  
     Isso se aplica à replicação de mesclagem. Se o limite especificado for atingido ou excedido, o status será exibido como **Desempenho crítico**. Você pode especificar limites diferentes para conexões discadas e LAN.  
  
 Para obter mais informações, consulte [definir limites e avisos no Replication Monitor](../../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md).  
  
## Exibir as medições de desempenho  
 O Replication Monitor exibe valores de qualidade de desempenho para replicação transacional de replicação e de mesclagem no **desempenho médio atual** e **pior desempenho atual** colunas para publicações e **desempenho** coluna para assinaturas. Os valores são:  
  
-   Excelente  
  
-   Bom  
  
-   Razoável  
  
-   Fraco  
  
-   Crítico (replicação transacional somente)  
  
 Os valores são determinados das seguintes maneiras:  
  
-   Para a replicação transacional, a qualidade de desempenho é determinada pelo limite de latência. Se o limite não for definido, não será exibido um valor. A tabela a seguir mostra a correlação entre o limite e o valor de qualidade de desempenho. Por exemplo, se a latência for selecionada para 60 segundos e a latência real for de 30 segundos, a latência será 50% do limite, resultando em um valor Bom.  
  
    |Excelente|Bom|Razoável|Fraco|Crítico|  
    |---------------|----------|----------|----------|--------------|  
    |0 – 34%|35 – 59%|60 – 84%|85 – 99%|100% +|  
  
-   Para replicação de mesclagem, qualidade de desempenho é independente de qualquer limite (o limite de processamento de linha determina se o valor de **desempenho crítico** é exibido no **Status** coluna). A qualidade de desempenho é determinada comparando-se o desempenho de uma assinatura individual, do desempenho histórico médio de assinaturas, com a publicação que tem o mesmo tipo de conexão (discada ou LAN). O Replication Monitor exibe um valor após a ocorrência de cinco sincronizações com 50 ou mais alterações cada, no mesmo tipo de conexão. Se houver menos de cinco sincronizações com 50 ou mais alterações ou se a sincronização mais recente tiver menos de 50 alterações, o Replication Monitor não exibirá um valor.  
  
     A tabela seguinte mostra a correlação entre o desempenho médio e o valor de qualidade de desempenho. Por exemplo, se dez Assinantes tiverem sincronizado em uma conexão LAN com uma taxa média de 100 linhas por segundo, e uma das assinaturas sincronizar a uma taxa de 125 linhas por segundo, o desempenho da sincronização do Assinante será 125% da média, resultando em um valor Bom.  
  
    |Excelente|Bom|Razoável|Fraco|  
    |---------------|----------|----------|----------|  
    |151+%|76 – 150%|26 – 75%|0 – 25%|  
  
 Para obter mais informações sobre como exibir informações de assinatura, consulte [Exibir informações e executar tarefas para uma assinatura e 40; Monitor de replicação e 41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-subscription-replication-monitor.md).  
  
## Determinar a latência com os tokens de rastreamento  
 A replicação transacional permite medir a latência em um sistema inserindo um token (uma pequena quantidade de dados) no log de transações do banco de dados de publicação e registrando o tempo necessário para chegar até o Distribuidor e os Assinantes. O token permitirá também a identificação de dados que não chegam até o Distribuidor ou Assinante. Para obter mais informações, consulte [medidas latência e validar conexões para replicação transacional](../../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md).  
  
## Exibir o desempenho de sincronização detalhado para replicação de mesclagem  
 Para a replicação de mesclagem, o Replication Monitor exibe as estatísticas detalhadas para cada artigo processado durante a sincronização, incluindo o tempo gasto em cada fase do processamento (carregar alterações, baixar alterações e assim por diante). Ajuda a definir tabelas específicas que estão causando lentidão e é o melhor local para a solução de problemas de desempenho com assinaturas de mesclagem. Para obter mais informações sobre como exibir estatísticas detalhadas, consulte [Exibir informações e executar tarefas para os agentes associados a uma assinatura & #40. Monitor de replicação e 41;](../../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md).  
  
## Exibir as transações e a hora de entrega para replicação transacional  
 Para replicação transacional, o Replication Monitor exibe informações sobre o número de transações no banco de dados de distribuição que ainda não foi distribuído ao Assinante e o tempo estimado para distribuir essas transações. Para obter mais informações, consulte [Exibir informações e executar tarefas para os agentes associados a uma assinatura & #40. Monitor de replicação e 41;](../../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md).  
  
## Consulte também  
 [Replicação de monitoramento](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)   
 [Set Thresholds and Warnings in Replication Monitor](../../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md)  
  
  