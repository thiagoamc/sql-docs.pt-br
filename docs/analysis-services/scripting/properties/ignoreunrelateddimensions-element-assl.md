---
title: Elemento IgnoreUnrelatedDimensions (ASSL) | Microsoft Docs
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
apiname: IgnoreUnrelatedDimensions Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: IgnoreUnrelatedDimensions
helpviewer_keywords: IgnoreUnrelatedDimensions element
ms.assetid: c7d7a1cd-a8e0-4ae7-9464-a1d2a55a86ab
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 717d36bd445d777981c24e466c4bdcea674e00b1
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2018
---
# <a name="ignoreunrelateddimensions-element-assl"></a>Elemento IgnoreUnrelatedDimensions (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Determina se as dimensões não relacionadas são forçadas para seu nível superior quando os membros das dimensões não relacionadas ao grupo de medidas são incluídos em uma consulta.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
  
<MeasureGroup>  
   ...  
   <IgnoreUnrelatedDimensions>...</IgnoreUnrelatedDimensions>  
   ...  
</MeasureGroup>  
```  
  
## <a name="element-characteristics"></a>Características do elemento  
  
|Característica|Description|  
|--------------------|-----------------|  
|Comprimento e tipo de dados|Booliano|  
|Valor padrão|True|  
|Cardinalidade|0-1: elemento opcional que pode ocorrer apenas uma única vez.|  
  
## <a name="element-relationships"></a>Relações do elemento  
  
|Relação|Elemento|  
|------------------|-------------|  
|Elemento pai|[MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)|  
|Elementos filho|Nenhum|  
  
## <a name="remarks"></a>Remarks  
 Quando **IgnoreUnrelatedDimensions** for **true**, dimensões não relacionadas serão forçadas para seu nível superior; quando o valor for **false**, as dimensões não serão forçadas para seu nível superior. Esta propriedade é semelhante para o MDX (Multidimensional Expressions) [ValidMeasure](../../../mdx/validmeasure-mdx.md) função.  
  
 O elemento que corresponde ao pai do **IgnoreUnrelatedDimensions** no objeto Analysis Management Objects (AMO) o modelo é <xref:Microsoft.AnalysisServices.MeasureGroup>.  
  
## <a name="see-also"></a>Consulte Também  
 [Propriedades &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
