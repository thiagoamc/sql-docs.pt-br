---
title: "Definir a orientação da caixa de texto (Construtor de Relatórios e SSRS) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: report-design
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64bd53f4-2f31-4732-8c2e-64c7b54b6972
caps.latest.revision: "9"
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 9635769283ed34f997b0a16b4240e69ae37d3709
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2018
---
# <a name="set-text-box-orientation-report-builder-and-ssrs"></a>Definir a orientação da caixa de texto (Construtor de Relatórios e SSRS)
Em um relatório paginado do [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] , você pode girar uma caixa de texto em direções diferentes:   
* Horizontalmente   
* Verticalmente (rotação de 90 graus, com texto lido de cima para baixo)  
* Rotação de 270 graus (texto lido de baixo para cima).   
  
Como a caixa de texto é girada, e não o texto, a rotação se aplica a todo o texto na caixa de texto. Não é possível especificar direções diferentes para partes do texto. Dimensione manualmente a largura da coluna e a altura da linha para acomodar o texto girado.  
  
 A propriedade WritingMode, que você usa para especificar a orientação do texto, não está na caixa de diálogo **Propriedades da Caixa de Texto** . Abra o painel Propriedades e defina a propriedade.   
  
## <a name="to-rotate-text"></a>Para girar texto  
  
1.  Crie um relatório ou abra um relatório existente e [adicione uma caixa de texto](../../reporting-services/report-design/add-move-or-delete-a-text-box-report-builder-and-ssrs.md) à superfície de design.  
  
3.  Marque a caixa de texto que deseja girar.  
  
2.  Se o painel Propriedades não estiver aberto, na guia **Exibir** , marque a caixa de seleção **Propriedades** .  
  
4.  No painel Propriedades, encontre a propriedade WritingMode e selecione a orientação do texto a ser aplicada à caixa de texto.  
  
    > [!NOTE]  
    >  Quando as propriedades no painel Propriedades estiverem organizadas em categorias, WritingMode estará na categoria **Localização** .  
  
5.  Na caixa de listagem, selecione **Horizontal**, **Vertical**ou **Rotate270**.  
  
## <a name="see-also"></a>Consulte Também  
 [Caixas de texto &#40;Construtor de Relatórios e SSRS&#41;](../../reporting-services/report-design/text-boxes-report-builder-and-ssrs.md)   
 [Tutorial: Formatar texto &#40;Construtor de Relatórios&#41;](../../reporting-services/tutorial-format-text-report-builder.md)  
  
  
