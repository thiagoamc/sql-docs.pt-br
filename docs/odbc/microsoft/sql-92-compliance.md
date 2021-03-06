---
title: Conformidade de SQL-92 | Microsoft Docs
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
- Jet-based ODBC drivers [ODBC], SQL-92 compliance
- desktop database drivers [ODBC], SQL-92 compliance
- SQL-92 compliance [ODBC]
- ODBC desktop database drivers [ODBC], SQL-92 compliance
ms.assetid: 50c8c7df-df01-4f4d-ad62-d059cf29d73a
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ad887c4653c98a6fb4cab3df498233e6d196bd8b
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="sql-92-compliance"></a>Conformidade de SQL-92
Os Drivers de banco de dados de área de trabalho do ODBC e o mecanismo subjacente do Microsoft Jet não são compatíveis com o SQL-92. Eles oferecem suporte a muitos recursos que foram definidos em SQL-92. Não há suporte para alguns recursos com suporte no driver em SQL-92. Para obter mais informações, consulte o *guia do programador do Microsoft Jet Database Engine*. A seguir está as principais diferenças entre os dois:  
  
-   O SQL usado pelos Drivers de banco de dados da área de trabalho suporta expressões mais complexas que o especificado pelo SQL-92.  
  
-   Aplicam regras diferentes para o predicado BETWEEN.  
  
-   O SQL usado pelos Drivers de banco de dados de área de trabalho e ANSI SQL oferece suporte a palavras-chave diferentes.  
  
 Não há suporte para os seguintes recursos do SQL-92 SQL do Microsoft Jet:  
  
-   Instruções de segurança, como GRANT e bloqueio.  
  
-   DISTINCT com referências de função de agregação.  
  
 Os recursos a seguir são aprimoramentos no SQL usada pelos Drivers de banco de dados de área de trabalho que não são especificados pelo SQL-92:  
  
-   A instrução de TRANSFORMAÇÃO fornecendo suporte para consultas de tabela de referência cruzada.  
  
-   Funções de agregação adicionais (**StDev** e **VarP**).  
  
> [!NOTE]  
>  Os Drivers de banco de dados de área de trabalho oferecem suporte a sintaxe ANSI padrão para % (porcentagem) e _ (sublinhado), não * (asterisco) e? (ponto de interrogação).
