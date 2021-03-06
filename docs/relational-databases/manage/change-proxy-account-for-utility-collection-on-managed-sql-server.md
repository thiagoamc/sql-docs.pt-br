---
title: "Alterar a conta proxy da coleta do utilitário no SQL Server gerenciado| Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: maintenance-plans
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ff37ba8b-a08c-4109-b6e2-5748c995a52c
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a150b82f10849b0c24cf6b6821fdbc26be159ddc
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/18/2018
---
# <a name="change-proxy-account-for-utility-collection-on--managed-sql-server"></a>Alterar a conta proxy para coleta do utilitário no SQL Server gerenciado
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Este tópico descreve como alterar a conta proxy para o Conjunto de Coleta do Utilitário em uma instância gerenciada do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] usando o [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
##  <a name="SSMSProcedure"></a> Usando o SQL Server Management Studio  
  
#### <a name="to-change-the-proxy-account-for-the-utility-collection-set-on-a-managed-instance-of-sql-server"></a>Para alterar a conta proxy do conjunto de coleta do utilitário em uma instância gerenciada do SQL Server  
  
1.  Remova a instância gerenciada do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.  
  
    -   No **Gerenciador do Utilitário** no SSMS, clique no nó **Instâncias Gerenciadas** .  
  
    -   Na exibição de lista do **Gerenciador do Utilitário** , clique com o botão direito do mouse no nome da instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e selecione **Remover Instância Gerenciada...**. Para obter mais informações, veja [Remover uma instância do SQL Server do Utilitário do SQL Server](../../relational-databases/manage/remove-an-instance-of-sql-server-from-the-sql-server-utility.md).  
  
2.  Inscreva a instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no Utilitário do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] novamente.  
  
    -   No **Gerenciador do Utilitário** no SSMS, clique com o botão direito do mouse no nó **Instâncias Gerenciadas** e selecione **Adicionar Instância Gerenciada...**.  
  
    -   Siga os prompts para concluir o assistente, especificando a nova conta proxy.  
  
## <a name="see-also"></a>Consulte Também  
 [Recursos e tarefas do Utilitário do SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)   
 [Solucionar problemas do Utilitário do SQL Server](http://msdn.microsoft.com/library/f5f47c2a-38ea-40f8-9767-9bc138d14453)  
  
  
