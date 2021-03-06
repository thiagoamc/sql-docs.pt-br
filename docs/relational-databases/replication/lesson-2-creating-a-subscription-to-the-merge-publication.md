---
title: "Lição 2: Criando uma assinatura na publicação de mesclagem | Microsoft Docs"
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
ms.assetid: 06722baa-9065-443e-b1d5-99036cf89074
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ff899aa93ddedd959cdbe70a0a292752d851c92b
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2018
---
# <a name="lesson-2-creating-a-subscription-to-the-merge-publication"></a>Lição 2: Criando uma assinatura na publicação de mesclagem
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Nesta lição, você criará uma assinatura usando o [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Em seguida, definirá permissões no banco de dados da assinatura e gerará manualmente o instantâneo de dados filtrados para a nova assinatura. Esta lição exige que você tenha concluído a lição anterior, [Lição 1: Publicando dados usando a replicação de mesclagem](../../relational-databases/replication/lesson-1-publishing-data-using-merge-replication.md).  
  
### <a name="to-create-the-subscription"></a>Para criar a assinatura  
  
1.  Conecte-se ao Assinante no [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expanda o nó de servidor, expanda a pasta **Replicação** , clique com o botão direito do mouse na pasta **Assinaturas Locais** e clique em **Novas Assinaturas**.  
  
    O Assistente para Nova Assinatura é iniciado.  
  
2.  Na página **Publicação** , clique em **Encontrar Publicador SQL Server** na lista **Publicador** .  
  
3.  Na caixa de diálogo **Conectar ao Servidor** , insira o nome da instância do Publicador na caixa **Nome do servidor** e clique em **Conectar**.  
  
4.  Clique em **AdvWorksSalesOrdersMerge**e em **Avançar**.  
  
5.  Na página Local do Agente de Mesclagem, clique em **Executar cada agente em seu Assinante**e em **Avançar**.  
  
6.  Na página Assinantes, selecione o nome da instância do servidor Assinante e, em **Banco de Dados de Assinatura**, selecione **<New Database>** na lista.  
  
7.  Na caixa de diálogo **Novo Banco de Dados** , insira **SalesOrdersReplica** na caixa **Nome do banco de dados** , clique em **OK**e em **Avançar**.  
  
8.  Na página Segurança do Agente de Mesclagem, clique no botão de reticências (**…**), insira \<*Machine_Name>***\repl_merge** na caixa **Conta de processo** e forneça a senha dessa conta. Em seguida, clique em **OK**, em **Avançar** e, em seguida, **Avançar** novamente.  
  
9. Na página Inicializar Assinaturas, selecione **Na primeira sincronização** na lista **Inicializar Quando** , clique em **Avançar**e em **Avançar** novamente.  
  
10. Na página Valores de HOST_NAME, insira um valor de **adventure-works\pamela0** na caixa **Valor de HOST_NAME** e clique em **Concluir**.  
  
11. Clique em **Concluir** novamente. Após a criação da assinatura, clique em **Fechar**.  
  
### <a name="setting-database-permissions-at-the-subscriber"></a>Definindo permissões de banco de dados no Assinante  
  
1.  Conecte-se ao Assinante no [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expanda **Bancos de Dados**, **SalesOrdersReplica**e **Segurança**, clique com o botão direito do mouse em **Usuários**e selecione **Novo Usuário**.  
  
2.  Na página **Geral**, insira \<*Machine_Name>***\repl_merge** na caixa **Nome de usuário**, clique no botão de reticências (**…**); clique em **Procurar**, selecione \<*Machine_Name>***\repl_merge**. Em seguida, clique em **OK**, em **Verificar Nomes** e, em seguida, em **OK**.  
  
3.  Em **Associação à função do banco de dados**, selecione **db_owner**e clique em **OK** para criar o usuário.  
  
### <a name="to-create-the-filtered-data-snapshot-for-the-subscription"></a>Para criar o instantâneo de dados filtrados para a assinatura  
  
1.  Conecte-se ao Publicador no [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expanda o nó do servidor e depois expanda a pasta **Replicação** .  
  
2.  Na pasta **Publicações Locais** , clique com o botão direito do mouse na publicação **AdvWorksSalesOrdersMerge** e clique em **Propriedades**.  
  
    A caixa de diálogo **Propriedades da Publicação** é exibida.  
  
3.  Selecione a página **Partições de Dados** e clique em **Adicionar**.  
  
4.  Na caixa de diálogo **Adicionar Partição de Dados** , digite **adventure-works\pamela0** na caixa **Valor de HOST_NAME** e clique em **OK**.  
  
5.  Selecione a partição recém-adicionada, clique em **Gerar os instantâneos selecionados agora**e em **OK**.  
  
## <a name="next-steps"></a>Next Steps  
Você criou com êxito uma assinatura para a publicação mesclada e gerou o instantâneo filtrado para a partição de dados da nova assinatura, de modo que ele esteja disponível no momento da inicialização das assinaturas. Em seguida, conceda direitos ao Merge Agent no banco de dados de assinatura e execute o Merge Agent para iniciar a sincronização e iniciar a assinatura. Consulte [Lição 3: Sincronizando a assinatura com a publicação de mesclagem](../../relational-databases/replication/lesson-3-synchronizing-the-subscription-to-the-merge-publication.md).  
  
## <a name="see-also"></a>Consulte Também  
[Assinar publicações](../../relational-databases/replication/subscribe-to-publications.md)  
[Criar uma assinatura pull](../../relational-databases/replication/create-a-pull-subscription.md)  
[Instantâneos para publicações de mesclagem com filtros com parâmetros](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md)  
  
