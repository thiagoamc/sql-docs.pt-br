---
title: "Exibindo o log do aplicativo do Windows | Microsoft Docs"
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
  - "logs do aplicativo [SQL Server]"
  - "Logs do aplicativo do Windows [SQL Server]"
  - "exibindo os logs do aplicativo do Windows"
  - "erros [SQL Server], logs"
  - "logs do sistema [SQL Server]"
  - "logs de segurança [SQL Server]"
  - "exibindo os logs do aplicativo do Windows"
  - "logs [SQL Server], logs dos aplicativos do Windows "
ms.assetid: f9853b74-7db7-47cc-b957-e49ed5bc0a1a
caps.latest.revision: 20
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 20
---
# Exibindo o log do aplicativo do Windows
  Quando o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] é configurado para usar o log do aplicativo do Microsoft Windows, cada sessão do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] grava novos eventos nesse log. Ao contrário do log de erros do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , não é criado um novo log de aplicativos cada vez que uma instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]é iniciada.  
  
 Exiba e gerencie o log do aplicativo do Windows usando Visualizador de Eventos do Windows ou o Visualizador de Log no [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 Há três logs que podem ser exibidos com Visualizador de Eventos.  
  
|Tipo de log do Windows|Description|  
|----------------------|-----------------|  
|Log do sistema|Registra eventos registrados pelos componentes do sistema operacional Windows. Por exemplo, a falha de um driver ou de outro componente do sistema carregados durante a inicialização é gravada no log do sistema.|  
|Log de segurança|Registra eventos de segurança, como tentativas de logon com falha. Também ajuda a localizar alterações no sistema de segurança e a identificar possíveis violações de segurança. Por exemplo, tentativas de logon no sistema podem ser gravadas no log de segurança, dependendo das definições de auditoria no Gerenciador de Usuários.<br /><br /> Somente os membros da função de servidor fixa **sysadmin** podem exibir os logs de segurança.|  
|Log do aplicativo|Registra eventos que são registrados através de aplicativos. Por exemplo, um aplicativo de banco de dados poderia registrar um erro de arquivo no log do aplicativo.|  
  
 Para obter mais informações sobre o recurso Visualizador de Eventos, como gerenciar o log do aplicativo e como compreender as informações apresentadas, consulte a documentação do Windows.  
  
 **Para exibir o log de aplicativos do Windows**  
  
 [Exibir o log de aplicativos do Windows &#40;Windows&#41;](../../relational-databases/performance/view-the-windows-application-log-windows.md)  
  
  