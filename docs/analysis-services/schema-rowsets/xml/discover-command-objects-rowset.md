---
title: Conjunto de linhas DISCOVER_COMMAND_OBJECTS | Microsoft Docs
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
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DISCOVER_COMMAND_OBJECTS rowset
ms.assetid: 325114ee-3a50-4504-9782-dbf7c1a44778
caps.latest.revision: 21
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: cae36b0ff5492555137952c2ad9b19f609c53948
ms.contentlocale: pt-br
ms.lasthandoff: 09/01/2017

---
# <a name="discovercommandobjects-rowset"></a>Conjunto de linhas DISCOVER_COMMAND_OBJECTS
  Oferece uso de recursos e informações de atividade sobre os objetos em uso pelo comando referenciado.  
  
 **Aplica-se a:** modelos de tabela, modelos multidimensionais  
  
## <a name="rowset-columns"></a>Colunas do conjunto de linhas  
 O conjunto de linhas **DISCOVER_COMMAND_OBJECTS** contém as colunas a seguir.  
  
|Nome da coluna|Indicador de tipo|Restrição|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|**SESSION_SPID**|**DBTYPE_I4**|Sim|A ID da sessão.|  
|**SESSION_ID**|**DBTYPE_WSTR**|Sim|O identificador exclusivo da sessão, como um GUID.|  
|**SESSION_COMMAND_COUNT**|**DBTYPE_I4**||O número de sequência do comando.|  
|**OBJECT_PARENT_PATH**|**DBTYPE_WSTR**|Sim|O caminho para o pai do objeto atual.|  
|**OBJECT_ID**|**DBTYPE_WSTR**|Sim|A ID do objeto como definida em sua criação.|  
|**OBJECT_VERSION**|**DBTYPE_I4**||O número de versão de metadados do objeto; esse número mudará sempre que o objeto for alterado.|  
|**OBJECT_DATA_VERSION**|**DBTYPE_I4**||O número de linhagem dos dados do objeto. Esse número será incrementado sempre que o objeto for processado.|  
|**OBJECT_CPU_TIME_MS**|**DBTYPE_I8**||O tempo de CPU, em milissegundos, consumido pelo objeto desde o início do comando.|  
|**OBJECT_READ_KB**|**DBTYPE_I8**||O valor acumulado de dados, em quilobytes, lidos pelo objeto desde o início do comando.|  
|**OBJECT_READS**|**DBTYPE_I8**||O número acumulado de operações de leitura pelo objeto desde o início do comando.|  
|**OBJECT_WRITE_KB**|**DBTYPE_I8**||O valor acumulado de dados, em quilobytes, gravados pelo objeto desde o início do comando.|  
|**OBJECT_WRITES**|**DBTYPE_I8**||O número acumulado de operações de gravação pelo objeto desde o início do comando.|  
|**OBJECT_ROWS_RETURNED**|**DBTYPE_I8**||O número de linhas retornado pelo objeto ao chamador desde o início do comando.|  
|**OBJECT_ROWS_SCANNED**|**DBTYPE_I8**||O número de linhas verificadas pelo objeto desde o início do comando.|  
  
 Este conjunto de linhas do esquema não é classificado.  
  
> [!IMPORTANT]  
>  O conjunto de linhas do esquema DISCOVER_COMMAND_OBJECTS não informa a atividade por meio de consultas DMV.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Usando ADOMD.NET para retornar o conjunto de linhas  
 Ao usar ADOMD.NET e o conjunto de linhas de esquema para recuperar metadados, você pode usar o GUID ou a cadeia de caracteres para referenciar um objeto de conjunto de linhas de esquema no método GetSchemaDataSet. Para obter mais informações, consulte [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 A tabela a seguir fornece os valores de GUID e de cadeia de caracteres que identificam este conjunto de linhas.  
  
|Argumento|Valor|  
|--------------|-----------|  
|GUID|a07ccd35-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|CommandObjects|  
  
## <a name="see-also"></a>Consulte também  
 [XML for Analysis conjuntos de linhas de esquema](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  