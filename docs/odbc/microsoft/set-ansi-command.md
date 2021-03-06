---
title: Comando de ANSI SET | Microsoft Docs
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
helpviewer_keywords: set ANSI command [ODBC]
ms.assetid: cf9a01b2-14bf-458c-a73c-2a58ddef32d8
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ef87baef7367068b5a22225f3bb9b4c3e1783ca6
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="set-ansi-command"></a>Comando de ANSI SET
Determina como as comparações entre cadeias de caracteres de comprimentos diferentes são feitas com o operador = em comandos do Visual FoxPro SQL.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
SET ANSI ON | OFF  
```  
  
## <a name="arguments"></a>Argumentos  
 ON  
 (Padrão para o driver; o padrão para o Visual FoxPro é OFF). Preenche para que a cadeia de caracteres mais curto com os espaços em branco necessário torná-lo igual a mais de cadeia de caracteres. As duas cadeias de caracteres são, em seguida, em comparação com o caractere de caractere para seus comprimentos inteiros. Considere essa comparação:  
  
```  
'Tommy' = 'Tom'  
```  
  
 O resultado é False (. F.) se SET ANSI, porque quando preenchidas, 'Tom' torna-se 'Tom' e as cadeias de caracteres 'Tom' e 'Tommy' não correspondem a caractere.  
  
 O = = operador usa esse método para comparações em comandos SQL do Visual FoxPro.  
  
 OFF  
 Especifica que a cadeia de caracteres mais curto não ser preenchida com espaços em branco. As duas cadeias de caracteres são comparadas caracteres para caracteres até o final da cadeia de caracteres mais curto é atingido. Considere essa comparação:  
  
```  
'Tommy' = 'Tom'  
```  
  
 O resultado será True (. T.) quando SET ANSI estiver desativado, pois a comparação é interrompido depois de 'Tom'.  
  
## <a name="remarks"></a>Remarks  
 SET ANSI determina se a mais curta das duas cadeias de caracteres é preenchida com espaços em branco quando é feita uma comparação de cadeia de caracteres SQL. SET ANSI não tem nenhum efeito o operador; = = Quando você usa o operador = =, a cadeia de caracteres menor sempre será preenchida com espaços em branco para a comparação.  
  
## <a name="string-order"></a>Ordem de cadeia de caracteres  
 Em comandos SQL, a ordem da esquerda para direita das duas cadeias de caracteres em uma comparação é irrelevantswitching uma cadeia de caracteres de um lado do = ou = = operador para o outro não afeta o resultado da comparação.  
  
## <a name="see-also"></a>Consulte Também  
 [Selecione - o comando SQL](../../odbc/microsoft/select-sql-command.md)   
 [Comando SET EXACT](../../odbc/microsoft/set-exact-command.md)
