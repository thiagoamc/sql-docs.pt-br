---
title: "Central de seguran&#231;a do Mecanismo de Banco de Dados do SQL Server e Banco de Dados SQL do Azure | Microsoft Docs"
ms.custom: 
  - "MSDN content"
  - "MSDN - SQL DB"
ms.date: "01/31/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.service: "sql-database"
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Security [SQL Server]"
helpviewer_keywords: 
  - "SQL Server, segurança"
  - "segurança [SQL Server]"
  - "segurança de banco de dados [SQL Server]"
  - "bancos de dados [SQL Server], segurança"
ms.assetid: dfb39d16-722a-4734-94bb-98e61e014ee7
caps.latest.revision: 55
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 54
---
# Central de seguran&#231;a do Mecanismo de Banco de Dados do SQL Server e Banco de Dados SQL do Azure
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Esta página fornece links para ajudá-lo a localizar as informações necessárias sobre Segurança e Proteção no [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] e [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)].  
  
 **Legenda**  
  
 ![security-center-legend](../../relational-databases/performance/media/security-center-legend.PNG "security-center-legend")  
  
##  <a name="Who"></a> Autenticação: quem é você?  
  
|||  
|-|-|  
|**Quem autentica?**<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") Autenticação do Windows<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Autenticação|Quem autentica? (Windows ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])<br /><br /> [Escolher um modo de autenticação](../../relational-databases/security/choose-an-authentication-mode.md)<br /><br /> [Conectar-se ao Banco de Dados SQL usando a autenticação do Azure Active Directory](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/)|  
|**Onde é autenticado?**<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") No Banco de Dados mestre: Logons e Usuários de Banco de Dados<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") No Banco de Dados mestre: Usuários de Banco de Dados independentes|Autenticação no banco de dados mestre (logons e usuários de banco de dados)<br /><br /> [Criar um logon do SQL Server](../../relational-databases/security/authentication-access/create-a-login.md)<br /><br /> [Gerenciando bancos de dados e logons no banco de dados do Azure SQL](http://msdn.microsoft.com/library/ee336235.aspx)<br /><br /> [Criar um usuário de banco de dados](../../relational-databases/security/authentication-access/create-a-database-user.md)<br /><br /> <br /><br /> Autenticar em um banco de dados do usuário<br /><br /> [Usuários de bancos de dados independentes - Tornando seu banco de dados portátil](../../relational-databases/security/contained-database-users-making-your-database-portable.md)|  
|**Usando outras identidades**<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") Credenciais<br /><br /> ![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") Executar como outro logon<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") Executar como outro usuário de banco de dados|[Credenciais &#40;Mecanismo de Banco de Dados&#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)<br /><br /> [Executar como outro logon](../../t-sql/statements/execute-as-transact-sql.md)<br /><br /> [Executar como outro usuário de banco de dados](../../t-sql/statements/execute-as-transact-sql.md)|  
  
##  <a name="What"></a> Autorização: o que você pode fazer?  
  
