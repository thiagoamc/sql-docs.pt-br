---
title: "Lição 3: Validando a assinatura e medindo a latência | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
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
applies_to:
- SQL Server 2016
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 147f7b93-1804-4e0b-9e17-57a51d035b2a
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9ad3fadb0017628fa54a102366f132bbc72b9cfb
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2018
---
# <a name="lesson-3-validating-the-subscription-and-measuring-latency"></a>Lição 3: Validando a assinatura e medindo a latência
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Nesta lição, você usará tokens de rastreadores para verificar se as alterações estão sendo replicadas para o Assinante e para determinar: a latência, o tempo decorrido entre o momento em que a alteração é feita no Publicador, e o momento em que ela aparece no Assinante. Esta lição exige que você tenha concluído a lição anterior, [Lição 2: Criando uma assinatura na publicação transacional](../../relational-databases/replication/lesson-2-creating-a-subscription-to-the-transactional-publication.md).  
  
### <a name="to-insert-a-tracer-token-and-view-information-on-the-token"></a>Para inserir um token de rastreamento e exibir informações sobre o token  
  
1.  Conecte-se ao Publicador no [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expanda o nó de servidor, clique com o botão direito do mouse na pasta **Replicação** e clique em **Iniciar o Replication Monitor**.  
  
    O Replication Monitor é iniciado.  
  
2.  Expanda um grupo Publicador no painel esquerdo; expanda a instância do Publicador e, depois, clique na publicação **AdvWorksProductTrans** .  
  
3.  Clique na guia **Tokens de Rastreamento** .  
  
4.  Clique em **Inserir Rastreador**.  
  
5.  Exiba o tempo decorrido para o token de rastreamento nas seguintes colunas: **Publicador para Distribuidor**, **Distribuidor para Assinante**, **Latência Total**. Um valor de **Pendente** indica que o token não alcançou um determinado ponto.  
  
## <a name="next-steps"></a>Next Steps  
Nessa lição, você usou tokens de rastreador com êxito, para validar que as alterações de dados sejam replicadas do Publicador para o Assinante. É igualmente possível inserir, atualizar ou excluir dados da tabela **Product** do Publicador e consultar a tabela **Product** do Assinante para exibir essas alterações após serem replicadas.  
  
Isso encerra o tutorial Replicando Dados entre Servidores Conectados Continuamente Para obter um tutorial semelhante, que utilize replicação de mesclagem, consulte [Tutorial: Replicating Data with Mobile Clients](../../relational-databases/replication/tutorial-replicating-data-with-mobile-clients.md).  
  
## <a name="see-also"></a>Consulte Também  
[Measure Latency and Validate Connections for Transactional Replication](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
  
  
