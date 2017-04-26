---
title: "Aplicativo sqlagent90 | Microsoft Docs"
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
  - "iniciando o SQL Server Agent"
  - "aplicativo sqlagent90"
  - "SQL Server Agent, iniciando"
  - "utilitários de prompt de comando [SQL Server], sqlagent90"
ms.assetid: e8b80e8d-d0c9-4500-a868-0ce08233da08
caps.latest.revision: 34
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 34
---
# Aplicativo sqlagent90
  O aplicativo **sqlagent90** inicia o [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent no prompt de comando. Normalmente, o [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent deve ser executado no [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ou usando métodos SQL-SMO em um aplicativo. Execute o **sqlagent90** no prompt de comando apenas quando estiver diagnosticando o [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent ou quando for direcionado a ele por seu provedor de suporte.  
  
## Sintaxe  
  
```  
  
sqlagent90  
-c [-v] [-i instance_name]  
```  
  
## Argumentos  
 **-c**  
 Indica que o [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent está sendo executado pelo prompt de comando e é independente do Gerenciador de Controle de Serviços do Microsoft Windows. Quando **-c** é usado, o [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent não pode ser controlado no aplicativo de Serviços nas Ferramentas Administrativas nem no [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Configuration Manager. Esse argumento é obrigatório.  
  
 **-v**  
 Indica que o [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent é executado em modo detalhado e grava informações de diagnóstico na janela do prompt de comando. As informações de diagnóstico são iguais às informações gravadas no log de erros do [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent.  
  
 **-i** *instance_name*  
 Indica que o [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent se conecta com a instância do [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] nomeada especificada por *instance_name*.  
  
## Comentários  
 Depois de exibir uma mensagem de direitos autorais, o **sqlagent90** exibe a saída na janela de prompt de comando somente quando a opção **-v** é especificada. Para interromper o **sqlagent90**, pressione CTRL+C no prompt de comando. Não feche a janela do prompt de comando antes de interromper o **sqlagent90**.  
  
## Consulte também  
 [Tarefas de administração automatizadas &#40;SQL Server Agent&#41;](../ssms/agent/automated-administration-tasks-sql-server-agent.md)  
  
  