---
title: Alterar um nome de atributo e um tipo de dados (Master Data Services) | Microsoft Docs
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: non-specific
ms.reviewer: 
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- attributes [Master Data Services], changing name
ms.assetid: d348f238-f59d-41c7-ad20-3ccd55bfd9e5
caps.latest.revision: 
author: leolimsft
ms.author: lle
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 9811d14dff86ed16ec207f47625ee151b6eda959
ms.sourcegitcommit: 6ac1956307d8255dc544e1063922493b30907b80
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2018
---
# <a name="change-an-attribute-name-and-data-type-master-data-services"></a>Alterar um Nome de Atributo e um Tipo de Dados (Master Data Services)
  No [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], você pode alterar o nome de um atributo.  
  
## <a name="prerequisites"></a>Prerequisites  
 Para executar esse procedimento:  
  
-   Você deve ter permissão para acessar a área funcional **Administração do Sistema** .  
  
-   Você deve ser um administrador de modelo. Para obter mais informações, veja [Administradores &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-change-an-attribute-name-and-type"></a>Para alterar um nome e um tipo de atributo  
  
1.  No [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], clique em **Administração do Sistema**.  
  
2.  Na página **Gerenciar Modelo** , selecione um modelo na grade e clique em **Entidades**.  
  
3.  Na página **Gerenciar Entidade** , selecione a linha da entidade para a qual deseja criar um atributo.  
  
4.  Clique em **Atributos**.  
  
5.  Na página **Gerenciar atributos** , realize um dos procedimentos a seguir.  
  
    -   Se o atributo for para membros folha, selecione **Folha** na caixa de listagem **Tipos de Membro** .  
  
    -   Se o atributo for para membros consolidados, selecione **Consolidado** na caixa de listagem **Tipos de Membro** .  
  
    -   Se o atributo for para coleções, selecione **Coleção** na caixa de listagem **Tipos de Membro** .  
  
6.  Selecione a linha do atributo que deseja editar e clique em **Editar**.  
  
7.  Na caixa **Nome**, digite o nome atualizado do atributo. Para obter uma lista de palavras que não devem ser usadas como nomes de atributo, consulte [Palavras reservadas &#40;Master Data Services&#41;](../master-data-services/reserved-words-master-data-services.md).  
  
8.  Na lista **Tipo de atributo**, selecione outro tipo.  
  
9. Clique em **Salvar**.  
  
## <a name="see-also"></a>Consulte Também  
 [Criar um atributo de texto &#40;Master Data Services&#41;](../master-data-services/create-a-text-attribute-master-data-services.md)   
 [Excluir um atributo &#40;Master Data Services&#41;](../master-data-services/delete-an-attribute-master-data-services.md)   
 [Atributos &#40;Master Data Services&#41;](../master-data-services/attributes-master-data-services.md)  
  
  
