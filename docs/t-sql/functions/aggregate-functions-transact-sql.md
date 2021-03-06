---
title: Aggregate Functions (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 01/16/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- functions [SQL Server], aggregate
- aggregate functions [SQL Server], about aggregate functions
- summarizing functions
- aggregate functions [SQL Server]
ms.assetid: 0c06ae42-eb0a-4d77-9d74-aa1e7f344009
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 74cc3903f4d5e10718c2d4488e4c3b8da4448b80
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/18/2018
---
# <a name="aggregate-functions-transact-sql"></a>Funções de agregação (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

As funções de agregação executam um cálculo em um conjunto de valores e retornam um único valor. Com exceção de COUNT, as funções de agregação ignoram valores nulos. As funções de agregação normalmente são usadas com a cláusula GROUP BY da instrução SELECT.
  
Todas as funções de agregação são determinísticas. Isso significa que as funções de agregação retornam o mesmo valor sempre que são chamadas com o uso de um conjunto específico de valores de entrada. Para obter mais informações sobre determinismo de funções, consulte [Funções determinísticas e não determinísticas](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md). A [cláusula OVER](../../t-sql/queries/select-over-clause-transact-sql.md) pode seguir todas as funções de agregação, exceto GROUPING e GROUPING_ID.
  
As funções de agregação podem ser usadas como expressões apenas no seguinte:
-   A lista de seleção de uma instrução SELECT (uma subconsulta ou uma consulta externa).  
-   Uma cláusula HAVING.  
  
[!INCLUDE[tsql](../../includes/tsql-md.md)] fornece as seguintes funções de agregação:
  
|||  
|-|-|  
|[AVG](../../t-sql/functions/avg-transact-sql.md)|[MIN](../../t-sql/functions/min-transact-sql.md)|  
|[CHECKSUM_AGG](../../t-sql/functions/checksum-agg-transact-sql.md)|[SUM](../../t-sql/functions/sum-transact-sql.md)|  
|[COUNT](../../t-sql/functions/count-transact-sql.md)|[STDEV](../../t-sql/functions/stdev-transact-sql.md)|  
|[COUNT_BIG](../../t-sql/functions/count-big-transact-sql.md)|[STDEVP](../../t-sql/functions/stdevp-transact-sql.md)|  
|[GROUPING](../../t-sql/functions/grouping-transact-sql.md)|[STRING_AGG](../../t-sql/functions/string-agg-transact-sql.md)|  
|[GROUPING_ID](../../t-sql/functions/grouping-id-transact-sql.md)|[VAR](../../t-sql/functions/var-transact-sql.md)|  
|[MAX](../../t-sql/functions/max-transact-sql.md)|[VARP](../../t-sql/functions/varp-transact-sql.md)|  
  
## <a name="see-also"></a>Consulte também
[Funções internas &#40;Transact-SQL&#41;](../../t-sql/functions/functions.md)  
[Cláusula OVER &#40;Transact-SQL&#41;](../../t-sql/queries/select-over-clause-transact-sql.md)
  
  
