---
title: "Anotar uma transa&#231;&#227;o (Master Data Services) | Microsoft Docs"
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
  - "anotações [Master Data Services], para transações"
ms.assetid: f5a6b2ca-56de-4e42-9da8-fba0ac3e8d92
caps.latest.revision: 6
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 6
---
# Anotar uma transa&#231;&#227;o (Master Data Services)
  No [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], anote uma transação quando desejar fornecer detalhes de suporte sobre a transação para objetivos históricos.  
  
> [!NOTE]  
>  Não é possível excluir anotações.  
  
## Pré-requisitos  
  
-   Para anotar as transações criadas, você deve ter permissões para acessar a área funcional **Explorer** e ter, no mínimo, a permissão **Atualizar** no objeto do modelo que você deseja anotar.  
  
-   Para anotar transações para todos os usuários, você deve ter permissão para acessar a área funcional **Gerenciamento de Versões** e ser um administrador de modelo. Para obter mais informações, veja [Administradores &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### Para anotar uma transação no Explorer  
  
1.  Na página inicial do [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , na lista **Modelo** , selecione um modelo.  
  
2.  Na lista **Versão** , selecione uma versão.  
  
3.  Clique em **Gerenciador**.  
  
4.  Na barra de menus, aponte para **Entidades** e clique na entidade que contém o membro com a transação que você deseja anotar.  
  
5.  Na grade, clique na linha do membro.  
  
6.  Clique em **Exibir Transações**.  
  
7.  Na caixa de diálogo **Exibir Transações**, clique na transação que você deseja anotar.  
  
8.  Na caixa na parte inferior da caixa de diálogo, digite sua anotação.  
  
9. Clique em **Adicionar Anotação**. A anotação é exibida no painel **Anotações**.  
  
### Para anotar uma transação no Gerenciamento de Versão (somente administradores)  
  
1.  Na home page do [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , clique em **Gerenciamento de Versões**.  
  
2.  Na barra de menus, clique em **Transações**.  
  
3.  No painel **Transações**, clique na linha da grade da transação que você deseja anotar.  
  
4.  No painel **Anotações da Transação**, na caixa **Anotação**, digite a anotação.  
  
5.  Clique em **OK**.  
  
## Consulte também  
 [Anotações &#40;Master Data Services&#41;](../master-data-services/annotations-master-data-services.md)   
 [Transações &#40;Master Data Services&#41;](../master-data-services/transactions-master-data-services.md)  
  
  