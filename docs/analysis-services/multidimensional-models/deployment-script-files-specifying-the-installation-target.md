---
title: Especificar o destino de instalação | Microsoft Docs
ms.custom: ''
ms.date: 03/27/2018
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining - "setup-install"
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- input files [Analysis Services]
- installation targets [Analysis Services]
- Analysis Services deployments, installation targets
- Analysis Services Deployment Wizard, installation targets
- deploying [Analysis Services], installation targets
- modifying installation targets
ms.assetid: cb706817-6f63-4771-92c3-b70030bbce3d
caps.latest.revision: ''
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c9977badf4e1e8e05cb35ed8828d4cc4ae12cfae
ms.sourcegitcommit: d6881107b51e1afe09c2d8b88b98d075589377de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/28/2018
---
# <a name="deployment-script-files---specifying-the-installation-target"></a>Arquivos de Script de implantação - especificar o destino de instalação
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  O [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Assistente de implantação do lê as informações de destino da instalação de \< *nome do projeto*>. deploymenttargets arquivo. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]cria esse arquivo quando você cria o [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] projeto. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] usa o banco de dados e o servidor especificado no **implantação** página do  *\<nome do projeto >* **páginas de propriedades** caixa de diálogo para criar o \< *nome do projeto*> arquivo. targets.  
  
## <a name="modifying-the-installation-target-for-deployment"></a>Modificando o destino de instalação para a implantação  
 Em alguns casos, talvez seja necessário implantar um projeto do [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] em um banco de dados ou instância do [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] diferente do especificado na página **Implantação** . Por exemplo, você talvez queira implantar o projeto em um servidor para teste antes da implantação e, em seguida, implantá-lo em um servidor de produção após a conclusão do teste. Também é possível implantar um projeto concluído e testado em vários servidores de produção em um cluster de Balanceamento de Carga de Rede ou em um servidor de preparação e em um de produção.  
  
 Para implantar um projeto do [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] em um banco de dados ou instância do [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] diferente, altere o destino de instalação no arquivo de entrada usando um dos métodos descritos no procedimento a seguir.  
  
#### <a name="to-change-the-installation-target-after-the-input-files-have-been-generated"></a>Para alterar o destino de instalação depois que os arquivos de entrada tiverem sido gerados  
  
-   Execute o Assistente para Implantação do [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] de modo interativo. Na página **Destino da Instalação** , especifique um novo destino para a instância e o banco de dados do [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
     — ou —  
  
-   Execute o Assistente para Implantação do [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] no prompt de comando e defina o assistente para executar em modo de arquivo de resposta. Para obter mais informações sobre o modo de arquivo de resposta, consulte [Running the Analysis Services Deployment Wizard](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md).  
  
     — ou —  
  
-   Modificar o \< *nome do projeto*> arquivo. deploymenttargets usando qualquer editor de texto.  
  
## <a name="see-also"></a>Consulte também  
 [Especificando opções de implantação de função e de partição](../../analysis-services/multidimensional-models/deployment-script-files-partition-and-role-deployment-options.md)   
 [Especificando definições de configuração para implantação de solução](../../analysis-services/multidimensional-models/deployment-script-files-solution-deployment-config-settings.md)   
 [Especificando opções de processamento](../../analysis-services/multidimensional-models/deployment-script-files-specifying-processing-options.md)  
  
  