|||  
|-|-|  
|**Concedendo, revogando e negando permissões**<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") Classes Protegíveis<br /><br /> ![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") Permissões Granulares de Servidor<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") Permissões Granulares de Banco de Dados|[Hierarquia de permissões &#40;Mecanismo de Banco de Dados&#41;](../../relational-databases/security/permissions-hierarchy-database-engine.md)<br /><br /> [Permissões](../../relational-databases/security/permissions-database-engine.md)<br /><br /> [Protegíveis](../../relational-databases/security/securables.md)<br /><br /> [Guia de Introdução às permissões do mecanismo de banco de dados](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)|  
|**Segurança por funções**<br /><br /> ![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") Funções de nível de servidor<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") Funções de nível de banco de dados|[Funções de nível de servidor](../../relational-databases/security/authentication-access/server-level-roles.md)<br /><br /> [Funções de nível de banco de dados](../../relational-databases/security/authentication-access/database-level-roles.md)|  
|**Restringindo o acesso a dados aos elementos de dados selecionados**<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") Restringir acesso a dados com modos de exibição/procedimentos<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") Segurança em nível de linha<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") Mascaramento de dados dinâmicos<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") Objetos assinados|Restringir acesso a dados usando [Exibições](../../relational-databases/views/views.md) e [Procedimentos](../../relational-databases/stored-procedures/stored-procedures-database-engine.md)<br /><br /> [Segurança em nível de linha (SQL Server)](../../relational-databases/security/row-level-security.md)<br /><br /> [Segurança em nível de linha (banco de dados SQL do Azure)](http://msdn.microsoft.com/library/azure/dn765131.aspx)<br /><br /> [Mascaramento de dados dinâmicos (SQL Server)](../../relational-databases/security/dynamic-data-masking.md)<br /><br /> [Mascaramento de Dados Dinâmicos (Banco de Dados SQL do Azure)](http://azure.microsoft.com/documentation/articles/sql-database-dynamic-data-masking-get-started/)<br /><br /> [Objetos assinados](../../t-sql/statements/add-signature-transact-sql.md)|  
  
##  <a name="Encrypt"></a> Criptografia: armazenando dados secretos  
  
|||  
|-|-|  
|**Criptografando arquivos**<br /><br /> ![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") Criptografia BitLocker (Nível de Unidade)<br /><br /> ![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") Criptografia de NTFS (nível de pasta)<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") Criptografia transparente de dados (nível de arquivo)<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") Criptografia de backup (nível de arquivo)|[BitLocker (nível de unidade)](http://support.microsoft.com/kb/2855131)<br /><br /> [Criptografia de NTFS (nível de pasta)](http://msdn.microsoft.com/library/dd163562.aspx)<br /><br /> [Criptografia transparente de dados (nível de arquivo)](../../relational-databases/security/encryption/transparent-data-encryption-tde.md)<br /><br /> [Criptografia de backup (nível de arquivo)](../../relational-databases/backup-restore/backup-encryption.md)|  
|**Criptografando fontes**<br /><br /> ![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") Módulo de Gerenciamento Extensível de Chaves<br /><br /> ![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") Chaves armazenadas no cofre principal do Azure<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") Sempre Criptografado|[Módulo de Gerenciamento Extensível de Chaves](../../relational-databases/security/encryption/extensible-key-management-ekm.md)<br /><br /> [Chaves armazenadas no cofre principal do Azure](../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)<br /><br /> [Sempre Criptografado](../../relational-databases/security/encryption/always-encrypted-database-engine.md)|  
|**Coluna, dados e criptografia de chave**<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") Criptografar por certificado<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") Criptografar por chave simétrica<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") Criptografar por chave assimétrica<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") Criptografar por frase secreta|[Criptografar por certificado](../../t-sql/functions/encryptbycert-transact-sql.md)<br /><br /> [Criptografar por chave assimétrica](../../t-sql/functions/encryptbyasymkey-transact-sql.md)<br /><br /> [Criptografar por chave simétrica](../../t-sql/functions/encryptbykey-transact-sql.md)<br /><br /> [Criptografar por frase secreta](../../t-sql/functions/encryptbypassphrase-transact-sql.md)<br /><br /> [Criptografar uma coluna de dados](../../relational-databases/security/encryption/encrypt-a-column-of-data.md)|  
  
##  <a name="Connect"></a> Segurança de conexão: restringir e proteger  
  
