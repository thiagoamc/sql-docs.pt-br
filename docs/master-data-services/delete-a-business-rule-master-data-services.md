---
title: "Excluir uma regra de negócios (Master Data Services) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
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
- deleting business rules [Master Data Services]
- business rules [Master Data Services], deleting
ms.assetid: b97aa4f9-569f-451d-ad62-65b81f980299
caps.latest.revision: 
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2f8e68c57e9a17313c6b2348bc463280131ffb37
ms.sourcegitcommit: 6ac1956307d8255dc544e1063922493b30907b80
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2018
---
# <a name="delete-a-business-rule-master-data-services"></a>Excluir uma regra de negócio (Master Data Services)
  No [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], exclua uma regra de negócio quando ela não for mais necessária.  
  
> [!NOTE]  
>  Você pode evitar a validação de dados em relação a uma regra de negócio excluindo-a. Para obter mais informações, consulte [Excluir uma regra de negócio &#40;Master Data Services&#41;](../master-data-services/exclude-a-business-rule-master-data-services.md).  
  
## <a name="prerequisites"></a>Prerequisites  
 Para executar esse procedimento:  
  
-   Você deve ter permissão para acessar a área funcional **Administração do Sistema** .  
  
-   Você deve ser um administrador de modelo. Para obter mais informações, veja [Administradores &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-delete-a-business-rule"></a>Para excluir uma regra de negócio  
  
1.  No [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], clique em **Administração do Sistema**.  
  
2.  Na barra de menus, aponte para **Gerenciar** e clique em **Regras de Negócios**.  
  
3.  Na página **Regras de Negócio** , na lista suspensa **Modelo** , selecione um modelo.  
  
4.  Na lista suspensa **Entidade** , escolha uma entidade.  
  
5.  Na lista suspensa **Tipos de Membro** , selecione um tipo de membro ao qual a regra de negócio será aplicada.  
  
6.  Na grade, clique na linha da regra de negócios que você deseja excluir.  
  
7.  Clique em **Excluir**.  
  
8.  Na caixa de diálogo de confirmação, clique em **OK**. O valor da coluna **Estado da Regra de Negócios** é **Exclusão pendente**.  
  
9. Clique em **Publicar Tudo**.  
  
10. Na caixa de diálogo de confirmação, clique em **OK**. A regra de negócio excluída não é mais exibida na grade.  
  
## <a name="see-also"></a>Consulte Também  
 [Excluir uma regra de negócio &#40;Master Data Services&#41;](../master-data-services/exclude-a-business-rule-master-data-services.md)   
 [Criar e publicar uma regra de negócios &#40;Master Data Services&#41;](../master-data-services/create-and-publish-a-business-rule-master-data-services.md)   
 [Regras de negócio &#40;Master Data Services&#41;](../master-data-services/business-rules-master-data-services.md)  
  
  
