---
title: "Hierarquias derivadas com extremidades explícitas (Master Data Services) | Microsoft Docs"
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
- hierarchies [Master Data Services], derived hierarchies with explicit caps
- explicit hierarchies, derived hierarchies with explicit caps
- derived hierarchies, derived hierarchies with explicit caps
ms.assetid: 6a82ff66-c137-4757-99bb-787d189b4295
caps.latest.revision: 
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 83cddafb34feeca8a69aa337638c21f699df6a56
ms.sourcegitcommit: 6ac1956307d8255dc544e1063922493b30907b80
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2018
---
# <a name="derived-hierarchies-with-explicit-caps-master-data-services"></a>Hierarquias derivadas com nível superior (Master Data Services)
  No [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], quando os níveis de uma hierarquia explícita são usados como os níveis mais altos de uma hierarquia derivada, isso é chamado de hierarquia derivada com níveis superiores.  
  
 A hierarquia explícita deve ser baseada na mesma entidade que a entidade do alto da hierarquia derivada.  
  
 Na interface do usuário do [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , é possível criar este tipo de hierarquia arrastando uma hierarquia explícita até a parte superior de uma hierarquia derivada.  
  
 ![mds_conc_explicit_cap_UI_structure](../master-data-services/media/mds-conc-explicit-cap-ui-structure.gif "mds_conc_explicit_cap_UI_structure")  
  
## <a name="derived-hierarchy-with-explicit-cap-example"></a>Hierarquia derivada com exemplo de extremidade explícita  
 Neste exemplo, os membros na hierarquia explícita são da entidade Subcategoria. Na hierarquia derivada, os membros da hierarquia de nível superior também são da entidade Subcategoria.  
  
 ![mds_conc_explicit_cap_UI_example](../master-data-services/media/mds-conc-explicit-cap-ui-example.gif "mds_conc_explicit_cap_UI_example")  
  
 Ao usar a hierarquia explícita na parte superior de uma hierarquia derivada, a hierarquia derivada torna-se irregular.  
  
## <a name="rules"></a>Regras  
  
-   Você não pode ter mais de uma hierarquia explícita em uma hierarquia derivada com nível superior.  
  
-   Você pode usar a mesma hierarquia explícita como um nível superior para várias hierarquias derivadas.  
  
-   Você não pode atribuir permissões de membro de hierarquia a hierarquias derivadas com níveis superiores. Se você atribuir permissões individualmente à hierarquia explícita ou à hierarquia derivada, as permissões afetarão ambas as hierarquias.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Descrição da tarefa|Tópico|  
|----------------------|-----------|  
|Criar uma hierarquia derivada.|[Criar uma hierarquia derivada &#40;Master Data Services&#41;](../master-data-services/create-a-derived-hierarchy-master-data-services.md)|  
|Criar uma hierarquia explícita.|[Criar uma hierarquia explícita &#40;Master Data Services&#41;](../master-data-services/create-an-explicit-hierarchy-master-data-services.md)|  
|Excluir uma hierarquia derivada existente.|[Excluir uma hierarquia derivada &#40;Master Data Services&#41;](../master-data-services/delete-a-derived-hierarchy-master-data-services.md)|  
|||  
  
## <a name="related-content"></a>Conteúdo relacionado  
  
-   [Hierarquias derivadas &#40;Master Data Services&#41;](../master-data-services/derived-hierarchies-master-data-services.md)  
  
-   [Hierarquias explícitas &#40;Master Data Services&#41;](../master-data-services/explicit-hierarchies-master-data-services.md)  
  
  
