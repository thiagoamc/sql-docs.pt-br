---
title: '@@TOTAL_ERRORS (Transact-SQL) | Microsoft Docs'
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@TOTAL_ERRORS'
- '@@TOTAL_ERRORS_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@TOTAL_ERRORS function'
- total errors [SQL Server]
- errors [SQL Server], read/write
- number of disk read/write errors
- disks [SQL Server], errors
- write errors [SQL Server]
- read/write errors
ms.assetid: 09e62428-ee0e-4ef5-b969-da9d255f1199
caps.latest.revision: 18
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 83d639209d35d6516bd9348f40f4eddfd30ddff5
ms.contentlocale: pt-br
ms.lasthandoff: 09/01/2017

---
# <a name="totalerrors-transact-sql"></a>@@TOTAL_ERRORS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retorna o número de erros de gravação de disco encontrados pelo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] desde que o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] foi iniciado pela última vez.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Convenções da sintaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
@@TOTAL_ERRORS  
```  
  
## <a name="return-types"></a>Tipos de retorno  
 **inteiro**  
  
## <a name="remarks"></a>Comentários  
 Nem todos os erros de gravação encontrados pelo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] são considerados por esta função. Os erros de gravação não fatais ocasionais são controlados pelo próprio servidor e não são considerados como erros. Para exibir um relatório que contém várias [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] estatísticas, incluindo o número total de erros, execute **sp_monitor**.  
  
## <a name="examples"></a>Exemplos  
 Este exemplo mostra o número de erros encontrado pelo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a partir da data e hora atuais.  
  
```  
SELECT @@TOTAL_ERRORS AS 'Errors', GETDATE() AS 'As of';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Errors      As of                   
----------- ----------------------  
0           3/28/2003 12:32:11 PM   
```  
  
## <a name="see-also"></a>Consulte também  
 [sp_monitor &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md)   
 [Funções estatísticas do sistema &#40; Transact-SQL &#41;](../../t-sql/functions/system-statistical-functions-transact-sql.md)  
  
  