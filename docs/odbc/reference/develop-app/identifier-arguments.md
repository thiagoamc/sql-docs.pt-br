---
title: Argumentos de identificador | Microsoft Docs
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
helpviewer_keywords:
- identifier arguments [ODBC]
- catalog functions [ODBC], arguments
- arguments in catalog functions [ODBC], identifier
ms.assetid: b9de003f-cb49-4dec-b528-14a5b8ff12bd
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1a6800d7cb73790c61ec94acaffdeb291fa6b475
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="identifier-arguments"></a>Argumentos de identificador
Se uma cadeia de caracteres em um argumento de identificador está entre aspas, o driver remove à esquerda e à direita de espaços em branco e literalmente trata a cadeia de caracteres entre aspas. Se a cadeia de caracteres não está entre aspas, o driver remove dobras e espaços em branco à direita a cadeia de caracteres em maiusculas. A definição de um argumento de identificador para um ponteiro nulo retornará SQL_ERROR e SQLSTATE HY009 (uso inválido de ponteiro nulo), a menos que o argumento é um nome de catálogo e não há suporte para catálogos.  
  
 Esses argumentos são tratados como argumentos de identificador se o atributo da instrução SQL_ATTR_METADATA_ID for definido como SQL_TRUE. Nesse caso, o sublinhado (_) e o sinal de porcentagem (%) será tratado como o caractere real, não como um caractere de padrão de pesquisa. Esses argumentos são tratados como um argumento comum ou um argumento padrão, dependendo do argumento, se esse atributo é definido como SQL_FALSE.  
  
 Embora identificadores que contenham caracteres especiais devem estar entre aspas em instruções SQL, eles devem não estar entre aspas quando transmitidos como argumentos de função de catálogo, como caracteres de aspas passados para as funções de catálogo são interpretados literalmente. Por exemplo, suponha que o identificador de caractere de aspas (que é específico do driver e retornado por meio de **SQLGetInfo**) é uma aspas duplas ("). A primeira chamada para **SQLTables** retorna um conjunto de resultados contendo informações sobre a tabela de contas a pagar, enquanto a segunda chamada retorna informações sobre a tabela "Contas a pagar", que é provável que nem o pretendido.  
  
```  
SQLTables(hstmt1, NULL, 0, NULL, 0, "Accounts Payable", SQL_NTS, NULL, 0);  
SQLTables(hstmt2, NULL, 0, NULL, 0, "\"Accounts Payable\"", SQL_NTS, NULL, 0);  
```  
  
 Identificadores entre aspas são usados para distinguir um nome de coluna true de uma coluna pseudo o mesmo nome, como ROWID no Oracle. Se for passado "ROWID" em um argumento de uma função de catálogo, a função funcionarão com a coluna pseudo ROWID se ele existir. Se a coluna pseudo não existir, a função funciona apenas com a coluna "ROWID". Se ROWID é passado um argumento de uma função de catálogo, a função funciona apenas com a coluna ROWID.  
  
 Para obter mais informações sobre os identificadores entre aspas, consulte [identificadores entre aspas](../../../odbc/reference/develop-app/quoted-identifiers.md).
