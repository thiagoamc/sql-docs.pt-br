---
title: "Método Close (SQLServerResultSet) | Microsoft Docs"
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
apiname: SQLServerResultSet.close
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 8f3adf5b-874e-4cf2-b4ef-672dda42d77a
caps.latest.revision: "14"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cabdcad9f2a358e767af49f0ec3772f5ed552a74
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2017
---
# <a name="close-method-sqlserverresultset"></a>Método close (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Libera isso [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) do objeto banco de dados e recursos do JDBC imediatamente em vez de aguardar que isso aconteça quando ele é fechado automaticamente.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public void close()  
```  
  
## <a name="exceptions"></a>Exceções  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentários  
 Esse método fechar é especificado pelo método na interface Java.SQL. ResultSet fechar.  
  
 Um objeto SQLServerResultSet é fechado automaticamente pelo [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) objeto que o gerou quando esse objeto SQLServerStatement estiver fechado, novamente executado ou usado para recuperar o próximo resultado de uma sequência de vários resultados . Um objeto SQLServerResultSet é fechado automaticamente quando é coletado como lixo.  
  
 Ao executar uma instrução que produz um único conjunto de resultados grande, apenas de encaminhamento, somente leitura, você pode estar interessado apenas em algum conjunto inicial de linhas no conjunto de resultados retornado. Nesse caso, o aplicativo pode chamar o [Cancelar](../../../connect/jdbc/reference/cancel-method-sqlserverstatement.md) método do objeto de instrução associado antes de fechar o resultado definido para minimizar o tempo de processamento necessário para descartar as linhas desnecessárias restantes. Ao decidir se essa técnica será usada ou não, é recomendável considerar a compensação entre o tempo de processamento que seria economizado e o tempo e a viagem de ida e volta adicional ao servidor, necessários para cancelar a execução.  
  
## <a name="see-also"></a>Consulte também  
 [Membros de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
