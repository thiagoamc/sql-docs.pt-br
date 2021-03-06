---
title: "SQL estático | Microsoft Docs"
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
- static SQL [ODBC]
- SQL [ODBC], embedded SQL
- SQL statements [ODBC], embedded SQL
- SQL statements [ODBC], static SQL
- embedded SQL [ODBC]
- SQL [ODBC], static SQL
ms.assetid: 667d92ec-fed9-4028-81d4-bb9ba867356a
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 249d3114af6631b56dd5d5106564f3912072ab29
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="static-sql"></a>SQL Estático
O embedded SQL mostrado na [exemplo do Embedded SQL](../../odbc/reference/embedded-sql-example.md) é conhecido como SQL estático. Ele é chamado SQL estático porque as instruções SQL no programa são estáticas; ou seja, elas não se alteram cada vez que o programa é executado. Conforme descrito na seção anterior, essas instruções são compiladas quando o restante do programa é compilado.  
  
 SQL estático funciona bem em muitas situações e pode ser usado em qualquer aplicativo para o qual o acesso a dados pode ser determinado em tempo de design do programa. Por exemplo, um programa de entrada de ordem sempre usa a mesma instrução para inserir um novo pedido e um sistema de reserva aérea sempre usa a mesma instrução para alterar o status de uma estação de disponível reservada. Cada uma dessas instruções deve ser generalizada com o uso de variáveis do host; valores diferentes podem ser inseridos em uma ordem de venda e estações diferentes podem ser reservadas. Como tais instruções podem ser codificados no programa, esses programas têm a vantagem de que as instruções precisam ser analisado, validado e otimização de uma só vez, em tempo de compilação. Isso resulta em código relativamente rápido.
