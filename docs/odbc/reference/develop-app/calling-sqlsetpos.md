---
title: Chamar SQLSetPos | Microsoft Docs
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
- compatibility [ODBC], SQLSetPos
- SQLSetPos function [ODBC], calling
- upgrading applications [ODBC], SQLSetPos
- backward compatibility [ODBC], SqlSetPos
- application upgrades [ODBC], SQLSetPos
ms.assetid: 846354b8-966c-4c2c-b32f-b0c8e649cedd
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 70351e468a6038a26b7b647d6bc7c64d3263f3d6
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="calling-sqlsetpos"></a>Chamar SQLSetPos
No ODBC 2. *x*, o ponteiro para a matriz de status de linha era um argumento para **SQLExtendedFetch**. A matriz de status de linha fosse atualizada posteriormente por uma chamada para **SQLSetPos**. Alguns drivers têm baseava-se no fato de que essa matriz não é alterado entre **SQLExtendedFetch** e **SQLSetPos**. Em ODBC 3. *x*, o ponteiro para a matriz de status é um campo de descritor e, portanto, o aplicativo pode alterar facilmente-o para apontar para uma matriz diferente. Isso pode ser um problema quando um ODBC 3. *x* aplicativo estiver trabalhando com um ODBC 2. *x* driver, mas está chamando **SQLSetStmtAttr** para definir o ponteiro de status de matriz e que está chamando **SQLFetchScroll** para buscar dados. O Gerenciador de Driver mapeia como uma sequência de chamadas para **SQLExtendedFetch**. No código a seguir, um erro deve normalmente ser gerado quando o Gerenciador de Driver mapeia o segundo **SQLSetStmtAttr** chamar ao trabalhar com um ODBC 2*. x* driver:  
  
```  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, rgfRowStatus, 0);  
SQLFetchScroll(hstmt, fFetchType, iRow);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, rgfRowStat1, 0);  
SQLSetPos(hstmt, iRow, fOption, fLock);  
```  
  
 O erro será gerado se não houvesse nenhuma maneira de alterar o ponteiro de status de linha no ODBC 2. *x* entre as chamadas para **SQLExtendedFetch**. Em vez disso, o Gerenciador de Driver executa as seguintes etapas ao trabalhar com um ODBC 2*. x* driver:  
  
1.  Inicializa um sinalizador de Gerenciador de Driver interno *fSetPosError* como TRUE.  
  
2.  Quando um aplicativo chama **SQLFetchScroll**, define o Gerenciador de Driver *fSetPosError* como FALSE.  
  
3.  Quando o aplicativo chama **SQLSetStmtAttr** para definir SQL_ATTR_ROW_STATUS_PTR, o Gerenciador de Driver define *fSetPosError* toTRUE igual.  
  
4.  Quando o aplicativo chama **SQLSetPos**, com *fSetPosError* igual a TRUE, o Gerenciador de Driver gera SQL_ERROR com SQLSTATE HY011 (atributo não pode ser definido agora) para indicar que o aplicativo tentativa de chamar **SQLSetPos** depois de alterar o ponteiro de status de linha, mas antes de chamar **SQLFetchScroll**.
