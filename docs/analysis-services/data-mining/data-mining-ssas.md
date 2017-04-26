---
title: "Minera&#231;&#227;o de dados (SSAS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "mineração de dados [Analysis Services], sobre a mineração de dados"
ms.assetid: b1c912da-72f6-4d96-89c8-55a2c4f19e88
caps.latest.revision: 31
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 31
---
# Minera&#231;&#227;o de dados (SSAS)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tem sido o líder em análise preditiva desde a versão 2000, fornecendo a mineração de dados no [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. A combinação de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Data Mining fornece uma plataforma integrada para análise preditiva que abrange a preparação e a limpeza de dados, aprendizado de máquina e relatórios. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] O Data Mining inclui vários algoritmos padrão, incluindo modelos de clustering EM e K-means, redes neurais, regressão logística e linear, árvores de decisão e classificadores naive bayes. Todos os modelos integraram visualizações para ajudá-lo a desenvolver, refinar e avaliar os modelos.  Integrar a mineração de dados na solução de business intelligence ajuda a tomar decisões inteligentes sobre problemas complexos.  
  
## Benefícios da mineração de dados  
 A mineração de dados (também chamada de análise preditiva e aprendizado de máquina) usa princípios estatísticos bem pesquisados para descobrir padrões nos dados. Ao aplicar os algoritmos de mineração de dados a seus dados no [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , você pode prever tendências, identificar padrões, criar regras e recomendações, analisar a sequência de eventos em conjuntos de dados complexos e ter novas ideias.  
  
 No [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], a mineração de dados é um recurso avançado, acessível e integrado com as ferramentas que muitas pessoas preferem usar para análise e relatório.  
  
## Principais recursos de mineração de dados  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] O Data Mining fornece os recursos a seguir ao dar suporte a soluções de mineração de dados integradas:  
  
-   Várias fontes de dados: você pode usar qualquer fonte de dados tabular para mineração de dados, incluindo planilhas e arquivos de texto. Também é possível minerar facilmente cubos OLAP criados no [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. No entanto, você não pode usar dados de um banco de dados na memória.  
  
-   Limpeza de dados integrada, gerenciamento de dados e relatórios: o [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] fornece ferramentas avançadas para criação de perfil e limpeza de dados. Você pode criar processos ETL para limpeza de dados em preparação para modelagem e ssISnoversion também facilita a manter e atualizar modelos.  
  
-   Vários algoritmos personalizáveis: além de fornecer algoritmos como clustering, redes neurais e árvores de decisões, o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Data Mining dá suporte ao desenvolvimento de seus próprios algoritmos de plug-in personalizados.  
  
-   Infraestrutura de testes de modelo: teste seus modelos e conjuntos de dados usando ferramentas estatísticas importantes como validação cruzada, matrizes de classificação, gráficos de comparação de precisão e dispersões. Crie e gerencie conjuntos de teste e treinamento com facilidade.  
  
-   Consulta e drillthrough: o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Data Mining fornece a linguagem DMX para integrar as consultas de previsão em aplicativos. Você também pode recuperar estatísticas detalhadas e padrões dos modelos e fazer drillthrough para dados de caso.  
  
-   Ferramentas de cliente: além dos estúdios de desenvolvimento e design fornecidos pelo SQL Server, você pode usar os Suplementos de Mineração de Dados para Excel para criar, consultar e procurar modelos. Ou crie clientes personalizados, inclusive serviços Web.  
  
-   Suporte a linguagem de scripts e API gerenciada: todos os objetos de mineração de dados são completamente programáveis. Gerar scripts é possível por meio do MDX, XMLA ou as extensões de PowerShell para o [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Use a linguagem DMX (Data Mining Extensions) para consultar e gerar script rapidamente.  
  
-   Segurança e implantação: fornece segurança baseada em função por meio do [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], inclusive permissões separadas para drillthrough para modelar e estruturar dados. Implantação fácil de modelos para outros servidores, de forma que os usuários possam acessar os padrões ou executar previsões  
  
## Nesta seção  
 Os tópicos nesta seção apresentam os recursos principais de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Data Mining e tarefas relacionadas.  
  
-   [Conceitos de mineração de dados](../../analysis-services/data-mining/data-mining-concepts.md)  
  
-   [Algoritmos de mineração de dados &#40;Analysis Services – Data Mining&#41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)  
  
-   [Estruturas de Mineração &#40;Analysis Services – Data Mining&#41;](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)  
  
-   [Modelos de mineração &#40;Analysis Services – Data Mining&#41;](../../analysis-services/data-mining/mining-models-analysis-services-data-mining.md)  
  
-   [Teste e validação &#40;Mineração de dados&#41;](../../analysis-services/data-mining/testing-and-validation-data-mining.md)  
  
-   [Consultas de mineração de dados](../../analysis-services/data-mining/data-mining-queries.md)  
  
-   [Soluções de mineração de dados](../../analysis-services/data-mining/data-mining-solutions.md)  
  
-   [Ferramentas de mineração de dados](../../analysis-services/data-mining/data-mining-tools.md)  
  
-   [Arquitetura de mineração de dados](../../analysis-services/data-mining/data-mining-architecture.md)  
  
-   [Visão geral de segurança &#40;Mineração de dados&#41;](../../analysis-services/data-mining/security-overview-data-mining.md)  
  
## Consulte também  
 [SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services.md)  
  
  