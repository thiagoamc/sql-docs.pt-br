---
title: STIsClosed (tipo de dados geography) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STIsClosed (geography Data Type)
- STIsClosed_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STIsClosed method
ms.assetid: eba1643f-07c4-4500-8643-b7e90f908147
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5926dd4be979793fc164e84752a4b456e42565a3
ms.contentlocale: pt-br
ms.lasthandoff: 09/01/2017

---
# <a name="stisclosed-geography-data-type"></a>STIsClosed (tipo de dados geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retornará 1 se os pontos inicial e final da determinado **geografia** instância são os mesmos. Retorna 1 para **geografia** tipos de coleção, se cada contido **geografia** instância está fechada. Retornará 0 se a instância não for fechada.  
  
 Isso **geografia** método dá suporte ao tipo de dados **FullGlobe** instâncias ou a instâncias espaciais maiores que um hemisfério.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
.STIsClosed ( )  
```  
  
## <a name="return-types"></a>Tipos de retorno  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo de retorno: **bits**  
  
 Tipo de retorno CLR: **SqlBoolean**  
  
## <a name="remarks"></a>Comentários  
 Esse método retornará 0 se nenhuma figuras de um **geografia** instância são pontos, ou se a instância estiver vazia.  
  
 Esse método retornará true se um **FullGlobe** instância é um **polígono** ou outro tipo de instância.  
  
 Todos os **polígono** instâncias são consideradas fechadas.  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir cria uma instância `Polygon` e usa `STIsClosed()` para testar se `Polygon` está fechada.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SELECT @g.STIsClosed();  
```  
  
## <a name="see-also"></a>Consulte também  
 [Métodos do OGC em instâncias de Geografia](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  