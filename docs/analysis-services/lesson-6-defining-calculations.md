---
title: "Li&#231;&#227;o 6: Definindo c&#225;lculos | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: e0a1e354-e879-4eb8-bb2b-6c3809e32cb6
caps.latest.revision: 19
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 19
---
# Li&#231;&#227;o 6: Definindo c&#225;lculos
Nesta lição, você aprenderá a definir cálculos, que são scripts ou expressões MDX (Multidimensional Expressions). Os cálculos permitem que você defina membros calculados, conjuntos nomeados ou execute outros comandos de script para aumentar os recursos de um cubo do [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Por exemplo, você pode executar um comando de script para definir um subcubo e depois atribuir um cálculo às células no subcubo.  
  
Ao definir um novo cálculo no Designer de Cubo, o cálculo é adicionado ao painel **Organizador de Script** da guia **Cálculos** do Designer de Cubo, e os campos deste tipo específico de cálculo são exibidos em um formulário de cálculos no painel **Expressões de Cálculo** . Os cálculos são executados na ordem em que estão listados no painel **Organizador de Script** . Você pode reordenar os cálculos clicando com o botão direito do mouse em um cálculo específico e selecionando **Mover para Cima** ou **Mover para Baixo**, ou clicando em cálculo específico e usando os ícones **Mover para Cima** ou **Mover para Baixo** na barra de ferramentas da guia **Cálculos**.  
  
Na guia **Cálculos** , você pode adicionar novos cálculos e exibir ou editar cálculos existentes nas seguintes exibições do painel **Expressões de Cálculo** :  
  
-   Exibição de formulário. Esta exibição mostra as expressões e propriedades de um único comando em um formato gráfico. Quando você edita um script MDX, uma caixa de expressão preenche a exibição Formulário.  
  
-   Exibição de script. Esta exibição mostra todos os scripts de cálculo em um editor de código que permite alterar os scripts de cálculo facilmente. Quando o painel **Expressões de Cálculo** está na Exibição de script, o **Organizador de Script** fica oculto. A Exibição de script fornece codificação por cor, correspondência de parênteses, preenchimento automático e regiões de código MDX. Você pode expandir ou recolher as regiões de código MDX para facilitar a edição.  
  
Para alternar entre esses exibições no painel **Expressões de Cálculo** , clique em **Exibição de Formulário** ou **Exibição de Script** na barra de ferramentas da guia **Cálculos** .  
  
> [!NOTE]  
> Se o [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] detectar um erro de sintaxe em qualquer cálculo, a Exibição de formulário não será exibida até que o erro seja corrigido na Exibição de script.  
  
Você também pode usar o Assistente de Business Intelligence para adicionar determinados cálculos a um cubo. Por exemplo, você pode usar esse assistente para adicionar inteligência de tempo a um cubo, o que significa definir membros calculados para cálculos relacionados ao tempo como período até esta data, médias de movimentação ou crescimento de período sobre período. Para obter mais informações, consulte [Definir cálculos de inteligência de tempo com o Assistente de Business Intelligence](../analysis-services/multidimensional-models/define-time-intelligence-calculations-using-the-business-intelligence-wizard.md).  
  
> [!IMPORTANT]  
> Na guia **Cálculos** , o script de cálculo inicia com o comando CALCULATE. O comando CALCULATE controla a agregação das células do cubo e deve ser editado apenas se você pretender especificar manualmente como as células do cubo devem ser agregadas.  
  
Para obter mais informações, consulte [Cálculos](../analysis-services/multidimensional-models-olap-logical-cube-objects/calculations.md) e [Cálculos em modelos multidimensionais](../analysis-services/multidimensional-models/calculations-in-multidimensional-models.md).  
  
> [!NOTE]  
> Projetos concluídos de todas as lições deste tutorial estão disponíveis online. Você pode avançar para qualquer lição com o uso do projeto concluído na lição anterior como um ponto de partida. [Clique aqui](http://go.microsoft.com/fwlink/?LinkID=221866) para baixar os projetos de exemplo fornecidos com este tutorial.  
  
Esta lição contém as seguintes tarefas:  
  
[Definindo membros calculados](../analysis-services/defining-calculated-members.md)  
Nesta tarefa, você aprenderá a definir membros calculados.  
  
[Definindo conjuntos nomeados](../analysis-services/defining-named-sets.md)  
Nesta tarefa, você aprenderá a definir conjuntos nomeados.  
  
## Próxima lição  
[Lição 7: Definindo KPIs &#40;Indicadores Chave de Desempenho&#41;](../analysis-services/lesson-7-defining-key-performance-indicators-kpis.md)  
  
## Consulte também  
[Cenário do tutorial de Analysis Services](../analysis-services/analysis-services-tutorial-scenario.md)  
[Modelagem multidimensional &#40;Tutorial do Adventure Works&#41;](../analysis-services/multidimensional-modeling-adventure-works-tutorial.md)  
[Criar conjuntos nomeados](../analysis-services/multidimensional-models/create-named-sets.md)  
[Criar membros calculados](../analysis-services/multidimensional-models/create-calculated-members.md)  
  
  
  