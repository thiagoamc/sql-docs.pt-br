---
title: Cubos locais (Analysis Services - dados multidimensionais) | Microsoft Docs
ms.custom: 
ms.date: 03/16/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords: cubes [Analysis Services], local
ms.assetid: e52e1515-35a7-4dc3-9bbf-736d176ba0c7
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: b9b84028e2561b5a0fc25c6866d86d667b8873f2
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2018
---
# <a name="local-cubes-analysis-services---multidimensional-data"></a>Cubos locais (Analysis Services – Dados Multidimensionais)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Para criar, atualizar ou excluir cubos locais, você deve gravar e executar um script ASSL ou um programa AMO.  
  
 Os cubos locais e os modelos de mineração locais permitem a análise em uma estação de trabalho cliente enquanto ela estiver desconectada da rede. Por exemplo, um aplicativo cliente pode chamar o OLE DB for OLAP 9.0 Provider (MSOLAP.3), que carrega o mecanismo do cubo local para criar e consultar cubos locais, conforme mostra a seguinte ilustração:  
  
 ![Arquitetura de cliente para cubos locais e modelos](../../../analysis-services/multidimensional-models/olap-physical/media/as-localcubearch9.gif "arquitetura de cliente para cubos locais e modelos")  
  
 O ADMOD.NET e os Objetos de Gerenciamento de Análise (AMO) também carregam o mecanismo do cubo local ao interagir com cubos locais. Apenas um processo simples pode acessar um arquivo de cubo local, pois o mecanismo de cubo local bloqueia com exclusividade um arquivo de cubo local quando estabelece uma conexão com o cubo local. Com um processo, são permitidas até 5 conexões simultâneas.  
  
 Um arquivo .cub pode conter mais de um cubo ou modelo de mineração de dados. As consultas aos cubos locais e modelos de mineração de dados são tratadas pelo mecanismo de cubo local e não requerem uma conexão com uma instância do [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
> [!NOTE]  
>  Não há suporte para a utilização do [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] nem do [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] para gerenciar cubos locais.  
  
## <a name="local-cubes"></a>Cubos locais  
 Um cubo local pode ser criado e preenchido a partir de um cubo existente em um [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instância ou de uma fonte de dados relacional.  
  
|Fonte para obter dados para cubo local|Método de criação|  
|------------------------------------|---------------------|  
|Cubo baseado em servidor|Você pode usar a instrução CREATE GLOBAL CUBE ou um [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] script Scripting Language (ASSL) para criar e popular um cubo a partir de um cubo com base em servidor. Para obter mais informações, consulte [instrução CREATE GLOBAL CUBE &#40; MDX &#41; ](../../../mdx/mdx-data-definition-create-global-cube.md) ou [do Analysis Services Scripting Language &#40; ASSL para XMLA &#41; ](../../../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md).|  
|Fonte de dados relacionais|Você usa um script ASSL para criar e popular um cubo de um banco de dados relacional OLE DB. Para criar um cubo local usando ASSL, simplesmente conecte-se a um arquivo de cubo local (* .cub) e execute o script ASSL da mesma maneira que faria com um script ASSL em uma instância do [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] para criar um cubo de servidor. Para obter mais informações, consulte [Linguagem de script do Analysis Services &#40;ASSL para XMLA&#41;](../../../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md).|  
  
 Use a instrução REFRESH CUBE para recriar um cubo local e atualizar seus dados. Para obter mais informações, consulte [atualizar cubo instrução &#40; MDX &#41; ](../../../mdx/mdx-data-definition-refresh-cube.md).  
  
### <a name="local-cubes-created-from-server-based-cubes"></a>Cubos locais criados de cubos baseados em servidor  
 Na criação de cubos locais de cubos baseados em servidor, as seguintes considerações se aplicam:  
  
-   Não há suporte para medidas de contagens distintas.  
  
-   Ao adicionar uma medida, você também deve incluir pelo menos uma dimensão relacionada à medida sendo adicionada. Para obter mais informações sobre relações de dimensão para grupos de medidas, consulte [relações de dimensão](../../../analysis-services/multidimensional-models-olap-logical-cube-objects/dimension-relationships.md).  
  
-   Quando você adiciona uma hierarquia pai-filho, os níveis e filtros dessa hierarquia são ignorados e toda a hierarquia pai-filho é incluída.  
  
-   Não são criadas propriedades do membro.  
  
-   Quando você inclui uma medida semiaditiva, nenhuma fatia é permitida na dimensão Conta ou Tempo.  
  
-   Dimensões de referência sempre são materializadas.  
  
-   Quando uma dimensão muitos para muitos é incluída, as seguintes regras são aplicadas:  
  
    -   Você não pode fatiar a dimensão muitos para muitos.  
  
    -   Você deve adicionar uma medida do grupo de medidas intermediário.  
  
    -   Você não pode fatiar nenhuma das dimensões comuns aos dois grupos de medidas envolvidos na relação muitos para muitos.  
  
-   Somente esses membros calculados, conjuntos nomeados e atribuições que se baseiam em medidas e dimensões adicionadas ao cubo local serão exibidas nele. Membros calculados inválidos, conjuntos nomeados e atribuições serão excluídos automaticamente.  
  
### <a name="security"></a>Segurança  
 Em ordem de um usuário para criar um cubo local a partir de um cubo de servidor, o usuário deve ser concedido **detalhamento e cubo Local** permissões no cubo de servidor. Para obter mais informações, consulte [conceder ao cubo ou permissões de modelo &#40; Analysis Services &#41; ](../../../analysis-services/multidimensional-models/grant-cube-or-model-permissions-analysis-services.md).  
  
 Os cubos locais não são protegidos por meio de funções como os cubos de servidor. Qualquer um com acesso no nível de arquivo a um arquivo de cubo local pode consultar os cubos. Você pode usar o **senha de criptografia** propriedade de conexão em um arquivo de cubo local para definir uma senha no arquivo de cubo local. A definição de uma senha em um arquivo de cubo local requer que todas as conexões futuras com o arquivo de cubo local utilizem essa senha para consultar o arquivo.  
  
## <a name="see-also"></a>Consulte Também  
 [Criar cubo GLOBAL instrução &#40; MDX &#41;](../../../mdx/mdx-data-definition-create-global-cube.md)   
 [Desenvolvendo com o Analysis Services Scripting Language &#40; ASSL &#41;](../../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)   
 [Instrução do cubo de atualização de &#40; MDX &#41;](../../../mdx/mdx-data-definition-refresh-cube.md)  
  
  
