---
title: COL_NAME (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 07/24/2017
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
f1_keywords:
- COL_NAME
- COL_NAME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- column properties [SQL Server]
- COL_NAME function
- column names [SQL Server]
- names [SQL Server], columns
ms.assetid: 214144ab-f2bc-4052-83cf-caf0a85c4cc6
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c69e738d69be578b92becba95e70534061286f43
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="colname-transact-sql"></a>COL_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Retorna o nome de uma coluna de um número de identificação de tabela correspondente especificado e o número de identificação de coluna.
  
![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Convenções da sintaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintaxe  
  
```sql
COL_NAME ( table_id , column_id )  
```  
  
## <a name="arguments"></a>Argumentos  
*table_id*  
É o número de identificação da tabela que contém a coluna. *table_id* é do tipo **int**.
  
*column_id*  
É o número de identificação da coluna. O parâmetro de *column_id* é do tipo **int**.
  
## <a name="return-types"></a>Tipos de retorno
**sysname**
  
## <a name="exceptions"></a>Exceções  
Retornará NULL em caso de erro ou se um chamador não tiver permissão para exibir o objeto.
  
Um usuário só pode exibir metadados de protegíveis de sua propriedade ou para os quais recebeu permissão. Isso significa que funções internas que emitem metadados, como COL_NAME, poderão retornar NULL se o usuário não tiver permissão para o objeto. Para obter mais informações, consulte [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).
  
## <a name="remarks"></a>Remarks  
Os parâmetros de *table_id* e *column_id* juntos produzem uma cadeia de caracteres de nome de coluna.
  
Para obter mais informações sobre como obter números de identificação de tabela e de coluna, consulte [OBJECT_ID &#40;Transact-SQL&#41;](../../t-sql/functions/object-id-transact-sql.md).
  
## <a name="examples"></a>Exemplos  
O exemplo a seguir retorna o nome da primeira coluna em uma tabela `Employee` de exemplo.
  
```sql
-- Uses AdventureWorks  
  
SELECT COL_NAME(OBJECT_ID('dbo.FactResellerSales'), 1) AS FirstColumnName,  
COL_NAME(OBJECT_ID('dbo.FactResellerSales'), 2) AS SecondColumnName;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
ColumnName          
------------   
BusinessEntityID  
```  
  
## <a name="see-also"></a>Consulte também
[Expressões &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
[Funções de metadados &#40;Transact-SQL&#41;](../../t-sql/functions/metadata-functions-transact-sql.md)  
[COLUMNPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/columnproperty-transact-sql.md)  
[COL_LENGTH &#40;Transact-SQL&#41;](../../t-sql/functions/col-length-transact-sql.md)
  
  

