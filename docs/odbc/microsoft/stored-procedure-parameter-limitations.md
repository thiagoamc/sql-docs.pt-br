---
title: "Limitações de parâmetro do procedimento de armazenado | Microsoft Docs"
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
- stored procedures [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], stored procedures
ms.assetid: 8b804bcf-4cce-4e6f-aa45-00bab9ef9921
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9755f10bd5eb1bf88549bb2fd417049d45b59c6a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="stored-procedure-parameter-limitations"></a>Limitações do parâmetro de procedimento armazenado
> [!IMPORTANT]  
>  Este recurso será removido em uma versão futura do Windows. Evite usar esse recurso em desenvolvimentos novos e planeje modificar os aplicativos que atualmente o utilizam. Em vez disso, use o driver ODBC fornecido pela Oracle.  
  
 Quando executando Oracle procedimentos armazenados que utilizam 10 ou mais parâmetros de saída, a chamada de procedimento armazenado falhará, resultando em um erro de violação de acesso ou ActiveX Data Objects (ADO). Isso pode ocorrer ao usar o Microsoft ODBC Driver para Oracle com as versões 8.0.4.0.0 e 8.0.4.0.4 do software cliente Oracle.  
  
 Para corrigir o problema, o software cliente Oracle deve ser atualizado para a versão 8.0.4.2.0 ou superior. Entre em contato com o Oracle Corporation para obter mais informações sobre o [patches](../../odbc/microsoft/oracle-software-patches.md).  
  
> [!NOTE]  
>  Esse problema não ocorre com a versão mais recente do software cliente Oracle versão 8.0.3.0.0.
