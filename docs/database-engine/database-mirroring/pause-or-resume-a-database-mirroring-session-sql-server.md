---
title: "Pausar ou retomar uma sess&#227;o de espelhamento de banco de dados (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "continuando o espelhamento de banco de dados"
  - "espelhamento de banco de dados [SQL Server], sessões"
  - "espelhamento de banco de dados [SQL Server], pausando"
  - "espelhamento de banco de dados [SQL Server], retomando"
  - "pausando o espelhamento de banco de dados"
ms.assetid: 05ede3b4-6abe-4442-abb7-9f5aee1d6bc0
caps.latest.revision: 34
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 34
---
# Pausar ou retomar uma sess&#227;o de espelhamento de banco de dados (SQL Server)
  Este tópico descreve como pausar ou retomar o espelhamento de banco de dados no [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] usando o [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Neste tópico**  
  
-   **Antes de começar:**  
  
     [Segurança](#Security)  
  
-   **Para ReplaceThisText usando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Acompanhamento:**  [depois de pausar ou retomar o espelhamento do banco de dados](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Antes de começar  
 A qualquer momento, você pode suspender uma sessão de espelhamento de banco de dados, o que pode melhorar o desempenho durante afunilamentos, e pode retomar uma sessão suspensa.  
  
> [!CAUTION]  
>  Depois um serviço forçado, quando o servidor principal original é reconectado, o espelhamento é suspenso. A retomada do espelhamento nessa situação pode causar perda de dados no servidor principal original. Para obter informações sobre o gerenciamento de perda de dados em potencial, veja [Troca de função durante uma Sessão de Espelhamento de Banco de Dados &#40;SQL Server&#41;](../../database-engine/database-mirroring/role-switching-during-a-database-mirroring-session-sql-server.md).  
  
###  <a name="Security"></a> Segurança  
  
####  <a name="Permissions"></a> Permissões  
 Requer a permissão ALTER no banco de dados.  
  
##  <a name="SSMSProcedure"></a> Usando o SQL Server Management Studio  
 Para pausar ou retomar uma sessão de espelhamento de banco de dados, use a página **Espelhamento de Propriedades do Banco de Dados** .  
  
#### Para pausar ou retomar o espelhamento de banco de dados  
  
1.  Durante uma sessão de espelhamento de banco de dados, faça a conexão com a instância do servidor principal e, no Pesquisador de Objetos, clique no nome do servidor para expandir a árvore do servidor.  
  
2.  Expanda **Bancos de Dados**e selecione o banco de dados.  
  
3.  Clique com o botão direito do mouse no banco de dados, selecione **Tarefas** e clique em **Espelhar**. Isso abre a página **Espelhamento** da caixa de diálogo **Propriedades do Banco de Dados** .  
  
4.  Para pausar a sessão, clique em **Pausar**.  
  
     Um prompt pedirá confirmação; se você clicar em **Sim**, a sessão será pausada e o botão será alterado para **Retomar**.  
  
     Para obter mais informações sobre o impacto de pausar uma sessão, veja [Pausar e retomar o Espelhamento de Banco de Dados &#40;SQL Server&#41;](../../database-engine/database-mirroring/pausing-and-resuming-database-mirroring-sql-server.md).  
  
5.  Para retomar a sessão, clique em **Retomar**.  
  
##  <a name="TsqlProcedure"></a> Usando Transact-SQL  
  
#### Para pausar o espelhamento de banco de dados  
  
1.  Conecte-se ao [!INCLUDE[ssDE](../../includes/ssde-md.md)] para qualquer um dos parceiros.  
  
2.  Na barra Padrão, clique em **Nova Consulta**.  
  
3.  Emita a seguinte instrução [!INCLUDE[tsql](../../includes/tsql-md.md)]:  
  
     ALTER DATABASE *database_name* SET PARTNER SUSPEND  
  
     em que *database_name* é o banco de dados espelhado cuja sessão você deseja suspender.  
  
     O exemplo a seguir pausa o banco de dados de exemplo [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET PARTNER SUSPEND;  
    ```  
  
##### Para retomar o espelhamento de banco de dados.  
  
1.  Conecte-se ao [!INCLUDE[ssDE](../../includes/ssde-md.md)] para qualquer um dos parceiros.  
  
2.  Na barra Padrão, clique em **Nova Consulta**.  
  
3.  Emita a seguinte instrução Transact-SQL:  
  
     ALTER DATABASE *database_name* SET PARTNER RESUME  
  
     em que *database_name* é o banco de dados espelhado cuja sessão você deseja retomar.  
  
     O exemplo a seguir pausa o banco de dados de exemplo [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET PARTNER RESUME;  
    ```  
  
##  <a name="FollowUp"></a> Acompanhamento: depois de pausar ou retomar o espelhamento do banco de dados  
  
-   **Depois de pausar o espelhamento de banco de dados**  
  
     No banco de dados primário, tome precauções para evitar um log de transações cheio. Para obter mais informações, veja [O log de transações &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md).  
  
-   **Depois de retomar o espelhamento de banco de dados**  
  
     A retomada do espelhamento de banco de dados coloca o banco de dados espelho no estado SYNCHRONIZING. Se o nível de segurança for FULL, o espelho alcançará o banco de dados principal e o banco de dados espelho entrará no estado SYNCHRONIZED. Neste momento, o failover torna-se possível. Se a testemunha estiver presente e ON, o failover automático será possível. Na ausência de uma testemunha, o failover manual será possível.  
  
##  <a name="RelatedTasks"></a> Tarefas relacionadas  
  
-   [Remover o espelhamento de banco de dados &#40;SQL Server&#41;](../../database-engine/database-mirroring/remove-database-mirroring-sql-server.md)  
  
## Consulte também  
 [Espelhamento de banco de dados &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)  
  
  