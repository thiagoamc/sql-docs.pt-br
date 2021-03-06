---
title: "Lição 1: Publicando dados que usam a replicação transacional | Microsoft Docs"
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
ms.assetid: 9c55aa3c-4664-41fc-943f-e817c31aad5e
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 6ca922b7ea63781a337f32108e8165d64cb9e0c0
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2018
---
# <a name="lesson-1-publishing-data-using-transactional-replication"></a>Lição 1: publicando dados que usam replicação transacional
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Nesta lição, você aprenderá a criar uma publicação transacional usando o [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] para publicar um subconjunto filtrado da tabela **Produto** no banco de dados de exemplo do [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . Você também adicionará o logon do SQL Server usado pelo Distribution Agent à PAL (lista de acesso à publicação). Antes de iniciar este tutorial, você deverá ter completado o tutorial anterior, [Preparando o servidor para replicação](../../relational-databases/replication/tutorial-preparing-the-server-for-replication.md).  
  
### <a name="to-create-a-publication-and-define-articles"></a>Para criar uma publicação e definir artigos  
  
1.  Conecte-se ao Publicador no [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]e expanda o nó de servidor.  
  
2.  Expanda a pasta **Replicação** , clique com o botão direito do mouse na pasta **Publicações Locais** e clique em **Nova Publicação**.  
  
    O Assistente de Configuração de Publicação é inicializado.  
  
3.  Na página Banco de Dados de Publicação, selecione [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]e clique em **Avançar**.  
  
4.  Na página Tipo de Publicação, selecione **Publicação transacional**e clique em **Avançar**.  
  
5.  Na página Artigos, expanda o nó **Tabelas** , selecione a caixa de seleção **Produto** , expanda **Produto** e desmarque as caixas de seleção **ListPrice** e **StandardCost** . Clique em **Avançar**.  
  
6.  Na página Filtrar Linhas da Tabela, clique em **Adicionar**.  
  
7.  Na caixa de diálogo **Adicionar Filtro** , clique na coluna **SafetyStockLevel** , clique na seta para a direita para adicionar a coluna à cláusula WHERE da instrução de Filtro da consulta de filtro e modifique a cláusula WHERE da seguinte maneira:  
  
    ```  
    WHERE [SafetyStockLevel] < 500  
    ```  
  
8.  Clique em **OK**e em **Avançar**.  
  
9. Marque a caixa de seleção **Criar um instantâneo imediatamente e mantê-lo disponível para inicializar assinaturas** e clique em **Avançar**.  
  
10. Na página Segurança do Agente, desmarque a caixa de seleção **Usar as configurações de segurança do Agente de Instantâneo** .  
  
11. Clique em **Configurações de Segurança** do Agente de Instantâneo, insira \<*Machine_Name>***\repl_snapshot** na caixa **Conta de processo**, forneça a senha dessa conta e, em seguida, clique em **OK**.  
  
12. Repita a etapa anterior para configurar repl_logreader como a conta de processo do Agente de Leitor de Log e clique em **Concluir**.  
  
13. Na página Concluir o Assistente, digite **AdvWorksProductTrans** na caixa **Nome da publicação** e clique em **Concluir**.  
  
14. Depois que a publicação for criada, clique em **Fechar** para concluir o assistente.  
  
### <a name="to-view-the-status-of-snapshot-generation"></a>Para exibir o status de geração do instantâneo  
  
1.  Conecte-se ao Publicador no [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expanda o nó do servidor e depois expanda a pasta **Replicação** .  
  
2.  Na pasta **Publicações Locais** , clique com o botão direito do mouse em **AdvWorksProductTrans**e clique em **Exibir Status do Agente de Instantâneo**.  
  
3.  O status atual do trabalho do Snapshot Agent para a publicação é exibido. Verifique se o trabalho de instantâneo teve êxito antes de continuar à próxima lição.  
  
### <a name="to-add-the-distribution-agent-login-to-the-pal"></a>Para adicionar o logon Distribution Agent à PAL  
  
1.  Conecte-se ao Publicador no [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expanda o nó do servidor e depois expanda a pasta **Replicação** .  
  
2.  Na pasta **Publicações Locais** , clique com o botão direito do mouse em **AdvWorksProductTrans**e clique em **Propriedades**.  
  
    A caixa de diálogo **Propriedades da Publicação** é exibida.  
  
3.  Selecione a página **Lista de Acesso à Publicação** e clique em **Adicionar**.  
  
4.  Na caixa de diálogo **Adicionar Acesso à Publicação**, selecione *<Machine_Name>***\repl_distribution** e clique em **OK**. Clique em **OK**.  
  
## <a name="next-steps"></a>Next Steps  
Você criou a publicação transacional com êxito. A seguir, você assinará essa publicação. Consulte [Lição 2: Criando uma assinatura na publicação transacional](../../relational-databases/replication/lesson-2-creating-a-subscription-to-the-transactional-publication.md).  
  
## <a name="see-also"></a>Consulte Também  
[Filtrar dados publicados](../../relational-databases/replication/publish/filter-published-data.md)  
[Defina um Artigo](../../relational-databases/replication/publish/define-an-article.md)  
[Criar e aplicar o instantâneo](../../relational-databases/replication/create-and-apply-the-snapshot.md)  
  
  
  
