---
title: Elemento AttributeHierarchyOptimizedState (ASSL) | Microsoft Docs
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
apiname: AttributeHierarchyOptimizedState Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: AttributeHierarchyOptimizedState
helpviewer_keywords: AttributeHierarchyOptimizedState element
ms.assetid: d87148c8-2011-45ae-94c3-851f48babc5f
caps.latest.revision: "37"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 77d6f65f6214f83b93bd6ba8e5c41a984cc342e0
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2018
---
# <a name="attributehierarchyoptimizedstate-element-assl"></a>Elemento AttributeHierarchyOptimizedState (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Determina o nível de otimização aplicado à hierarquia de atributo.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
  
<DimensionAttribute> <!-- or CubeAttribute -->  
   ...  
   <AttributeHierarchyOptimizedState>...  
   </AttributeHierarchyOptimizedState>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Características do elemento  
  
|Característica|Description|  
|--------------------|-----------------|  
|Comprimento e tipo de dados|Cadeia de caracteres (enumeração)|  
|Valor padrão|*FullyOptimized*|  
|Cardinalidade|0-1: elemento opcional que pode ocorrer apenas uma única vez.|  
  
## <a name="element-relationships"></a>Relações do elemento  
  
|Relação|Elemento|  
|------------------|-------------|  
|Elemento pai|[CubeAttribute](../../../analysis-services/scripting/data-type/cubeattribute-data-type-assl.md), [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|Elementos filho|Nenhum|  
  
## <a name="remarks"></a>Remarks  
 O valor desse elemento é limitado a uma das cadeias de caracteres listadas na tabela a seguir.  
  
|Valor|Description|  
|-----------|-----------------|  
|*FullyOptimized*|A instância constrói índices para a hierarquia de atributos a fim de melhorar o desempenho das consultas.|  
|*NotOptimized*|Nenhum índice adicional é criado pela instância.|  
  
 A enumeração que corresponde aos valores permitidos para **AttributeHierarchyOptimizedState** no objeto Analysis Management Objects (AMO) o modelo é <xref:Microsoft.AnalysisServices.OptimizationType>. Os elementos que correspondem aos pais de **AttributeHierarchyOptimizedState** no modelo de objeto AMO são <xref:Microsoft.AnalysisServices.CubeAttribute> e <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>Consulte Também  
 [Propriedades &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
