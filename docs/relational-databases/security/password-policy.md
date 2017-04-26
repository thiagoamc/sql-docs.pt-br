---
title: "Pol&#237;tica de senha | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "09/25/2015"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "instrução ALTER LOGON"
  - "senhas [SQL Server], imposição de política"
  - "logons [SQL Server], senhas"
  - "Opção CHECK_EXPIRATION"
  - "senhas complexas [SQL Server]"
  - "senhas [SQL Server], expiração"
  - "redefinições manuais de contagem de senha inválida"
  - "opção MUST_CHANGE"
  - "validade [SQL Server]"
  - "senha expirada [SQL Server]"
  - "símbolos [SQL Server]"
  - "NetValidatePasswordPolicy() API"
  - "senhas [SQL Server]"
  - "política de senha [SQL Server]"
  - "redefinindo contagens de senha incorreta"
  - "segurança [SQL Server], senhas"
  - "Opção CHECK_POLICY"
  - "senhas [SQL Server], símbolos"
  - "contagens de senha incorreta"
  - "senhas [SQL Server], complexidade"
  - "caracteres [SQL Server], políticas de senha"
ms.assetid: c0040c0a-a18f-45b9-9c40-0625685649b1
caps.latest.revision: 41
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 41
---
# Pol&#237;tica de senha
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pode usar os mecanismos de política de senha do Windows. A política de senha se aplica a um logon que usa a autenticação do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e a um usuário de banco de dados independente com senha.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pode aplicar as mesmas políticas de complexidade e expiração usadas no Windows para senhas usadas no [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Esta funcionalidade depende da `NetValidatePasswordPolicy` API.  
  
 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] impõe a complexidade da senha. As seções de imposição de política e expiração de senha não se aplicam ao [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
## Complexidade de senha  
 As políticas de complexidade de senha são projetadas para deter ataques de força bruta aumentando o número de possíveis senhas. Quando a política de complexidade de senha é imposta, as novas senhas devem atender às seguintes diretrizes:  
  
-   A senha não contém o nome de conta do usuário.  
  
-   A senha tem um comprimento de pelo menos oito caracteres.  
  
-   A senha contém caracteres de três das quatro categorias seguintes:  
  
    -   Letras maiúsculas latinas (A a Z)  
  
    -   Letras minúsculas latinas (a a z)  
  
    -   10 dígitos base (0 a 9)  
  
    -   Caracteres não alfanuméricos como: ponto de exclamação (!), cifrão ($), sinal numérico (#) ou porcentagem (%).  
  
 As senhas podem ter até 128 caracteres. Você deve usar senhas que sejam longas e complexas.  
  
## Vencimento da senha  
 As políticas de vencimento da senha são usadas para gerenciar o tempo de vida de uma senha. Quando o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] impõe a política de expiração de senha, os usuários são lembrados a alterar as senhas antigas e as contas com senhas expiradas são desabilitadas.  
  
## Imposição de política  
 A imposição da política de senha pode ser configurada separadamente para cada logon do SQL Server. Use [ALTER LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/alter-login-transact-sql.md) Para configurar as opções da política de senha de um logon do SQL Server. As regras seguintes se aplicam à configuração da imposição de política de senha:  
  
-   Quando CHECK_POLICY é alterado para ON, o seguinte comportamento ocorre:  
  
    -   CHECK_EXPIRATION também é definido como ON, a menos que seja definido explicitamente como OFF.  
  
    -   O histórico de senhas é inicializado com o valor do hash da senha atual.  
  
    -   As opções **duração do bloqueio de conta**, **limite de bloqueio de conta** e **zerar contador de bloqueios de conta após** também estão habilitadas.  
  
-   Quando CHECK_POLICY é alterado para OFF, o seguinte comportamento ocorre:  
  
    -   CHECK_EXPIRATION também será definido como OFF.  
  
    -   O histórico de senhas será apagado.  
  
    -   O valor de `lockout_time` é redefinido.  
  
 Algumas combinações de opções de política não têm suporte.  
  
-   Se MUST_CHANGE for especificado, CHECK_EXPIRATION e CHECK_POLICY deverão ser definidos como ON. Caso contrário, a instrução falhará.  
  
-   Se CHECK_POLICY for definido como OFF, CHECK_EXPIRATION não poderá ser definido como ON. Uma instrução ALTER LOGON com essa combinação de opções falhará.  
  
 A definição de CHECK_POLICY = ON impedirá a criação de senhas que são:  
  
-   Nulas ou em branco  
  
-   A mesma do computador ou logon  
  
-   Qualquer dos seguintes: "password", "admin", "administrator", "sa", "sysadmin"  
  
 A política de senha pode ser configurada no Windows ou transmitida por um domínio. Para exibir a política de senha do computador, use o snap-in do MMC da Política de Segurança Local (**secpol.msc**).  
  
## Tarefas relacionadas  
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)  
  
 [ALTER LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/alter-login-transact-sql.md)  
  
 [CREATE USER &#40;Transact-SQL&#41;](../../t-sql/statements/create-user-transact-sql.md)  
  
 [ALTER USER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-user-transact-sql.md)  
  
 [Crie um logon](../../relational-databases/security/authentication-access/create-a-login.md)  
  
 [Criar um usuário de banco de dados](../../relational-databases/security/authentication-access/create-a-database-user.md)  
  
## Conteúdo relacionado  
 [Senhas fortes](../../relational-databases/security/strong-passwords.md)  
  
  