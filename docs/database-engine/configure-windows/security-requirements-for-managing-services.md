---
title: "Requisitos de seguran&#231;a para gerenciar servi&#231;os | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Serviço do SQL Server Agent, segurança"
  - "serviços [SQL Server], segurança"
  - "Serviços do SQL Server, segurança"
  - "Provedores WMI [SQL Server]"
  - "configuração do servidor [SQL Server]"
  - "segurança [SQL Server], serviços"
  - "serviços [SQL Server], WMI"
ms.assetid: 1874a317-ddb2-425d-98d9-b53e1be6fc6a
caps.latest.revision: 28
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 28
---
# Requisitos de seguran&#231;a para gerenciar servi&#231;os
  Para gerenciar [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Services, use SQL Server Configuration Manager ou [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Gerencie os serviços em servidores agrupados com o Administrador Clusterizado.  
  
 Para gerenciar o serviço [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e definir as opções de configuração de servidor, você deve ser um membro da função de servidor fixa **serveradmin** ou **sysadmin** . Membros do grupo **Administradores** do Windows podem iniciar e interromper serviços e configurar as opções de servidor que o Windows fornece.  
  
> [!NOTE]  
>  Para operar corretamente, as contas usadas para os serviços devem ser configuradas com o domínio, sistema de arquivo e permissões de registro corretos. Para obter informações sobre as permissões necessárias, consulte [Configurar contas de serviço e permissões do Windows](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
## Instrumentação de Gerenciamento do Windows  
 O SQL Server Configuration Manager e [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] usam Instrumentação de Gerenciamento do Windows (WMI) para exibir e modificar algumas das propriedades de servidor. Para administrar serviços e obter o status dos serviços, o usuário deve ter direitos para acessar o objeto WMI. Em [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], as seguintes páginas de propriedades de servidor usam o WMI:  
  
-   Iniciar serviços automaticamente  
  
-   Parâmetros de inicialização  
  
-   Segurança  
  
-   Diversas configurações de servidor  
  
## Tarefas relacionadas  
 [Configurar o WMI para mostrar o status do servidor nas ferramentas do SQL Server](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md)  
  
## Conteúdo relacionado  
 [Provedor WMI para conceitos de gerenciamento de configuração](../Topic/WMI%20Provider%20for%20Configuration%20Management%20Concepts.md)  
  
  