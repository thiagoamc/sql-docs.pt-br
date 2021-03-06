---
title: Tipo de dados EnumString (XMLA) | Microsoft Docs
ms.custom: 
ms.date: 03/16/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: EnumString Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- EnumString
- urn:schemas-microsoft-com:xml-analysis#EnumString
- http://schemas.microsoft.com/analysisservices/2003/engine#EnumString
helpviewer_keywords: EnumString data type
ms.assetid: 9214195e-4539-419b-95ec-b7aa75e033ab
caps.latest.revision: "29"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: b00fa29ae9dc0bb4529e013f9767451c3d0f1720
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2018
---
# <a name="enumstring-data-type-xmla"></a>Tipo de dados EnumString (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Define um tipo de dados derivado que representa um conjunto de constantes nomeadas para um determinado enumerador.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
  
<EnumString>...</EnumString>  
```  
  
## <a name="data-type-characteristics"></a>Características do tipo de dados  
  
|Característica|Description|  
|--------------------|-----------------|  
|Tipos de dados base|**cadeia de caracteres**|  
|Tipos de dados derivados|Nenhum|  
  
## <a name="data-type-relationships"></a>Relação do tipo de dados  
  
|Relação|Elemento|  
|------------------|-------------|  
|Elementos pai|Nenhum|  
|Elementos filho|Nenhum|  
|Elementos derivados|Nenhum|  
  
## <a name="remarks"></a>Remarks  
 XMLA (XML for Analysis) usa enumeração para limitar os valores de cadeia para um conjunto de configurações verificáveis. **EnumString** usa o XML padrão **cadeia de caracteres** tipo de dados. São especificados os valores específicos para cada uma das constantes nomeadas com a definição de enumerador. Enumeradores são definidos pela inclusão deles para o [DISCOVER_ENUMERATORS](../../../analysis-services/schema-rowsets/xml/discover-enumerators-rowset.md) linhas de esquema e pode ser recuperado usando o [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) tipo de solicitação de método com o DISCOVER_ENUMERATORS.  
  
 A tabela a seguir descreve os enumeradores suportados por uma instância do [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
|Enumerador|Description|  
|----------------|-----------------|  
|ProviderType|Oferece suporte à coluna ProviderType no [DISCOVER_DATASOURCES](../../../analysis-services/schema-rowsets/xml/discover-datasources-rowset.md) de linhas de esquema, que determina o tipo de dados que podem ser retornados por uma [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instância.<br /><br /> Esta enumeração também aceita a propriedade XMLA, **ProviderType**, que determina os tipos de provedor com suporte por um [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instância. Essa enumeração também é usada no conjunto de linhas de esquema DISCOVER_DATASOURCES.<br /><br /> Para obter mais informações sobre **ProviderType**, consulte [suporte para propriedades de XMLA &#40; XMLA &#41; ](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|AuthenticationMode|Fornece suporte à coluna AuthenticationMode no conjunto de linhas do esquema DISCOVER_DATASOURCES, que determina as credenciais de segurança que devem ser aprovadas para o acesso a uma instância [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|PropertyAccessType|Oferece suporte à coluna PropertyAccessType no [DISCOVER_PROPERTIES](../../../analysis-services/schema-rowsets/xml/discover-properties-rowset.md) de linhas de esquema, que determina o tipo de acesso disponível para uma propriedade XMLA.|  
|StateSupport|Oferece suporte à propriedade XMLA, **StateSupport**, que determina o nível de status do processo com suporte por um [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instância.<br /><br /> Para obter mais informações sobre **StateSupport**, consulte [suporte para propriedades de XMLA &#40; XMLA &#41; ](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|StateActionVerb|Contém uma lista de verbos aceitos por XMLA nos cabeçalhos SOAP e utilizados para iniciar, identificar e finalizar uma sessão.<br /><br /> Para obter mais informações sobre as sessões, consulte [&#40; gerenciamento de conexões e sessões XMLA &#41; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md).|  
|ResultsetFormat|Oferece suporte à propriedade XMLA, **formato**, que determina o tipo de dados retornados em uma [raiz](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) elemento.<br /><br /> Para obter mais informações sobre **formato**, consulte [suporte para propriedades de XMLA &#40; XMLA &#41; ](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|ResultsetAxisFormat|Oferece suporte à propriedade XMLA, **AxisFormat**, que determina o formato das informações de eixo retornados em uma **raiz** elemento que contém dados multidimensionais.<br /><br /> Para obter mais informações sobre **AxisFormat**, consulte [suporte para propriedades de XMLA &#40; XMLA &#41; ](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|ResultsetContents|Oferece suporte à propriedade XMLA, **conteúdo**, que determina se os metadados ou dados são retornados em uma **raiz** elemento.<br /><br /> Para obter mais informações sobre **conteúdo**, consulte [suporte para propriedades de XMLA &#40; XMLA &#41; ](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
|MDXSupportLevel|Oferece suporte à propriedade XMLA, **MDXSupport**, que indica o nível de suporte de MDX (Multidimensional Expressions) disponível em um [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instância.<br /><br /> Para obter mais informações sobre **MDXSupport**, consulte [suporte para propriedades de XMLA &#40; XMLA &#41; ](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).|  
  
## <a name="see-also"></a>Consulte Também  
 [Tipos de dados XML &#40; XMLA &#41;](../../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)  
  
  
