---
title: "Usando dados de uma tabela aninhada como entrada para um gr&#225;fico de precis&#227;o | Microsoft Docs"
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
  - "Gráfico de precisão de mineração [Analysis Services], tabelas aninhadas"
  - "Gráfico de precisão de mineração [Analysis Services], tabelas de entrada"
  - "tabelas aninhadas"
  - "adicionando tabelas aninhadas"
ms.assetid: 162e0686-ada3-4dd3-9151-9589926e6613
caps.latest.revision: 24
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 24
---
# Usando dados de uma tabela aninhada como entrada para um gr&#225;fico de precis&#227;o
  Quando você testar a precisão de um modelo de mineração usando dados externos, se o modelo de mineração contiver tabelas aninhadas, os dados externos também deverão contar uma tabela de casos e uma tabela aninhada associada.  
  
 Este tópico descreve como trabalhar com tabelas aninhadas usadas para testar modelos, como mapear tabelas de casos e aninhadas no modo e nos dados externos e como aplicar um filtro a uma tabela aninhada.  
  
 Ao trabalhar com tabelas aninhadas, lembre-se destas dicas:  
  
-   Se você selecionar a opção **Usar casos de teste do modelo de mineração** ou **Usar casos de teste da estrutura de mineração**, não será necessário especificar uma tabela de casos ou aninhada. Com essas opções, a definição dos dados de teste é armazenada na estrutura de mineração e os dados de teste serão selecionados automaticamente quando você criar o gráfico de precisão.  
  
-   Se já existir uma relação entre a tabela de caso e a tabela aninhada na fonte de dados, as colunas da estrutura de mineração serão mapeadas automaticamente para as colunas que têm o mesmo nome na tabela de entrada.  
  
-   Não será possível selecionar uma tabela aninhada até que você especifique a tabela de casos. Além disso, você não pode especificar uma tabela aninhada como uma entrada, a menos que o modelo de mineração também use uma estrutura de tabela de casos e tabela aninhada.  
  
### Usar uma tabela aninhada como entrada para um gráfico de precisão  
  
1.  Clique duas vezes na estrutura de mineração para abri-la no Designer de Mineração de Dados.  
  
2.  Selecione a guia **Gráfico de Precisão da Mineração** e, em seguida, selecione a guia **Seleção de Entrada** .  
  
3.  Em **Selecionar conjunto de dados a ser usado para o Gráfico de Precisão**, selecione a opção **Especificar um conjunto de dados diferente**.  
  
4.  Clique no botão Procurar **(…)** para escolher um conjunto de dados externo em uma lista de exibições da fonte de dados do servidor atual.  
  
5.  Clique em **Selecionar Tabela de Casos**. Na caixa de diálogo **Selecionar Tabela** , escolha a tabela na exibição da fonte de dados que contém os dados do caso e, em seguida, clique em **OK**.  
  
6.  Clique em **Selecionar Tabela Aninhada**. Na caixa de diálogo **Selecionar Tabela** , selecione a tabela que contém os dados aninhados e, em seguida, clique em **OK**.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     Se você precisar modificar a relação entre a tabela aninhada e a tabela de casos, clique em **Modificar Junção** para abrir a caixa de diálogo **Criar Relação** .  
  
## Consulte também  
 [Escolher e mapear dados de testes modelo](../../analysis-services/data-mining/choose-and-map-model-testing-data.md)   
 [Aplicar filtros a dados de testes de modelo](../../analysis-services/data-mining/apply-filters-to-model-testing-data.md)  
  
  