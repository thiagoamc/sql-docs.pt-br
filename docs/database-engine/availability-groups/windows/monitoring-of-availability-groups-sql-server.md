---
title: "Monitoramento de grupos de disponibilidade (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Grupos de disponibilidade (SQL Server), monitorando"
  - "Grupos de disponibilidade [SQL Server], solução de problemas"
ms.assetid: 1d5e3291-0d0a-45a1-88e5-1fc242d17210
caps.latest.revision: 27
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 26
---
# Monitoramento de grupos de disponibilidade (SQL Server)
  Para monitorar as propriedades e o estado de um grupo de disponibilidade AlwaysOn, você pode usar as seguintes ferramentas.  
  
|Ferramenta|Descrição breve|Links|  
|----------|-----------------------|-----------|  
|Pacote de monitoramento do System Center para SQL Server|O pacote de Monitoramento para SQL Server (SQLMP) é a solução indicada para monitorar grupos de disponibilidade, réplica de disponibilidade e bancos de dados de disponibilidade para administradores de TI. Os recursos de monitoramento que são de particular relevância para o [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] incluem o seguinte:<br /><br /> Capacidade de descoberta automática de grupos de disponibilidade, réplicas de disponibilidade e banco de dados de disponibilidade dentre centenas de computadores. Isto permite que você mantenha o controle de seu inventário de [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].<br /><br /> Alertas e tickets totalmente capazes do System Center Operations Manager (SCOM). Estes recursos fornecem um conhecimento detalhado que permite uma resolução mais rápida para um problema.<br /><br /> Uma extensão personalizada para o monitoramento de integridade AlwaysOn usando um PBM (gerenciamento baseado em políticas).<br /><br /> Acúmulos de integridade de bancos de dados de disponibilidade para réplicas de disponibilidade.<br /><br /> Tarefas personalizadas que gerenciam o [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] do console do System Center Operations Manager.|Para baixar o pacote de monitoramento (SQLServerMP.msi) e o *Guia do Pacote de Gerenciamento do SQL Server para System Center Operations Manager* (SQLServerMPGuide.doc), consulte:<br /><br /> [Pacote de monitoramento do System Center para SQL Server](http://www.microsoft.com/download/details.aspx?displaylang=en&id=10631)|  
|[!INCLUDE[tsql](../../../includes/tsql-md.md)]|[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] e as exibições de gerenciamento dinâmico fornecem informações preciosas sobre seus grupos de disponibilidade e suas réplicas, bancos de dados, ouvintes e ambiente de cluster WSFC.|[Monitorar grupos de disponibilidade &#40;Transact-SQL&#41;](../../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)|  
|[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]|O painel **Detalhes do Pesquisador de Objetos** exibe informações básicas sobre os grupos de disponibilidade hospedados na instância do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à qual você está conectado.<br /><br /> **\*\* Dica \*\*** use esse painel para selecionar vários grupos de disponibilidade, réplicas ou bancos de dados e executar tarefas administrativas rotineiras nos objetos selecionados; por exemplo, remover várias réplicas ou bancos de dados de disponibilidade de um grupo de disponibilidade.|[Usar os detalhes do Pesquisador de Objetos para monitorar grupos de disponibilidade &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use object explorer details to monitor availability groups.md)|  
|[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]|As caixas de diálogo de**Propriedades** permitem que você exiba as propriedades dos grupos de disponibilidade, réplicas ou ouvintes e, em alguns casos, alterar os seus valores.|-   [Exibir as propriedades do grupo de disponibilidade &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/view-availability-group-properties-sql-server.md)<br />-   [Exibir as propriedades da réplica de disponibilidade &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/view-availability-replica-properties-sql-server.md)<br />-   [Exibir propriedades do ouvinte do grupo de disponibilidade &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/view-availability-group-listener-properties-sql-server.md)|  
|Monitor do Sistema|O objeto de desempenho **SQLServer:Availability Replica** contém contadores de desempenho que relatam informações sobre réplicas de disponibilidade.|[SQL Server, Réplica de Disponibilidade](../../../relational-databases/performance-monitor/sql-server-availability-replica.md)|  
|Monitor do Sistema|O objeto de desempenho **SQLServer:Database Replica** contém contadores de desempenho que relatam informações sobre os bancos de dados secundários em uma determinada réplica secundária.<br /><br /> O objeto **SQLServer:Databases** no SQL Server contém contadores de desempenho que monitoram atividades do log de transações, entre outras coisas. Os contadores a seguir são particularmente relevantes para o monitoramento de atividades do log de transações em bancos de dados de disponibilidade: **Tempo de Gravação de Liberação de Log (ms)**, **Liberações de log/s**, **Erros de Cache do Pool de Logs/s**, **Leituras de Disco do Pool de Logs/s** e **Solicitações do Pool de Logs/s**.|[SQL Server, Réplica de banco de dados](../../../relational-databases/performance-monitor/sql-server-database-replica.md) e [SQL Server, objeto Databases](../../../relational-databases/performance-monitor/sql-server-databases-object.md)|  
  
##  <a name="RelatedContent"></a> Conteúdo relacionado  
  
-   **Blogs:**  
  
     [The Always On Health Model Part 1 – Health Model Architecture (O modelo de integridade AlwaysOn Parte 1 – Arquitetura do modelo de integridade)](http://blogs.msdn.com/b/sqlAlways%20On/archive/2012/02/09/overview-of-the-Always%20On-manageability-health-model.aspx)  
  
     [The Always On Health Model Part 2 – Extending the Health Model (O modelo de integridade AlwaysOn Parte 2 – Estendendo o modelo de integridade)](http://blogs.msdn.com/b/sqlAlways%20On/archive/2012/02/13/extending-the-Always%20On-health-model.aspx)  
  
     [Monitoring Always On Health with PowerShell – Part 1: Basic Cmdlet Overview (Monitorando a integridade do AlwaysOn com o PowerShell – Parte 1: Visão geral básica do cmdlet)](http://blogs.msdn.com/b/sqlAlways%20On/archive/2012/02/13/monitoring-Always%20On-health-with-powershell-part-1.aspx)  
  
     [Monitoring Always On Health with PowerShell – Part 2: Advanced Cmdlet Usage (Monitorando a integridade do AlwaysOn com o PowerShell – Parte 2: Uso avançado do cmdlet)](http://blogs.msdn.com/b/sqlAlways%20On/archive/2012/02/13/monitoring-Always%20On-health-with-powershell-part-2.aspx)  
  
     [Monitoring Always On Health with PowerShell – Part 3: A Simple Monitoring Application (Monitorando a integridade do AlwaysOn com o PowerShell – Parte 3: Um aplicativo simples de monitoramento)](http://blogs.msdn.com/b/sqlAlways%20On/archive/2012/02/15/monitoring-Always%20On-health-with-powershell-part-3.aspx)  
  
     [Monitoring Always On Health with PowerShell – Part 4: Integration with SQL Server Agent (Monitorando a integridade do AlwaysOn com o PowerShell – Parte 4: Integração com o SQL Server Agent)](http://blogs.msdn.com/b/sqlAlways%20On/archive/2012/02/15/the-always-on-health-model-part-4.aspx)  
  
     [Blogs da equipe do AlwaysOn do SQL Server: o blog oficial da equipe do AlwaysOn do SQL Server](http://blogs.msdn.com/b/sqlAlways%20On/)  
  
     [Blogs dos engenheiros do CSS SQL Server](http://blogs.msdn.com/b/psssql/)  
  
-   **White papers:**  
  
     [White papers da Microsoft para SQL Server 2012](http://msdn.microsoft.com/library/hh403491.aspx)  
  
     [White papers da equipe de consultoria do cliente do SQL Server](http://sqlcat.com/)  
  
## Consulte também  
 [Exibições de catálogo de grupos de disponibilidade AlwaysOn &#40;Transact-SQL&#41;](../../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)   
 [Funções e exibições de gerenciamento dinâmico de grupos de disponibilidade AlwaysOn &#40;Transact-SQL&#41;](../../../relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions.md)   
 [Política de failover flexível para failover automático de um grupo de disponibilidade &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/flexible automatic failover policy - availability group.md)   
 [Visão geral dos grupos de disponibilidade AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Reparo automático de página &#40;Grupos de disponibilidade: espelhamento de banco de dados&#41;](../../../sql-server/failover-clusters/automatic-page-repair-availability-groups-database-mirroring.md)   
 [Usar o Painel AlwaysOn &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  