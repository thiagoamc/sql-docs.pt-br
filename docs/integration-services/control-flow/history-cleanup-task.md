---
title: "Tarefa Limpeza do Hist&#243;rico | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.historycleanuptask.f1"
helpviewer_keywords: 
  - "tabelas de histórico [SQL Server]"
  - "Tarefa Limpeza do Histórico [Integration Services]"
ms.assetid: 5defc5b9-dfd3-4859-a7fe-ac8c2b5480f8
caps.latest.revision: 43
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 43
---
# Tarefa Limpeza do Hist&#243;rico
  A tarefa Limpeza do Histórico exclui entradas das seguintes tabelas de histórico do banco de dados msdb [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   backupfile  
  
-   backupfilegroup  
  
-   backupmediafamily  
  
-   backupmediaset  
  
-   backupset  
  
-   restorefile  
  
-   restorefilegroup  
  
-   restorehistory  
  
 Por meio da tarefa Limpeza do Histórico, um pacote pode excluir dados históricos relacionados a atividades de backup e restauração, a trabalhos do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent e a planos de manutenção do banco de dados.  
  
 Essa tarefa encapsula o procedimento armazenado do sistema sp_delete_backuphistory e transfere a data especificada ao procedimento como um argumento. Para obter mais informações, consulte [sp_delete_backuphistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md).  
  
## Configuração da tarefa Limpeza do Histórico  
 A tarefa inclui uma propriedade para especificação da data mais antiga dos dados retidos nas tabelas de histórico. Você pode indicar a data por número de dias, semanas, meses ou anos do dia atual, e a tarefa automaticamente converte o intervalo para uma data.  
  
 Você pode definir propriedades por meio do [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer. Esta tarefa está na seção **Tarefas do Plano de Manutenção** da **Caixa de Ferramentas** , no Designer [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Para obter mais informações sobre as propriedades que podem ser definidas no [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, clique no tópico a seguir:  
  
-   [Tarefa limpeza de histórico &#40;Plano de manutenção&#41;](../../relational-databases/maintenance-plans/history-cleanup-task-maintenance-plan.md)  
  
 Para obter mais informações sobre como definir essas propriedades no [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, clique no tópico a seguir:  
  
-   [Definir as propriedades de uma tarefa ou contêiner](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)  
  
## Consulte também  
 [Tarefas do Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Fluxo de Controle](../../integration-services/control-flow/control-flow.md)  
  
  