---
title: "Padrão de fonte de dados | Microsoft Docs"
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
- data sources [ODBC], connection functions
- connecting to data source [ODBC], default data source
- functions [ODBC], data source or driver connections
- data sources [ODBC], default
- default data source [ODBC]
- connecting to data source [ODBC], functions
- connecting to driver [ODBC], default data source
- connecting to driver [ODBC], functions
- connection functions [ODBC]
- ODBC drivers [ODBC], connection functions
ms.assetid: dd473cc6-f051-4aa0-ab14-3dd1b37fe99e
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 995b47b42691935df0c3aa6d0776af15c99c6551
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="default-data-source"></a>Fonte de dados padrão
O driver pode selecionar uma fonte de dados, chamada de fonte de dados padrão, em certos casos em que o aplicativo não especificar explicitamente um:  
  
-   Em uma chamada para **SQLConnect** onde o *ServerName* argumento é uma cadeia de caracteres de comprimento zero, um ponteiro nulo ou padrão.  
  
-   Em uma chamada para **SQLDriverConnect** onde *InConnectionString* o especifica **DSN**= padrão ou especifica o **DSN** palavra-chave um fonte de dados que não está contido nas informações do sistema.  
  
 Ele é definido pelo driver como a fonte de dados padrão é especificada. Isso pode envolver a ação administrativa e pode depender do usuário.
