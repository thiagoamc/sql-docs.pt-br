---
title: "Método getTimestamp (Java, java.util.Calendar) | Microsoft Docs"
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
apiname: SQLServerResultSet.getTimestamp (java.lang.String, java.util.Calendar)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 44474000-8951-49ee-93a5-c8cb879eaf55
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 62466b3b77d2ce85fcc9573804b1cd8b7347280e
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2017
---
# <a name="gettimestamp-method-javalangstring-javautilcalendar-sqlserverresultset"></a>Método getTimestamp (Java, java.util.Calendar) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera o valor do nome da coluna designada na linha atual deste [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objeto como um objeto Java.SQL. timestamp no Java linguagem de programação, usando um objeto de calendário.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public java.sql.Timestamp getTimestamp(java.lang.String colName,  
                                       java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *colName*  
  
 Um **cadeia de caracteres** que contém o nome da coluna.  
  
 *CAL*  
  
 Um objeto de calendário.  
  
## <a name="return-value"></a>Valor de retorno  
 Um objeto de carimbo de hora.  
  
## <a name="exceptions"></a>Exceções  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentários  
 Esse método getTimestamp é especificado pelo método getTimestamp na interface Java.SQL. resultset.  
  
 Este método retorna valores apenas das [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] colunas datetime e smalldatetime.  
  
## <a name="see-also"></a>Consulte também  
 [Método getTimestamp &#40; SQLServerResultSet &#41;](../../../connect/jdbc/reference/gettimestamp-method-sqlserverresultset.md)   
 [Membros de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
