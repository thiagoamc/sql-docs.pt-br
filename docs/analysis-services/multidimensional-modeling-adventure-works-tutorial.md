---
title: "Modelagem multidimensional (Tutorial do Adventure Works) | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
helpviewer_keywords: 
  - "tutoriais [Analysis Services]"
  - "Analysis Services, tutoriais"
ms.assetid: db55e226-601a-4026-8651-573195555a59
caps.latest.revision: 31
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 31
---
# Modelagem multidimensional (Tutorial do Adventure Works)
Bem-vindo ao Tutorial do [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Este tutorial descreve como usar o [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] para desenvolver e implantar um projeto do [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] usando a empresa fictícia [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] em todos os exemplos.  
  
## O que você aprenderá  
Neste tutorial, você aprenderá a:  
  
-   Definir fontes de dados, exibições da fonte de dados, dimensões, atributos, relações de atributo, hierarquias e cubos em um projeto do [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] no [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].  
  
-   Exibir dados de cubo e dimensão implantando o projeto do [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] em uma instância do [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]e, depois, processar os objetos implantados para populá-los com dados da fonte de dados subjacente.  
  
-   Modificar medidas, dimensões, hierarquias, atributos e grupos de medidas do projeto do [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] e, depois, implantar as alterações incrementais no cubo implantado no servidor de desenvolvimento.  
  
-   Definir cálculos, KPIs (indicadores chave de desempenho), ações, perspectivas, traduções e funções de segurança dentro de um cubo.  
  
Uma descrição de cenário acompanha este tutorial de forma que você possa entender melhor o contexto para estas lições. Para obter mais informações, consulte [Analysis Services Tutorial Scenario](../analysis-services/analysis-services-tutorial-scenario.md).  
  
## Pré-requisitos  
Você precisará de dados de exemplo, arquivos de projeto de exemplo e software para concluir toda as lições deste tutorial. Para obter instruções sobre como localizar e instalar os pré-requisitos deste tutorial, consulte [Install Sample Data and Projects for the Analysis Services Multidimensional Modeling Tutorial](../analysis-services/install sample data and projects.md).  
  
Além disso, as seguintes permissões devem estar em vigor para que o tutorial seja concluído com êxito:  
  
-   Você deve ser um membro do grupo Administradores local no computador do [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ou ser um membro da função de administração de servidor na instância do [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
-   Você deve ter permissões de leitura no banco de dados de exemplo **AdventureWorksDW2012** . Esse banco de dados de exemplo é válido para a versão do [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] .  
  
## Lições  
Este tutorial inclui as seguintes lições.  
  
|Lição|Tempo estimado para concluir|  
|----------|------------------------------|  
|[Lição 1: Definindo uma exibição da fonte de dados em um Projeto do Analysis Services](../analysis-services/lesson-1-defining-a-data-source-view-within-an-analysis-services-project.md)|15 minutos|  
|[Lição 2: Definindo e implantando um cubo](../analysis-services/lesson-2-defining-and-deploying-a-cube.md)|30 minutos|  
|[Lição 3: Modificando medidas, atributos e hierarquias](../analysis-services/lesson-3-modifying-measures-attributes-and-hierarchies.md)|45 minutos|  
|[Lição 4: Definindo propriedades de dimensão e atributo avançadas](../analysis-services/lesson-4-defining-advanced-attribute-and-dimension-properties.md)|120 minutos|  
|[Lição 5: Definindo relações entre grupos de medidas e dimensões](../analysis-services/lesson-5-defining-relationships-between-dimensions-and-measure-groups.md)|45 minutos|  
|[Lição 6: Definindo cálculos](../analysis-services/lesson-6-defining-calculations.md)|45 minutos|  
|[Lição 7: Definindo KPIs &#40;Indicadores Chave de Desempenho&#41;](../analysis-services/lesson-7-defining-key-performance-indicators-kpis.md)|30 minutos|  
|[Lição 8: Definindo ações](../analysis-services/lesson-8-defining-actions.md)|30 minutos|  
|[Lição 9: Definindo perspectivas e traduções](../analysis-services/lesson-9-defining-perspectives-and-translations.md)|30 minutos|  
|[Lição 10: Definindo funções administrativas](../analysis-services/lesson-10-defining-administrative-roles.md)|15 minutos|  
  
> [!NOTE]  
> O banco de dados de cubo que você criará neste tutorial é uma versão simplificada do projeto de modelo multidimensional do [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] que faz parte dos bancos de dados de exemplo da Adventure Works disponível para download no site do codeplex. A versão de tutorial do banco de dados multidimensional do Adventure Works é simplificada para trazer maior foco às habilidades específicas que você desejará dominar imediatamente. Depois que você concluir o tutorial, explore o projeto de modelo multidimensional por conta própria para avançar sua compreensão da modelagem multidimensional do [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
## Próxima etapa  
Para começar o tutorial, vá para a primeira lição: [Lesson 1: Defining a Data Source View within an Analysis Services Project](../analysis-services/lesson-1-defining-a-data-source-view-within-an-analysis-services-project.md).  
  
  
  