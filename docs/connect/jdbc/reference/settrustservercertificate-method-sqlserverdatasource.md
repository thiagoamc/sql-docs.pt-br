---
title: "Método setTrustServerCertificate (SQLServerDataSource) | Microsoft Docs"
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
apiname: setTrustServerCertificate Method (SQLServerDataSource)
apilocation: setTrustServerCertificate Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 6c37b518-147e-4cd9-9eff-b48a3f5888c6
caps.latest.revision: "14"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8b0248cec1f5ba4fd760fe8ef3b641d0f346783a
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2017
---
# <a name="settrustservercertificate-method-sqlserverdatasource"></a>Método setTrustServerCertificate (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Define uma **booliano** valor que indica se a propriedade trustServerCertificate está habilitada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public void setTrustServerCertificate(boolean trustServerCertificate)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *trustServerCertificate*  
  
 **True** se o certificado do Secure Sockets Layer (SSL) de servidor for automaticamente confiável quando a camada de comunicação for criptografada com SSL. Caso contrário, **false**.  
  
## <a name="remarks"></a>Comentários  
 Se a propriedade trustServerCertificate estiver definida como **true**, o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] certificado SSL será automaticamente confiável quando a camada de comunicação for criptografada com SSL. Em outras palavras, o [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] não validará o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] certificado SSL. O valor padrão é **false**.  
  
 Se a propriedade trustServerCertificate estiver definida como **false**, o [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] validará o certificado SSL do servidor.  
  
## <a name="see-also"></a>Consulte também  
 [Membros de SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
