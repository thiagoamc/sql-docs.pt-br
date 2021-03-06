---
title: Elemento Properties (XMLA) | Microsoft Docs
ms.custom: 
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Properties Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Properties
- microsoft.xml.analysis.properties
- urn:schemas-microsoft-com:xml-analysis#Properties
- Properties
helpviewer_keywords: Properties element
ms.assetid: 0b5468e5-bf23-4d22-862f-72e27a9fff2f
caps.latest.revision: "30"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 937abfbd3ba8d06ee4d25f97c47471a04435cfba
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2018
---
# <a name="properties-element-xmla"></a>Elemento Properties (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Contém o XML para propriedades de análise (XMLA) usadas pelo [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) e [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) métodos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
<Discover> <!-- or Execute -->  
...  
   <Properties>  
      <PropertyList>...</PropertyList>  
   </Properties>  
...  
</Discover>  
```  
  
## <a name="element-characteristics"></a>Características do elemento  
  
|Característica|Description|  
|--------------------|-----------------|  
|Comprimento e tipo de dados|Nenhum|  
|Valor padrão|Nenhum|  
|Cardinalidade|1-1: elemento obrigatório que ocorre apenas uma única vez.|  
  
## <a name="element-relationships"></a>Relações do elemento  
  
|Relação|Elemento|  
|------------------|-------------|  
|Elementos pai|[Descobrir](../../../analysis-services/xmla/xml-elements-methods-discover.md), [executar](../../../analysis-services/xmla/xml-elements-methods-execute.md)|  
|Elementos filho|[PropertyList](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-xmla.md)|  
  
## <a name="remarks"></a>Remarks  
 O **propriedades** elemento representa propriedades XMLA usadas para controlar aspectos do **Discover** e **Execute** métodos, como definir as informações necessárias para Conecte-se à fonte de dados, especificando o formato de retorno do conjunto de resultados ou especificando o local no qual os dados devem ser formatados.  
  
 As propriedades disponíveis e seus valores podem ser obtidos usando o tipo de solicitação DISCOVER_PROPERTIES com o método **Discover** .  
  
## <a name="example"></a>Exemplo  
  
```  
<Properties>  
   <PropertyList>  
      <DataSourceInfo>  
         Provider=MSOLAP;Data Source=local;  
      </DataSourceInfo>  
      <Catalog>  
         Foodmart 2000  
      </Catalog>  
      <Format>  
         Multidimensional  
      </Format>  
   </PropertyList>  
</Properties>  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Propriedades &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
