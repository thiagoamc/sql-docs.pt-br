---
title: "Método setSelectMethod (SQLServerDataSource) | Microsoft Docs"
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
apiname: SQLServerDataSource.setSelectMethod
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 7934276d-5ac9-4cbc-a2a0-2c65c93733ac
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1348b8e7724edb9366ffff07594874dcc8d5c2b0
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2017
---
# <a name="setselectmethod-method-sqlserverdatasource"></a>Método setSelectMethod (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Define o tipo de cursor padrão que é usado para todos os conjuntos de resultados que são criados usando esse [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public void setSelectMethod(java.lang.String selectMethod)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *selectMethod*  
  
 Um **cadeia de caracteres** valor que contém o tipo de cursor padrão.  
  
## <a name="remarks"></a>Comentários  
 O selectMethod é o tipo de cursor padrão que é usado para um conjunto de resultados. Essa propriedade é útil quando você está lidando com conjuntos de resultados grandes e não deseja armazenar o conjunto de resultados inteiro na memória no lado do cliente. Ao definir a propriedade como "cursor", você pode criar um cursor do lado do servidor que pode buscar partes menores de dados por vez. Se a propriedade selectMethod não for definida, [getSelectMethod](../../../connect/jdbc/reference/getselectmethod-method-sqlserverdatasource.md) retorna o valor padrão de "direto".  
  
## <a name="see-also"></a>Consulte também  
 [Membros de SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
