---
title: "Tipo de elemento (ação) (ASSL) | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Type Element (Action)
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- TYPE
helpviewer_keywords:
- Type element
ms.assetid: 534cdf99-1edf-4490-9eaa-61f189a19434
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 62735cdcc160bccf6b90ed2c26b269b8b3d1d3eb
ms.contentlocale: pt-br
ms.lasthandoff: 09/01/2017

---
# <a name="type-element-action-assl"></a>Elemento Type (Ação) (ASSL)
  Contém o tipo do [ação](../../../analysis-services/scripting/objects/action-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
  
<Action>  
   ...  
   <Type>...</Type>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Características do elemento  
  
|Característica|Descrição|  
|--------------------|-----------------|  
|Comprimento e tipo de dados|Cadeia de caracteres (enumeração)|  
|Valor padrão|Nenhuma|  
|Cardinalidade|1-1: elemento obrigatório que ocorre apenas uma única vez.|  
  
## <a name="element-relationships"></a>Relações do elemento  
  
|Relação|Elemento|  
|------------------|-------------|  
|Elemento pai|[Ação](../../../analysis-services/scripting/objects/action-element-assl.md)|  
|Elementos filho|Nenhuma|  
  
## <a name="remarks"></a>Comentários  
 O valor desse elemento é limitado a uma das cadeias de caracteres listadas na tabela a seguir.  
  
|Valor|Description|  
|-----------|-----------------|  
|*URL*|Exibe uma página variável em um navegador de Internet.|  
|*HTML*|Executa um script HTML em um navegador de Internet.|  
|*Instrução*|Executa um comando OLE DB.|  
|*Detalhamento*|Recupera um conjunto de linhas para extração de detalhes.<br /><br /> Esse valor é idêntico ao *linhas* e identifica ações de detalhamento. Ele só pode ser usado em ações cujo [TargetType](../../../analysis-services/scripting/properties/targettype-element-assl.md) valor é definido como *células*.|  
|*Conjunto de dados*|Recupera um conjunto de dados.|  
|*Conjunto de linhas*|Recupera um conjunto de linhas.|  
|*Linha de comando*|Executa um comando em um prompt de comando.|  
|*Proprietários*|Executa uma operação usando uma interface diferente das listadas anteriormente nesta tabela.|  
|*Relatório*|Exibe uma página variável em um navegador de Internet.<br /><br /> Esse valor é idêntico ao *Url* e identifica ações de relatório.|  
  
 O elemento que corresponde ao pai do **tipo** no objeto Analysis Management Objects (AMO) o modelo é <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>Consulte também  
 [Tipo de dados DrillThroughAction &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/drillthroughaction-data-type-assl.md)   
 [Tipo de dados ReportAction &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/reportaction-data-type-assl.md)   
 [Propriedades &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  