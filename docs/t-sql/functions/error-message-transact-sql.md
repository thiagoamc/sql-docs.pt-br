---
title: ERROR_MESSAGE (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/16/2017
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
- ERROR_MESSAGE_TSQL
- ERROR_MESSAGE
dev_langs:
- TSQL
helpviewer_keywords:
- ERROR_MESSAGE function
- errors [SQL Server], text of
- messages [SQL Server], text of
- TRY...CATCH [SQL Server]
- CATCH block
ms.assetid: f32877a6-5f17-418c-a32c-5a1a344b3c45
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 598b89a47941c038b39387468de8bd3036acae2b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="errormessage-transact-sql"></a>ERROR_MESSAGE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retorna o texto da mensagem do erro que fez o bloco CATCH de uma construção TRY…CATCH ser executado.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Convenções da sintaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
ERROR_MESSAGE ( )   
```  
  
## <a name="return-types"></a>Tipos de retorno  
 **nvarchar(4000)**  
  
## <a name="return-value"></a>Valor de retorno  
 Quando chamado em um bloco CATCH, retorna o texto completo da mensagem do erro que fez o bloco ser executado. O texto inclui os valores fornecidos para qualquer parâmetro substituível, como comprimentos, nomes de objeto ou horas.  
  
 Retorna NULL se for chamado fora do escopo de um bloco CATCH.  
  
## <a name="remarks"></a>Remarks  
 ERROR_MESSAGE pode ser acionado em qualquer lugar dentro do escopo de um bloco CATCH.  
  
 ERROR_MESSAGE retorna a mensagem de erro, independentemente do número de vezes que ele é executado ou se é executado dentro do escopo do bloco CATCH. É diferente de funções como @@ERROR, que retornam apenas um número de erro na instrução imediatamente posterior àquela que causa um erro ou a primeira instrução de um bloco CATCH.  
  
 Em blocos CATCH aninhados, ERROR_MESSAGE retorna a mensagem de erro específica do escopo do bloco CATCH no qual é referenciado. Por exemplo, o bloco CATCH de uma construção TRY...CATCH externa poderia ter uma construção TRY...CATCH aninhada. Dentro do bloco CATCH aninhado, ERROR_MESSAGE retornará a mensagem de erro que invocou o bloco CATCH aninhado. Se ERROR_MESSAGE for executado em um bloco CATCH externo, retornará a mensagem de erro que invocou esse bloco CATCH.  
  
## <a name="examples"></a>Exemplos  
  
### <a name="a-using-errormessage-in-a-catch-block"></a>A. Usando ERROR_MESSAGE em um bloco CATCH  
 O exemplo de código a seguir mostra uma instrução `SELECT` que gera um erro de divisão por zero. A mensagem do erro é retornada.  
  
```  
  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  
```  
  
### <a name="b-using-errormessage-in-a-catch-block-with-other-error-handling-tools"></a>B. Usando ERROR_MESSAGE em um bloco CATCH com outras ferramentas de tratamento de erros  
 O exemplo de código a seguir mostra uma instrução `SELECT` que gera um erro de divisão por zero. Além da mensagem de erro, são retornadas as informações relacionadas ao erro.  
  
```  
  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT  
        ERROR_NUMBER() AS ErrorNumber  
        ,ERROR_SEVERITY() AS ErrorSeverity  
        ,ERROR_STATE() AS ErrorState  
        ,ERROR_PROCEDURE() AS ErrorProcedure  
        ,ERROR_LINE() AS ErrorLine  
        ,ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemplos: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-errormessage-in-a-catch-block-with-other-error-handling-tools"></a>C. Usando ERROR_MESSAGE em um bloco CATCH com outras ferramentas de tratamento de erros  
 O exemplo de código a seguir mostra uma instrução `SELECT` que gera um erro de divisão por zero. Além da mensagem de erro, são retornadas as informações relacionadas ao erro.  
  
```  
  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT  
        ERROR_NUMBER() AS ErrorNumber  
        ,ERROR_SEVERITY() AS ErrorSeverity  
        ,ERROR_STATE() AS ErrorState  
        ,ERROR_PROCEDURE() AS ErrorProcedure  
        ,ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  
```  
  

