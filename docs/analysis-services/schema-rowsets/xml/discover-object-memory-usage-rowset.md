---
title: Conjunto de linhas DISCOVER_OBJECT_MEMORY_USAGE | Microsoft Docs
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
helpviewer_keywords: DISCOVER_OBJECT_MEMORY_USAGE rowset
ms.assetid: 211cfa04-7bd6-43fe-8bd5-bfbff78bdafb
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 9be5091d26d264d71dad5e6892f7f8d7448d83c4
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2018
---
# <a name="discoverobjectmemoryusage-rowset"></a>Conjunto de linhas DISCOVER_OBJECT_MEMORY_USAGE
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Fornece informações sobre os recursos de memória usada pelos objetos.  
  
## <a name="rowset-columns"></a>Colunas do conjunto de linhas  
 O conjunto de linhas **DISCOVER_OBJECT_MEMORY_USAGE** contém as colunas a seguir.  
  
|Nome da coluna|Indicador de tipo|Comprimento|Description|  
|-----------------|--------------------|------------|-----------------|  
|**OBJECT_PARENT_PATH**|**DBTYPE_WSTR**||O caminho para o pai do objeto atual.|  
|**OBJECT_ID**|**DBTYPE_WSTR**||A ID do objeto como definida na hora de criação.|  
|**OBJECT_MEMORY_SHRINKABLE**|**DBTYPE_I8**||A quantidade total de memória (bytes) usada para todos os objetos reduzíveis que são de propriedade direta do objeto atual. O valor atual não inclui memória de objetos pertencentes aos objetos nomeados dos quais o objeto atual é o proprietário direto.|  
|**OBJECT_MEMORY_NONSHRINKABLE**|**DBTYPE_I8**||A quantidade total de memória (bytes) de todos os objetos não reduzíveis que são de propriedade direta do objeto atual. O valor atual não inclui memória de objetos pertencentes aos objetos nomeados dos quais o objeto atual é o proprietário direto.|  
|**OBJECT_VERSION**|**DBTYPE_I4**||O número de versão de metadados do objeto. Esse número mudará sempre que o objeto for alterado.|  
|**OBJECT_DATA_VERSION**|**DBTYPE_I4**||O número de linhagem dos dados do objeto. Esse número será incrementado sempre que o objeto for processado.|  
|**OBJECT_TYPE_ID**|**DBTYPE_I4**||Reservado para uso interno.|  
|**OBJECT_TIME_CREATED**|**DBTYPE_DBTIMESTAMP**||A hora do servidor UTC no momento em que o objeto foi criado.|  
  
 Este conjunto de linhas do esquema não é classificado.  
  
## <a name="restriction-columns"></a>Colunas de restrição  
 O conjunto de linhas **DISCOVER_OBJECT_MEMORY_USAGE** pode ser restringido nas colunas listadas na tabela a seguir.  
  
|Nome da coluna|Indicador de tipo|Estado de restrição|  
|-----------------|--------------------|-----------------------|  
|**OBJECT_PARENT_PATH**|**DBTYPE_WSTR**|Opcional.|  
|**OBJECT_ID**|**DBTYPE_WSTR**|Opcional|  
  
## <a name="see-also"></a>Consulte Também  
 [Conjunto de linhas de esquema do XML](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
