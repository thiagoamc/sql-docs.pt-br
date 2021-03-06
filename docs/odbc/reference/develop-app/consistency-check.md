---
title: "Verificação de consistência | Microsoft Docs"
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
- descriptors [ODBC], consistency checks
- consistency checks [ODBC]
ms.assetid: deb80efa-ad1f-4ea5-b334-9817cd279e5c
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f1148984210013a8d5c0c6d9096d04ac21141d2a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="consistency-check"></a>Verificação de consistência
Uma verificação de consistência é executada pelo driver automaticamente sempre que um aplicativo define o campo SQL_DESC_DATA_PTR do IPD, descartar ou APD. Sempre que esse campo é definido, o driver verifica o valor do campo SQL_DESC_TYPE e os valores aplicáveis para o campo SQL_DESC_TYPE no mesmo registro são válidos e consistentes.  
  
 O campo SQL_DESC_DATA_PTR de um IPD normalmente não está definido; No entanto, um aplicativo pode fazê-lo para forçar uma verificação de consistência de campos do IPD. O valor definido para o campo SQL_DESC_DATA_PTR do IPD, na verdade, não é armazenado e não pode ser recuperado por uma chamada para **SQLGetDescField** ou **SQLGetDescRec**; a configuração é feita apenas para forçar o verificação de consistência. Uma verificação de consistência não pode ser executada em um IRD.  
  
 Para obter mais informações sobre a verificação de consistência, consulte [SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md).
