---
title: Elemento Parameter (XMLA) | Microsoft Docs
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Parameter Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Parameter
- microsoft.xml.analysis.parameter
- http://schemas.microsoft.com/analysisservices/2003/engine#Parameter
helpviewer_keywords: Parameter element
ms.assetid: fe31ac3d-a3e8-4f60-a81a-c43271ddbed4
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 1d0fbcea8ac8e919da27a1fb129037f7ca2bfa0a
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2018
---
# <a name="parameter-element-xmla"></a>Elemento Parameter (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Contém o nome e o valor de um parâmetro usado pelo [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) método.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
<Parameters>  
...  
   <Parameter>  
      <Name>...</Name>  
      <Value>...</Value>  
   </Parameter>  
...  
</Parameters>  
```  
  
## <a name="element-characteristics"></a>Características do elemento  
  
|Característica|Description|  
|--------------------|-----------------|  
|Comprimento e tipo de dados|Nenhum|  
|Valor padrão|Nenhum|  
|Cardinalidade|0-1: elemento opcional que pode ocorrer apenas uma única vez.|  
  
## <a name="element-relationships"></a>Relações do elemento  
  
|Relação|Elemento|  
|------------------|-------------|  
|Elementos pai|[Parâmetros](../../../analysis-services/xmla/xml-elements-properties/parameters-element-xmla.md)|  
|Elementos filho|[Nome](../../../analysis-services/xmla/xml-elements-properties/name-element-parameter-xmla.md), [Value](../../../analysis-services/xmla/xml-elements-properties/value-element-parameter-xmla.md)|  
  
## <a name="remarks"></a>Remarks  
 Alguns comandos do XMLA (XML for Analysis), como o comando [Process](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md) , podem requerer informações adicionais. O elemento **Parameter** fornece um mecanismo para fornecer informações adicionais, incluindo partes de informações, de um comando XMLA.  
  
## <a name="see-also"></a>Consulte Também  
 [Propriedades &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
