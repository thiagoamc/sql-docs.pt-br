---
title: Tipo de dados AggregationDesignDimension (ASSL) | Microsoft Docs
ms.custom: 
ms.date: 03/15/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: AggregationDesignDimension Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: AggregationDesignDimension
helpviewer_keywords: AggregationDesignDimension data type
ms.assetid: 06a0d418-014c-4f40-a63a-5cfeee3f6a41
caps.latest.revision: "39"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 3ddfc11592478d55a1ca8b253fa33c3b7af4b449
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2018
---
# <a name="aggregationdesigndimension-data-type-assl"></a>Tipo de dados AggregationDesignDimension (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Define um tipo de dados primitivo que representa a relação entre uma dimensão de cubo e um [AggregationDesign](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
  
<AggregationDesignDimension>  
   <CubeDimensionID>...</CubeDimensionID>  
   <Attributes>...</Attributes>  
      <Annotations>...</Annotations>  
</AggregationDesignDimension>  
```  
  
## <a name="data-type-characteristics"></a>Características do tipo de dados  
  
|Característica|Description|  
|--------------------|-----------------|  
|Tipos de dados base|Nenhum|  
|Tipos de dados derivados|Nenhum|  
  
## <a name="data-type-relationships"></a>Relação do tipo de dados  
  
|Relação|Elemento|  
|------------------|-------------|  
|Elementos pai|Nenhum|  
|Elementos filho|[Anotações](../../../analysis-services/scripting/collections/annotations-element-assl.md), [atributos](../../../analysis-services/scripting/collections/attributes-element-assl.md), [CubeDimensionID](../../../analysis-services/scripting/properties/cubedimensionid-element-assl.md)|  
|Elementos derivados|[Dimensão](../../../analysis-services/scripting/objects/dimension-element-assl.md) ([dimensões](../../../analysis-services/scripting/collections/dimensions-element-assl.md) coleção de [AggregationDesign](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md))|  
  
## <a name="remarks"></a>Remarks  
 O elemento correspondente no modelo de objeto Analysis Management Objects (AMO) é <xref:Microsoft.AnalysisServices.AggregationDesignDimension>.  
  
## <a name="see-also"></a>Consulte Também  
 [Elemento AggregationDesign &#40; ASSL &#41;](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md)   
 [Tipos de dados XML de linguagem de script &#40; do Analysis Services ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
