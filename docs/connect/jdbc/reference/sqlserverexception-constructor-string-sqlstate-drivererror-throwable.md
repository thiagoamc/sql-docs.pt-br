---
title: Construtor SQLServerException (Java, SQLState, DriverError, Throwable) | Microsoft Docs
ms.custom: 
ms.date: 01/19/2018
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 101eca8f837dcbda00b252d5dc9867dfeb754351
ms.sourcegitcommit: 9d0467265e052b925547aafaca51e5a5e93b7e38
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/02/2018
---
# <a name="sqlserverexception-constructor-javalangstring-sqlstate-drivererror-javalangthrowable"></a>Construtor SQLServerException (Java, SQLState, DriverError, Throwable)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Inicializa uma nova instância do [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) classe quando é fornecido um **cadeia de caracteres** objeto, um **sqlstate** objeto, um **drivererror** objeto e um **throwable** objeto.

## <a name="syntax"></a>Sintaxe  
  
```  
public SQLServerException(java.lang.String errText,
            SQLState sqlState,
            DriverError driverError,
            java.lang.Throwable cause)
            
```  
  
#### <a name="parameters"></a>Parâmetros  
 *errText*  
  
 Uma cadeia de caracteres que contém o texto do erro.
  
 *sqlState*  
  
 Um objeto de enumeração que contém o estado SQL.
 
 *driverError*  
  
 Um objeto de enumeração que contém o erro do driver.
 
 *cause*  
  
 Um objeto throwable que contém a causa da exceção.
  
## <a name="see-also"></a>Consulte também  
 [Construtores de SQLServerException](../../../connect/jdbc/reference/sqlserverexception-constructors.md)   
 [Membros SQLServerException](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [Classe SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
  
