---
title: "Método setPacketSize (SQLServerDataSource) | Microsoft Docs"
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
apiname: SQLServerDataSource.setPacketSize
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 5d490edc-a223-4870-a838-784952497e5f
caps.latest.revision: "20"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: aca0de41e907beb56752838554bb6c752b25e96f
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2017
---
# <a name="setpacketsize-method-sqlserverdatasource"></a>Método setPacketSize (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Define o tamanho de pacote de rede atual usado para se comunicar com [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)], especificado em bytes.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public void setPacketSize(int packetSize)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *tamanho do pacote*  
  
 Um **int** valor que contém o tamanho do pacote de rede.  
  
## <a name="remarks"></a>Comentários  
 O intervalo de valores aceitáveis dessa propriedade é [-1 | 0 | 512..32767]. Se essa propriedade for definida como um valor fora do intervalo aceitável, ocorrerá uma exceção.  
  
 O aplicativo poderá definir a propriedade packetSize enquanto estiver conectado com criptografia SSL (Protocolo SSL). O [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] negocia o tamanho do pacote com o servidor. Se a propriedade de criptografia é definida como "**true**" e o tamanho de pacote negociado for maior que o tamanho do registro SSL do provedor de segurança padrão do Java JVM (Máquina Virtual) do, o driver irá gerar um erro e encerrar a conexão.  
  
 Além disso, o aplicativo poderá definir a propriedade packetSize sem solicitar a criptografia SSL. Nesse caso, se o servidor exigir que o cliente dê suporte à criptografia SSL, o driver verificará o tamanho do registro SSL do provedor de segurança padrão da Máquina Virtual Java. Se a propriedade packetSize for maior que o tamanho do registro SSL do provedor de segurança padrão da Máquina Virtual Java, o driver retornará um erro e finalizará a conexão.  
  
 Para obter mais informações sobre como usar SSL, consulte [usando a criptografia SSL](../../../connect/jdbc/using-ssl-encryption.md).  
  
## <a name="see-also"></a>Consulte também  
 [Membros de SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
