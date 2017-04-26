---
title: "Habilitar ou desabilitar as somas de verifica&#231;&#227;o de backup durante backup ou restaura&#231;&#227;o (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "somas de verificação de backup [SQL Server]"
  - "desabilitando somas de verificação"
  - "somas de verificação [SQL Server]"
ms.assetid: 6786bd1e-ad97-430a-8dfb-d4ba952d6c4d
caps.latest.revision: 31
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 31
---
# Habilitar ou desabilitar as somas de verifica&#231;&#227;o de backup durante backup ou restaura&#231;&#227;o (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Este tópico descreve como habilitar ou desabilitar somas de verificação de backup durante processos de backup ou restauração de bancos de dados no [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] usando o [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Neste tópico**  
  
-   **Antes de começar:**  
  
     [Segurança](#Security)  
  
-   **Para habilitar ou desabilitar as somas de verificação de backup usando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Antes de começar  
  
###  <a name="Security"></a> Segurança  
  
####  <a name="Permissions"></a> Permissões  
 BACKUP  
 As permissões BACKUP DATABASE e BACKUP LOG usam como padrão os membros da função de servidor fixa **sysadmin** e as funções de banco de dados fixas **db_owner** e **db_backupoperator**.  
  
 Os problemas de propriedade e permissão no arquivo físico do dispositivo de backup podem interferir em uma operação de backup. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deve ser capaz de ler e gravar no dispositivo; a conta sob a qual o serviço do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] executa deve ter permissões de gravação. No entanto, [sp_addumpdevice](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md), que adiciona uma entrada para um dispositivo de backup nas tabelas do sistema, não verifica permissões de acesso a arquivos. Esses problemas no arquivo físico do dispositivo de backup podem não aparecer até que o recurso físico seja acessado quando o backup ou restauração é tentado.  
  
 RESTORE  
 Se o banco de dados que está sendo restaurado não existir, o usuário deverá ter permissões CREATE DATABASE para poder executar o comando RESTORE. Se o banco de dados existir, as permissões RESTORE usarão como padrão os membros das funções de servidor fixas **sysadmin** e **dbcreator** e o proprietário (**dbo**) do banco de dados (para a opção FROM DATABASE_SNAPSHOT, o banco de dados sempre existe).  
  
 As permissões RESTORE são concedidas a funções nas quais as informações de associação estão sempre disponíveis para o servidor. Como a associação da função de banco de dados fixa pode ser verificada apenas quando o banco de dados está acessível e não danificado, o que nem sempre é o caso quando RESTORE é executado, os membros da função de banco de dados fixa **db_owner** não têm permissões RESTORE.  
  
##  <a name="SSMSProcedure"></a> Usando o SQL Server Management Studio  
  
#### Para habilitar ou desabilitar as somas de verificação durante operações de backup  
  
1.  Siga as etapas para [criar um backup de banco de dados](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md).  
  
2.  Na página **Opções** , na seção **Confiabilidade** , clique em **Executar soma de verificação antes de gravar na mídia**.  
  
##  <a name="TsqlProcedure"></a> Usando Transact-SQL  
  
#### Para habilitar ou desabilitar a soma de verificação de backup durante operações de backup  
  
1.  Conecte-se ao [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Na barra Padrão, clique em **Nova Consulta**.  
  
3.  Para habilitar somas de verificação de backup em uma instrução [BACKUP](../../t-sql/statements/backup-transact-sql.md) , especifique a opção WITH CHECKSUM. Para desabilitar somas de verificação de backup, especifique a opção WITH NO_CHECKSUM. Esse é o comportamento padrão, com exceção de um backup compactado. O exemplo a seguir especifica que somas de verificação serão executadas.  
  
```tsql  
BACKUP DATABASE AdventureWorks2012   
 TO DISK = 'Z:\SQLServerBackups\AdvWorksData.bak'  
   WITH CHECKSUM;  
GO  
```  
  
#### Para habilitar ou desabilitar a soma de verificação de backup durante operações de restauração  
  
1.  Conecte-se ao [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Na barra Padrão, clique em **Nova Consulta**.  
  
3.  Para habilitar somas de verificação de backup em uma instrução [RESTORE](../Topic/RESTORE%20\(Transact-SQL\).md) , especifique a opção WITH CHECKSUM. Esse é o comportamento padrão de um backup compactado. Para desabilitar somas de verificação de backup, especifique a opção WITH NO_CHECKSUM. Esse é o comportamento padrão, com exceção de um backup compactado. O exemplo a seguir especifica que somas de verificação de backup serão executadas.  
  
```tsql  
RESTORE DATABASE AdventureWorks2012   
 FROM DISK = 'Z:\SQLServerBackups\AdvWorksData.bak'  
   WITH CHECKSUM;  
GO  
```  
  
> [!WARNING]  
>  Se você solicitar CHECKSUM explicitamente para uma operação de restauração e se o backup contiver somas de verificação de backup, as somas de verificação de backup e as somas de verificação de página serão ambas verificadas, como no caso padrão. Porém, se o conjunto de backup não tiver as somas de verificação de backup, a operação de restauração falha com uma mensagem indicando que as somas de verificação não estão presentes.  
  
## Consulte também  
 [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](../Topic/RESTORE%20FILELISTONLY%20\(Transact-SQL\).md)   
 [RESTORE HEADERONLY &#40;Transact-SQL&#41;](../Topic/RESTORE%20HEADERONLY%20\(Transact-SQL\).md)   
 [RESTORE LABELONLY &#40;Transact-SQL&#41;](../Topic/RESTORE%20LABELONLY%20\(Transact-SQL\).md)   
 [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](../Topic/RESTORE%20VERIFYONLY%20\(Transact-SQL\).md)   
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [conjunto de backup &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupset-transact-sql.md)   
 [Argumentos de RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20Arguments%20\(Transact-SQL\).md)   
 [Erros de mídia possíveis durante backup e restauração &#40;SQL Server&#41;](../../relational-databases/backup-restore/possible-media-errors-during-backup-and-restore-sql-server.md)   
 [Especificar se uma operação de backup ou restauração continua ou é interrompida após um erro &#40;SQL Server&#41;](../../relational-databases/backup-restore/specify if backup or restore continues or stops after error.md)  
  
  