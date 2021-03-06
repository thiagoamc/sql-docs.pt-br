---
title: Tipo de dados ComAssembly (ASSL) | Microsoft Docs
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
apiname: ComAssembly Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: ComAssembly
helpviewer_keywords: ComAssembly data type
ms.assetid: 23c0f4b3-b6ac-4ec8-9254-74d2f84f5244
caps.latest.revision: "48"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ba15ade9aaad8586806da3cd4b19cf8998dfca62
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2018
---
# <a name="comassembly-data-type-assl"></a>Tipo de dados ComAssembly (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Define um tipo de dados derivado que representa uma biblioteca COM associada a um [servidor](../../../analysis-services/scripting/objects/server-element-assl.md) ou [banco de dados](../../../analysis-services/scripting/objects/database-element-assl.md) elemento.  
  
> [!IMPORTANT]  
>  Os assemblies COM podem representar um risco à segurança. Devido a esse risco e outras considerações, os assemblies COM foram preteridos no [!INCLUDE[ssASversion10](../../../includes/ssasversion10-md.md)]. Talvez não haja suporte para assemblies COM em versões futuras.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
  
<ComAssembly>  
      <!-- The following elements extend Assembly -->  
   <Source>...</Source>  
</ComAssembly>  
```  
  
## <a name="data-type-characteristics"></a>Características do tipo de dados  
  
|Característica|Description|  
|--------------------|-----------------|  
|Tipos de dados base|[Assembly](../../../analysis-services/scripting/objects/assembly-element-assl.md)|  
|Tipos de dados derivados|Nenhum|  
  
## <a name="data-type-relationships"></a>Relação do tipo de dados  
  
|Relação|Elemento|  
|------------------|-------------|  
|Elementos pai|Nenhum|  
|Elementos filho|[Origem](../../../analysis-services/scripting/properties/source-element-comassembly-assl.md)|  
|Elementos derivados|Consulte [Assembly](../../../analysis-services/scripting/objects/assembly-element-assl.md) ([Assemblies](../../../analysis-services/scripting/collections/assemblies-element-assl.md) coleção de [banco de dados](../../../analysis-services/scripting/objects/database-element-assl.md) ou [Server](../../../analysis-services/scripting/objects/server-element-assl.md))|  
  
## <a name="remarks"></a>Remarks  
 O **ComAssembly** elemento contém uma referência (o nome de arquivo totalmente qualificado ou o identificador programático) a uma biblioteca COM associada a uma instância de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ou com um determinado banco de dados em uma instância do [!INCLUDE[ssAS](../../../includes/ssas-md.md)].  
  
 O elemento correspondente no modelo de objeto Analysis Management Objects (AMO) é <xref:Microsoft.AnalysisServices.ComAssembly>.  
  
## <a name="see-also"></a>Consulte Também  
 [Tipo de dados ClrAssembly &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md)   
 [Tipos de dados XML de linguagem de script &#40; do Analysis Services ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
