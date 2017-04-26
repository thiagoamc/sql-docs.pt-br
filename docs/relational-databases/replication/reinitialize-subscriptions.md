---
title: "Reinicializar as assinaturas | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "inicializando assinaturas [replicação do SQL Server], reinicializando"
  - "assinaturas [replicação do SQL Server], reinicializando"
  - "reinicializando assinaturas"
ms.assetid: fb13712b-e7ad-4f1f-b605-4554bad0cb60
caps.latest.revision: 51
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 51
---
# Reinicializar as assinaturas
  Reinicializar uma assinatura envolve aplicar um novo instantâneo de um ou mais artigos a um ou mais Assinantes: a replicação transacional e de instantâneo permitem que artigos individuais sejam reinicializados, e a replicação de mesclagem requer que todos os artigos sejam reinicializados. Os nós em uma topologia de replicação transacional ponto a ponto não podem ser reinicializados. Se for necessário assegurar que um nó tenha uma nova cópia dos dados, restaure o backup no nó. A reinicialização ocorre por um ou mais motivos:  
  
-   Marque explicitamente uma assinatura para reinicialização.  
  
-   Execute uma ação, como uma alteração de propriedade, que requeira uma reinicialização. Para obter mais informações sobre as ações que requerem reinicialização, consulte [alterar propriedades da publicação e artigo](../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
 Em ambos os casos, o instantâneo mais recente será aplicado ao Assinante da próxima vez em que o Agente de Distribuição ou o Agente de Mesclagem forem executados. Com relação à replicação de instantâneo e transacional, quando ocorre a reinicialização, todas as alterações feitas no Assinante, mas ainda não sincronizadas com o Publicador, são substituídas pelo aplicativo do novo instantâneo.  
  
 Quanto à replicação de mesclagem, é possível optar por ter todas as alterações de dados carregadas do Assinante antes da aplicação do instantâneo. Todos os esquemas pendentes no Publicador são aplicados ao Assinante e, depois, todas as atualizações feitas no Assinante desde a última sincronização são propagadas para o Publicador, antes da reaplicação do instantâneo. Esse comportamento é controlado pelo **upload_first** e **automatic_reinitialization_policy** Propriedades; para obter mais informações, consulte [reinicializar uma assinatura](../../relational-databases/replication/reinitialize-a-subscription.md). Se você marcar uma assinatura para reinicialização com o SQL Server Management Studio ou o Replication Monitor, você terá uma opção **reinicializar assinaturas** caixa de diálogo para carregar alterações primeiro.  
  
> [!IMPORTANT]  
>  Se você adicionar, descartar ou alterar um filtro com parâmetros em uma publicação de mesclagem, as alterações pendentes no Assinante não poderão ser carregadas no Publicador durante a reinicialização. Para carregar alterações pendentes, sincronize todas as assinaturas antes de alterar o filtro.  
  
 Se estiver especificado que nenhum instantâneo inicial seria aplicado ao Assinante durante a criação da assinatura e, posteriormente, a assinatura for marcada para reinicialização, não se aplicará um instantâneo. Para obter mais informações, consulte [inicializar um transacional assinatura sem um instantâneo](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).  
  
 **Para reinicializar uma assinatura**  
  
 Para reinicializar todos os artigos de uma assinatura, use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], procedimentos armazenados ou RMO (Replication Management Objects). Para reinicializar artigos individuais em publicações transacionais ou de instantâneo, é preciso usar procedimentos armazenados. Para obter mais informações, consulte [reinicializar uma assinatura](../../relational-databases/replication/reinitialize-a-subscription.md).  
  
## Consulte também  
 [Inicializar uma assinatura](../../relational-databases/replication/initialize-a-subscription.md)   
 [Validade e desativação de assinatura](../../relational-databases/replication/subscription-expiration-and-deactivation.md)  
  
  