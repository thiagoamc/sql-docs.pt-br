---
title: "Método getTimestamp (int) | Microsoft Docs"
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
apiname: SQLServerCallableStatement.getTimestamp (int)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: a9fd6496-c72e-4cc6-b46a-4aa9f13f90ff
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c2941eaaf240220e21fe6bac2761e914e6c89d3e
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2017
---
# <a name="gettimestamp-method-int"></a>Método getTimestamp (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera o valor do parâmetro designado como um objeto java.sql.Timestamp na linguagem de programação Java, considerando o índice do parâmetro.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public java.sql.Timestamp getTimestamp(int index)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *índice*  
  
 Um **int** que indica o índice do parâmetro.  
  
## <a name="return-value"></a>Valor de retorno  
 Um objeto de carimbo de hora.  
  
## <a name="exceptions"></a>Exceções  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentários  
 Esse método getTimestamp é especificado pelo método getTimestamp na interface do CallableStatement.  
  
 Este método retorna valores apenas das [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] **datetime** e **smalldatetime** colunas.  
  
## <a name="see-also"></a>Consulte também  
 [Método getTimestamp &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/gettimestamp-method-sqlservercallablestatement.md)   
 [Membros SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Classe SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
