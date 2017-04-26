---
title: "Criar um dom&#237;nio vinculado | Microsoft Docs"
ms.custom: ""
ms.date: "11/08/2011"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dqs.kb.linkeddomain.f1"
ms.assetid: fd99d422-c53d-4d7c-9cdd-303c703683b6
caps.latest.revision: 20
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 20
---
# Criar um dom&#237;nio vinculado
  Este tópico descreve como criar um domínio vinculado em uma base de dados de conhecimento no [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). Um domínio vinculado é criado a partir de outro domínio já existente e herda todos os valores, regras e propriedades do domínio ao qual é vinculado, com a exceção do nome e da descrição. Você pode gerenciar um conjunto de domínios vinculados como um. Ao vincular um domínio ao outro, você cria um domínio que herda seu conteúdo de outro domínio.  
  
## Cenários  
 Os domínios vinculados são particularmente úteis nos cenários a seguir.  
  
### Mapeamento de vários campos para domínios que compartilham valores, regras e propriedades  
 Não é possível mapear dois campos para o mesmo domínio, mas você pode mapear um campo para um domínio e depois mapear um segundo campo para um domínio vinculado ao primeiro domínio. Fazer isso mapeará os campos para dois domínios diferentes com o mesmo conteúdo e as mesmas propriedades (exceto o nome e a descrição). Para obter mais informações, consulte [Mapear dois campos para domínios vinculados](#Map).  
  
### Controlando o fluxo de dados para domínios compostos  
 Os domínios vinculados permitem que você controle o fluxo de dados entre campos e entre domínios compostos. Você pode diferenciar quando dados de um campo fluem para um domínio composto e quando dados de outro campo bastante semelhante não fluem para o domínio composto. Você faz isso ao especificar que, de dois domínios vinculados, um faz parte de um domínio composto e outro não faz. De uma perspectiva de domínio, os domínios vinculados são idênticos. Eles contêm o mesmo conhecimento. Entretanto, de uma perspectiva de um domínio composto, os domínios vinculados são diferentes. Um participa do domínio composto, o outro não.  
  
 Um exemplo é um registro que contém os seguintes campos: Nome do Cliente, Sobrenome do Cliente e Nome do Pai. Suponha você mapeie o nome do cliente e o nome do pai para um domínio Nome, e faça com que o domínio Nome e o domínio Sobrenome façam parte de um domínio composto Nome Completo. O problema é que o nome do pai será adicionado ao domínio composto sem um sobrenome. Se, no entanto, você vincular cada um dos dois campos de nome a um domínio, e vincular os dois domínios, então poderá adicionar o domínio Nome do Cliente ao domínio composto Nome Completo e não adicionar o campo Nome do Pai ao domínio composto, impedindo que o Nome do Pai seja adicionado ao domínio composto.  
  
##  <a name="BeforeYouBegin"></a> Antes de começar  
  
###  <a name="Prerequisites"></a> Pré-requisitos  
 Para criar um domínio vinculado, você deve ter uma base de dados de conhecimento e um domínio existente ao qual você deseja vincular.  
  
###  <a name="Security"></a> Segurança  
  
####  <a name="Permissions"></a> Permissões  
 Você deve ter a função dqs_kb_editor ou dqs_administrator no banco de dados DQS_MAIN para criar um domínio vinculado.  
  
##  <a name="Create"></a> Criar um domínio vinculado  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Executar o aplicativo de cliente de qualidade de dados](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Na tela inicial do [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , abra ou crie uma base de dados de conhecimento. Selecione **Gerenciamento de Domínio** como a atividade e, depois, clique em **Abrir** ou **Criar**. Para obter mais informações, consulte [Create a Knowledge Base](../data-quality-services/create-a-knowledge-base.md) ou [Open a Knowledge Base](../data-quality-services/open-a-knowledge-base.md).  
  
3.  Do **lista de domínios** sobre o **gerenciamento de domínio** página, clique no domínio que você deseja vincular um novo domínio e, em seguida, clique em **criar domínio vinculado**.  
  
    > [!NOTE]  
    >  Não há um ícone dedicado à criação de um domínio vinculado. Você só pode fazer isso usando o comando no menu de contexto.  
  
4.  Na caixa de diálogo **Criar Domínio** , insira um nome que seja exclusivo da base de dados de conhecimento e uma descrição de até 256 caracteres. Verifique se o nome do domínio ao qual foi feita a vinculação está correto.  
  
5.  Clique em **OK** para concluir a criação do domínio vinculado.  
  
6.  Se necessário, você pode alterar o nome ou a descrição do domínio vinculado na guia Propriedades do Domínio.  
  
7.  Clique em **Concluir** para concluir a atividade de gerenciamento de domínio, conforme descrito em [End the Domain Management Activity](../Topic/End%20the%20Domain%20Management%20Activity.md).  
  
##  <a name="Map"></a> Mapear dois campos para domínios vinculados  
  
1.  Abra uma base de dados de conhecimento para a atividade de descoberta de conhecimento e mapeie a base de dados de conhecimento para o banco de dados e a tabela ou exibição.  
  
2.  Mapeie um campo para um domínio e então tente mapear um segundo campo para o mesmo domínio.  
  
3.  No pop-up que indica que o domínio já é em uso, clique em Sim para criar um domínio vinculado.  
  
4.  Na caixa de diálogo Criar Domínio, insira um nome de domínio e uma descrição e clique em OK.  
  
##  <a name="FollowUp"></a> Acompanhamento: após a criação de um domínio vinculado  
 Depois que você criar um domínio vinculado, poderá executar outras tarefas de gerenciamento de domínio, poderá executar a descoberta da base de dados de conhecimento para adicionar conhecimento ao domínio ou poderá adicionar uma política de correspondência ao domínio. Para obter mais informações, consulte [executar a descoberta de Conhecimento](../data-quality-services/perform-knowledge-discovery.md), [Gerenciando um domínio](../data-quality-services/managing-a-domain.md), ou [criar uma política de correspondência](../data-quality-services/create-a-matching-policy.md).  
  
##  <a name="Behavior"></a> Comportamento de um domínio vinculado  
 Você pode alterar as configurações de um domínio vinculado desta maneira:  
  
-   Você pode alterar o nome e a descrição de um domínio vinculado.  
  
-   Para alterar as propriedades do domínio para as propriedades **Tipo de Dados**, **Usar Valores Principais**ou **Formatar Saída para** , selecione o domínio que deseja vincular e altere essas configurações na guia **Propriedades do Domínio** desse domínio. Não é possível alterar essas configurações nas propriedades do domínio vinculado. Para obter mais informações, consulte [Create a Domain](../data-quality-services/create-a-domain.md).  
  
-   Configurações de **dados de referência**, **regras de domínio**, **valores de domínio**, e **relações baseadas em termos** guias da página de gerenciamento de domínio podem ser alterados para o domínio vinculado ou o domínio ao qual ele estava vinculado, e as alterações serão herdadas por outro domínio.  
  
 Os domínios vinculados têm as seguintes características:  
  
-   Não é possível desvincular dois domínios. Para remover o link, exclua um dos domínios vinculados.  
  
-   Quando você seleciona um domínio vinculado na lista de domínios da página Gerenciamento de Domínio, a cadeia de caracteres que identifica o domínio vinculado no painel com a tabela **Valor** contém uma indicação de que o domínio é um domínio vinculado.  
  
-   Se você excluir um domínio ao qual outro domínio esteja vinculado, ambos os domínios serão excluídos. Entretanto, você pode excluir um domínio vinculado e o domínio ao qual foi feita a vinculação não serão excluídos.  
  
-   Um domínio vinculado não pode ser vinculado a um domínio que, por sua vez, esteja vinculado a outro domínio.  
  
-   Você não pode criar um domínio vinculado ou um domínio composto vinculado para um domínio composto.  
  
-   Quando você clicar duas vezes em um domínio vinculado em qualquer uma das guias Gerenciamento de Domínio, o domínio estará aberto para edição com uma indicação na cadeia de caracteres de nome que é um domínio vinculado.  
  
  