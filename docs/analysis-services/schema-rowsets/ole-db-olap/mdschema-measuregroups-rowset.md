---
title: Conjunto de linhas mdschema_measuresgroups | Microsoft Docs
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
apiname: MDSCHEMA_MEASUREGROUPS
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: MDSCHEMA_MEASUREGROUPS rowset
ms.assetid: bab1bbd0-421b-4fad-9aee-e6511e0e1f1b
caps.latest.revision: "28"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: aebac1aafd7d49e6b5b5c21343161184ba19da34
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2018
---
# <a name="mdschemameasuregroups-rowset"></a>Conjunto de linhas MDSCHEMA_MEASURESGROUPS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Descreve os grupos de medidas em um banco de dados.  
  
## <a name="rowset-columns"></a>Colunas do conjunto de linhas  
 O conjunto de linhas **MDSCHEMA_MEASUREGROUPS** contém as colunas a seguir.  
  
|Nome da coluna|Indicador de tipo|Comprimento|Description|  
|-----------------|--------------------|------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**||O nome do catálogo ao qual pertence esse grupo de medidas. **NULL** se o provedor não oferecer suporte a catálogos.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**||Sem suporte.|  
|**CUBE_NAME**|**DBTYPE_WSTR**||O nome do cubo ao qual pertence esse grupo de medidas.|  
|**MEASUREGROUP_NAME**|**DBTYPE_WSTR**||O nome do grupo de medidas.|  
|**DESCRIPTION**|**DBTYPE_WSTR**||Uma descrição legível do membro.|  
|**IS_WRITE_ENABLED**|**DBTYPE_BOOL**||Um Booliano que indica se um grupo de medidas está habilitado para gravação.<br /><br /> Retornará **true** se o grupo de medidas estiver habilitado para gravação.|  
|**MEASUREGROUP_CAPTION**|**DBTYPE_WSTR**||A legenda de exibição do grupo de medidas.|  
  
 Este conjunto de linhas do esquema não é classificado.  
  
## <a name="restriction-columns"></a>Colunas de restrição  
 O conjunto de linhas **MDSCHEMA_MEASUREGROUPS** pode ser restringido nas colunas da tabela a seguir.  
  
|Nome da coluna|Indicador de tipo|Estado de restrição|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Opcional.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Opcional.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Opcional.|  
|**MEASUREGROUP_NAME**|**DBTYPE_WSTR**|Opcional.|  
  
## <a name="see-also"></a>Consulte Também  
 [Conjuntos de linhas de esquema OLE DB para OLAP](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
