---
title: "Criar Rela&#231;&#245;es | Microsoft Docs"
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
  - "sql13.dts.designer.createrelationships.f1"
ms.assetid: 6ebd305f-ffd2-4a1d-b24c-e28c151b94f5
caps.latest.revision: 21
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 21
---
# Criar Rela&#231;&#245;es
  Use a caixa de diálogo **Criar Relações** para editar mapeamentos entre as colunas de origem e as colunas da tabela de pesquisa que você configurou no Editor de Transformação Pesquisa Difusa, no Editor de Transformação Pesquisa e no Editor de Transformação Pesquisa de Termos.  
  
> [!NOTE]  
>  A caixa de diálogo **Criar Relações** exibe só as listas de **Coluna de Entrada** e **Coluna de Pesquisa** quando invocada do Editor de Transformação Pesquisa de Termos.  
  
 Para saber mais sobre as transformações que usam a caixa de diálogo **Criar Relações** , consulte [Fuzzy Lookup Transformation](../../../integration-services/data-flow/transformations/fuzzy-lookup-transformation.md), [Lookup Transformation](../../../integration-services/data-flow/transformations/lookup-transformation.md)e [Term Lookup Transformation](../../../integration-services/data-flow/transformations/term-lookup-transformation.md).  
  
## Opções  
 **Coluna de Entrada**  
 Selecione na lista de colunas de entrada disponíveis.  
  
 **Coluna de Pesquisa**  
 Selecione na lista de colunas de pesquisa disponíveis.  
  
 **Tipo de Mapeamento**  
 Selecione correspondência difusa ou exata.  
  
 Quando é usada correspondência difusa, as linhas serão consideradas duplicatas se forem suficientemente semelhantes em todas as colunas que têm tipo de correspondência difusa. Para obter resultados melhores na correspondência difusa, você pode especificar que algumas colunas devem usar a correspondência exata. Por exemplo, se souber que certa coluna não contém nenhum erro ou inconsistência, você poderá especificar correspondência exata para ela, de forma que só as linhas que contêm valores idênticos nessa coluna sejam consideradas como possíveis duplicatas. Isso aumenta a exatidão da correspondência difusa em outras colunas.  
  
 **Sinalizadores de Comparação**  
 Para obter mais informações sobre as opções de comparação de cadeias de caracteres, consulte [Comparando dados de cadeia de caracteres](../../../integration-services/data-flow/comparing-string-data.md).  
  
 **Similaridade Mínima**  
 Defina o limite de similaridade no nível de coluna usando o controle deslizante. Quanto mais próximo de 1 for o valor, maior deverá ser a semelhança entre o valor de pesquisa e o valor da origem para a qualificação de correspondências. Aumentar o limite pode melhorar a velocidade de correspondência, pois menos registros candidatos precisam ser considerados.  
  
 **Alias de Saída de Similaridade**  
 Especifique o nome da nova coluna de saída que conterá as pontuações de similaridade da coluna selecionada. Se você deixar este valor vazio, a coluna de saída não será criada.  
  
## Consulte também  
 [Referência de mensagens e erros do Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Editor de Transformação Pesquisa Difusa &#40;guia Colunas&#41;](../../../integration-services/data-flow/transformations/fuzzy-lookup-transformation-editor-columns-tab.md)   
 [Editor de Transformação Pesquisa &#40;Guia Colunas&#41;](../../../integration-services/data-flow/transformations/lookup-transformation-editor-columns-page.md)   
 [Editor de Transformação Pesquisa de Termos &#40;Guia Pesquisa de Termos&#41;](../../../integration-services/data-flow/transformations/term-lookup-transformation-editor-term-lookup-tab.md)  
  
  