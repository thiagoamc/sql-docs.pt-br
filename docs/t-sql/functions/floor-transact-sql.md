---
title: FLOOR (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FLOOR_TSQL
- FLOOR
dev_langs:
- TSQL
helpviewer_keywords:
- integers [SQL Server]
- largest integers
- FLOOR function [Transact-SQL]
ms.assetid: 4f26c784-9240-491f-b854-754be3fccae4
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 1ca177e0b168b5091a251157df5d4ece616f1323
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="floor-transact-sql"></a>FLOOR (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Retorna o maior inteiro menor ou igual à expressão numérica especificada.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Convenções da sintaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
FLOOR ( numeric_expression )  
```  
  
## <a name="arguments"></a>Argumentos  
 *numeric_expression*  
 É uma expression da categoria de tipo de dados numéricos exatos ou aproximados, com exceção do tipo de dados **bit**.  
  
## <a name="return-types"></a>Tipos de retorno  
 Retorna o mesmo tipo que *numeric_expression*.  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir mostra valores numéricos positivos, numéricos negativos e de moeda com a função `FLOOR`.  
  
```  
SELECT FLOOR(123.45), FLOOR(-123.45), FLOOR($123.45);  
```  
  
 O resultado é a parte inteira do valor calculado no mesmo tipo de dados que *numeric_expression*.  
  
```  
---------      ---------     -----------  
123            -124          123.0000     
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemplos: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 O exemplo a seguir mostra valores numéricos positivos, numéricos negativos e valores com a função `FLOOR`.  
  
```  
SELECT FLOOR(123.45), FLOOR(-123.45), FLOOR($123.45);  
```  
  
 O resultado é a parte inteira do valor calculado no mesmo tipo de dados que *numeric_expression*.  
  
 ```
 -----   ---------    -----------  
  
 123     -124         123
 ```  
  
## <a name="see-also"></a>Consulte Também  
 [Funções matemáticas &#40;Transact-SQL&#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)  
  
  

