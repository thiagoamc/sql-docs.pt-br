---
title: "Tarefa Atualizar Estat&#237;sticas | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.updatestatisticstask.f1"
helpviewer_keywords: 
  - "atualizando estatísticas"
  - "Tarefa Atualizar Estatísticas [Integration Services]"
ms.assetid: 0247483b-f092-4511-8fa8-3610108bd1bc
caps.latest.revision: 45
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 45
---
# Tarefa Atualizar Estat&#237;sticas
  A tarefa Atualizar Estatísticas atualiza informações sobre a distribuição de valores de chaves para um ou mais grupos de estatísticas (coleções) na tabela ou na exibição indexada especificada. Para obter mais informações, consulte [Statistics](../../relational-databases/statistics/statistics.md).  
  
 Utilizando-se a tarefa Atualizar Estatísticas, um pacote pode atualizar as estatísticas de um único banco de dados ou de vários bancos de dados. Se a tarefa atualizar só as estatísticas em um único banco de dados, você poderá escolher as exibições e as tabelas cujas estatísticas a tarefa atualizará. É possível configurar a atualização para atualizar todas as estatísticas, apenas as estatísticas de coluna, ou apenas as estatísticas de índice.  
  
 Esta tarefa encapsula uma instrução UPDATE STATISTICS, inclusive os seguintes argumentos e cláusulas:  
  
-   Os argumentos *table_name* ou *view_name*.  
  
-   Se a atualização se aplicar a todas as estatísticas, a cláusula WITH ALL estará implícita.  
  
-   Se a atualização se aplicar apenas a colunas, a cláusula WITH COLUMN será incluída.  
  
-   Se a atualização se aplicar apenas a índices, a cláusula WITH COLUMN será incluída.  
  
 Se a tarefa Atualizar Estatísticas atualizar estatísticas em vários bancos de dados, a tarefa executará várias instruções UPDATE STATISTICS, uma para cada tabela ou exibição. Todas as instâncias de UPDATE STATISTICS usam a mesma cláusula, mas têm valores diferentes para *table_name* ou *view_name*. Para obter mais informações, veja [CREATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/create-statistics-transact-sql.md) e [UPDATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md).  
  
> [!IMPORTANT]  
>  O tempo que a tarefa necessita para criar a instrução Transact-SQL que ela executa é proporcional ao número de estatísticas que a tarefa atualiza. Se a tarefa for configurada para atualizar estatísticas em todas as tabelas e exibições em um banco de dados com um grande número de índices ou em vários bancos de dados, ela pode levar um tempo considerável para gerar a instrução Transact-SQL.  
  
## Configuração da tarefa Atualizar Estatísticas  
 Você pode definir propriedades por meio do [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer. Esta tarefa está na seção **Tarefas do Plano de Manutenção** da **Caixa de Ferramentas** , no Designer [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Para obter mais informações sobre as propriedades que podem ser definidas no [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, clique no tópico a seguir:  
  
-   [Tarefa Atualização de Estatísticas &#40;Plano de manutenção&#41;](../../relational-databases/maintenance-plans/update-statistics-task-maintenance-plan.md)  
  
## Tarefas relacionadas  
 Para obter mais informações sobre como definir essas propriedades no [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, clique no tópico a seguir:  
  
-   [Definir as propriedades de uma tarefa ou contêiner](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)  
  
## Consulte também  
 [Tarefas do Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Fluxo de Controle](../../integration-services/control-flow/control-flow.md)  
  
  