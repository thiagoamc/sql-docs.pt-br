---
title: Estruturas de inteiro de 64 bits | Microsoft Docs
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
- C data types [ODBC], 64-bit integer structures
- data types [ODBC], C data types
- 64-bit integer structures [ODBC]
ms.assetid: ac80c798-d9b2-4430-85ed-bd2461db0ac7
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 15176629e0154b59c1dfadd9d58f755eb2c423ed
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="64-bit-integer-structures"></a>Estruturas de inteiro de 64 bits
O tipo de C para os identificadores de tipo de dados SQL_C_SBIGINT e SQL_C_UBIGINT na Microsoft C compiladores é _int64. Quando um compilador que um compilador Microsoft® C é usado, o tipo C pode ser diferente. Se o compilador dá suporte a inteiros de 64 bits nativo, o driver ou o aplicativo deve definir ODBCINT64 para ser do tipo inteiro de 64 bits nativo. Se o compilador não oferecer suporte a inteiros de 64 bits nativo, um aplicativo ou driver pode definir as estruturas a seguir para garantir que ele tenha acesso a esses dados:  
  
```  
typedef struct{  
SQLUINTEGER dwLowWord;  
SQLUINTEGER dwHighWord;  
} SQLUBIGINT  
  
typedef struct{  
SQLUINTEGER dwLowWord;  
SQLINTEGER sdwHighWord;  
} SQLBIGINT  
```  
  
 Essas estruturas devem ser alinhadas a um limite de 8 bytes, como um inteiro de 64 bits é alinhado com o limite de 8 bytes.
