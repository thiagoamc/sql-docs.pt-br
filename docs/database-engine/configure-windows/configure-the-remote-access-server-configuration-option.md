---
title: "Configurar a op&#231;&#227;o remote access de configura&#231;&#227;o de servidor | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "servidores remotos [SQL Server], execução de procedimento armazenado"
ms.assetid: f5de748d-1c55-4714-9661-38fe62e5095f
caps.latest.revision: 31
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 31
---
# Configurar a op&#231;&#227;o remote access de configura&#231;&#227;o de servidor
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Este tópico é sobre o recurso "Acesso Remoto". Esse é um recurso de comunicação obscura do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que foi substituído e provavelmente você não deveria usá-lo. Se você chegou a esta página porque está com problemas para se conectar ao [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consulte um dos tópicos a seguir:  
  
-   [Tutorial: introdução ao Mecanismo de Banco de Dados](../../relational-databases/tutorial-getting-started-with-the-database-engine.md)  
  
-   [Fazendo o logon no SQL Server](../../database-engine/configure-windows/logging-in-to-sql-server.md)  
  
-   [Conectar-se ao SQL Server quando os administradores do sistema estão bloqueados](../../database-engine/configure-windows/connect-to-sql-server-when-system-administrators-are-locked-out.md)  
  
-   [Conectar-se a um servidor registrado &#40;SQL Server Management Studio&#41;](../../tools/sql-server-management-studio/connect-to-a-registered-server-sql-server-management-studio.md)  
  
-   [Conectar a qualquer componente do SQL Server a partir do SQL Server Management Studio](../../ssms/f1-help/connect-to-any-sql-server-component-from-sql-server-management-studio.md)  
  
-   [Conectar-se ao Mecanismo de Banco de Dados com sqlcmd](../../relational-databases/scripting/connect-to-the-database-engine-with-sqlcmd.md)  
  
-   [Como solucionar problemas na conexão ao Mecanismo de Banco de Dados do SQL Server](http://social.technet.microsoft.com/wiki/contents/articles/2102.how-to-troubleshoot-connecting-to-the-sql-server-database-engine.aspx)  
  
 Os tópicos a seguir podem interessar programadores:  
  
-   [Como se conectar ao SQL Server usando a Autenticação do SQL no ASP.NET 2.0](https://msdn.microsoft.com/library/ff648340.aspx)  
  
-   [Conectando-se a uma instância do SQL Server](https://msdn.microsoft.com/library/ms162132.aspx)  
  
-   [Como Criar Conexões com Bancos de Dados do SQL Server](https://msdn.microsoft.com/library/s4yys16a.aspx)  
  
 **O corpo principal deste tópico começa aqui.**  
  
 Este tópico descreve como configurar a opção de configuração de servidor **remote access** no [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] usando o [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou o [!INCLUDE[tsql](../../includes/tsql-md.md)]. A opção **remote access** controla a execução de procedimentos armazenados de servidores locais ou remotos nos quais instâncias do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] estão sendo executadas. O valor padrão dessa opção é 1. Isso concede permissão para executar procedimentos armazenados locais de servidores remotos ou procedimentos armazenados remotos do servidor local. Para evitar que procedimentos armazenados locais sejam executados a partir de um servidor remoto ou que procedimentos armazenados remotos sejam executados no servidor local, defina a opção como 0.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] Em vez disso, use [sp_addlinkedserver](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md) .  
  
 **Neste tópico**  
  
-   **Antes de começar:**  
  
     [Limitações e restrições](#Restrictions)  
  
     [Segurança](#Security)  
  
-   **Para configurar a opção remote access, usando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Acompanhamento:**  [depois de configurar a opção remote access](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Antes de começar  
  
###  <a name="Restrictions"></a> Limitações e restrições  
  
-   A opção **remote access** se aplica apenas aos servidores que são adicionados usando [sp_addserver](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)e está incluída para ter compatibilidade com versões anteriores.  
  
###  <a name="Security"></a> Segurança  
  
####  <a name="Permissions"></a> Permissões  
 Permissões de execução sem parâmetros ou com apenas o primeiro parâmetro em **sp_configure** são concedidas a todos os usuários por padrão. Para executar **sp_configure** com ambos os parâmetros para alterar uma opção de configuração ou executar a instrução RECONFIGURE, o usuário deve ter a permissão ALTER SETTINGS no nível do servidor. A permissão ALTER SETTINGS é implicitamente mantida pelas funções de servidor fixas **sysadmin** e **serveradmin** .  
  
##  <a name="SSMSProcedure"></a> Usando o SQL Server Management Studio  
  
#### Para configurar a opção remote access  
  
1.  No Pesquisador de Objetos, clique com o botão direito do mouse em um servidor e selecione **Propriedades**.  
  
2.  Clique no nó **Conexões** .  
  
3.  Em **Conexões do servidor remoto**, marque ou desmarque a caixa de seleção **Permitir conexões remotas com este servidor** .  
  
##  <a name="TsqlProcedure"></a> Usando Transact-SQL  
  
#### Para configurar a opção remote access  
  
1.  Conecte-se ao [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Na barra Padrão, clique em **Nova Consulta**.  
  
3.  Copie e cole o exemplo a seguir na janela de consulta e clique em **Executar**. Este exemplo mostra como usar [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) para definir o valor da opção `remote access` como `0`.  
  
```tsql  
EXEC sp_configure 'remote access', 0 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
 Para obter mais informações, consulte [Server Configuration Options &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
##  <a name="FollowUp"></a> Acompanhamento: depois de configurar a opção remote access  
 Essa configuração não entrará em vigor até que você reinicie o SQL Server.  
  
## Consulte também  
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Opções de configuração do servidor &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  