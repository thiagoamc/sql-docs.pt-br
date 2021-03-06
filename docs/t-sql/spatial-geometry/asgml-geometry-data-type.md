---
title: AsGml (tipo de dados geometry) | Microsoft Docs
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- AsGml(geometry_Data_Type)_TSQL
- AsGml
- AsGml(geometry Data Type)
- AsGml_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- AsGml (geometry Data Type)
ms.assetid: f6c2e130-05f3-4ef3-921b-d78b51437d48
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6e95bef8ad53d9393467843fe05c67304ad4d86a
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2018
---
# <a name="asgml-geometry-data-type"></a>AsGml (tipo de dados geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retorna a representação GML (Geography Markup Language) de uma instância de **geometry**.
  
Para obter mais informações sobre Geography Markup Language, confira a seguinte especificação do Open Geospatial Consortium:[Especificação do OGC, Geography Markup Language.](http://go.microsoft.com/fwlink/?LinkId=93629)
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
.AsGml ( )  
```  
  
## <a name="return-types"></a>Tipos de retorno  
 Tipo de retorno [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **XML**  
  
 Tipo de retorno do CLR: **SqlXml**  
  
## <a name="remarks"></a>Remarks  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir cria uma instância `LineString` e usa `AsGML()` para retornar uma descrição GML da instância.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 0 1, 1 0)', 0)  
SELECT @g.AsGml();  
```  
  
 Esse método retorna a descrição como uma instância `LineString`.  
  
```  
<LineString xmlns="http://www.opengis.net/gml">  
<posList>0 0 0 1 1 0</posList></LineString>  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Métodos estendidos em instâncias geometry](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

