---
title: "Função CAST SQL-92 | Microsoft Docs"
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
- functions [ODBC], SQL-92 functions
- SQL-92 functions [ODBC]
- CAST function [ODBC]
ms.assetid: 982f09e5-8205-41b9-98b3-8f898e24743f
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e0e62a85a53da521710ed4cc61d0260e2182fb26
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="sql-92-cast-function"></a>Função CAST SQL-92
O **CAST** função definida no SQL-92 é equivalente ao **converter** função definida no ODBC. A sintaxe das funções equivalentes é o seguinte:  
  
```  
{ fn CONVERT (value-exp, data-type) } /* ODBC  
CAST (value-exp AS data-type) /* SQL92  
```  
  
 O SQL-92 **CAST** função determina quais tipos de dados podem ser convertidos para que outros tipos de dados. (Para obter mais informações, consulte a especificação de SQL-92). O **CAST** há suporte para a função no nível de transição de FIPS.  
  
 Um aplicativo pode determinar se há suporte para o **CAST** funciona da seguinte maneira:  
  
1.  Chamar **SQLGetInfo** com o tipo de informação SQL_SQL_CONFORMANCE. Se o valor de retorno para o tipo de informações é SQL_SC_FIPS127_2_TRANSITIONAL, SQL_SC_SQL92_INTERMEDIATE ou SQL_SC_SQL92_FULL, o **CAST** suporte para a função.  
  
2.  Se o valor de retorno do tipo de informações SQL_SQL_CONFORMANCE é SQL_SC_ENTRY_LEVEL ou 0, chame **SQLGetInfo** com o tipo de informação SQL_SQL92_VALUE_EXPRESSIONS. Se o bit SQL_SVE_CAST for definido, o **CAST** suporte para a função.
