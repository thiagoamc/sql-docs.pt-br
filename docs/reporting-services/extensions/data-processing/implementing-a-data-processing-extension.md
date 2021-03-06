---
title: "Implementando uma extensão de processamento de dados | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: extensions
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- custom data processing extensions [Reporting Services]
- data sources [Reporting Services], data processing extensions
- data processing extensions [Reporting Services]
- extensions [Reporting Services], data processing
ms.assetid: 8dc2b44e-5ad9-411d-a29f-7213e29321a9
caps.latest.revision: "35"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 0af2bbfa0c6a02f57c1d09092ce05ac36f8d3c42
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2018
---
# <a name="implementing-a-data-processing-extension"></a>Implementando uma extensão de processamento de dados
  As extensões de processamento de dados do [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] permitem que você se conecte a uma fonte de dados e recupere dados. Eles também servem como uma ponte entre uma fonte de dados e um conjunto de dados. As extensões de processamento de dados do [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] são modeladas de acordo com um subconjunto das interfaces do provedor de dados do [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão geral das extensões de processamento de dados](../../../reporting-services/extensions/data-processing/data-processing-extensions-overview.md)  
 Apresenta como escrever uma extensão de processamento de dados personalizada para o [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 [Preparar a implementação de uma extensão de processamento de dados](../../../reporting-services/extensions/data-processing/preparing-to-implement-a-data-processing-extension.md)  
 Descreve as interfaces disponíveis durante a implementação de uma extensão de processamento de dados do [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], como também quando você precisa implementar uma interface específica.  
  
 [Criar uma biblioteca de extensões de processamento de dados](../../../reporting-services/extensions/data-processing/creating-a-data-processing-extension-library.md)  
 Descreve a atribuição de um namespace para a sua extensão de processamento de dados do [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] e a compilação da sua extensão de processamento de dados em uma DLL de biblioteca.  
  
 [Implementar uma classe Connection para uma extensão de processamento de dados](../../../reporting-services/extensions/data-processing/implementing-a-connection-class-for-a-data-processing-extension.md)  
 Descreve os atributos de uma conexão e como implementar sua própria classe **Connection** para a extensão de processamento de dados.  
  
 [Implementar uma classe Command para uma extensão de processamento de dados](../../../reporting-services/extensions/data-processing/implementing-a-command-class-for-a-data-processing-extension.md)  
 Descreve os atributos de um comando e como implementar sua própria classe **Command** para a extensão de processamento de dados.  
  
 [Implementar uma classe DataReader para uma extensão de processamento de dados](../../../reporting-services/extensions/data-processing/implementing-a-datareader-class-for-a-data-processing-extension.md)  
 Descreve os atributos de um leitor de dados e como implementar sua própria classe **DataReader** para a extensão de processamento de dados.  
  
 [Usar um conjunto de dados externo com o Reporting Services](../../../reporting-services/extensions/data-processing/using-an-external-dataset-with-reporting-services.md)  
 Descreve como expor os objetos **DataSet** personalizados para o servidor de relatório para consumo.  
  
 [Implantando uma extensão de processamento de dados](../../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension.md)  
 Descreve como implantar a sua extensão de processamento de dados.  
  
 [Depurar o código de extensão de processamento de dados](../../../reporting-services/extensions/data-processing/debugging-data-processing-extension-code.md)  
 Descreve como depurar código em suas extensões de processamento de dados.  
  
 [Remover uma extensão de processamento de dados](../../../reporting-services/extensions/data-processing/removing-a-data-processing-extension.md)  
 Descreve como remover uma extensão de processamento de dados de um servidor de relatório ou do Designer de Relatórios.  
  
 Para obter uma amostra de uma extensão de processamento de dados totalmente implementada, consulte [Amostras de produto do SQL Server Reporting Services](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>Consulte Também  
 [Extensões do Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Biblioteca de extensões do Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
