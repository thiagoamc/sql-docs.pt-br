---
title: "Categoria de eventos Transactions | Microsoft Docs"
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
  - "classes de evento do SQL Server, categoria de evento de transações"
  - "classes de evento [SQL Server], categoria de evento de transações"
  - "categoria de eventos Transactions [SQL Server]"
ms.assetid: bfc75c5b-7115-49d8-9148-a0c84ee66a9a
caps.latest.revision: 28
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 28
---
# Categoria de eventos Transactions
  As classes de evento **Transactions** podem ser usadas para monitorar o status das transações. Os nomes da classe de evento que são predeterminados com **TM:** são usados para rastrear as operações relacionadas à transação que são enviadas pela interface de gerenciamento de transações.  
  
## Nesta seção  
  
|Tópico|Descrição|  
|-----------|-----------------|  
|[Classe de evento DTCTransaction](../../relational-databases/event-classes/dtctransaction-event-class.md)|Rastreia as transações coordenadas pelo MS DTC (Coordenador de Transações Distribuídas da [!INCLUDE[msCoName](../../includes/msconame-md.md)]). Essas são transações distribuídas entre dois ou mais bancos de dados ou instâncias do [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].|  
|[Classe de evento SQLTransaction](../../relational-databases/event-classes/sqltransaction-event-class.md)|Rastreia as instruções [!INCLUDE[tsql](../../includes/tsql-md.md)] BEGIN TRAN, COMMIT TRAN, SAVE TRAN e ROLLBACK TRAN.|  
|[Classe de evento TM: Begin Tran Completed](../../relational-databases/event-classes/tm-begin-tran-completed-event-class.md)|Indica que uma solicitação BEGIN TRANSACTION foi concluída.|  
|[Classe de evento TM: Begin Tran Starting](../../relational-databases/event-classes/tm-begin-tran-starting-event-class.md)|Indica que uma solicitação BEGIN TRANSACTION está iniciando.|  
|[Classe de evento TM: Commit Tran Completed](../../relational-databases/event-classes/tm-commit-tran-completed-event-class.md)|Indica que uma solicitação COMMIT TRANSACTION foi concluída.|  
|[Classe de evento TM: Commit Tran Starting](../../relational-databases/event-classes/tm-commit-tran-starting-event-class.md)|Indica que uma solicitação COMMIT TRANSACTION está iniciando.|  
|[Classe de evento TM: Promote Tran Completed](../../relational-databases/event-classes/tm-promote-tran-completed-event-class.md)|Indica que uma solicitação PROMOTE TRANSACTION foi concluída.|  
|[Classe de evento TM: Promote Tran Starting](../../relational-databases/event-classes/tm-promote-tran-starting-event-class.md)|Indica que uma solicitação PROMOTE TRANSACTION está iniciando.|  
|[Classe de evento TM: Rollback Tran Completed](../../relational-databases/event-classes/tm-rollback-tran-completed-event-class.md)|Indica que uma solicitação ROLLBACK TRANSACTION foi concluída.|  
|[Classe de evento TM: Rollback Tran Starting](../../relational-databases/event-classes/tm-rollback-tran-starting-event-class.md)|Indica que uma solicitação ROLLBACK TRANSACTION está iniciando.|  
|[Classe de evento TM: Save Tran Completed](../../relational-databases/event-classes/tm-save-tran-completed-event-class.md)|Indica que uma solicitação SAVE TRANSACTION foi concluída.|  
|[Classe de evento TM: Save Tran Starting](../../relational-databases/event-classes/tm-save-tran-starting-event-class.md)|Indica que uma solicitação SAVE TRANSACTION está iniciando.|  
|[Classe de evento TransactionLog](../../relational-databases/event-classes/transactionlog-event-class.md)|Rastreia quando as transações são gravadas em um log de transações do banco de dados.|  
  
  