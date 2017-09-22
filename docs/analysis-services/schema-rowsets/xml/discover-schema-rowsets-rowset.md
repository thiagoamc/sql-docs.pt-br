---
title: Conjunto de linhas DISCOVER_SCHEMA_ROWSETS | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DISCOVER_SCHEMA_ROWSETS
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DISCOVER_SCHEMA_ROWSETS rowset
ms.assetid: e5012aa0-6ef8-497f-96c1-2772e2394f62
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1ba7d3abc8f5ba5fdb941a8f97901d35c20f6b42
ms.contentlocale: pt-br
ms.lasthandoff: 09/01/2017

---
# <a name="discoverschemarowsets-rowset"></a>Conjunto de linhas DISCOVER_SCHEMA_ROWSETS
  Retorna os nomes, as restrições, a descrição e outras informações para todos os valores de enumeração e quaisquer valores adicionais de enumeração específica de provedor que recebem suporte do provedor do [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis (XMLA).  
  
 Se você chamar o [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) método com o **DISCOVER_SCHEMA_ROWSETS** valor de enumeração no [RequestType](../../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md) elemento, o **Discover**método retorna o **DISCOVER_SCHEMA_ROWSETS** conjunto de linhas.  
  
## <a name="rowset-columns"></a>Colunas do conjunto de linhas  
 O conjunto de linhas DISCOVER_SCHEMA_ROWSETS contém as colunas a seguir.  
  
|Nome da coluna|Indicador de tipo|Comprimento|Description|  
|-----------------|--------------------|------------|-----------------|  
|**SchemaName**|**DBTYPE_WSTR**||O nome do esquema ou solicitação. Essa solicitação retorna os valores na enumeração *RequestTypes* .|  
|**SchemaGuid**|**DBTYPE_GUID**||O GUID do esquema.|  
|**Restrições**|**DBTYPE_HCHAPTER**||Uma matriz das restrições suportadas pelo provedor.|  
|**Description**|**DBTYPE_WSTR**||Uma descrição localizável do esquema.|  
|**RestrictionsMask**|**DBTYPE_UI8**|||  
  
 Este conjunto de linhas do esquema não é classificado.  
  
 Para um provedor que dá suporte a três restrições para o conjunto de linhas de esquema de DBSCHEMA_MEMBERS, a matriz **Restrictions** deve retornar o resultado a seguir. Os elementos no resultado se referem a nomes de colunas no esquema.  
  
```  
<Restrictions>  
      <CATALOG_NAME type="string" />   
      <SCHEMA_NAME type="string" />   
      <CUBE_NAME type="string" />   
</Restrictions>  
```  
  
## <a name="restriction-columns"></a>Colunas de restrição  
 O conjunto de linhas **DISCOVER_SCHEMA_ROWSETS** pode ser restringido nas colunas listadas na tabela a seguir.  
  
|Nome da coluna|Indicador de tipo|Estado de restrição|  
|-----------------|--------------------|-----------------------|  
|**SchemaName**|**DBTYPE_WSTR**||  
  
## <a name="see-also"></a>Consulte também  
 [XML for Analysis conjuntos de linhas de esquema](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  