---
title: "Método isSparseColumnSet (SQLServerResultSetMetaData) | Microsoft Docs"
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
ms.assetid: ac363670-78ae-49f1-aeda-4fba3329a258
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0486fd19f95b6a9b4d987c4b4dc7f1810e82543d
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2017
---
# <a name="issparsecolumnset-method-sqlserverresultsetmetadata"></a>Método isSparseColumnSet (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Indica se uma coluna em um conjunto de resultados é um conjunto de colunas esparsas.  
  
## <a name="syntax"></a>Sintaxe  
  
```scr  
public boolean isSparseColumnSet(int column)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *coluna*  
  
 O índice (base um) da coluna.  
  
## <a name="return-value"></a>Valor de retorno  
 **True** se uma coluna em um conjunto de resultados é um conjunto de colunas esparsas, caso contrário, **false**.  
  
## <a name="remarks"></a>Comentários  
 Esse método não recupera informações do banco de dados.  
  
## <a name="see-also"></a>Consulte também  
 [Métodos SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-methods.md)   
 [Membros de SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [Classe SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
