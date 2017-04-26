---
title: "Usu&#225;rios e grupos (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "usuários [Master Data Services]"
  - "grupos [Master Data Services]"
  - "usuários [Master Data Services], sobre usuários"
  - "grupos [Master Data Services], sobre grupos"
ms.assetid: ed08dd2d-248e-4b68-91d4-e9961cb50eed
caps.latest.revision: 8
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 8
---
# Usu&#225;rios e grupos (Master Data Services)
  Para acessar o aplicativo Web do [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], o usuário deve ter uma conta de domínio do Windows ou uma conta no computador servidor em que o [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] está instalado. Para conceder acesso ao [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], você pode:  
  
-   Adicionar a conta de usuário a um domínio ou grupo local e adicionar o grupo à lista de grupos no [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
-   Adicionar a conta de usuário à lista de usuários no [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
    > [!NOTE]  
    >  Quando um usuário pertence a um grupo que tem acesso ao [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], o nome do usuário é adicionado automaticamente à lista de usuários na primeira vez que ele acessa o [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ou o MDS [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)].  
  
 Para executar qualquer ação na área funcional **Explorer** da interface do usuário, o grupo ou usuário deverá ter recebido acesso à área funcional **Explorer** e permissão aos objetos de modelo.  
  
 Se um usuário ou grupo precisar de acesso a outras áreas funcionais, deverá ser atribuído ao usuário ou grupo acesso à área funcional específica.  
  
## Prática recomendada  
 Para simplificar a administração, crie grupos e atribua cada permissão de grupo para áreas funcionais e objetos modelo. Em seguida, você pode adicionar e remover usuários dos grupos sem acessar a interface do usuário do [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
 Não atribua permissões adicionais a um usuário individual e não inclua um usuário em vários grupos que têm acesso ao [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]. Além disso, não use permissões de membro de hierarquia a menos que você deseje que um grupo tenha acesso limitado a membros específicos.  
  
## Consulte também  
 [Adicionar um usuário &#40;Master Data Services&#41;](../master-data-services/add-a-user-master-data-services.md)   
 [Adicionar um grupo &#40;Master Data Services&#41;](../master-data-services/add-a-group-master-data-services.md)   
 [Excluir usuários ou grupos &#40;Master Data Services&#41;](../master-data-services/delete-users-or-groups-master-data-services.md)   
 [Testar permissões de um usuário &#40;Master Data Services&#41;](../master-data-services/test-a-user-s-permissions-master-data-services.md)  
  
  