---
title: "Lição 14: Implantar | Microsoft Docs"
ms.custom: 
ms.date: 03/27/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 24863a8a-9017-415a-a97b-fbac76ed0675
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 29a05dfbeea281b2468b95e69b458d4948f7f624
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/23/2018
---
# <a name="lesson-13-deploy"></a>Lição 13: implantar
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

Nesta lição, você irá configurar propriedades de implantação. especificando um local ou instância de servidor do Azure e um nome para o modelo. Em seguida, você implantará o modelo a essa instância. Depois que o modelo é implantado, os usuários podem se conectar a ele usando um aplicativo cliente de relatório. Para saber mais sobre a implantação, consulte [implantação de solução de modelo Tabular](../analysis-services/tabular-models/tabular-model-solution-deployment-ssas-tabular.md) e [implantar no Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-deploy).  
  
Tempo estimado para concluir esta lição: **5 minutos**  
  
## <a name="prerequisites"></a>Prerequisites  
Este tópico faz parte de um tutorial de modelo de tabela, que deve ser concluído na ordem. Antes de executar as tarefas nesta lição, você deve ter concluído a lição anterior: [lição 12: analisar no Excel](../analysis-services/lesson-12-analyze-in-excel.md).  
  
## <a name="deploy-the-model"></a>Implantar o modelo  
  
#### <a name="to-configure-deployment-properties"></a>Para configurar propriedades de implantação  
  
1.  Em **Solution Explorer**, com o botão direito do **de vendas pela Internet AW** do projeto e, em seguida, clique em **propriedades**.  
  
2.  No **páginas de propriedades de vendas de Internet AW** caixa de diálogo **o servidor de implantação**, no **Server** propriedade, digite o nome de um servidor de serviços de análise do Azure ou um instância de servidor local executando no modo de tabela. Essa será a instância de servidor que seu modelo será implantado.  

    ![aas-deploy-deployment-server-property](../analysis-services/media/aas-deploy-deployment-server-property.png)
 
    > [!IMPORTANT]  
    > Você deve ter permissões de administrador na remoto do Analysis Services instância em ordem para implantar a ele.  
  
3.  No **banco de dados** propriedade, digite **Adventure Works Internet Sales**.  
  
4.  No **nome do modelo** propriedade, digite **modelo de vendas do Adventure Works Internet**.  
  
5.  Verifique as seleções e clique em **OK**.  
  
#### <a name="to-deploy-the-adventure-works-internet-sales-tabular-model"></a>Para implantar o modelo de tabela de vendas pela Internet da Adventure Works.  
  
1.  Em **Solution Explorer**, com o botão direito do **de vendas pela Internet AW** projeto > **criar**.  

2.  Clique com botão direito do **de vendas pela Internet AW** projeto > **implantar**.

    Ao implantar o Azure Analysis Services, provavelmente será solicitado a inserir sua conta. Insira sua conta organizacional e uma senha, por exemplo nancy@adventureworks.com. Essa conta deve estar em administradores na instância do servidor.
  
    A caixa de diálogo Implantar aparecerá com o status de implantação dos metadados e cada tabela incluída no modelo.  
    
    ![aas-deploy-status](../analysis-services/media/aas-deploy-status.png)
  
3. Quando a implantação for concluída com êxito, continue e clique em **Fechar**.  
  
## <a name="conclusion"></a>Conclusão  
Parabéns! Você terminar de criar e implantar seu primeiro modelo de tabela do Analysis Services. Este tutorial ajudou você a concluir as tarefas mais comuns da criação de um modelo de tabela. Agora que o Modelo de Vendas pela Internet do Adventure Works está implantado, você pode usar o SQL Server Management Studio para gerenciar o modelo; crie scripts de processo e um plano de backup. Os usuários agora também podem se conectar ao modelo usando um aplicativo cliente de relatório, como o Microsoft Excel ou Power BI.  

![as-tabular-lesson13-ssms](../analysis-services/media/as-tabular-lesson13-ssms.png)
  
  
## <a name="see-also"></a>Consulte também  
[Modo DirectQuery](../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)  
[Configurar propriedades de implantação e modelagem de dados padrão](../analysis-services/tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md)  
[Bancos de dados de modelo de tabela](../analysis-services/tabular-models/tabular-model-databases-ssas-tabular.md)  
  
  
  ## <a name="whats-next"></a>O que vem a seguir?
*  [Lição suplementar - implementar a segurança dinâmica usando filtros de linha](../analysis-services/supplemental-lesson-implement-dynamic-security-by-using-row-filters.md).

*  [Complementares lição - configurar propriedades de relatório para relatórios do Power View](../analysis-services/supplemental-lesson-configure-reporting-properties-for-power-view-reports.md).
