---
title: "Método storesLowerCaseIdentifiers (SQLServerDatabaseMetaData) | Microsoft Docs"
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
apiname: SQLServerDatabaseMetaData.storesLowerCaseIdentifiers
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: b7dd60f5-c4f3-4b14-9a33-d95327395083
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 22aec90378d48a194fe19dc595c2bc5847c25958
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2017
---
# <a name="storeslowercaseidentifiers-method-sqlserverdatabasemetadata"></a>Método storesLowerCaseIdentifiers (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera se esse banco de dados trata identificadores de SQL que usam maiúsculas e minúsculas, e que não estão entre aspas, como sem diferenciação de maiúsculas e minúsculas e os armazena em minúsculas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public boolean storesLowerCaseIdentifiers()  
```  
  
## <a name="return-value"></a>Valor de retorno  
 **True** se os identificadores forem armazenados em minúsculas. Caso contrário, **false**.  
  
## <a name="exceptions"></a>Exceções  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentários  
 Esse método storesLowerCaseIdentifiers é especificado pelo método storesLowerCaseIdentifiers na interface DatabaseMetadata.  
  
## <a name="see-also"></a>Consulte também  
 [Métodos SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membros de SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
