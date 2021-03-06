---
title: Elemento SolveOrder (ASSL) | Microsoft Docs
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: SolveOrder Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: SolveOrder
helpviewer_keywords: SolveOrder element
ms.assetid: ec43e055-97dd-4f2a-9a7c-2df2e1119e56
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e9d9cb2bcba3bf11cd1674dda39b960dc71de24b
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2018
---
# <a name="solveorder-element-assl"></a>Elemento SolveOrder (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Indica a ordem de resolução na qual o [CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md) elemento é aplicado a um membro calculado ou definição de célula calculada.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
  
<CalculationProperty>  
   ...  
   <SolveOrder>...</SolveOrder>  
   ...  
</CalculationProperty>  
```  
  
## <a name="element-characteristics"></a>Características do elemento  
  
|Característica|Description|  
|--------------------|-----------------|  
|Comprimento e tipo de dados|Integer|  
|Valor padrão|Nenhum|  
|Cardinalidade|0-1: elemento opcional que pode ocorrer apenas uma única vez.|  
  
## <a name="element-relationships"></a>Relações do elemento  
  
|Relação|Elemento|  
|------------------|-------------|  
|Elemento pai|[CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md)|  
|Elementos filho|Nenhum|  
  
## <a name="remarks"></a>Remarks  
 O **SolveOrder** propriedade se aplica a **CalculationProperty** elementos com um [CalculationType](../../../analysis-services/scripting/properties/calculationtype-element-assl.md) de *membro* ou  *Células*.  
  
 O elemento que corresponde ao pai do **SolveOrder** no objeto Analysis Management Objects (AMO) o modelo é <xref:Microsoft.AnalysisServices.CalculationProperty>.  
  
## <a name="see-also"></a>Consulte Também  
 [Elemento CalculationProperties &#40; ASSL &#41;](../../../analysis-services/scripting/collections/calculationproperties-element-assl.md)   
 [Elemento MdxScript &#40; ASSL &#41;](../../../analysis-services/scripting/objects/mdxscript-element-assl.md)   
 [Elemento MdxScripts &#40; ASSL &#41;](../../../analysis-services/scripting/collections/mdxscripts-element-assl.md)   
 [Propriedades &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
