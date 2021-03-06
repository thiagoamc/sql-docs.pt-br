---
title: "Observações de segurança do thread em funções de API (Driver ODBC para Oracle) | Microsoft Docs"
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
- ODBC driver for Oracle [ODBC], threading
- threading options [ODBC]
- multiple concurrent statements [ODBC]
ms.assetid: f0c9bdfd-f79d-4088-9ecb-afcd8ca7fb73
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f8519d900e9cbb4e9c942fdfcccfb21a63d14705
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="thread-safety-notes-on-api-functions-odbc-driver-for-oracle"></a>Observações de segurança do thread em funções de API (Driver ODBC para Oracle)
> [!IMPORTANT]  
>  Este recurso será removido em uma versão futura do Windows. Evite usar esse recurso em desenvolvimentos novos e planeje modificar os aplicativos que atualmente o utilizam. Em vez disso, use o driver ODBC fornecido pela Oracle.  
  
 O Microsoft ODBC Driver for Oracle é thread-safe; No entanto, a Oracle não permite várias instruções simultâneas em uma única conexão. O driver impõe essa restrição. Em outras palavras, em aplicativos multissegmentados, embora qualquer thread pode chamar o Driver ODBC do Oracle a qualquer momento, o driver de blocos de qualquer outro segmento do driver na mesma conexão até que o thread original deixa o driver.  
  
 O driver não bloqueia se houver duas instruções de duas conexões diferentes. No entanto, se houver uma conexão única com duas instruções, há potencial de bloqueio.
