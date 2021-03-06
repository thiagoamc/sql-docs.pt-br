---
title: Protegendo aplicativos do JDBC Driver | Microsoft Docs
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
ms.assetid: 90724ec6-a9cb-43ef-903e-793f89410bc0
caps.latest.revision: "19"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 7e26574a8a11256136b376546e1f52533a986711
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2017
---
# <a name="securing-jdbc-driver-applications"></a>Protegendo aplicativos do JDBC Driver
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Aprimorar a segurança de um [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] aplicativo envolve mais que evitar armadilhas de codificação comuns. Um aplicativo que acessa dados tem muitos pontos potenciais de falha que um invasor pode explorar para recuperar, manipular, ou destruir dados confidenciais. É importante entender todos os aspectos de segurança, do processo de modelagem de ameaça durante a fase de design de seu aplicativo à implantação consequente, e continuando pela manutenção contínua.  
  
 Os tópicos nesta seção descrevem algumas preocupações comuns de segurança inclusive cadeias de caracteres de conexão, validação de entrada do usuário e segurança geral de aplicativo.  
  
## <a name="in-this-section"></a>Nesta seção  
  
|Tópico|Description|  
|-----------|-----------------|  
|[Protegendo cadeias de conexão](../../connect/jdbc/securing-connection-strings.md)|Descreve técnicas para ajudar a proteger informações usadas para conectar a uma fonte de dados.|  
|[Validando entradas de usuário](../../connect/jdbc/validating-user-input.md)|Descreve técnicas para validar a entrada do usuário.|  
|[Segurança do aplicativo](../../connect/jdbc/application-security.md)|Descreve como usar permissões de política de Java para ajudar a proteger um aplicativo do driver JDBC.|  
|[Usando criptografia SSL](../../connect/jdbc/using-ssl-encryption.md)|Descreve como estabelecer um canal de comunicação seguro com um [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] usando SSL Secure Sockets Layer () do banco de dados.|  
|[Modo FIPS](../../connect/jdbc/fips-mode.md)|Descreve como usar o driver JDBC em modo compatível com FIPS.| 
  
## <a name="see-also"></a>Consulte também  
 [Visão geral do JDBC Driver](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
