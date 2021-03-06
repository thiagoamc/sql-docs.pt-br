---
title: Cache de biblioteca de cursor | Microsoft Docs
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
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- cache [ODBC]
ms.assetid: d6a91cd6-3905-4e3a-98ab-37fce893dbe1
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0da55a85fa5f8e1fd53656aa1cac37959a4200f7
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="cursor-library-cache"></a>Cache de biblioteca de cursor
> [!IMPORTANT]  
>  Este recurso será removido em uma versão futura do Windows. Evite usar esse recurso em desenvolvimentos novos e planeje modificar os aplicativos que atualmente o utilizam. A Microsoft recomenda o uso da funcionalidade de cursor do driver.  
  
 Para cada linha de dados no conjunto de resultados, a biblioteca de cursores armazena em cache os dados para cada coluna associada, o comprimento dos dados em cada coluna associada e o status da linha. A biblioteca de cursores usa os valores no cache de ambos para retornar pelo **SQLFetch** e **SQLFetchScroll** e para construir instruções pesquisadas para operações posicionadas. Para obter mais informações, consulte [construindo instruções pesquisados](../../../odbc/reference/appendixes/constructing-searched-statements.md).  
  
 Esta seção contém os tópicos a seguir.  
  
-   [Dados de coluna](../../../odbc/reference/appendixes/column-data.md)  
  
-   [Comprimento dos dados da coluna](../../../odbc/reference/appendixes/length-of-column-data.md)  
  
-   [Status da linha](../../../odbc/reference/appendixes/row-status.md)  
  
-   [Local do cache](../../../odbc/reference/appendixes/location-of-cache.md)
