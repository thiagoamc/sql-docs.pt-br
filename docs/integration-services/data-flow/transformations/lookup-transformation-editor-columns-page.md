---
title: "Editor da Transforma&#231;&#227;o Pesquisa (p&#225;gina Colunas) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.lookuptransformation.columns.f1"
helpviewer_keywords: 
  - "Editor da Transformação Pesquisa"
ms.assetid: 690ffef5-fd59-4e95-a27d-4fcf0d6b1c0b
caps.latest.revision: 39
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 39
---
# Editor da Transforma&#231;&#227;o Pesquisa (p&#225;gina Colunas)
  Use a página **Colunas** da caixa de diálogo **Editor da Transformação Pesquisa** para especificar a junção entre a tabela de origem e a tabela de referência, e para selecionar as colunas de pesquisa a partir da tabela de referência.  
  
 Para saber mais sobre a transformação Pesquisa, consulte [Lookup Transformation](../../../integration-services/data-flow/transformations/lookup-transformation.md).  
  
## Opções  
 **Colunas de Entrada Disponíveis**  
 Exiba a lista das colunas de entrada disponíveis. As colunas de entrada são as colunas no fluxo de dados de uma origem conectada. As colunas de entrada e de pesquisa devem ter tipos de dados correspondentes.  
  
 Use uma operação arrastar e soltar para mapear as colunas de entrada disponíveis para as colunas de pesquisa.  
  
 Você também pode mapear as colunas de entrada para as colunas de pesquisa usando o teclado, destacando a coluna na tabela **Colunas de Entrada Disponíveis** , pressionando a tecla Aplicativo e clicando em **Editar Mapeamentos**.  
  
 **Colunas de Pesquisa Disponíveis**  
 Exiba a lista de colunas de pesquisa. As colunas de pesquisa são as colunas na tabela de referência que permitem pesquisar os valores que correspondem às colunas de entrada.  
  
 Use uma operação arrastar e soltar para mapear as colunas de pesquisa disponíveis para as colunas de entrada.  
  
 Use as caixas de seleção para selecionar as colunas de pesquisa na tabela de referência nas quais serão executadas as operações de pesquisa.  
  
 Você também pode mapear as colunas de pesquisa para as colunas de entrada usando o teclado, destacando a coluna na tabela **Colunas de Pesquisa Disponíveis** , pressionando a tecla Aplicativo e clicando em **Editar Mapeamentos**.  
  
 **coluna de pesquisa**  
 Exiba as colunas de pesquisa selecionadas. As escolhas são refletidas nas caixas de seleção da tabela **Colunas de Pesquisa Disponíveis** .  
  
 **Operação de Pesquisa**  
 Selecione uma operação de pesquisa da lista a ser executada na coluna de pesquisa.  
  
 **Alias de Saída**  
 Digite um alias para a saída de cada coluna de pesquisa. O padrão é o nome da coluna de pesquisa; entretanto, é possível selecionar qualquer nome descritivo exclusivo.  
  
## Consulte também  
 [Editor de Transformação Pesquisa &#40;Página Geral&#41;](../../../integration-services/data-flow/transformations/lookup-transformation-editor-general-page.md)   
 [Editor de Transformação Pesquisa &#40;Página Conexão&#41;](../../../integration-services/data-flow/transformations/lookup-transformation-editor-connection-page.md)   
 [Editor de Transformação Pesquisa &#40;Página Avançado&#41;](../../../integration-services/data-flow/transformations/lookup-transformation-editor-advanced-page.md)   
 [Editor de Transformação Pesquisa &#40;Página Saída de Erro&#41;](../../../integration-services/data-flow/transformations/lookup-transformation-editor-error-output-page.md)   
 [Transformação Pesquisa Difusa](../../../integration-services/data-flow/transformations/fuzzy-lookup-transformation.md)  
  
  