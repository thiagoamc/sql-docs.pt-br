---
title: Definindo procedimentos armazenados | Microsoft Docs
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
ms.topic: article
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- stored procedures [Analysis Services]
- OLAP [Analysis Services], stored procedures
- external routines [Analysis Services]
- stored procedures [Analysis Services], about stored procedures
ms.assetid: f9c57d91-f60f-4f0e-8f7f-d87f4ba97b7c
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: af5d0ffc0b7aaa1b03ca4166d59667692566b036
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2018
---
# <a name="defining-stored-procedures"></a>Definindo procedimentos armazenados
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Você pode usar procedimentos armazenados para chamar rotinas externas de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. É possível gravar rotinas externas chamadas por um procedimento armazenado em uma linguagem CLR (Common Language Runtime), como C, C++, C#, Visual Basic ou Visual Basic .NET. Um procedimento armazenado pode ser criado e então chamado a partir de diversos contextos, como outros procedimentos armazenados, medidas calculadas ou aplicativos cliente. Os procedimentos armazenados simplificam o desenvolvimento e a implementação de bancos de dados do [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ao possibilitar que um código comum seja desenvolvido e então armazenado em um único local. Eles podem ser usados para adicionar a seus aplicativos funcionalidades comerciais que não existem como funcionalidade nativa do MDX.  
  
 Esta seção fornece as informações necessárias para você entender, projetar e implementar procedimentos armazenados.  
  
|Tópico|Description|  
|-----------|-----------------|  
|[Projetando procedimentos armazenados](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/designing-stored-procedures.md)|Descreve como projetar assemblies para uso com o [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[Criando procedimentos armazenados](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/creating-stored-procedures.md)|Descreve como criar assemblies para o [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[Chamando procedimentos armazenados](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/calling-stored-procedures.md)|Fornece informações sobre como usar assemblies no [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[Acessando o contexto de consulta nos procedimentos armazenados](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/accessing-query-context-in-stored-procedures.md)|Descreve como acessar informações de escopo e contexto com assemblies.|  
|[Configurando a segurança para procedimentos armazenados](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/setting-security-for-stored-procedures.md)|Descreve como configurar a segurança de assemblies no [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[Depurando procedimentos armazenados](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/debugging-stored-procedures.md)|Descreve como depurar assemblies no [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
  
## <a name="see-also"></a>Consulte também  
 [Gerenciamento de Assemblies de modelo multidimensional](../../analysis-services/multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  
