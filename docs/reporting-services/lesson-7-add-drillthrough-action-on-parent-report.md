---
title: "Lição 7: Adicionar uma ação de detalhamento ao relatório pai | Microsoft Docs"
ms.custom: 
ms.date: 05/18/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: reporting-services
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
ms.assetid: aad2da1a-d7b1-4afa-a66a-1ff102e8306f
caps.latest.revision: "13"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7f894423bef4c87e53256e496ebd6f452591c4d5
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2018
---
# <a name="lesson-7-add-drillthrough-action-on-parent-report"></a>Lição 7: Adicionar ação de detalhamento ao relatório pai
Depois que você adicionar um controle ReportViewer para o aplicativo de site, a próxima etapa será adicionar uma ação de detalhamento no relatório pai.  
  
### <a name="to-add-drillthrough-action-on-the-parent-report"></a>Para adicionar uma ação de detalhamento no relatório pai  
  
1.  Vá para o relatório pai.  
  
2.  Selecione a caixa de texto que contém o valor **Nome**.  
  
3.  Clique com o botão direito do mouse na caixa de texto e selecione **Propriedades da Caixa de Texto**.  
  
4.  Vá para a guia **Ação** e selecione a opção **Ir para o relatório** .  
  
5.  Insira o nome do relatório filho na seção **Especificar um relatório** .  
  
    > [!NOTE]
    > Não inclua a extensão de arquivo do nome do relatório.  
  
6.  Clique em **Adicionar** na seção **Usar estes parâmetros para executar o relatório** .  
  
7.  Digite **productid** na caixa **Nome** e selecione **ProductID** na lista suspensa **Valor** .  
  
8.  Selecione **OK** para concluir.  
  
## <a name="next-task"></a>Próxima tarefa  
Você adicionou uma ação de detalhamento no relatório pai. Em seguida, você criará um filtro de dados para a tabela de dados definida para o relatório filho. Consulte [Lição 8: Criar um filtro de dados](../reporting-services/lesson-8-create-a-data-filter.md).  
  
  
  

