---
title: ROWCOUNT_BIG (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ROWCOUNT_BIG
- ROWCOUNT_BIG_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ROWCOUNT_BIG function
- number of rows affected by statement
- row affected by statements [SQL Server]
- statements [SQL Server], last statement
- counting rows
ms.assetid: 6e18a0eb-bb36-4348-90d9-8b1ecf095064
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6b40fbc3cca4d396c32b192a7c59a485da70ea8b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="rowcountbig-transact-sql"></a>ROWCOUNT_BIG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retorna o número de linhas afetadas pela última instrução executada. Essa função opera como [@@ROWCOUNT](../../t-sql/functions/rowcount-transact-sql.md), exceto que o tipo de retorno de ROWCOUNT_BIG é **bigint**.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Convenções da sintaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
ROWCOUNT_BIG ( )  
```  
  
## <a name="return-types"></a>Tipos de retorno  
 **bigint**  
  
## <a name="remarks"></a>Remarks  
 Seguindo uma instrução SELECT, esta função retorna o número de linhas retornado pela instrução SELECT.  
  
 Seguindo uma instrução INSERT, UPDATE ou DELETE, esta função retorna o número de linhas afetadas pela instrução de modificação de dados.  
  
 Seguindo instruções que não retornam linhas, como uma instrução IF, esta função retorna 0.  
  
## <a name="see-also"></a>Consulte Também  
 [COUNT_BIG &#40;Transact-SQL&#41;](../../t-sql/functions/count-big-transact-sql.md)   
 [Tipos de dados &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
  
  
