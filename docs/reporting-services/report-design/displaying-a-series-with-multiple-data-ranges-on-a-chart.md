---
title: "Exibindo uma s&#233;rie com v&#225;rios intervalos de dados em um gr&#225;fico (Construtor de Relat&#243;rios e SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 45da3d39-278e-4760-a4b3-9932c9547cf2
caps.latest.revision: 11
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 11
---
# Exibindo uma s&#233;rie com v&#225;rios intervalos de dados em um gr&#225;fico (Construtor de Relat&#243;rios e SSRS)
  O gráfico usará os valores mínimo e máximo de uma série para calcular a escala do eixo. Quando uma série do gráfico contiver mais que um intervalo de dados, os pontos de dados poderão ficar obscuros e apenas alguns deles poderão ser visualizados facilmente no gráfico. Por exemplo, suponha que um relatório exiba informações sobre o total de vendas diário de um período de 30 dias.  
  
 ![Gráfico com vários intervalos de dados](../../reporting-services/report-design/media/rs-multipledatarangeschart.gif "Gráfico com vários intervalos de dados")  
  
 Na maior parte do mês, as vendas ficam entre 10 e 40. No entanto, uma campanha publicitária de uma semana provocou um aumento repentino nas vendas no início de abril. Essa alteração nos dados de vendas produz uma distribuição irregular dos pontos de dados que reduz a legibilidade geral do gráfico.  
  
 Existem maneiras diferentes de melhorar a legibilidade:  
  
-   **Habilitar quebras de escala**. Se os dados formarem dois ou mais conjuntos de intervalos de dados, use uma quebra de escala para remover a lacuna entre os intervalos. Uma quebra de escala é uma faixa desenhada em uma área de plotagem para indicar a quebra entre os valores altos e baixos de uma série.  
  
-   **Filtrar valores desnecessários**. Se houver pontos de dados que estão encobrindo um intervalo de dados importante que deve aparecer no gráfico, remova os pontos indesejados usando um filtro de relatório. Para obter informações sobre como adicionar um filtro ao gráfico no [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], consulte [Adicionar filtros de conjunto de dados, de região de dados e de grupo &#40;Construtor de Relatórios e SSRS&#41;](../../reporting-services/report-design/add dataset filters, data region filters, and group filters.md).  
  
-   **Plotar cada intervalo de dados como uma série separada para comparar várias séries**. Se houver dois ou mais intervalos de dados, considere separá-los em séries distintas. Para obter mais informações, consulte [Várias séries em um gráfico &#40;Construtor de Relatórios e SSRS&#41;](../../reporting-services/report-design/multiple-series-on-a-chart-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## Exibindo vários intervalos de dados usando quebras de escala  
 Quando você habilita uma quebra de escala, o gráfico calcula onde desenhar uma linha no gráfico. Deve haver espaço suficiente entre os intervalos para desenhar uma quebra de escala. Por padrão, a quebra de escala poderá ser adicionada somente se houver uma separação entre os intervalos de dados de pelo menos 25% do gráfico.  
  
 ![Gráfico com quebra de escala](../../reporting-services/report-design/media/rs-multipledatarangeschart-scalebreak.gif "Gráfico com quebra de escala")  
  
> [!NOTE]  
>  Não é possível especificar onde posicionar a quebra de escala em um gráfico. No entanto, você pode modificar como ela será calculada, o que será descrito adiante neste tópico.  
  
 Se você habilitar uma quebra de escala mas ela não aparecer, mesmo que haja distância suficiente entre os intervalos de dados, será possível definir a propriedade CollapsibleSpaceThreshold com um valor inferior a 25. CollapsibleSpaceThreshold especifica o percentual de espaço recolhível necessário entre os intervalos de dados. Para obter mais informações, consulte [Adicionar quebras de escala a um gráfico &#40;Construtor de Relatórios e SSRS&#41;](../../reporting-services/report-design/add-scale-breaks-to-a-chart-report-builder-and-ssrs.md).  
  
 Os gráficos suportam até cinco quebras de escala por gráfico; no entanto, exibir mais de uma quebra de escala pode deixar o gráfico ilegível. Se houver dois ou mais intervalos de dados, considere o uso de outro método para exibir esses dados. Para obter mais informações, consulte [Várias séries em um gráfico &#40;Construtor de Relatórios e SSRS&#41;](../../reporting-services/report-design/multiple-series-on-a-chart-report-builder-and-ssrs.md).  
  
## Cenários de quebra de escala não suportados  
 As quebras de escala não são suportadas nos seguintes cenários:  
  
-   O gráfico está habilitado para 3D.  
  
-   Um eixo de valor logarítmico foi especificado.  
  
-   O eixo de valor mínimo ou máximo foi definido explicitamente.  
  
-   O tipo de gráfico é polar, radar, pizza, anel, funil, pirâmide ou algum gráfico empilhado.  
  
 Um exemplo de gráfico com quebras de escala está disponível como um relatório de exemplo. Para obter mais informações sobre como baixar esse relatório de exemplo e outros, consulte [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][(Relatórios de exemplo do Construtor de relatórios e Designer de relatórios) do](http://go.microsoft.com/fwlink/?LinkId=198283).  
  
## Consulte também  
 [Várias séries em um gráfico &#40;Construtor de Relatórios e SSRS&#41;](../../reporting-services/report-design/multiple-series-on-a-chart-report-builder-and-ssrs.md)   
 [Formatando um gráfico &#40;Construtor de Relatórios e SSRS&#41;](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)   
 [Efeitos 3D, bisel e outros efeitos em um gráfico &#40;Construtor de Relatórios e SSRS&#41;](../../reporting-services/report-design/3d-bevel-and-other-effects-in-a-chart-report-builder-and-ssrs.md)   
 [Gráficos &#40;Construtor de Relatórios e SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
 [Caixa de diálogo Propriedades do Eixo, Opções do Eixo &#40;Construtor de Relatórios e SSRS&#41;](../Topic/Axis%20Properties%20Dialog%20Box,%20Axis%20Options%20\(Report%20Builder%20and%20SSRS\).md)   
 [Coletar fatias pequenas em um gráfico de pizza &#40;Construtor de Relatórios e SSRS&#41;](../../reporting-services/report-design/collect-small-slices-on-a-pie-chart-report-builder-and-ssrs.md)  
  
  