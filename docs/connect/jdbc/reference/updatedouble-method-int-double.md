---
title: "Método updateDouble (int, double) | Microsoft Docs"
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
apiname: SQLServerResultSet.updateDouble (int, double)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 90c47643-e27e-425d-85a0-63866f858367
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4d3b59a08d5e7734590884401d128cf68f5c3515
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2017
---
# <a name="updatedouble-method-int-double"></a>Método updateDouble (int, double)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Atualiza a coluna designada com um **duplo** valor, considerando o índice da coluna.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public void updateDouble(int index,  
                         double x)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *índice*  
  
 Um **int** que indica o índice da coluna.  
  
 *x*  
  
 Um **duplo** valor.  
  
## <a name="exceptions"></a>Exceções  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentários  
 Esse método updateDouble é especificado pelo método updateDouble na interface Java.SQL. resultset.  
  
## <a name="see-also"></a>Consulte também  
 [Método updateDouble &#40; SQLServerResultSet &#41;](../../../connect/jdbc/reference/updatedouble-method-sqlserverresultset.md)   
 [Membros de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
