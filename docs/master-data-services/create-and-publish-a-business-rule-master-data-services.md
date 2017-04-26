---
title: "Criar e publicar uma regra de neg&#243;cio (Master Data Services) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "regras de negócio [Master Data Services], criando"
  - "criando regras de negócio [Master Data Services]"
ms.assetid: 6961d636-4d69-468e-81f7-8d0be6a4a039
caps.latest.revision: 14
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 14
---
# Criar e publicar uma regra de neg&#243;cio (Master Data Services)
  No [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], crie uma regra de negócio para garantir a exatidão de seus dados mestres. Depois de ser criada, uma regra deve ser publicada para poder ser aplicada aos dados.  
  
## Pré-requisitos  
 Para executar esse procedimento:  
  
-   Você deve ter permissão para acessar a área funcional **Administração do Sistema** .  
  
-   Você deve ser um administrador de modelo. Para obter mais informações, veja [Administradores &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### Para criar e publicar uma regra de negócio  
  
1.  No [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], clique em **Administração do Sistema**.  
  
2.  Na barra de menus, aponte para **Gerenciar** e clique em **Regras de Negócios**.  
  
3.  Na página **Regra de Negócio**, na lista suspensa **Modelo**, selecione um modelo.  
  
4.  Na lista suspensa **Entidade**, escolha uma entidade.  
  
5.  Na lista suspensa **Tipos de Membro**, selecione um tipo de membro ao qual a regra de negócio será aplicada.  
  
6.  Clique em **Adicionar**.  
  
7.  Na caixa **Nome** , digite um nome para a regra de negócio.  
  
8.  Opcionalmente, no campo **Descrição** , digite a descrição da regra de negócio.  
  
9. Opcionalmente, marque a opção **Enviar Notificações** e, na lista suspensa, selecione um usuário ou grupo ao qual a notificação por email será enviada.  
  
    > [!NOTE]  
    >  Notificações são enviadas somente para regras que incluem uma ação de validação.  
  
10. Sob o bloco **Se** , clique em **Adicionar**. Um painel será exibido.  
  
11. Na lista suspensa **Atributo**, selecione um atributo.  
  
12. Na lista suspensa **Operador**, selecione uma condição.  
  
13. Preencha quaisquer campos obrigatórios.  
  
14. Clique no botão **Salvar** . Uma nova linha será adicionada à grade **Se** .  
  
    > [!TIP]  
    >  Você pode excluir itens da regra de negócio clicando com o botão direito do mouse em cada item e escolhendo **Excluir**.  
  
15. Opcionalmente, adicione várias condições à regra. Para obter mais informações, consulte [Adicionar várias condições a uma regra de negócio &#40;Master Data Services&#41;](../master-data-services/add-multiple-conditions-to-a-business-rule-master-data-services.md).  
  
16. Sob o bloco **Então** , clique em **Adicionar** . Um painel será exibido.  
  
17. Na lista suspensa **Atributo**, selecione um atributo.  
  
18. Na lista suspensa **Operador**, selecione uma ação.  
  
19. Preencha quaisquer campos obrigatórios.  
  
20. Clique em **Salvar**. Uma nova linha será adicionada à grade **Então** .  
  
21. Opcionalmente, para adicionar a ação **Senão** , conclua as etapas a seguir.  
  
    1.  Sob o bloco **Senão** , clique em **Adicionar**. Um painel será exibido.  
  
    2.  Na lista suspensa **Atributo**, selecione um atributo.  
  
    3.  Na lista suspensa **Operador**, selecione uma ação.  
  
    4.  Preencha quaisquer campos obrigatórios.  
  
    5.  Clique em **Salvar**. Uma nova linha será adicionada à grade **Senão** .  
  
22. Clique em **Salvar**. Uma nova linha será adicionada à grade regras de negócio.  
  
23. Clique em **Publicar Tudo**.  
  
24. Na caixa de diálogo de confirmação, clique em **OK**. O valor da coluna **Estado da Regra de Negócio** é **Ativa**.  
  
## Colunas da grade  
 Para cada regra de negócio criada, uma linha com seis colunas é adicionada à grade. A seguir estão as colunas.  
  
|Nome|Description|  
|----------|-----------------|  
|Status|Quando você clica em **Salvar** , a imagem a seguir é exibida indicando que a regra de negócio está sendo atualizada.<br /><br /> ![mds_BR_refresh](../master-data-services/media/mds-br-refresh.png "mds_BR_refresh")<br /><br /> Se houver erros ao criar ou editar uma regra de negócio, a imagem a seguir será exibida.<br /><br /> ![mds_br_error](../master-data-services/media/mds-br-error.png "mds_br_error")<br /><br /> Se o status for OK, a imagem a seguir será exibida.<br /><br /> ![mds_BR_success](../master-data-services/media/mds-br-success.png "mds_BR_success")|  
|Nome|O nome da regra de negócio.|  
|Description|A descrição da regra de negócio.|  
|Estado da Regra de Negócio|Um dos seguintes status de regra de negócio: Regra não definida, Ativa, Excluída, Alterações pendentes, Exclusão pendente e Exclusão pendente.|  
|Excluído|Especifica se a regra de negócio é ou não excluída.|  
|Notification|Especifica o usuário ou grupo selecionado para o qual enviar a notificação por email.|  
  
## Próximas etapas  
  
-   Aplique regras de negócio a dados seguindo um destes procedimentos:  
  
    -   [Validar membros específicos em relação a regras de negócio &#40;Master Data Services&#41;](../master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [Validar uma versão em relação a regras de negócio &#40;Master Data Services&#41;](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
## Consulte também  
 [Configurar regras de negócio para enviar notificações &#40;Master Data Services&#41;](../master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)   
 [Alterar o nome de uma regra de negócio &#40;Master Data Services&#41;](../master-data-services/change-a-business-rule-name-master-data-services.md)   
 [Adicionar várias condições a uma regra de negócio &#40;Master Data Services&#41;](../master-data-services/add-multiple-conditions-to-a-business-rule-master-data-services.md)  
  
  