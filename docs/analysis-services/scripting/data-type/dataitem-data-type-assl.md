---
title: Tipo de dados DataItem (ASSL) | Microsoft Docs
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
apiname: DataItem Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: DataItem
helpviewer_keywords: DataItem data type
ms.assetid: f4f5155f-9c3d-49a1-a390-a9c734fafbce
caps.latest.revision: "44"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ec40eca06225eef5d9c7e505e4fe2c9dee6972b1
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2018
---
# <a name="dataitem-data-type-assl"></a>Tipos de dados DataItem (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Define um tipo de dados primitivo que representa as características de dados relacionados de um item de dados, como uma coluna ou um atributo.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
  
<DataItem>  
   <DataType>...</DataType>  
   <DataSize>...</DataSize>  
   <MimeType>...</MimeType>  
   <NullProcessing>...</NullProcessing>  
   <Trimming>...</Trimming>  
   <InvalidXmlCharacters>...</InvalidXmlCharacters>  
      <Collation>...</Collation>  
   <Format>...</Format>  
   <Source>...</Source>  
   <Annotations>...</Annotations>  
</DataItem>  
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
|Elementos filho|[Anotações](../../../analysis-services/scripting/collections/annotations-element-assl.md), [agrupamento](../../../analysis-services/scripting/properties/collation-element-assl.md), [DataSize](../../../analysis-services/scripting/properties/datasize-element-assl.md), [DataType](../../../analysis-services/scripting/properties/datatype-element-assl.md), [formato](../../../analysis-services/scripting/properties/format-element-assl.md), [InvalidXmlCharacters ](../../../analysis-services/scripting/properties/invalidxmlcharacters-element-assl.md), [MimeType](../../../analysis-services/scripting/properties/mimetype-element-assl.md), [NullProcessing](../../../analysis-services/scripting/properties/nullprocessing-element-assl.md), [fonte](../../../analysis-services/scripting/properties/source-element-binding-assl.md), [Trimming](../../../analysis-services/scripting/properties/trimming-element-assl.md)|  
|Elementos derivados|Consulte a tabela em Comentários.|  
  
## <a name="remarks"></a>Remarks  
 O **DataItem** tipo de dados é usado para qualquer item de dados que pode ser associada; por exemplo, uma medida, chave de atributo e nome do atributo. Os detalhes que são relevantes e os padrões que se aplicam dependem do uso; por exemplo, nomes de atributos devem ser cadeias de caracteres.  
  
 Uma instância de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] aceita apenas um determinado conjunto de tipos de dados. O uso de outros tipos de dados resulta em um erro, em vez de uma conversão implícita em um dos tipos válidos.  
  
 A tabela a seguir lista os elementos do tipo **DataItem**.  
  
|Elemento pai|Elemento do tipo **DataItem**|Comentários|  
|--------------------|----------------------------------|--------------|  
|[AttributeTranslation](../../../analysis-services/scripting/data-type/attributetranslation-data-type-assl.md)|[CaptionColumn](../../../analysis-services/scripting/objects/captioncolumn-element-assl.md)|**Origem** elemento o **DataItem** deve ser do tipo [ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md) ou [AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md)|  
|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|[CustomRollupColumn](../../../analysis-services/scripting/objects/customrollupcolumn-element-assl.md)|**Origem** elemento o **DataItem** deve ser do tipo [ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md) ou [AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md)|  
|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|[CustomRollupPropertiesColumn](../../../analysis-services/scripting/objects/customrolluppropertiescolumn-element-assl.md)|**Origem** elemento o **DataItem** deve ser do tipo [ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md) ou [AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md)|  
|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|[KeyColumn](../../../analysis-services/scripting/objects/keycolumn-element-assl.md)|**Origem** elemento o **DataItem** deve ser do tipo [ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md), [AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md) ou [TimeBinding](../../../analysis-services/scripting/data-type/timebinding-data-type-assl.md)|  
|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|[NameColumn](../../../analysis-services/scripting/objects/namecolumn-element-assl.md)|**Origem** elemento o **DataItem** deve ser do tipo [ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md) ou [AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md)|  
|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|[SkippedLevelsColumn](../../../analysis-services/scripting/objects/skippedlevelscolumn-element-assl.md)|**Origem** elemento o **DataItem** deve ser do tipo [ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md) ou [AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md)|  
|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|[UnaryOperatorColumn](../../../analysis-services/scripting/objects/unaryoperatorcolumn-element-assl.md)|**Origem** elemento o **DataItem** deve ser do tipo [ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md) ou [AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md)|  
|[Medida](../../../analysis-services/scripting/objects/measure-element-assl.md)|[Origem](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|**Origem** elemento o **DataItem** deve ser do tipo [RowBinding](../../../analysis-services/scripting/data-type/rowbinding-data-type-assl.md), [ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md), [MeasureBinding](../../../analysis-services/scripting/data-type/measurebinding-data-type-assl.md), ou [CubeDimensionBinding](../../../analysis-services/scripting/data-type/cubedimensionbinding-data-type-assl.md)|  
|[MeasureGroupAttribute](../../../analysis-services/scripting/data-type/measuregroupattribute-data-type-assl.md)|[KeyColumn](../../../analysis-services/scripting/objects/keycolumn-element-assl.md)|**Origem** elemento o **DataItem** deve ser do tipo [ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md), [AttributeBinding](../../../analysis-services/scripting/data-type/attributebinding-data-type-assl.md) ou [InheritedBinding](../../../analysis-services/scripting/data-type/inheritedbinding-data-type-assl.md)|  
|[ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)|[KeyColumn](../../../analysis-services/scripting/objects/keycolumn-element-assl.md)|**Origem** elemento o **DataItem** deve ser do tipo [ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md)|  
|[ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)|[NameColumn](../../../analysis-services/scripting/objects/namecolumn-element-assl.md)|**Origem** elemento o **DataItem** deve ser do tipo [ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md)|  
|[TableMiningStructureColumn](../../../analysis-services/scripting/data-type/tableminingstructurecolumn-data-type-assl.md)|[ForeignKeyColumn](../../../analysis-services/scripting/objects/foreignkeycolumn-element-assl.md)|**Origem** elemento o **DataItem** deve ser do tipo [ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md)|  
  
 O elemento correspondente no modelo de objeto Analysis Management Objects (AMO) é <xref:Microsoft.AnalysisServices.DataItem>.  
  
## <a name="see-also"></a>Consulte Também  
 [Tipos de dados XML de linguagem de script &#40; do Analysis Services ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
