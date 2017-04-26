---
title: "Excluir um membro ou uma cole&#231;&#227;o (Master Data Services) | Microsoft Docs"
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
  - "coleções [Master Data Services], excluindo"
  - "membros folha [Master Data Services], excluindo"
  - "excluindo membros [Master Data Services]"
  - "membros [Master Data Services], excluindo"
  - "membros consolidados [Master Data Services], excluindo"
ms.assetid: 519130a7-4226-4d71-9124-d2ee0ce7e5bd
caps.latest.revision: 10
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 10
---
# Excluir um membro ou uma cole&#231;&#227;o (Master Data Services)
  No [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], exclua um membro ou coleção quando não precisar mais dele. Se você quiser excluir membros em massa, use as tabelas de preparo. Para obter mais informações, consulte [Importar dados de tabelas &#40;Master Data Services&#41;](../master-data-services/import-data-from-tables-master-data-services.md)  
  
> [!NOTE]  
>  Você não poderá excluir um membro se ele for usado como um valor de atributo baseado em domínio de outro membro.  
  
## Pré-requisitos  
 Para executar esse procedimento:  
  
-   Você deve ter permissão para acessar a área funcional do **Gerenciador** .  
  
-   Para membros, você deve ter, no mínimo, a permissão **Excluir** para o objeto modelo de folha de onde está excluindo um membro.  
  
-   Para coleções, você deve ter, no mínimo, a permissão de **Atualizar** para o objeto da coleção de folhas que você está excluindo.  
  
### Para excluir um membro ou uma coleção  
  
1.  Na página inicial do [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , na lista **Modelo** , selecione um modelo.  
  
2.  Na lista **Versão** , selecione uma versão.  
  
3.  Clique em **Gerenciador**.  
  
4.  Para excluir:  
  
    -   Um membro folha, na barra de menus, aponte para **Entidades** e clique no nome da entidade que contém o membro.  
  
    -   Um membro consolidado, na barra de menus, aponte para **Hierarquias** e clique no nome da hierarquia que contém o membro. Em seguida, o nó na hierarquia que contém o membro.  
  
    -   Uma coleção, na barra de menus, aponte para **Coleções** e clique no nome da entidade que contém a coleção.  
  
5.  Na grade, clique na linha do membro ou coleção que você deseja excluir.  
  
6.  Clique **Excluir Membro**, **Excluir**ou **Excluir Coleção**.  
  
7.  Os administradores de entidade também verão uma opção de menu para Limpar (excluir definitivamente) todos os membros excluídos de forma reversível na versão da entidade.  
  
8.  Na caixa de diálogo de confirmação, clique em **OK**.  
  
## Consulte também  
 [Reativar um membro ou uma coleção &#40;Master Data Services&#41;](../master-data-services/reactivate-a-member-or-collection-master-data-services.md)   
 [Membros &#40;Master Data Services&#41;](../master-data-services/members-master-data-services.md)   
 [Coleções &#40;Master Data Services&#41;](../master-data-services/collections-master-data-services.md)  
  
  