---
title: "Método setIntegratedSecurity (SQLServerDataSource) | Microsoft Docs"
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
apiname: SQLServerDataSource.setIntegratedSecurity
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 4c968ee4-b041-424a-bf69-cc2c4a4f51c6
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5c82fad6b2fe56afe748b22ea8c131e8aff0e25d
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2017
---
# <a name="setintegratedsecurity-method-sqlserverdatasource"></a>Método setIntegratedSecurity (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Define uma **booliano** valor que indica se a propriedade integratedSecurity está habilitada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public void setIntegratedSecurity(boolean enable)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *Habilitar*  
  
 **True** se integratedSecurity estiver habilitada. Caso contrário, **false**.  
  
## <a name="remarks"></a>Comentários  
 Definido como "**true**" para indicar que as credenciais do Windows serão usadas por [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] para autenticar o usuário do aplicativo. Se "**true**", o [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] procurará no cache de credencial do computador local as credenciais que já foram fornecidas no logon do computador ou na rede. Se "**false**", o nome de usuário e a senha devem ser fornecidos.  
  
> [!NOTE]  
>  Essa propriedade só é suportada em [!INCLUDE[msCoName](../../../includes/msconame_md.md)] sistemas operacionais Windows.  
  
 Para obter mais informações sobre como usar a autenticação integrada, consulte [criar a URL de Conexão](../../../connect/jdbc/building-the-connection-url.md).  
  
## <a name="see-also"></a>Consulte também  
 [Membros de SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
