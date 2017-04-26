---
title: "Tarefa Transferir Trabalhos | Microsoft Docs"
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
  - "sql13.dts.designer.transferjobstask.f1"
helpviewer_keywords: 
  - "tarefa Transferir Trabalhos [Integration Services]"
ms.assetid: 1bf33885-9c5b-47e4-a549-f5920b66a1de
caps.latest.revision: 28
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 28
---
# Tarefa Transferir Trabalhos
  A tarefa Transferir Trabalhos transfere um ou mais trabalhos do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent entre instâncias do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 A tarefa Transferir Trabalhos pode ser configurada para transferir todos os trabalhos ou só os trabalhos especificados. Você também pode indicar se os trabalhos transferidos são habilitados no destino.  
  
 Os trabalhos a ser transferidos já podem existir no destino. A tarefa Transferir Trabalhos pode ser configurada para manipular os trabalhos existentes dos modos a seguir:  
  
-   Substituir os trabalhos existentes.  
  
-   Interromper a tarefa quando houver trabalhos duplicados.  
  
-   Ignorar trabalhos duplicados.  
  
 No tempo de execução, a tarefa Transferir Trabalhos conecta-se aos servidores de origem e de destino usando um ou dois gerenciadores de conexões SMO. O gerenciador de conexões SMO é configurado separadamente da tarefa Transferir Trabalhos e depois é referenciado na tarefa Transferir Trabalhos. O gerenciador de conexões SMO especifica o servidor e o modo de autenticação a ser usado ao acessar o servidor. Para obter mais informações, consulte [SMO Connection Manager](../../integration-services/connection-manager/smo-connection-manager.md).  
  
## Transferindo trabalhos entre instâncias do SQL Server  
 A tarefa Transferir Trabalhos dá suporte a uma origem e a um destino do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Não há nenhuma restrição quanto à versão a ser usada como origem ou destino.  
  
## Eventos  
 A tarefa Transferir Trabalhos gera um evento de informação com o número de trabalhos transferidos e um evento de aviso quando um trabalho é substituído. A tarefa não informa o progresso incremental da transferência de trabalhos; informa só 0% e 100% concluídos.  
  
## Valor de execução  
 O valor de execução, definido na propriedade **ExecutionValue** da tarefa retorna o número de trabalhos que são transferidos. Ao atribuir uma variável definida pelo usuário à propriedade **ExecValueVariable** da tarefa Transferir Trabalhos, informações sobre a transferência de trabalhos podem se tornar disponíveis a outros objetos no pacote. Para obter mais informações, consulte [Variáveis do Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md) e [Usar variáveis em pacotes](../Topic/Use%20Variables%20in%20Packages.md).  
  
## Entradas de log  
 A tarefa Transferir Trabalhos inclui as seguintes entradas de log personalizadas:  
  
-   TransferJobsTaskStarTransferringObjects   Essa entrada de log informa que a transferência foi iniciada. A entrada do log contém a hora de início.  
  
-   TransferJobsTaskFinishedTransferringObjects    Essa entrada de log informa que a transferência foi concluída. A entrada do log contém a hora de término.  
  
 Além disso, uma entrada de log para o evento **OnInformation** informa o número de trabalhos que foram transferidos e uma entrada de log para o evento **OnWarning** é gravada para cada trabalho no destino que for substituído.  
  
## Segurança e permissões  
 Para transferir trabalhos, o usuário deve ser membro da função de servidor fixa sysadmin ou de uma das funções de banco de dados fixas Agent do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no banco de dados msdb em ambas as instâncias de origem e de destino do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## Configuração da tarefa Transferir Trabalhos  
 Você pode definir propriedades pelo Designer do [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou programaticamente.  
  
 Para obter informações sobre as propriedades que podem ser definidas no [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, clique em um dos tópicos a seguir:  
  
-   [Editor da Tarefa Transferir Trabalhos &#40;Página Geral&#41;](../../integration-services/control-flow/transfer-jobs-task-editor-general-page.md)  
  
-   [Editor da Tarefa Transferir Trabalhos &#40;página Trabalhos&#41;](../../integration-services/control-flow/transfer-jobs-task-editor-jobs-page.md)  
  
-   [Página Expressões](../../integration-services/expressions/expressions-page.md)  
  
 Para obter informações sobre como definir essas propriedades programaticamente, clique no tópico a seguir:  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferJobsTask.TransferJobsTask>  
  
## Tarefas relacionadas  
 Para obter mais informações sobre como definir essas propriedades no [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, clique no tópico a seguir:  
  
-   [Definir as propriedades de uma tarefa ou contêiner](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)  
  
## Consulte também  
 [Tarefas do Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Fluxo de Controle](../../integration-services/control-flow/control-flow.md)  
  
  