|||  
|-|-|  
|**Proteção de firewall**<br /><br /> ![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") Configurações de Firewall do Windows<br /><br /> ![security-center-sqldb](../../relational-databases/security/media/security-center-sqldb.png "security-center-sqldb") Configurações de Firewall de serviço do Azure<br /><br /> ![security-center-sqldb](../../relational-databases/security/media/security-center-sqldb.png "security-center-sqldb") Configurações de Firewall do Banco de Dados|[Configurar um Firewall do Windows para acesso ao Mecanismo de Banco de Dados](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)<br /><br /> [Configurações de Firewall de banco de dados do SQL do Azure](../../relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database.md)<br /><br /> [Configurações de Firewall de serviço do Azure](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)|  
|**Criptografando dados em trânsito**<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") Conexões SSL Forçadas<br /><br /> ![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") Conexões SSL Opcionais|[Protocolo SSL para o mecanismo de banco de dados](../../database-engine/configure-windows/enable encrypted connections to the database engine.md)<br /><br /> [Protocolo SSL para o banco de dados SQL](https://msdn.microsoft.com/library/azure/ff394108.aspx)<br /><br /> [Suporte a TLS 1.2 para o Microsoft SQL Server](https://support.microsoft.com/kb/3135244)|  
  
##  <a name="Audit"></a> Auditoria: acesso à gravação  
  
|||  
|-|-|  
|**Auditoria automatizada**<br /><br /> ![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Auditoria (Nível de Banco de Dados e Servidor)<br /><br /> ![security-center-sqldb](../../relational-databases/security/media/security-center-sqldb.png "security-center-sqldb") [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Auditoria (Nível de Banco de Dados)<br /><br /> ![security-center-sqldb](../../relational-databases/security/media/security-center-sqldb.png "security-center-sqldb") Detecção de Ameaças|[Auditoria do SQL Server &#40;Mecanismo de Banco de Dados&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md)<br /><br /> [Auditoria do banco de dados SQL](http://azure.microsoft.com/documentation/articles/sql-database-auditing-get-started/)<br /><br /> [Introdução à Detecção de Ameaças do Banco de Dados SQL](https://azure.microsoft.com/documentation/articles/sql-database-threat-detection-get-started/)|  
|**Auditoria personalizada**<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") Gatilhos|Implementação de auditoria personalizada: criando [DDL Triggers](../../relational-databases/triggers/ddl-triggers.md) e [DML Triggers](../../relational-databases/triggers/dml-triggers.md)|  
|**Conformidade**<br /><br /> ![security-center-both](../../relational-databases/performance/media/security-center-both.png "security-center-both") Conformidade|SQL Server:<br />                        [critérios comuns](http://go.microsoft.com/fwlink/?LinkId=616319)<br /><br /> Banco de dados SQL:<br />                        [Central de Confiabilidade do Microsoft Azure: conformidade por recurso](http://azure.microsoft.com/support/trust-center/services/)|  
  
##  <a name="SQLInjection"></a> Injeção SQL  
 Injeção de SQL é um ataque no qual um código mal-intencionado é inserido em cadeias de caracteres que são passadas posteriormente para o [!INCLUDE[ssDE](../../includes/ssde-md.md)] para análise e execução. Qualquer procedimento que construa instruções SQL deve ser verificado quanto a vulnerabilidades de injeção porque o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] executará todas as consultas sintaticamente válidas que receber. Todos os sistemas de banco de dados têm algum risco de Injeção de SQL e muitas das vulnerabilidades são introduzidas no aplicativo que está consultando o [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Você pode impedir ataques de injeção de SQL usando procedimentos armazenados e comandos parametrizados, evitando o SQL dinâmico e restringindo as permissões de todos os usuários.  Para obter mais informações, consulte [SQL Injection](../../relational-databases/security/sql-injection.md).  
  
 Links adicionais para programadores de aplicativos:  
  
-   [Cenários de Segurança de Aplicativo no SQL Server](https://msdn.microsoft.com/library/bb669057.aspx)  
  
-   [Gravação de SQL Dinâmico Seguro no SQL Server](https://msdn.microsoft.com/library/bb669091.aspx)  
  
-   [Como proteger-se contra ataques de injeção no ASP.NET](https://msdn.microsoft.com/library/ff648339.aspx)  
  
## Consulte também  
 [Guia de Introdução às permissões do mecanismo de banco de dados](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)   
 [Protegendo o SQL Server](../../relational-databases/security/securing-sql-server.md)   
 [Entidades &#40;Mecanismo de Banco de Dados&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Certificados e chaves assimétricas do SQL Server](../../relational-databases/security/sql-server-certificates-and-asymmetric-keys.md)   
 [Criptografia do SQL Server](../../relational-databases/security/encryption/sql-server-encryption.md)   
 [Configuração da Área de Superfície](../../relational-databases/security/surface-area-configuration.md)   
 [Senhas fortes](../../relational-databases/security/strong-passwords.md)   
 [Propriedade de banco de dados TRUSTWORTHY](../../relational-databases/security/trustworthy-database-property.md)   
 [Recursos e tarefas do Mecanismo de Banco de Dados](../Topic/Database%20Engine%20Features%20and%20Tasks.md)  
  
  