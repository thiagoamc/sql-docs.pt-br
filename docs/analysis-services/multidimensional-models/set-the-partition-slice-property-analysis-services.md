---
title: "Definir a propriedade Fatia de Parti&#231;&#227;o (Analysis Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "partições [Analysis Services], fatias de dados"
  - "fatias de dados [Analysis Services]"
ms.assetid: 507b91e5-7f85-4c22-be97-4d7a676e6667
caps.latest.revision: 33
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 33
---
# Definir a propriedade Fatia de Parti&#231;&#227;o (Analysis Services)
  Uma fatia de dados é um recurso de otimização importante que ajuda a direcionar consultas aos dados das partições apropriadas. Definir explicitamente a propriedade Fatia pode melhorar o desempenho da consulta, substituindo as fatias padrão geradas para partições MOLAP e HOLAP. Além disso, a propriedade Fatia fornece uma verificação de validação adicional ao processar a partição.  
  
 É possível especificar uma fatia de dados após criar uma partição, mas antes de processá-la, usando a propriedade Fatia. Na guia Partições, expanda um grupo de medidas, clique com o botão direito do mouse em uma partição e selecione **Propriedades**.  
  
 Para obter uma explicação sobre os benefícios da fatia de dados, consulte [Definir a fatia na partição de cubo SSAS](http://go.microsoft.com/fwlink/?LinkId=317783).  
  
## Definindo uma fatia  
 Os valores válidos para a propriedade Fatia são um membro, conjunto ou tupla MDX. Os seguintes exemplos ilustram a sintaxe de fatia válida:  
  
|Fatia|Membro, conjunto ou tupla|  
|-----------|--------------------------|  
|[Date].[Calendar].[Calendar Year].&[2010]|Especifique essa fatia em uma partição contendo fatos do ano 2010 (supondo que o modelo inclua uma dimensão de data com a hierarquia de ano civil, onde 2010 seja um membro). Embora a cláusula WHERE de origem da partição ou a tabela talvez já seja filtrada por 2010, especificar a Fatia fornece uma verificação adicional durante o processamento, bem como digitalizações mais direcionadas durante a execução da consulta.|  
|{ [Sales Territory].[Sales Territory Country].&[Australia], [Sales Territory].[Sales Territory Country].&[Canada] }|Especifique essa fatia em uma partição contendo fatos que incluam informações de território de vendas. Uma fatia pode ser um conjunto MDX que consiste em dois ou mais membros.|  
|[Measures].[Sales Amount Quota] > '5000'|Essa fatia mostra uma expressão MDX.|  
  
 A fatia de dados de uma partição deve refletir, com a maior integridade possível, os dados da partição. Por exemplo, se uma partição estiver limitada aos dados de 2012, a fatia de dados da partição deve especificar o membro 2012 da dimensão Tempo. Nem sempre é possível especificar uma fatia de dados que reflita o conteúdo exato de uma partição. Por exemplo, se uma partição contiver dados apenas para Janeiro e Fevereiro, mas os níveis da dimensão Tempo forem Ano, Trimestre e Mês, o Assistente para Partições não pode selecionar os membros Janeiro e Fevereiro ao mesmo tempo. Nesses casos, selecione o pai dos membros que refletem o conteúdo da partição. Nesse exemplo, selecione Trimestre 1.  
  
> [!NOTE]  
>  Observe que não há suporte para as funções MDX dinâmicas (como [Generate &#40;MDX&#41;](../../mdx/generate-mdx.md) ou [Except &#40;MDX&#41;](../Topic/Except%20\(MDX\).md)) na propriedade Slice das partições. Você deve definir a fatia usando tuplas explícitas ou referências de membro.  
>   
>  Por exemplo, em vez de usar o operador de intervalo (:) para definir um intervalo, você precisaria enumerar cada membro por anos específicos.  
>   
>  Se você precisa definir uma fatia complexa, recomendamos definir as tuplas na fatia usando um script XMLA Alter. Em seguida, você pode usar a ferramenta de linha de comando ascmd ou a [Tarefa Executar DDL do Analysis Services](../../integration-services/control-flow/analysis-services-execute-ddl-task.md) no Integration Services para executar o script e criar o conjunto especificado de membros imediatamente antes de processar a partição.  
  
## Consulte também  
 [Criar e gerenciar uma partição local &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/create-and-manage-a-local-partition-analysis-services.md)  
  
  