---
title: sp_change_log_shipping_secondary_primary (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
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
- sp_change_log_shipping_secondary_primary
- sp_change_log_shipping_secondary_primary_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_change_log_shipping_secondary_primary
ms.assetid: 5bcb4df7-6df3-4f2b-9207-b97b5addf2a6
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 26e82dc23da2641019fc0b6215dd633479ae0272
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2018
---
# <a name="spchangelogshippingsecondaryprimary-transact-sql"></a>sp_change_log_shipping_secondary_primary (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Altera as configurações do banco de dados secundário.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Convenções da sintaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
sp_change_log_shipping_secondary_primary  
[ @primary_server = ] 'primary_server',  
[ @primary_database = ] 'primary_database',  
[, [ @backup_source_directory = ] 'backup_source_directory']  
[, [ @backup_destination_directory = ] 'backup_destination_directory']  
[, [ @file_retention_period = ] file_retention_period]  
[, [ @monitor_server_security_mode = ] monitor_server_security_mode]  
[, [ @monitor_server_login = ] 'monitor_server_login']  
[, [ @monitor_server_password = ] 'monitor_server_password']  
```  
  
## <a name="arguments"></a>Argumentos  
 [ **@primary_server** = ] '*primary_server*'  
 O nome da instância primária do [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] na configuração de envio de logs. *primary_server* é **sysname** e não pode ser NULL.  
  
 [  **@primary_database**  =] '*primary_database*'  
 É o nome do banco de dados do servidor primário. *primary_database* é **sysname**, sem padrão.  
  
 [ **@backup_source_directory** = ] '*backup_source_directory*'  
 O diretório onde os arquivos de backup de log de transações do servidor primário são armazenados. *backup_source_directory* é **nvarchar (500)** e não pode ser NULL.  
  
 [ **@backup_destination_directory** = ] '*backup_destination_directory*'  
 O diretório no servidor secundário onde arquivos de backup são copiados. *backup_destination_directory* é **nvarchar (500)** e não pode ser NULL.  
  
 [  **@file_retention_period**  =] '*file_retention_period*'  
 É a duração de tempo em minutos na qual o histórico será retido. *history_retention_period* é **int**, com um padrão NULL. Se nenhum valor for especificado, será usado o valor 14.420.  
  
 [ **@monitor_server_security_mode** = ] '*monitor_server_security_mode*'  
 O modo de segurança usado para conexão ao servidor monitor.  
  
 1 = Autenticação do Windows;  
  
 0 = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] autenticação. *monitor_server_security_mode* é **bit** e não pode ser NULL.  
  
 [ **@monitor_server_login** = ] '*monitor_server_login*'  
 É o nome de usuário da conta usada para acessar o servidor monitor.  
  
 [ **@monitor_server_password** = ] '*monitor_server_password*'  
 Senha da conta usada para acessar o servidor monitor.  
  
## <a name="return-code-values"></a>Valores do código de retorno  
 0 (êxito) ou 1 (falha)  
  
## <a name="result-sets"></a>Conjuntos de resultados  
 Nenhuma  
  
## <a name="remarks"></a>Remarks  
 **sp_change_log_shipping_secondary_primary** deve ser executado a partir de **mestre** banco de dados no servidor secundário. Esse procedimento armazenado faz o seguinte:  
  
1.  Altera configurações de **log_shipping_secondary** registra conforme necessário.  
  
2.  Se o servidor monitor for diferente do servidor secundário, alterações de registro do monitor em **log_shipping_monitor_secondary** no monitor de servidor usando os argumentos fornecidos, se necessário.  
  
## <a name="permissions"></a>Permissões  
 Somente membros do **sysadmin** função fixa de servidor pode executar esse procedimento.  
  
## <a name="see-also"></a>Consulte também  
 [Sobre o envio de logs &#40; SQL Server &#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Procedimentos armazenados do sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
