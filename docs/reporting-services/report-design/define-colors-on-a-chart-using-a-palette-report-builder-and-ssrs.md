---
title: "Definir cores em um gr&#225;fico usando uma paleta (Construtor de Relat&#243;rios e SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d95efc22-5a32-43d4-9bd2-12753e7fd395
caps.latest.revision: 6
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 6
---
# Definir cores em um gr&#225;fico usando uma paleta (Construtor de Relat&#243;rios e SSRS)
  Você pode alterar a paleta de cores para um gráfico, selecionando uma paleta predefinida ou definindo uma paleta personalizada. Paletas personalizadas são específicas para relatórios.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### Para alterar as cores no gráfico usando uma paleta de cores interna  
  
1.  Abra o painel Propriedades.  
  
2.  Na superfície de design, clique no gráfico. São exibidas as propriedades do objeto de gráfico no painel Propriedades.  
  
     O nome do objeto (**Chart1** por padrão) é exibido na lista suspensa na parte superior do painel Propriedades.  
  
3.  Na seção **Gráfico**, da propriedade Palette, selecione uma paleta nova na lista suspensa.  
  
    > [!NOTE]  
    >  Você não pode alterar as cores nem classificar em uma paleta predefinida.  
  
### Para definir suas próprias cores no gráfico usando uma paleta de cores personalizada  
  
1.  Abra o painel Propriedades.  
  
2.  Na superfície de design, clique no gráfico. São exibidas as propriedades do objeto de gráfico no painel Propriedades.  
  
3.  Na seção **Gráfico** , para a propriedade **Palette** , selecione **Personalizada**.  
  
4.  Na propriedade CustomPaletteColors, clique no botão Editar Coleção (**...**). O **Editor de Coleção ReportColorExpression** é aberto.  
  
5.  Clique em **Adicionar** para adicionar uma cor. Selecione uma cor na lista suspensa ou selecione Expressão e especifique um valor hexadecimal para uma cor específica, como ff6600 para "Laranja".  
  
     Para obter mais informações sobre valores hexadecimais, consulte [Tabela de Cores](http://go.microsoft.com/fwlink/?linkid=9258) n MSDN.  
  
6.  Clique em **Adicionar** para adicionar mais cores à paleta.  
  
7.  Após concluir, clique em **OK**.  
  
 Se você estiver usando uma paleta personalizada, poderá alterar a ordem das cores para alterar a cor de séries diferentes no gráfico.  
  
## Consulte também  
 [Formatando as cores da série em um gráfico &#40;Construtor de Relatórios e SSRS&#41;](../../reporting-services/report-design/formatting-series-colors-on-a-chart-report-builder-and-ssrs.md)   
 [Gráficos &#40;Construtor de Relatórios e SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
 [Especificar cores consistentes em gráficos com várias formas &#40;Construtor de Relatórios e SSRS&#41;](../../reporting-services/report-design/specify-consistent-colors-across-multiple-shape-charts-report-builder-and-ssrs.md)  
  
  