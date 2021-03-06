---
title: "Método getXopenStates (SQLServerDataSource) | Microsoft Docs"
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
apiname: SQLServerDataSource.getXopenStates
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: de6fdf6b-8345-4490-b35e-7115b61e782e
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f90ff3fc2c843540fb9a95038203c9ce60d0b432
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2017
---
# <a name="getxopenstates-method-sqlserverdatasource"></a>Método getXopenStates (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retorna um **booliano** valor que indica se a conversão de estados SQL em estados compatíveis com XOPEN está habilitada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public boolean getXopenStates()  
```  
  
## <a name="return-value"></a>Valor de retorno  
 **True** se a conversão de estados SQL em estados compatíveis com XOPEN estiver habilitada. Caso contrário, **false**.  
  
## <a name="remarks"></a>Comentários  
 Se a propriedade xopenStates for definida como **true**, o [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] converterá estados SQL em estados compatíveis com XOPEN. O padrão é **false**, que faz com que o driver JDBC gerar códigos de estado SQL 99. Se xopenStates não for definido, o método getXopenStates retornará o valor padrão de **false**.  
  
## <a name="see-also"></a>Consulte também  
 [Membros de SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
