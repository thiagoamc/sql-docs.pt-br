---
title: "Método (SQLServerStatement) getMaxFieldSize | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerStatement.getMaxFieldSize
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: ed7bbcb8-660b-4e9b-8241-e216c42826f9
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bb2e2e6216631908efeed70e6cf5ac3a9b936abf
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2017
---
# <a name="getmaxfieldsize-method-sqlserverstatement"></a>getMaxFieldSize método (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera o número máximo de bytes que podem ser retornadas para caracteres e valores de coluna binária em um [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objeto que é produzido por esse [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public final int getMaxFieldSize()  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Um **int** que indica o número máximo de bytes que uma coluna pode conter ou 0 se não houver nenhum limite.  
  
## <a name="exceptions"></a>Exceções  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentários  
 Esse método getMaxFieldSize é especificado pelo método getMaxFieldSize na interface Java.SQL. Statement.  
  
## <a name="see-also"></a>Consulte também  
 [Métodos SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-methods.md)   
 [Classe SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
