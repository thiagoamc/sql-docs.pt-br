---
title: "Concedendo permiss&#245;es em um servidor de relat&#243;rio no modo nativo | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "funções [Reporting Services], criando"
  - "autorização [Reporting Services]"
  - "segurança do servidor [Reporting Services]"
  - "segurança com base em função [Reporting Services]"
  - "itens [Reporting Services], segurança"
  - "permissões [Reporting Services], modo nativo"
  - "relatórios publicados [Reporting Services], segurança"
  - "relatórios [Reporting Services], segurança"
  - "itens de relatório [Reporting Services], segurança"
  - "segurança baseada em função [Reporting Services], sobre a segurança baseada em função"
  - "segurança [Reporting Services], baseada em função"
ms.assetid: 260dc2e9-546c-4f04-9fa1-977e23c9d68c
caps.latest.revision: 60
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 60
---
# Concedendo permiss&#245;es em um servidor de relat&#243;rio no modo nativo
  O SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] usa autorização com base em funções e um subsistema de autenticação para determinar quem pode executar operações e acessar itens em um servidor de relatório. A autorização com base em funções é categorizada nas funções do conjunto de ações que um usuário ou grupo pode executar. A autenticação se baseia na Autenticação interna do Windows ou em um módulo de autenticação personalizado fornecido por você. É possível utilizar funções predefinidas ou personalizadas com qualquer tipo de autenticação.  
  
## Usando funções para conceder acesso ao servidor de relatório  
 Todos os usuários interagem com um servidor de relatório dentro do contexto de uma função que define um nível específico de acesso. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] inclui funções predefinidas que podem ser atribuídas a usuários e grupos para fornecer acesso imediato a um servidor de relatório. **ContentManager**, **Publisher** e **Browser** são exemplos de funções predefinidas. Cada função define uma coleção de tarefas relacionadas. Por exemplo, um **Publicador** tem permissão para adicionar relatórios e criar pastas para armazenar esses relatórios.  
  
 Em geral, as atribuições de funções são herdadas de um nó pai, mas você pode dividir a herança de permissões criando uma nova atribuição de função para um determinado item. Um usuário que seja membro da função **Gerenciador de Conteúdo** de um relatório pode ser membro da função **Navegador** de outro relatório.  
  
 Para conceder acesso a itens e operações de servidor de relatório, siga estas diretrizes:  
  
1.  Examine as funções predefinidas para determinar se você pode usá-las no estado em que se encontram. Se for necessário ajustar as tarefas ou definir funções adicionais, faça isso antes de começar a atribuir usuários a funções específicas. Para obter mais informações sobre cada função, consulte [funções predefinidas](../../reporting-services/security/predefined-roles.md).  
  
2.  Identifique quais usuários e grupos requerem acesso ao servidor de relatório, e em que nível. A maioria dos usuários deve ser atribuída à função **Navegador** ou à função **Construtor de Relatórios** . Um número menor de usuários deve ser atribuído à função **Publicador** . Pouquíssimos usuários devem receber a função **Gerenciador de Conteúdo**.  
  
3.  Use o Gerenciador de Relatórios para atribuir funções na pasta Base (essa é a pasta de nível superior da pasta de servidor de relatório hierarquicamente) para cada usuário ou grupo que requeira acesso.  
  
4.  No nível do site, na página Configurações de Site no Gerenciador de Relatórios, crie uma atribuição de função no nível do sistema para cada usuário e grupo usando as funções predefinidas **Usuário do Sistema** e **Administrador do Sistema**.  
  
5.  Crie atribuições de funções adicionais conforme o necessário para pastas, relatórios e outros itens específicos. Evite criar um número grande de atribuições de funções. Se você criar atribuições demais, será difícil controlar os diferentes níveis de permissão de cada usuário.  
  
> [!NOTE]  
>  Se você tiver configurado um servidor de relatório para ser executado no modo integrado do SharePoint, defina permissões no site do SharePoint para conceder acesso aos itens de servidor de relatório. Para obter mais informações, consulte [Concedendo permissões para itens do servidor de relatório em um site do SharePoint](../../reporting-services/security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md).  
  
## Quem define permissões  
 Inicialmente, apenas usuários que são os membros do grupo de administradores local podem acessar um servidor de relatório. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] é instalado com duas atribuições de função padrão que concedem acesso em nível de item e do sistema a membros do grupo de administradores local. Essas atribuições de funções internas permitem aos Administradores locais conceder acesso ao servidor de relatório para outros usuários e gerenciar itens do servidor de relatório. Não é possível excluir as atribuições de funções internas. Um administrador local sempre tem permissão para gerenciar totalmente uma instância do servidor de relatório.  
  
 Como as permissões totais em um servidor de relatório incluem permissões no nível de item e no nível de sistema, um administrador local recebe as seguintes funções:  
  
 A configuração adicional é necessária para que você possa administrar uma instância do servidor de relatório em um computador local com o Windows Vista ou o Windows Server 2008. Para obter mais informações, veja [Configurar um servidor de relatório no modo nativo para a Administração Local &#40;SSRS&#41;](../../reporting-services/report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).  
  
## Como as permissões são armazenadas  
 As atribuições de funções e definições são armazenadas no banco de dados do servidor de relatório. Se você estiver usando várias ferramentas de clientes ou interfaces programáticas, todo o acesso estará sujeito às permissões definidas para a instância do servidor de relatório como um todo. Se você estiver configurando vários servidores de relatório em uma implantação de expansão, as atribuições de função definidas em uma instância serão armazenadas em um banco de dados compartilhado e usadas por todas as outras instâncias na mesma implantação de expansão. Como as atribuições de funções são armazenadas com os itens que protegem, você pode mover o banco de dados para outra instância do servidor de relatório sem perder as permissões definidas.  
  
## Tarefas e ferramentas para o gerenciamento de permissões  
 Use as ferramentas a seguir para gerenciar definições e atribuições de funções.  
  
|Ferramenta|Tarefas|  
|----------|-----------|  
|Management Studio – Usado para exibir, modificar, criar e excluir definições de funções.|[Criar, excluir ou modificar uma função &#40;Management Studio&#41;](../../reporting-services/security/create-delete-or-modify-a-role-management-studio.md)|  
|Gerenciador de Relatórios - Usado para atribuir usuários e grupos a funções.|[Conceder acesso ao usuário a um servidor de relatório &#40;Gerenciador de Relatórios&#41;](../../reporting-services/security/grant-user-access-to-a-report-server-report-manager.md)<br /><br /> [Modificar ou excluir uma atribuição de função &#40;Gerenciador de Relatórios&#41;](../../reporting-services/security/modify-or-delete-a-role-assignment-report-manager.md)|  
  
## Consulte também  
 [Funções predefinidas](../../reporting-services/security/predefined-roles.md)   
 [Concedendo permissões para itens do servidor de relatório em um site do SharePoint](../../reporting-services/security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md)   
 [Autenticação com o servidor de relatório](../../reporting-services/security/authentication-with-the-report-server.md)   
 [Criar e gerenciar atribuições de função](../../reporting-services/security/create-and-manage-role-assignments.md)   
 [Segurança e proteção do Reporting Services](../../reporting-services/security/reporting-services-security-and-protection.md)   
 [Gerenciamento do conteúdo do Servidor de Relatório &#40;Modo Nativo do SSRS&#41;](../../reporting-services/report-server/report-server-content-management-ssrs-native-mode.md)  
  
  