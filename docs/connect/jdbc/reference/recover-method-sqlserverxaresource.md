---
title: "Método Recover (SQLServerXAResource) | Microsoft Docs"
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
apiname: SQLServerXAResource.recover
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 840ecfcf-0dd3-4b7b-976f-dc9a96cd1464
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 73f341196b8dd86a098031afc8c556ceb7f26a2c
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2017
---
# <a name="recover-method-sqlserverxaresource"></a>Método recover (SQLServerXAResource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Obtém uma lista de ramificações de transação preparadas de um gerenciador de recursos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public javax.transaction.xa.Xid[] recover(int flags)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *sinalizadores*  
  
 Um **int** valor que pode ter um dos seguintes valores: XAResource.TMSTARTRSCAN ou XAResource.TMENDRSCAN ou XAResource.TMNOFLAGS ou XAResource.TMSTARTTRSCAN | XAResource.TMENDRSCAN.  
  
## <a name="return-value"></a>Valor de retorno  
 Um objeto Xid.  
  
## <a name="exceptions"></a>Exceções  
 javax.transaction.xa.XAException  
  
## <a name="remarks"></a>Comentários  
 Esse método de recuperação é especificado pelo método de recuperação na interface javax.  
  
 Se o parâmetro **sinalizador** não é XAResource.TMSTARTRSCAN ou XAResource.TMSTARTRSCAN | XAResource.TMENDRSCAN, um exame de recuperação deve estar em andamento.  
  
## <a name="see-also"></a>Consulte também  
 [Métodos SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-methods.md)   
 [Membros SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [Classe SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
