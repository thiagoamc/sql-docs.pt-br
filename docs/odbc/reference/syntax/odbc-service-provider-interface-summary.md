---
title: "Resumo de Interface de provedor de serviço ODBC | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ace6085b-355b-435b-8734-503fc3c12ec2
caps.latest.revision: "4"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d5cd2ab9be5c49365e0a398677c901c4f2d46d9f
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="odbc-service-provider-interface-summary"></a>Resumo de Interface de provedor de serviço ODBC
A tabela a seguir descreve as funções de interface de provedor de serviços de ODBC. Para obter mais informações sobre a sintaxe e semântica para cada função, consulte [referência de Interface de provedor de serviço do ODBC (IDA)](../../../odbc/reference/syntax/odbc-service-provider-interface-spi-reference.md).  
  
|Nome da função|Finalidade|  
|-------------------|-------------|  
|[SQLSetConnectAttrForDbcInfo](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Mesmo que [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md), mas ela define o atributo no token de informações de conexão em vez de no identificador da conexão.|  
|[SQLSetDriverConnectInfo](../../../odbc/reference/syntax/sqldrivertodatasource-function.md)|Define a cadeia de caracteres de conexão para o token de informações de conexão para um aplicativo [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) chamar.|  
|[SQLSetConnectInfo](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Define a fonte de dados, ID de usuário e senha para o token de informações de conexão para um aplicativo [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) chamar.|  
|[SQLGetPoolID](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Recupera a ID do pool.|  
|[SQLRateConnection](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Determina se um driver pode reutilizar uma conexão existente no pool de conexão.|  
|[SQLPoolConnect](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Crie uma nova conexão se nenhuma conexão no pool pode ser reutilizada.|  
|[SQLCleanupConnectionPoolID](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Informa um driver que uma ID do pool foi atingida.|
