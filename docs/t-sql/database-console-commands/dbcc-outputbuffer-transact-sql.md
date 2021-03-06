---
title: DBCC OUTPUTBUFFER (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 07/16/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|database-console-commands
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DBCC OUTPUTBUFFER
- OUTPUTBUFFER_TSQL
- OUTPUTBUFFER
- DBCC_OUTPUTBUFFER_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DBCC OUTPUTBUFFER statement
- output buffers
- current output buffer
ms.assetid: e912a06d-9fde-4e26-b057-801255d79504
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 836055f5a80a7f3768d1485a6c0514eafd6258aa
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2018
---
# <a name="dbcc-outputbuffer-transact-sql"></a>DBCC OUTPUTBUFFER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Retorna o buffer de saída atual nos formatos hexadecimal e ASCII para a *session_id* especificada.
  
![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Convenções da sintaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintaxe  
```sql
DBCC OUTPUTBUFFER ( session_id [ , request_id ])  
[ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>Argumentos  
 *session_id*  
 É a ID da sessão associada a cada conexão primária ativa.  
  
 *request_id*  
 É a solicitação exata (lote) para pesquisar na sessão atual.  
 A seguinte consulta retorna *request_id*:  
  
```sql
SELECT request_id   
FROM sys.dm_exec_requests   
WHERE session_id = @@spid;  
```  
  
 com  
 Permite que as opções sejam especificadas.  
  
 NO_INFOMSGS  
 Suprime todas as mensagens informativas com níveis de severidade de 0 a 10.  
  
## <a name="remarks"></a>Remarks  
DBCC OUTPUTBUFFER exibe os resultados enviados ao cliente especificado (*session_id*). Para processos que não contêm fluxos de saída, é retornada uma mensagem de erro.
  
Para mostrar a instrução executada que retornou os resultados exibidos por DBCC OUTPUTBUFFER, execute DBCC INPUTBUFFER.
  
## <a name="result-sets"></a>Conjuntos de resultados  
DBCC OUTPUTBUFFER retorna o seguinte (os valores podem variar):
  
```sql
Output Buffer                                                              
------------------------------------------------------------------------   
01fb8028:  04 00 01 5f 00 00 00 00 e3 1b 00 01 06 6d 00 61  ..._.........m.a  
01fb8038:  00 73 00 74 00 65 00 72 00 06 6d 00 61 00 73 00  .s.t.e.r..m.a.s.  
'...'  
01fb8218:  04 17 00 00 00 00 00 d1 04 18 00 00 00 00 00 d1  ................  
01fb8228:   .  
  
(33 row(s) affected)  
  
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
## <a name="permissions"></a>Permissões  
Exige associação à função de servidor fixa **sysadmin** .
  
## <a name="examples"></a>Exemplos  
O exemplo a seguir retorna as informações de buffer de saída atuais para uma suposta ID de sessão `52`.
  
```sql
DBCC OUTPUTBUFFER (52);  
```  
  
## <a name="see-also"></a>Consulte Também  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[sp_who &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md)  
[Sinalizadores de rastreamento &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)
  
  
