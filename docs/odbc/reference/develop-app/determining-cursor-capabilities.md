---
title: Determinar os recursos do Cursor | Microsoft Docs
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
- scrollable cursors [ODBC]
- cursors [ODBC], capabilities
- cursors [ODBC], scrollable
ms.assetid: 35be486c-8f2d-4cec-beb8-df14151abfef
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 39d0678d8cae0c46e82cde79f8b21de3a75044d3
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="determining-cursor-capabilities"></a>Determinar os recursos do Cursor
As seguintes opções de quatro na **SQLGetInfo** descrevem quais tipos de cursor são suportados e quais são seus recursos:  
  
-   SQL_CURSOR_SENSITIVITY. Indica se um cursor é sensível às alterações feitas pelo outro cursor.  
  
-   SQL_SCROLL_OPTIONS. Lista os tipos de cursor com suporte (somente avanço, estáticos, controlado por, dinâmicos ou mistos). Todas as fontes de dados devem oferecer suporte a cursores de somente avanço.  
  
-   SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1 ou SQL_STATIC_CURSOR_ATTRIBUTES1 (dependendo do tipo de cursor). Lista os tipos de busca com suporte por cursores roláveis. Os bits no valor de retorno correspondem aos tipos de busca em **SQLFetchScroll**.  
  
-   SQL_KEYSET_CURSOR_ATTRIBUTES2 ou SQL_STATIC_CURSOR_ATTRIBUTES2 (dependendo do tipo de cursor). Indica se os cursores estáticos e controlados por conjunto de chaves podem detectar suas próprias atualizações, inserções e exclusões.  
  
 Um aplicativo pode determinar os recursos do cursor em tempo de execução chamando **SQLGetInfo** com essas opções. Normalmente, isso é feito por aplicativos genéricos. Recursos do cursor também podem ser determinados durante o desenvolvimento de aplicativo e seu uso embutido no aplicativo. Isso normalmente é feito por aplicativos verticais e personalizados, mas também pode ser feito por aplicativos genéricos que usam uma implementação de cursor do lado do cliente, como a biblioteca de cursores ODBC.
