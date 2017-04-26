---
title: "Excluir um filtro de um modelo de minera&#231;&#227;o | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "filtros [Analysis Services]"
ms.assetid: 91220b21-adbc-49a9-b200-8bf0a724eff1
caps.latest.revision: 13
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 13
---
# Excluir um filtro de um modelo de minera&#231;&#227;o
  Quando você cria um filtro em um modelo de mineração, pode criar modelos em um subconjunto dos dados na exibição da fonte de dados. Os filtros também são úteis para testar a precisão do modelo em um subconjunto dos dados originais.  
  
 Porém, você deve excluir o filtro se quiser exibir novamente o conjunto completo de casos. Este procedimento descreve como remover as condições em um filtro ou excluir completamente o filtro.  
  
### Para excluir uma condição de um filtro em um modelo de mineração  
  
1.  Em [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], no Gerenciador de Soluções, clique na estrutura de mineração que contém o modelo de mineração a filtrar.  
  
2.  Clique na guia **Modelos de Mineração** .  
  
3.  Selecione o modelo, e clique com o botão direito do mouse para abrir o menu de atalho.  
  
     –ou–  
  
     Selecione o modelo. No menu **Modelo de Mineração** , selecione **Definir Filtro de Modelos**.  
  
4.  Na caixa de diálogo **Filtro de Modelos**, clique com o botão direito do mouse na linha da grade que contém a condição a excluir.  
  
5.  Selecione **Excluir**.  
  
### Para desmarcar o filtro em um modelo de mineração na caixa de diálogo Editor de Filtro  
  
-   Na caixa de diálogo **Editor de Filtro**, clique com o botão direito do mouse em uma linha na grade e selecione **Excluir Tudo**.  
  
## Trabalhando com os filtros de modelos usando a janela Propriedades  
 Para excluir o filtro inteiro, você não precisa abrir as caixas de diálogo do editor de filtro. As condições de filtro que você criou estão disponíveis na propriedade **Filter** do modelo de mineração.  
  
> [!NOTE]  
>  Você pode exibir as propriedades de um modelo de mineração no [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], mas não no [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
#### Para desmarcar o filtro em um modelo de mineração no Gerenciador de Soluções  
  
1.  No Gerenciador de Soluções, clique no modelo de mineração que contém o filtro.  
  
2.  Na janela **Propriedades**, clique com o botão direito do mouse no texto do filtro na propriedade **Filtro** e marque **Selecionar Tudo**.  
  
3.  Pressione a tecla Backspace ou Delete.  
  
## Consulte também  
 [Detalhar dados do caso a partir do modelo de mineração](../../analysis-services/data-mining/drill-through-to-case-data-from-a-mining-model.md)   
 [Tarefas e instruções do modelo de mineração](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [Filtros para modelos de mineração &#40;Analysis Services – Mineração de dados&#41;](../../analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)  
  
  