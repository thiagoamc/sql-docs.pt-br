---
title: "Algoritmo Associa&#231;&#227;o da Microsoft | Microsoft Docs"
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
  - "propriedade MinimumProbability"
  - "conjuntos de itens [Analysis Services]"
  - "propriedade MaximumItemsetCount"
  - "propriedade MinimumSupport"
  - "OPTIMIZED_PREDICTION_COUNT"
  - "propriedade OptimizedPredictionCount"
  - "propriedade MaximumSupport"
  - "MINIMUM_PROBABILITY"
  - "algoritmos [mineração de dados]"
  - "algoritmos de associação [Analysis Services]"
  - "regras [Mineração de dados]"
  - "regras de associação"
  - "propriedade MinimumItemsetSize"
  - "análise da cesta de compras [Analysis Services]"
  - "associações [Analysis Services]"
  - "MINIMUM_SUPPORT"
  - "MAXIMUM_SUPPORT"
  - "MINIMUM_ITEMSET_SIZE"
  - "propriedade MaximumItemsetSize"
ms.assetid: 8b6b8247-62f9-4f6f-b1af-d01dab290e4c
caps.latest.revision: 55
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 55
---
# Algoritmo Associa&#231;&#227;o da Microsoft
  O algoritmo Associação da [!INCLUDE[msCoName](../../includes/msconame-md.md)] é um algoritmo normalmente usado pelos mecanismos de recomendação. Um mecanismo de recomendação recomenda itens aos clientes com base nos itens que eles já compraram ou pelos quais mostraram interesse. O algoritmo Associação da [!INCLUDE[msCoName](../../includes/msconame-md.md)] também é útil para análise da cesta básica.   
  
 Modelos de associação são criados a partir de conjuntos de dados que contêm identificadores de casos individuais e de itens contidos em casos. Um grupo de itens em um caso é chamado de *conjunto de itens*. Um modelo de associação é formado por uma série de conjuntos de itens e regras que descrevem como esses itens são agrupados nos casos. As regras que o algoritmo identificar podem ser usadas para prever as prováveis compras futuras do cliente com base nos itens já existentes em seu carrinho de compras. O diagrama a seguir mostra uma série de regras em um conjunto de itens.  
  
 ![Um conjunto de regras para um modelo de associação](../../analysis-services/data-mining/media/association.gif "Um conjunto de regras para um modelo de associação")  
  
 Como ilustra o diagrama, o algoritmo Associação da [!INCLUDE[msCoName](../../includes/msconame-md.md)] pode potencialmente localizar muitas regras em um conjunto de dados. O algoritmo usa dois parâmetros, suporte e probabilidade, para descrever os conjuntos de itens e as regras que gera. Por exemplo, se X e Y representassem dois itens que poderiam estar em um carrinho de compras, o parâmetro de suporte seria o número de casos no conjunto de dados que contém a combinação dos itens X e Y. Ao usar o parâmetro de suporte em combinação com os parâmetros definidos pelo usuário, *MINIMUM_SUPPORT* e *MAXIMUM_SUPPORT*, o algoritmo controla o número de conjuntos de itens gerados. O parâmetro de probabilidade, também chamado de *confiança*, representa a fração de casos no conjunto de dados que contém X e que também contém Y. Ao usar o parâmetro de probabilidade combinado com o parâmetro *MINIMUM_PROBABILITY*, o algoritmo controla o número de regras geradas.  
  
## Exemplo  
 A empresa [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] Cycle está redesenhando a funcionalidade de seu site. A meta do redesenho é aumentar a venda direta de produtos. Como a empresa registra cada venda em um banco de dados transacional, pode usar o algoritmo Associação da [!INCLUDE[msCoName](../../includes/msconame-md.md)] para identificar conjuntos de produtos que tendem a ser comprados juntos. Ela pode então prever outros itens pelos o quais o cliente poderia interessar-se com base nos itens que já estão no carrinho de compras.  
  
## Como o algoritmo funciona  
 O algoritmo Associação da [!INCLUDE[msCoName](../../includes/msconame-md.md)] atravessa um conjunto de dados para localizar itens que aparecem juntos em um caso. Em seguida, ele agrupa em conjuntos de itens todos os itens associados que aparecem, no mínimo, em diversos casos que são especificados pelo parâmetro *MINIMUM_SUPPORT*. Por exemplo, um conjunto de itens poderia ser "Mountain 200=Existing, Sport 100=Existing" e poderia ter um suporte de 710. Depois, o algoritmo gera as regras a partir dos conjuntos de itens. Essas regras são usadas para prever a presença de um item no banco de dados, de acordo com a presença de outros itens especificados que o algoritmo identifica como importante. Por exemplo, uma regra poderia ser "if Touring 1000=existing and Road bottle cage=existing, then Water bottle=existing" e ter a probabilidade de 0,812. Nesse exemplo, o algoritmo identifica que a presença no carrinho de compras do pneu Touring 1000 e do suporte para garrafa prevê que a garrafa de água também poderia estar no carrinho.  
  
 Para obter uma explicação mais detalhada do algoritmo e uma lista de parâmetros para personalizar seu comportamento e controlar os resultados no modelo de mineração, consulte [Referência técnica do algoritmo de associação da Microsoft](../../analysis-services/data-mining/microsoft-association-algorithm-technical-reference.md).  
  
