---
title: "Solucionar problemas de integridade de recursos do SQL Server (Utilitário do SQL Server) | Microsoft Docs"
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
ms.assetid: 614f07b5-f221-4013-9f8d-22964cf42270
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4b8b2c608c77443858f915cb9e7b3a84c96d2e86
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/18/2018
---
# <a name="troubleshoot-sql-server-resource-health-sql-server-utility"></a>Solucionar problemas de integridade de recursos do SQL Server (Utilitário do SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Solucionar problemas de integridade de recursos identificados por uma [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] UCP pode incluir a eliminação de uma CPU sobrecarregada em um computador ou em uma instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou a mitigação uma CPU sobrecarregada para um aplicativo da camada de dados. Outros problemas incluem a resolução de espaço de arquivo superutilizado para arquivos de banco de dados ou a resolução de superutilização de espaço em disco alocado em um volume de armazenamento.  
  
 Note que, se um banco de dados estiver no estado de "emergência", o estado de integridade exibirá o espaço de arquivo de log superutilizado.  
  
 Para obter mais informações sobre a coleta de dados com falha que resulta em ícones de status cinza na exibição de lista da instância gerenciada em um UCP, veja [Recursos e tarefas do Utilitário do SQL Server](http://msdn.microsoft.com/library/f5f47c2a-38ea-40f8-9767-9bc138d14453). Para obter mais informações sobre como começar a usar o Utilitário do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , veja [Recursos e tarefas do Utilitário do SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md).  
  
 Para obter mais informações sobre como eliminar problemas de integridade de recursos específicos identificados por um UCP do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , consulte os seguintes tópicos:  
  
-   [Como identificar sua versão de SQL Server e edição](http://go.microsoft.com/fwlink/?LinkID=178504)  
  
-   [Solucionando problemas de desempenho no SQL Server 2008](http://go.microsoft.com/fwlink/?LinkId=151354)  
  
  
