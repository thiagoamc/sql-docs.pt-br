---
title: Chamando SQLGetDiagField | Microsoft Docs
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
- application upgrades [ODBC], SQLGetDiagField
- backward compatibility [ODBC], SqlGetDiagField
- upgrading applications [ODBC], SQLGetDiagField
- SQLGetDiagField function [ODBC], calling
- compatibility [ODBC], SQLGetDiagField
ms.assetid: 3c4fb606-b81c-4f11-9820-f0a54e3bc401
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2d9a8ffdb5166840e53a7a3b05785f32d4dc1c1a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="calling-sqlgetdiagfield"></a>Chamar SQLGetDiagField
Quando um ODBC 3. *x* aplicativo chama **SQLGetDiagField** em um ODBC 2*. x* driver, o driver retornará SQL_SUCCESS e as informações apropriadas na  *\*DiagInfoPtr* se o *DiagIdentifier* é SQL_DIAG_CLASS_ORIGIN, SQL_DIAG_CLASS_SUBCLASS_ORIGIN, SQL_DIAG_CONNECTION_NAME, SQL_DIAG_MESSAGE_TEXT, SQL_DIAG_NATIVE, SQL_DIAG_ NÚMERO, SQL_DIAG_RETURNCODE, SQL_DIAG_SERVER_NAME ou SQL_DIAG_SQLSTATE. Todos os outros campos de diagnósticos retornará SQL_ERROR.
