---
title: "Método (Java, long) (SQLServerNClob) Position | Microsoft Docs"
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
ms.assetid: 46d4beec-831a-449f-98b6-322a80cc499a
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 733e4e3588c38303a6a84c794593a5e5111074fe
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2017
---
# <a name="position-method-javalangstring-long-sqlservernclob"></a>Método position (java.lang.String, long) (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera a posição do caractere no qual a subcadeia de caracteres especificada *searchstr* aparece no **NCLOB** valor representado por esse **NClob** objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public long position(java.lang.String searchstr,  
              long start)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *searchstr*  
  
 A subcadeia de caracteres pela qual pesquisar.  
  
 *Iniciar*  
  
 A posição em que a pesquisa deve ser iniciada; a primeira posição é 1.  
  
## <a name="return-value"></a>Valor de retorno  
 A posição em que a subcadeia de caracteres aparece; ou -1 se ela não estiver presente. A primeira posição é 1.  
  
## <a name="exceptions"></a>Exceções  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentários  
 Esse método de posição é especificado pelo método na interface Java.SQL. NCLOB posição.  
  
## <a name="see-also"></a>Consulte também  
 [Posicione o método &#40; SQLServerNClob &#41;](../../../connect/jdbc/reference/position-method-sqlservernclob.md)   
 [Métodos SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [Membros SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [Classe SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
