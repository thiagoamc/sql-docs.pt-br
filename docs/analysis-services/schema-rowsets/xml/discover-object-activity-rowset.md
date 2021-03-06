---
title: Conjunto de linhas DISCOVER_OBJECT_ACTIVITY | Microsoft Docs
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
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DISCOVER_OBJECT_ACTIVITY rowset
ms.assetid: 100f7de1-ad5c-4973-b863-3c10df1245c4
caps.latest.revision: "14"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 573b41cb848ee7a8e93bfdc4625b8a05857f2d61
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2018
---
# <a name="discoverobjectactivity-rowset"></a>Conjunto de linhas DISCOVER_OBJECT_ACTIVITY
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Oferece uso de recursos por objeto desde o início do serviço.  
  
## <a name="rowset-columns"></a>Colunas do conjunto de linhas  
 O conjunto de linhas **DISCOVER_OBJECT_ACTIVITY** contém as colunas a seguir.  
  
|Nome da coluna|Indicador de tipo|Comprimento|Description|  
|-----------------|--------------------|------------|-----------------|  
|**OBJECT_AGGREGATION_HIT**|**DBTYPE_I8**||O número de vezes que uma agregação do objeto foi atingida desde o início do serviço.|  
|**OBJECT_AGGREGATION_MISS**|**DBTYPE_I8**||O número de vezes que uma agregação existente, do objeto, não foi ignorada (ou seja, não foi usada) desde o início do serviço.|  
|**OBJECT_CPU_TIME_MS**|**DBTYPE_I8**||O tempo de CPU, em milissegundos, consumidos pelo objeto desde o início do serviço.|  
|**OBJECT_DATA_VERSION**|**DBTYPE_I4**||O número de linhagem dos dados no objeto; este número será incrementado sempre que o objeto for processado.|  
|**OBJECT_HIT**|**DBTYPE_I8**||O número de vezes que o objeto foi atingido no cache desde o início do serviço.|  
|**OBJECT_ID**|**DBTYPE_WSTR**||A ID do objeto como definida na hora de criação|  
|**OBJECT_MISS**|**DBTYPE_I8**||O número de vezes que o objeto foi ignorado no cache desde o início do serviço.|  
|**OBJECT_PARENT_PATH**|**DBTYPE_WSTR**||O caminho para o pai do objeto atual.|  
|**OBJECT_READ_KB**|**DBTYPE_I8**||O valor acumulado de leitura de dados pelo objeto desde o início do serviço, em quilobytes.|  
|**OBJECT_READS**|**DBTYPE_I8**||O número acumulado de operações de leitura pelo objeto desde o início do serviço.|  
|**OBJECT_ROWS_RETURNED**|**DBTYPE_I8**||O número de linhas retornado pelo objeto ao chamador desde o início do serviço.|  
|**OBJECT_ROWS_SCANNED**|**DBTYPE_I8**||O número de linhas verificadas pelo objeto desde o início do serviço.|  
|**OBJECT_VERSION**|**DBTYPE_I4**||O número de versão de metadados do objeto; esse número mudará sempre que o objeto for alterado.|  
|**OBJECT_WRITE_KB**|**DBTYPE_I8**||O valor acumulado dos dados gravados pelo objeto desde o início do serviço, em quilobytes.|  
|**OBJECT_WRITES**|**DBTYPE_I8**||O número acumulado de operações de gravação pelo objeto desde o início do serviço.|  
  
 Este conjunto de linhas do esquema não é classificado.  
  
## <a name="restriction-columns"></a>Colunas de restrição  
 O conjunto de linhas **DISCOVER_OBJECT_ACTIVTY** pode ser restringido nas colunas listadas na tabela a seguir.  
  
|Nome da coluna|Indicador de tipo|Estado de restrição|  
|-----------------|--------------------|-----------------------|  
|OBJECT_PARENT_PATH|DBTYPE_WSTR|Opcional.|  
|OBJECT_ID|DBTYPE_WSTR|Opcional.|  
  
## <a name="see-also"></a>Consulte Também  
 [Conjunto de linhas de esquema do XML](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
