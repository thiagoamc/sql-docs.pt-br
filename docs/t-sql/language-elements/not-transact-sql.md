---
title: "NÃO (Transact-SQL) | Microsoft Docs"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- NOT_TSQL
- NOT
dev_langs:
- TSQL
helpviewer_keywords:
- negating Boolean input
- NOT operator [Transact-SQL]
- expressions [SQL Server], negating
- reversing Boolean expression values
ms.assetid: dc07cc35-20f1-46e6-9995-2938390dc19a
caps.latest.revision: 39
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 85cdc60ebe0c6f66624b539e0f20d83f32c19500
ms.contentlocale: pt-br
ms.lasthandoff: 09/01/2017

---
# <a name="not-transact-sql"></a>NOT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Nega uma entrada booliana.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Convenções da sintaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
[ NOT ] boolean_expression  
```  
  
## <a name="arguments"></a>Argumentos  
 *boolean_expression*  
 É qualquer valor booliano válido [expressão](../../t-sql/language-elements/expressions-transact-sql.md).  
  
## <a name="result-types"></a>Tipos de resultado  
 **Booliano**  
  
## <a name="result-value"></a>Valor do resultado  
 NOT inverte o valor de qualquer expressão booliana.  
  
## <a name="remarks"></a>Comentários  
 Usar NOT nega uma expressão.  
  
 A tabela a seguir mostra os resultados ao comparar valores TRUE e FALSE que usam o operador NOT.  
  
||NOT|  
|------|---------|  
|**TRUE**|FALSE|  
|**FALSE**|TRUE|  
|**DESCONHECIDO**|UNKNOWN|  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir localiza todas as bicicletas coloridas prateadas que não têm um preço padrão acima de $ 400.  
  
```  
-- Uses AdventureWorks  
  
SELECT ProductID, Name, Color, StandardCost  
FROM Production.Product  
WHERE ProductNumber LIKE 'BK-%' AND Color = 'Silver' AND NOT StandardCost > 400;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `ProductID   Name                     Color         StandardCost`  
  
 `---------   -------------------      ------      ------------`  
  
 `984         Mountain-500 Silver, 40  Silver        308.2179`  
  
 `985         Mountain-500 Silver, 42  Silver        308.2179`  
  
 `986         Mountain-500 Silver, 44  Silver        308.2179`  
  
 `987         Mountain-500 Silver, 48  Silver        308.2179`  
  
 `988         Mountain-500 Silver, 52  Silver        308.2179`  
  
 `(6 row(s) affected)`  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemplos: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 O exemplo a seguir restringe os resultados para `SalesOrderNumber` para valores que começam com `SO6` e `ProductKeys` maior que ou igual a 400.  
  
```  
-- Uses AdventureWorks  
  
SELECT ProductKey, CustomerKey, OrderDateKey, ShipDateKey  
FROM FactInternetSales  
WHERE SalesOrderNumber LIKE 'SO6%' AND NOT ProductKey < 400;  
```  
  
## <a name="see-also"></a>Consulte também  
 [Expressões &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Funções internas &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [Operadores &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [ONDE &#40; Transact-SQL &#41;](../../t-sql/queries/where-transact-sql.md)  
  
  


