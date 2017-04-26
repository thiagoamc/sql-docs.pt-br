---
title: "Filtrar uma regra em um modelo de regras de associa&#231;&#227;o | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "filtrando regras [Analysis Services]"
  - "Visualizador do Modelo de Mineração [Analysis Services], regras"
  - "Visualizador de Regras"
ms.assetid: 26cdba5b-5bf1-439e-80a3-8759774e918b
caps.latest.revision: 28
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 28
---
# Filtrar uma regra em um modelo de regras de associa&#231;&#227;o
  Você pode usar a filtragem com modelos de associação para restringir os resultados a apenas as associações do seu interesse. Por exemplo, você pode filtrar as regras para mostrar apenas aquelas que incluem um produto específico.  
  
 No Designer de Mineração de Dados, você pode usar os controles na guia **Regras** do Visualizador de Regras de Associação da [!INCLUDE[msCoName](../../includes/msconame-md.md)] para filtrar as regras que são exibidas.  Você também pode criar uma consulta no modelo para ver apenas o conjunto de itens que contém um valor específico.  
  
> [!NOTE]  
>  Esta opção só está disponível para modelos de mineração que foram criados com o Algoritmo de Associação da Microsoft.  
  
### Filtrar uma regra em um modelo de associação  
  
1.  Abra o modelo de mineração usando o **Visualizador de Regras de Associação**. Para fazer isso no SQL Server Management Studio, clique com o botão direito do mouse no nome do modelo e selecione **Procurar**. Para fazer isso no [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], clique duas vezes na estrutura de mineração que contém o modelo e clique na guia **Visualizador do Modelo de Mineração** do **Designer de Mineração de Dados**.  
  
2.  Clique na guia **Regras** do **Visualizador de Regras de Associação**.  
  
3.  Digite em uma condição de regra na caixa **Filtrar Regra** . Por exemplo, uma condição de regra poderia ser "Posto de Bicicleta" que também retorna "Postos de Bicicleta."  
  
     A caixa de texto **Regra do Filtro** dá suporte a expressões regulares conforme a definição da linguagem .NET. Por isso, é possível usar expressões como as seguintes: `((.Helmets.*Fenders.*)|(.*Fenders.*Helmets.*))`. Essa expressão retornaria qualquer conjuntos de itens que incluísse atributos com as palavras Helmets e Fenders, em qualquer ordem.  
  
4.  Para **Probabilidade mínima**, aumente o valor da probabilidade para exibir menos regras ou diminua o valor para exibir mais regras.  
  
5.  Para **Importância mínima**, aumente o valor da importância para exibir menos regras ou diminua o valor para exibir mais regras.  
  
6.  Para **Mostrar**, selecione um das seguintes opções: **Mostrar nome e valor do atributo**, **Mostrar apenas o nome de atributo**ou **Mostrar apenas o valor de atributo**.  
  
7.  Para **Máximo de linhas**, aumente o valor para aumentar o número total de regras que atendem às condições especificadas ou diminua o valor para limitar o número de regras retornadas. As regras são ordenadas por probabilidade, assim você poderia eliminar regras adicionais que atendem às condições especificadas de probabilidade ou importância.  
  
8.  Marque ou desmarque a caixa de seleção **Mostrar nome longo** para alternar o modo como os nomes de regras são exibidos.  
  
     As regras agora são filtradas para exibir apenas as regras de exibição que contenham o item indicado. A condição de filtro se aplica a valores de atributo antes ou depois do delimitador de regra, "->".  
  
    > [!NOTE]  
    >  O visualizador armazena em cache a lista inicial de regras, baseado em uma consulta para o modelo de mineração, e não atualiza a lista de regras a menos que você altere as condições da consulta definindo o máximo de linhas, a probabilidade, importância ou a exibição de nomes longos. Por isso, se digitar uma condição e a exibição não for atualizada imediatamente, você poderá forçar o visualizador a atualizar os dados, marcando e desmarcando a caixa de seleção **Mostrar nomes longos** .  
  
### Criar uma consulta nos conjuntos de itens em um modelo de associação  
  
-   [Exemplos de consulta de um modelo de associação](../../analysis-services/data-mining/association-model-query-examples.md)  
  
## Consulte também  
 [Tarefas e instruções do visualizador do modelo de mineração](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)   
 [Procurar um modelo usando o Visualizador de Regras de Associação da Microsoft](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-association-rules-viewer.md)   
 [Lição 3: Criando um cenário de cesta de compras &#40;Tutorial intermediário de mineração de dados&#41;](../Topic/Lesson%203:%20Building%20a%20Market%20Basket%20Scenario%20\(Intermediate%20Data%20Mining%20Tutorial\).md)  
  
  