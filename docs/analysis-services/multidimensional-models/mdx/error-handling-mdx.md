---
title: Erro tratamento (MDX) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scripts [MDX], exceptions
- exceptions [MDX]
ms.assetid: bc6ff0af-9fe6-44d6-bc3c-801d71ea41a9
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f612a88976890a95b8fbd3d28826685d0e4ef414
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2018
---
# <a name="error-handling-mdx"></a>Tratamento de erros (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
Cada cubo pode controlar como são tratados os erros em um script MDX. O tratamento de erro é feito por meio do enumerador **ScriptErrorHandlingMode** . Os valores possíveis para esse enumerador são:  
  
 **IgnoreNone**  
 Faz com que o servidor produza um erro se o [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] localizar algum erro no script MDX.  
  
 **IgnoreAll**  
 Faz com que o servidor ignore todos os comandos do script MDX que contém um erro, incluindo erros de sintaxe, de resolução de nomes, entre outros.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.AnalysisServices.Cube.ScriptErrorHandlingMode%2A>  
  
  
