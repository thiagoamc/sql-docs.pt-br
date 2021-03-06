---
title: sp_addmessage (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_addmessage
- sp_addmessage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addmessage
ms.assetid: 54746d30-f944-40e5-a707-f2d9be0fb9eb
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 1b8b71c14da2b38bbc16c63b39143fd0a85ebf30
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2018
---
# <a name="spaddmessage-transact-sql"></a>sp_addmessage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Armazena uma nova mensagem de erro definida pelo usuário em uma instância do [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Mensagens armazenadas usando **sp_addmessage** podem ser exibidas usando o **messages** exibição do catálogo.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Convenções da sintaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
sp_addmessage [ @msgnum= ] msg_id , [ @severity= ] severity , [ @msgtext= ] 'msg'   
     [ , [ @lang= ] 'language' ]   
     [ , [ @with_log= ] { 'TRUE' | 'FALSE' } ]   
     [ , [ @replace= ] 'replace' ]   
```  
  
## <a name="arguments"></a>Argumentos  
 [ **@msgnum****=** ] *msg_id*  
 É a ID da mensagem. *msg_id* é **int** com um padrão NULL. *msg_id* erro definido pelo usuário de mensagens podem ser um inteiro entre 50.001 e 2.147.483.647. A combinação de *msg_id* e *idioma* deve ser exclusiva; um erro será retornado se a ID já existe para o idioma especificado.  
  
 [  **@severity =** ]*severidade*  
 É o nível de gravidade do erro. *severidade* é **smallint** com um padrão NULL. Os níveis válidos são de 1 a 25. Para obter mais informações sobre severidades, consulte [Severidade de erro do mecanismo de banco de dados](../../relational-databases/errors-events/database-engine-error-severities.md).  
  
 [ **@msgtext =** ] **'***msg***'**  
 É o texto da mensagem de erro. *msg* é **nvarchar (255)** com um padrão NULL.  
  
 [ **@lang =** ] **'***language***'**  
 É o idioma desta mensagem. *idioma* é **sysname** com um padrão NULL. Como vários idiomas podem ser instalados no mesmo servidor, *idioma* Especifica o idioma em que cada mensagem é gravada. Quando *idioma* for omitido, o idioma é o idioma padrão para a sessão.  
  
 [  **@with_log =** ] { **'**TRUE**'** | **'FALSE'** }  
 Especifica se a mensagem deve ser gravada no log do aplicativo do Windows quando ocorrer. **@with_log**é **varchar(5)** com um padrão de FALSE. Se for TRUE, o erro sempre será gravado no log do aplicativo do Windows. Se for FALSE, o erro nem sempre será gravado no log do aplicativo do Windows, mas poderá ser gravado dependendo de como foi gerado. Somente membros do **sysadmin** função de servidor pode usar essa opção.  
  
> [!NOTE]  
>  Se uma mensagem for gravada no log do aplicativo do Windows, ela também será gravada no arquivo de log de erros do [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 [ **@replace** *=* ] **'***replace***'**  
 Se for especificado como a cadeia de caracteres *substituir*, uma mensagem de erro existente será substituída com o novo nível de gravidade e texto da mensagem. *substituir* é **varchar(7)** com um padrão NULL. Essa opção deve ser especificada se *msg_id* já existe. Se você substituir uma mensagem Mensagem em inglês, o nível de severidade será substituída para todas as mensagens em todos os outros idiomas que têm o mesmo *msg_id*.  
  
## <a name="return-code-values"></a>Valores do código de retorno  
 0 (êxito) ou 1 (falha)  
  
## <a name="result-sets"></a>Conjuntos de resultados  
 Nenhuma  
  
## <a name="remarks"></a>Remarks  
 Para versões do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que não estão em inglês, a versão em inglês dos EUA de uma mensagem já deverá existir para que a mensagem possa ser adicionada usando outro idioma. A severidade das duas versões da mensagem deve corresponder.  
  
 Ao localizar mensagens contendo parâmetros, use números de parâmetro que correspondem aos parâmetros da mensagem original. Insira um ponto de exclamação (!) depois de cada número de parâmetro.  
  
|Mensagem original|Mensagem localizada|  
|----------------------|-----------------------|  
|'Original message param 1: %s,<br /><br /> param 2: % d'|'Localized message param 1: %1!,<br /><br /> param 2: %2!'|  
  
 Por causa das diferenças de sintaxe, os número de parâmetro na mensagem localizada podem não ocorrer na mesma sequência que a mensagem original.  
  
## <a name="permissions"></a>Permissões  
Requer a participação no **sysadmin** ou **serveradmin** funções de servidor fixas.  
  
## <a name="examples"></a>Exemplos  
  
### <a name="a-defining-a-custom-message"></a>A. Definindo uma mensagem personalizada  
 O exemplo a seguir adiciona uma mensagem personalizada para **messages**.  
  
```  
USE master;  
GO  
EXEC sp_addmessage 50001, 16,   
   N'Percentage expects a value between 20 and 100.   
   Please reexecute with a more appropriate value.';  
GO  
```  
  
### <a name="b-adding-a-message-in-two-languages"></a>B. Adicionando uma mensagem em dois idiomas  
 O exemplo seguinte adiciona primeiro uma mensagem em inglês dos EUA e, em seguida, adiciona a mesma mensagem em francês`.`  
  
```  
USE master;  
GO  
EXEC sp_addmessage @msgnum = 60000, @severity = 16,   
   @msgtext = N'The item named %s already exists in %s.',   
   @lang = 'us_english';  
  
EXEC sp_addmessage @msgnum = 60000, @severity = 16,   
   @msgtext = N'L''élément nommé %1! existe déjà dans %2!',   
   @lang = 'French';  
GO  
```  
  
### <a name="c-changing-the-order-of-parameters"></a>C. Alterando a ordem dos parâmetros  
 O exemplo seguinte adiciona primeiro uma mensagem em inglês ds EUA e, em seguida, adiciona a mensagem localizada na qual a ordem de parâmetros é alterada.  
  
```  
USE master;  
GO  
  
EXEC sp_addmessage   
    @msgnum = 60000,   
    @severity = 16,  
    @msgtext =   
        N'This is a test message with one numeric  
        parameter (%d), one string parameter (%s),   
        and another string parameter (%s).',  
    @lang = 'us_english';  
  
EXEC sp_addmessage   
    @msgnum = 60000,   
    @severity = 16,  
    @msgtext =   
        -- In the localized version of the message,  
        -- the parameter order has changed. The   
        -- string parameters are first and second  
        -- place in the message, and the numeric   
        -- parameter is third place.  
        N'Dies ist eine Testmeldung mit einem   
        Zeichenfolgenparameter (%3!),  
        einem weiteren Zeichenfolgenparameter (%2!),   
        und einem numerischen Parameter (%1!).',  
    @lang = 'German';  
GO    
  
-- Changing the session language to use the U.S. English  
-- version of the error message.  
SET LANGUAGE us_english;  
GO  
  
RAISERROR(60000,1,1,15,'param1','param2') -- error, severity, state,  
GO                                       -- parameters.  
  
-- Changing the session language to use the German  
-- version of the error message.  
SET LANGUAGE German;  
GO  
  
RAISERROR(60000,1,1,15,'param1','param2'); -- error, severity, state,   
GO                                       -- parameters.  
```  
  
## <a name="see-also"></a>Consulte também  
 [RAISERROR &#40;Transact-SQL&#41;](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [sp_altermessage &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-altermessage-transact-sql.md)   
 [sp_dropmessage &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmessage-transact-sql.md)   
 [Procedimentos armazenados do sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
