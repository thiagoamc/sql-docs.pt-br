---
title: "Copiar uma exibi&#231;&#227;o de um modelo de minera&#231;&#227;o | Microsoft Docs"
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
  - "Áreas de transferência [mineração de dados]"
  - "Visualizador do Modelo de Mineração [Analysis Services], áreas de transferência"
  - "copiando modelos de mineração para a área de transferência"
ms.assetid: 768372db-e5b4-4990-b459-03d854fd9a6d
caps.latest.revision: 38
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 38
---
# Copiar uma exibi&#231;&#227;o de um modelo de minera&#231;&#227;o
  O **Visualizador do Modelo de Mineração** do Designer de Mineração de Dados no [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] usa um visualizador separado para cada tipo de modelo de mineração. Muitos dos visualizadores têm componentes a partir dos quais você pode copiar o conteúdo para a Área de Transferência e de lá colar o conteúdo em um documento ou no software de manipulação de imagens. Os componentes a seguir tornam essa funcionalidade disponível:  
  
-   Diagrama de Cluster no Visualizador de Cluster da [!INCLUDE[msCoName](../../includes/msconame-md.md)] e o Visualizador de Cluster de Sequências da [!INCLUDE[msCoName](../../includes/msconame-md.md)]  
  
-   Árvore de Decisão no Visualizador de Árvore da [!INCLUDE[msCoName](../../includes/msconame-md.md)] e o Visualizador MTS [!INCLUDE[msCoName](../../includes/msconame-md.md)]  
  
-   Transições de estado no Visualizador de Cluster de Sequências da [!INCLUDE[msCoName](../../includes/msconame-md.md)]  
  
-   Rede de Dependências no Visualizador de Regras de Associação da [!INCLUDE[msCoName](../../includes/msconame-md.md)], Visualizador Naïve Bayes da [!INCLUDE[msCoName](../../includes/msconame-md.md)] e o Visualizador de Árvore da [!INCLUDE[msCoName](../../includes/msconame-md.md)]  
  
-   Conteúdo do modelo de mineração, do painel Detalhes do Nó do Visualizador de Árvore de Conteúdo Genérica da [!INCLUDE[msCoName](../../includes/msconame-md.md)]  
  
 Você pode copiar a representação completa do modelo de mineração ou apenas a parte que está visível no visualizador.  
  
> [!WARNING]  
>  Quando você copia um modelo usando o visualizador, ele não cria um novo objeto modelo. Para criar um novo modelo, você deve usar o assistente ou o Designer de Mineração de Dados. Para obter mais informações, consulte [Criar uma cópia de um modelo de mineração](../../analysis-services/data-mining/make-a-copy-of-a-mining-model.md).  
  
### Para copiar o modelo completo para a Área de Transferência  
  
1.  Na lista **Modelo de Mineração** na guia **Visualizador do Modelo de Mineração**, selecione o modelo de mineração que deseja exibir.  
  
2.  Selecione a guia apropriada, como a guia **Rede de Dependências** e, em seguida, clique em **Copiar Gráfico Inteiro** na barra de ferramentas da guia.  
  
### Para copiar a parte visível do modelo para a Área de Transferência  
  
1.  Na lista **Modelo de Mineração** na guia **Visualizador do Modelo de Mineração**, selecione o modelo de mineração que deseja exibir.  
  
2.  Selecione a guia apropriada, como a guia **Rede de Dependência** e, em seguida, aplique mais ou menos zoom para exibir o modelo no nível desejado.  
  
3.  Clique em **Copiar Exibição de Gráfico** na barra de ferramentas da guia selecionada.  
  
### Para copiar o conteúdo do modelo de mineração para a Área de Transferência  
  
1.  Na lista **Modelo de Mineração** na guia **Visualizador do Modelo de Mineração**, selecione o modelo de mineração que deseja exibir.  
  
2.  Na lista suspensa **Visualizador**, selecione **Visualizador de Árvore de Conteúdo Genérica da Microsoft**.  
  
3.  No painel **Legenda do Nó (ID Exclusiva)**, clique em um nó.  
  
4.  Clique com o botão direito do mouse no painel **Detalhes do Nó** e, em seguida, selecione **Selecionar tudo**.  
  
5.  Clique com o botão direito do mouse no painel **Detalhes do Nó** novamente e selecione **Copiar**.  
  
## Consulte também  
 [Tarefas e instruções do visualizador do modelo de mineração](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)  
  
  