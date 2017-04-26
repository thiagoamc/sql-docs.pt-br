---
title: "Exibir objetos do pacote | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Pacotes do Integration Services, propriedades"
  - "propriedades [Integration Services]"
  - "Janela Explorador de Pacotes [Integration Services]"
  - "pacotes [Integration Services], propriedades"
  - "visualização do explorador [Integration Services]"
  - "Pacotes do SSIS, propriedades"
  - "exibindo objetos de pacote"
  - "Pacotes do SQL Server Integration Services, propriedades"
ms.assetid: a85c0245-0a68-4eb0-83b1-9b11df80bd10
caps.latest.revision: 36
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 35
---
# Exibir objetos do pacote
  No Designer do [!INCLUDE[ssIS](../includes/ssis-md.md)], a guia **Explorador de Pacotes** fornece uma exibição de explorer do pacote. A exibição reflete a hierarquia de contêiner da arquitetura [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. O contêiner de pacote está no topo da hierarquia e você expande o pacote para exibir as conexões, executáveis, manipuladores de eventos, provedores de log, restrições de precedência e variáveis no pacote.  
  
 Os executáveis, que são contêineres e tarefas do pacote, podem incluir manipuladores de eventos, restrições de precedência e variáveis. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] dá suporte a uma hierarquia de contêineres aninhada, e os contêineres Loop For, Loop Foreach e Sequência podem incluir outros executáveis.  
  
 Se um pacote incluir um fluxo de dados, o **Explorador de Pacotes** listará a tarefa de Fluxo de Dados e incluirá uma pasta **Componentes** que lista os componentes de fluxo de dados.  
  
 Na guia **Explorador de Pacotes**, você pode excluir objetos em um pacote e acessar a janela **Propriedades** para exibir as propriedades do objeto.  
  
 O diagrama a seguir mostra uma exibição de árvore de um pacote simples.  
  
 ![Captura de tela da guia Explorador de Pacotes](../integration-services/media/packageexplorer.gif "Captura de tela da guia Explorador de Pacotes")  
  
### Para exibir o conteúdo do pacote  
  
-   [Exibir objetos de pacote no Explorador de Pacotes](../Topic/View%20Package%20Objects%20in%20Package%20Explorer.md)  
  
## Consulte também  
 [Tarefas do Integration Services](../integration-services/control-flow/integration-services-tasks.md)   
 [Contêineres do Integration Services](../integration-services/control-flow/integration-services-containers.md)   
 [Restrições de precedência](../integration-services/control-flow/precedence-constraints.md)   
 [Variáveis do SSIS &#40;Integration Services&#41;](../integration-services/integration-services-ssis-variables.md)   
 [Manipuladores de eventos do Integration Services &#40;SSIS&#41](../integration-services/integration-services-ssis-event-handlers.md)   
 [Registro em Log do Integration Services &#40;SSIS&#41;](../integration-services/performance/integration-services-ssis-logging.md)  
  
  