## Dados requeridos para os modelos de associação  
 Ao preparar dados para usar em um modelo de regras de associação, é preciso entender os requisitos de um determinado algoritmo, incluindo a quantidade de dados necessária e como eles são usados.  
  
 Os requisitos de um modelo de regras de associação são:  
  
-   **Uma única coluna de chave** Cada modelo deve conter uma coluna de texto ou numérica que identifique unicamente cada registro. Não são permitidas chaves compostas.  
  
-   **Uma única coluna previsível** Um modelo de associação pode ter apenas uma coluna previsível. Geralmente, é a coluna de chave da tabela aninhada, como aquela arquivada, que lista os produtos que foram comprados. Os valores devem ser discretos ou diferenciados.  
  
-   **Colunas de entrada**. As colunas de entrada devem ser discretas. Normalmente, os dados de entrada do modelo de associação são mantidos em duas tabelas. Por exemplo, uma tabela poderia conter informações sobre o cliente enquanto outra tabela contém as compras feitas pelo cliente. Você pode inserir esses dados no modelo usando uma tabela aninhada. Para obter mais informações sobre tabelas aninhadas, consulte [Tabelas aninhadas &#40;Analysis Services – Mineração de Dados&#41;](../../analysis-services/data-mining/nested-tables-analysis-services-data-mining.md).  
  
 Para obter informações mais detalhadas sobre os tipos de conteúdo e de dados com suporte pelos modelos de associação, consulte a seção Requisitos de [Referência técnica do algoritmo de associação da Microsoft](../../analysis-services/data-mining/microsoft-association-algorithm-technical-reference.md).  
  
## Exibindo um modelo de associação  
 Para explorar o modelo, você pode usar o **Visualizador de Associação da Microsoft**. Quando você exibir um modelo de associação, o [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] apresentará as correlações de ângulos diferentes para que você possa entender melhor as relações e as regras encontradas nos dados. O painel **Conjunto de Itens** do visualizador fornece uma análise detalhada das combinações, ou conjuntos de itens, mais comuns. O painel **Regras** apresenta uma lista de regras que foram generalizadas por meio dos dados, adiciona cálculos de probabilidade e classifica as regras por importância relativa. Com o Visualizador de Rede de Dependências, você pode explorar como se conectam itens diferentes. Para obter mais informações, consulte [Procurar um modelo usando o Visualizador de Cluster da Microsoft](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md).  
  
 Para obter mais detalhes sobre qualquer dos conjuntos de itens ou das regras, você pode navegar pelo modelo no [Visualizador de Árvore de Conteúdo Genérica da Microsoft](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md). O conteúdo armazenado para o modelo inclui o suporte para cada conjunto de itens, uma pontuação para cada regra e outras estatísticas. Para obter mais informações, consulte [Conteúdo do modelo de mineração para modelos de associação &#40;Analysis Services – Mineração de dados&#41;](../../analysis-services/data-mining/mining-model-content-for-association-models-analysis-services-data-mining.md).  
  
## Criando previsões  
 Depois de processado o modelo, você pode usar as regras e os conjuntos de itens para fazer previsões. Em um modelo de associação, uma previsão indica qual item deveria aparecer mediante a presença do item especificado, além de poder incluir informações como probabilidade, suporte ou importância. Para obter exemplos de como criar consultas em um modelo de associação, consulte [Exemplos de consulta de um modelo associação](../../analysis-services/data-mining/association-model-query-examples.md).  
  
 Para obter informações gerais sobre como criar uma consulta com base em um modelo de mineração de dados, consulte [Consultas de mineração de dados](../../analysis-services/data-mining/data-mining-queries.md).  
  
## Desempenho  
 O processo de criação de conjuntos de itens e de contagem de correlações pode ser demorado. Embora o algoritmo Regras de Associação da [!INCLUDE[msCoName](../../includes/msconame-md.md)] use técnicas de otimização para economizar espaço e acelerar o processamento, saiba que podem ocorrer problemas de desempenho sob as seguintes condições:  
  
-   O conjunto de dados é grande, com muitos itens individuais.  
  
-   O tamanho mínimo do conjunto de itens também é muito pequeno.  
  
 Para reduzir o tempo de processamento e a complexidade dos conjuntos de itens, convém tentar agrupar itens relacionados por categorias antes de analisar os dados.  
  
## Comentários  
  
-   Não dá suporte ao uso de PMML para criar modelos de mineração.  
  
-   Dá suporte ao detalhamento.  
  
-   Suporta o uso de modelos de mineração OLAP.  
  
-   Suporta a criação de dimensões de mineração de dados.  
  
## Consulte também  
 [Algoritmos de mineração de dados &#40;Analysis Services – Data Mining&#41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Procurar um modelo usando o Visualizador de Regras de Associação da Microsoft](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-association-rules-viewer.md)   
 [Conteúdo do modelo de mineração para modelos de associação &#40;Analysis Services – Data Mining&#41;](../../analysis-services/data-mining/mining-model-content-for-association-models-analysis-services-data-mining.md)   
 [Referência técnica do algoritmo de associação da Microsoft](../../analysis-services/data-mining/microsoft-association-algorithm-technical-reference.md)   
 [Exemplos de consulta de um modelo de associação](../../analysis-services/data-mining/association-model-query-examples.md)  
  
  