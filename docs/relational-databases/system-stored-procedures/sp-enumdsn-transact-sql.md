---
title: sp_enumdsn (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_enumdsn
- sp_enumdsn_TSQL
helpviewer_keywords:
- sp_enumdsn
ms.assetid: 171cbc7d-7406-4cb0-8602-9405243bfd1d
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e8d4dcb23cf06385d4c26a198f17e806bdc0671a
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="spenumdsn-transact-sql"></a>sp_enumdsn (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retorna uma lista de todos os nomes de fonte de dados ODBC e OLE DB definidos para um servidor em execução em uma conta especifica de usuário [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. Esse procedimento armazenado é executado no Publicador, em qualquer banco de dados.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Convenções da sintaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
sp_enumdsn  
```  
  
## <a name="return-code-values"></a>Valores do código de retorno  
 **0** (êxito) ou **1** (falha)  
  
## <a name="result-sets"></a>Conjuntos de resultados  
  
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|**Nome da fonte de dados**|**sysname**|Nome da fonte de dados.|  
|**Description**|**varchar (255)**|Descrição da fonte de dados|  
|**Tipo**|**int**|Tipo da fonte de dados.<br /><br /> **1** = DSN ODBC<br /><br /> **3** = fonte de dados OLE DB|  
|**Nome do provedor**|**varchar (255)**|Nome do provedor OLE DB. O valor é NULL para ODBC DSN.|  
  
## <a name="remarks"></a>Comentários  
 Cada [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] serviço tem um contexto de usuário. Um contexto de usuário é um conjunto de entradas de Registro que inclui as definições das fontes de dados ODBC para o usuário. O contexto de usuário é fornecido pelo nome de usuário sob o qual o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] está executando.  
  
 Por exemplo, se o servidor estiver em execução no contexto de usuário de conta do sistema, os DSNs (nomes das fontes de dados) retornados serão todos DSNs do sistema associados à conta do sistema. Se o servidor estiver em execução em uma conta de usuário particular, somente os DSNs definidos para aquela conta particular daquele usuário serão retornados.  
  
## <a name="permissions"></a>Permissões  
 Somente membros do **sysadmin** pode executar a função de servidor fixa **sp_enumdsn**.  
  
## <a name="see-also"></a>Consulte também  
 [sp_dsninfo &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-dsninfo-transact-sql.md)   
 [Procedimentos armazenados do sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
