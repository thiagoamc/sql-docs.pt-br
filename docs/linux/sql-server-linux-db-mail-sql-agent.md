---
title: Email de banco de dados e alertas de Email com o SQL Agent no Linux | Microsoft Docs
description: Este artigo descreve como usar o DB Mail e alertas de Email com o SQL Server no Linux
author: meet-bhagdev
ms.author: meetb
manager: craigg
ms.date: 02/20/2018
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: tbd
ms.workload: Inactive
ms.openlocfilehash: 69d1ff539d2e488030f32b9246f1ccf40d92bdd8
ms.sourcegitcommit: 57f45ee008141ddf009b1c1195442529e0ea1508
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2018
---
# <a name="db-mail-and-email-alerts-with-sql-agent-on-linux"></a>Email de banco de dados e alertas de Email com o SQL Agent no Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

As etapas a seguir mostram como configurar o email de banco de dados e usá-lo com o SQL Server Agent (**mssql-server-agente**) no Linux. 

## <a name="1-enable-db-mail"></a>1. Habilitar o DB Mail

```sql
USE master 
GO 
sp_configure 'show advanced options',1 
GO 
RECONFIGURE WITH OVERRIDE 
GO 
sp_configure 'Database Mail XPs', 1 
GO 
RECONFIGURE  
GO  
```

## <a name="2-create-a-new-account"></a>2. Criar uma conta nova
```sql
EXECUTE msdb.dbo.sysmail_add_account_sp 
@account_name = 'SQLAlerts', 
@description = 'Account for Automated DBA Notifications', 
@email_address = 'sqlagenttest@gmail.com', 
@replyto_address = 'sqlagenttest@gmail.com', 
@display_name = 'SQL Agent', 
@mailserver_name = 'smtp.gmail.com', 
@port = 587, 
@enable_ssl = 1, 
@username = 'sqlagenttest@gmail.com', 
@password = '<password>' 
GO
```

## <a name="3-create-a-default-profile"></a>3. Criar um perfil padrão

```sql
EXECUTE msdb.dbo.sysmail_add_profile_sp 
@profile_name = 'default', 
@description = 'Profile for sending Automated DBA Notifications' 
GO
```

## <a name="4-add-the-database-mail-account-to-a-database-mail-profile"></a>4. Adicionar a conta de email de banco de dados a um perfil do Database Mail
```sql
EXECUTE msdb.dbo.sysmail_add_principalprofile_sp 
@profile_name = 'default', 
@principal_name = 'public', 
@is_default = 1 ; 
 ```
 
## <a name="5-add-account-to-profile"></a>5. Adicionar conta ao perfil 
```sql
EXECUTE msdb.dbo.sysmail_add_profileaccount_sp   
@profile_name = 'default',   
@account_name = 'SQLAlerts',   
@sequence_number = 1;  
 ```
 
## <a name="6-send-test-email"></a>6. Enviar email de teste
> [!NOTE]
> Talvez você precise ir para o seu cliente de email e habilitar o "permitir que clientes menos seguros enviar email". Nem todos os clientes reconhecem o DB Mail como um daemon do email.

```
EXECUTE msdb.dbo.sp_send_dbmail 
@profile_name = 'default', 
@recipients = 'recipient-email@gmail.com', 
@Subject = 'Testing DBMail', 
@Body = 'This message is a test for DBMail' 
GO
```

## <a name="7-set-db-mail-profile-using-mssql-conf-or-environment-variable"></a>7. Definir o perfil de email do banco de dados usando a variável de ambiente ou mssql conf
Você pode usar o utilitário mssql conf ou variáveis de ambiente para registrar o seu perfil de email de banco de dados. Nesse caso, vamos chamar nosso padrão de perfil.

```bash
# via mssql-conf
sudo /opt/mssq/bin/mssql-conf set sqlagent.databasemailprofile default
# via environment variable
MSSQL_AGENT_EMAIL_PROFILE=default
```

## <a name="8-set-up-an-operator-for-sqlagent-job-notifications"></a>8. Configurar um operador para notificações de SQLAgent 

```sql
EXEC msdb.dbo.sp_add_operator 
@name=N'JobAdmins',  
@enabled=1, 
@email_address=N'recipient-email@gmail.com',  
@category_name=N'[Uncategorized]' 
GO 
```

## <a name="9-send-email-when-agent-test-job-succeeds"></a>9. Enviar email quando 'Trabalho de teste do agente' concluído com êxito 

```
EXEC msdb.dbo.sp_update_job 
@job_name='Agent Test Job', 
@notify_level_email=1, 
@notify_email_operator_name=N'JobAdmins' 
GO
```

## <a name="next-steps"></a>Próximas etapas
Para obter mais informações sobre como usar o SQL Server Agent para criar, agendar e executar trabalhos, consulte [executar um trabalho do SQL Server Agent no Linux](sql-server-linux-run-sql-server-agent-job.md).
