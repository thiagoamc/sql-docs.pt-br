---
title: Propriedades Filestore | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- Income property
- InitialBonus property
- PercentScanPerPrice property
- FileStore properties
- BackgroundTrimCost property
- Tax property
- PerformanceTrace property
- MinimumBalance property
- UnbufferedThreshold property
- BackgroundTrimAmount property
- MaximumBalance property
- MemoryLimitMin property
- MemoryLimit property
ms.assetid: 580cf0aa-7425-4d48-aa8d-128f5b488fcd
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 24a18751c7686de2d3d3731806374fe7a6db2080
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2018
---
# <a name="filestore-properties"></a>Propriedades FileStore
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  O [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] oferece suporte às propriedades do servidor de armazenamento de arquivos listadas nas tabelas a seguir. Estas são todas as propriedades avançadas que não devem ser alteradas, exceto sob orientação do suporte da [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Para obter mais informações sobre propriedades adicionais do servidor e como defini-las, consulte [Propriedades do servidor do Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md).  
  
 **Aplica-se a:** modo de servidor multidimensional e tabular  
  
## <a name="properties"></a>Propriedades  
 **MemoryLimit**  
 Uma propriedade avançada que não deve ser alterada, exceto sob orientação do suporte da [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **MemoryLimitMin**  
 Uma propriedade avançada que não deve ser alterada, exceto sob orientação do suporte da [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **PercentScanPerPrice**  
 Uma propriedade avançada que não deve ser alterada, exceto sob orientação do suporte da [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **PerformanceTrace**  
 Uma propriedade avançada que não deve ser alterada, exceto sob orientação do suporte da [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **RandomFileAccessMode**  
 Uma propriedade Booliana que indica se os arquivos de banco de dados e arquivos armazenados em cache são acessados em modo de acesso aleatório ao arquivo. Essa propriedade é desativada por padrão. Por padrão, o Analysis Services não define o sinalizador de acesso ao arquivo aleatório ao abrir arquivos de dados de partição para acesso de leitura.  
  
 Em sistemas avançados, especialmente os com recursos de memória grandes e vários nós NUMA, pode ser vantajoso usar acesso aleatório ao arquivo. No modo de acesso aleatório, o Windows ignora operações de mapeamento de página que leem dados do disco no cache de arquivo do sistema, diminuindo, portanto, a contenção no cache.  
  
 Você precisará executar testes de comparação para determinar se o desempenho da consulta melhorou como o resultado da alteração desta propriedade. Para conhecer as práticas recomendadas sobre como fazer testes de comparação, inclusive limpar o cache e evitar erros comuns, consulte [Guia de operações do SQL Server 2008 R2 Analysis Services](http://go.microsoft.com/fwlink/?LinkID=225539). Para obter informações adicionais sobre as compensações de usar esta propriedade, consulte [http://support.microsoft.com/kb/2549369](http://support.microsoft.com/kb/2549369).  
  
 Para exibir ou modificar esta propriedade no Management Studio, habilite a lista de propriedades avançadas na página de propriedades do servidor. Você também pode alterar a propriedade no arquivo msmdsrv.ini. Reiniciar o servidor é recomendado depois de definir esta propriedade; caso contrário, os arquivos que já estão abertos continuarão sendo acessados no modo anterior.  
  
 **UnbufferedThreshold**  
 Uma propriedade avançada que não deve ser alterada, exceto sob orientação do suporte da [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="memory-model-category"></a>Categoria de modelo de memória  
 **MemoryModel\Tax**  
 Uma propriedade avançada que não deve ser alterada, exceto sob orientação do suporte da [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **MemoryModel\Income**  
 Uma propriedade avançada que não deve ser alterada, exceto sob orientação do suporte da [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **MemoryModel\MaximumBalance**  
 Uma propriedade avançada que não deve ser alterada, exceto sob orientação do suporte da [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **MemoryModel\MinimumBalance**  
 Uma propriedade avançada que não deve ser alterada, exceto sob orientação do suporte da [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **MemoryModel\InitialBonus**  
 Uma propriedade avançada que não deve ser alterada, exceto sob orientação do suporte da [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="see-also"></a>Consulte também  
 [Propriedades do servidor no Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
 [Determina o Modo de Servidor de uma instância do Analysis Services](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
