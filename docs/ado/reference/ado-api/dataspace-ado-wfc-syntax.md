---
title: DataSpace (ADO - sintaxe WFC) | Microsoft Docs
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords:
- DataSpace collection [ADO], ADO/WFC syntax
ms.assetid: 950d45d8-07de-467b-b255-f9a7b997204c
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3a393ae11d8248bc10c7d9831743426e2687ae76
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="dataspace-ado---wfc-syntax"></a>DataSpace (ADO - WFC sintaxe)
O **createObject** método o **DataSpace** classe especifica um objeto comercial para processar solicitações de aplicativo cliente (*progid*) e o protocolo de comunicação e o servidor (*conexão*). **createObject** retorna um [ObjectProxy](../../../ado/reference/ado-api/objectproxy-ado-wfc-syntax.md) objeto que representa o servidor.  
  
## <a name="package-commswfcdata"></a>pacote com.ms.wfc.data  
  
### <a name="constructor"></a>Construtor  
  
```  
public DataSpace()  
```  
  
### <a name="methods"></a>Métodos  
  
```  
public static ObjectProxy DataSpace.createObject(String  
    progid, String connection)  
```  
  
### <a name="properties"></a>Propriedades  
  
```  
public static int getInternetTimeout()  
public static void setInternetTimeout(int plInetTimeout)  
```  
  
## <a name="see-also"></a>Consulte também  
 [Objeto DataSpace (RDS)](../../../ado/reference/rds-api/dataspace-object-rds.md)
