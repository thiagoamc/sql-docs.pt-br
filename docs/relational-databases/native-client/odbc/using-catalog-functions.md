---
title: "Usando funções de catálogo | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client|ODBC
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- ODBC, functions
- SQLLinkedCatalogs function
- SQL Server Native Client ODBC driver, catalog functions
- SQLLinkedServers function
- catalog functions [ODBC]
- functions [ODBC]
ms.assetid: 7773fb2e-06b5-4c4b-88e9-0ad9132ad273
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 77d2f7de5e43df5cfc559b12bb88dcdd4412af6e
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2018
---
# <a name="using-catalog-functions"></a>Usando funções de catálogo
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Todos os bancos de dados têm uma estrutura que contém os dados armazenados no banco de dados. Uma definição dessa estrutura, juntamente com outras informações, como permissões, é armazenada em um catálogo (implementado como um conjunto de tabelas do sistema), também conhecido como um dicionário de dados.  
  
 O [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] driver ODBC Native Client permite que um aplicativo determine a estrutura de banco de dados por meio de chamadas para funções de catálogo ODBC. As funções de catálogo retornam informações em conjuntos de resultados e são implementadas usando procedimentos armazenados de catálogo para consultar as tabelas do sistema no catálogo. Por exemplo, um aplicativo pode solicitar um conjunto de resultados que contém informações sobre todas as tabelas no sistema ou todas as colunas de uma tabela específica. As funções de catálogo ODBC padrão são usadas para obter informações de catálogo do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] com o qual o aplicativo está conectado.  
  
 O [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dá suporte a consultas distribuídas nas quais dados de várias fontes de dados OLE DB heterogêneas são acessadas em uma única consulta. Um dos métodos para acessar uma fonte de dados OLE DB remota é definir a fonte de dados como um servidor vinculado. Isso pode ser feito usando [sp_addlinkedserver](../../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md). Depois que o servidor vinculado foi definido, é possível referenciar objetos nesse servidor em instruções Transact-SQL usando um nome de quatro partes:  
  
 *linked_server_name.catalog.schema.object_name*.  
  
 O driver ODBC do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client dá suporte a duas funções específicas do driver que ajudam a obter informações de catálogo de servidores vinculados:  
  
-   **SQLLinkedServers**  
  
     Retorna uma lista dos servidores vinculados definidos para o servidor local.  
  
-   **SQLLinkedCatalogs**  
  
     Retorna uma lista dos catálogos contidos em um servidor vinculado.  
  
 Depois de ter um nome de servidor vinculado e um nome de catálogo, o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] driver ODBC Native Client oferece suporte à obtenção de informações do catálogo usando um nome de duas partes de *linked_server_name***.*** catálogo* para *CatalogName* funções de catálogo ODBC a seguir:  
  
-   **SQLColumnPrivileges**  
  
-   **SQLColumns**  
  
-   **SQLPrimaryKeys**  
  
-   **SQLStatistics**  
  
-   **SQLTablePrivileges**  
  
-   **SQLTables**  
  
 A parte dois *linked_server_name***.*** catálogo* também tem suporte para *FKCatalogName* e *PKCatalogName* na [SQLForeignKeys](../../../relational-databases/native-client-odbc-api/sqlforeignkeys.md).  
  
 O uso de SQLLinkedServers e SQLLinkedCatalogs exige os seguintes arquivos:  
  
-   sqlncli.h  
  
     Inclui protótipos de função e definições de constantes para funções de catálogo do servidor vinculado. O sqlncli.h deve ser incluído no aplicativo ODBC e deverá estar no caminho de inclusão quando o aplicativo for compilado.  
  
-   sqlncli11.lib  
  
     Deve estar no caminho da biblioteca do vinculador e ser especificado como um arquivo a ser vinculado. O sqlncli11.lib é distribuído com o driver ODBC do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
-   sqlncli11.dll  
  
     Deve estar presente no tempo de execução. O sqlncli11.dll é distribuído com o driver ODBC do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
## <a name="see-also"></a>Consulte também  
 [Cliente nativo do SQL Server &#40; ODBC &#41;](../../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)   
 [SQLColumnPrivileges](../../../relational-databases/native-client-odbc-api/sqlcolumnprivileges.md)   
 [SQLColumns](../../../relational-databases/native-client-odbc-api/sqlcolumns.md)   
 [SQLPrimaryKeys](../../../relational-databases/native-client-odbc-api/sqlprimarykeys.md)   
 [SQLTablePrivileges](../../../relational-databases/native-client-odbc-api/sqltableprivileges.md)   
 [SQLTables](../../../relational-databases/native-client-odbc-api/sqltables.md)   
 [SQLStatistics](../../../relational-databases/native-client-odbc-api/sqlstatistics.md)  
  
  
