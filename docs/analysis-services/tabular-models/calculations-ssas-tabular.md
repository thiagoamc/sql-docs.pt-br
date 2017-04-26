---
title: "C&#225;lculos (SSAS tabular) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 738816e3-0e1d-44a5-8d1b-81068dce8ac0
caps.latest.revision: 19
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 19
---
# C&#225;lculos (SSAS tabular)
  Depois de importar dados para o modelo, será possível adicionar cálculos para agregar, filtrar, estender, combinar e proteger esses dados. Os modelos tabulares usam o DAX (Data Analysis Expressions), uma linguagem de fórmula para criar cálculos personalizados. Nos modelos de tabela, os cálculos que você cria usando fórmulas DAX são usados em *Colunas Calculadas*, *Medidas*e *Filtros de Linha*.  
  
## Nesta seção  
  
|Tópico|Description|  
|-----------|-----------------|  
|[Noções básicas sobre DAX em modelos de tabela &#40;SSAS de Tabela&#41;](../../analysis-services/tabular-models/understanding-dax-in-tabular-models-ssas-tabular.md)|Descreve a linguagem de fórmula DAX usada para criar cálculos para colunas calculadas, medidas e filtros de linha em modelos de tabela.|  
|[Compatibilidade de Fórmula DAX no modo DirectQuery (SQL Server Analysis Services)](http://msdn.microsoft.com/pt-br/981b6a68-434d-4db6-964e-d92f8eb3ee3e)|Descreve as diferenças, lista as funções que não têm suporte no modo DirectQuery e lista as funções com suporte, mas que poderiam retornar resultados diferentes.|  
|[Referência de DAX (Data Analysis Expressions)](http://msdn.microsoft.com/pt-br/70a82136-0926-4a91-bcb3-e18e82593b0d)|Esta seção fornece descrições detalhadas de sintaxe DAX, operadores e funções.|  
  
> [!NOTE]  
>  Esta seção não contém tarefas passo a passo para criar cálculos. Como os cálculos são especificados em colunas calculadas, medidas e filtros de linha (em funções), as instruções sobre onde criar fórmulas DAX são fornecidas em tarefas relacionadas a esses recursos. Para obter mais informações, consulte [Criar uma coluna calculada &#40;SSAS de Tabela&#41;](../../analysis-services/tabular-models/create-a-calculated-column-ssas-tabular.md), [Criar e gerenciar medidas &#40;SSAS de Tabela&#41;](../../analysis-services/tabular-models/create-and-manage-measures-ssas-tabular.md) e [Criar e gerenciar funções &#40;SSAS de Tabela&#41;](../../analysis-services/tabular-models/create-and-manage-roles-ssas-tabular.md).  
  
> [!NOTE]  
>  Apesar de o DAX também poder ser usado para consultar um modelo de tabela, tópicos desta seção destacam especificamente o uso de fórmulas DAX para criar cálculos.  
  
  