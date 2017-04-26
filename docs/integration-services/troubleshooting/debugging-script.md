---
title: "Depurando script | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tarefa de script [Integration Services], depurando"
  - "depurando [Integration Services], scripts"
  - "scripts [Integration Services], depurando"
ms.assetid: fddf57d8-8607-4f88-85a0-1b683087b491
caps.latest.revision: 57
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 57
---
# Depurando script
  Os scripts usados pela tarefa Script e um componente Script são gravados no [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] VSTA (Tools for Applications).  
  
 É possível definir e escrever scripts de pontos de interrupção no VSTA. Você pode administrar pontos de interrupção no VSTA, mas também pode administrar os pontos de interrupção usando a caixa de diálogo **Definir Pontos de Interrupção** fornecida pelo Designer [!INCLUDE[ssIS](../../includes/ssis-md.md)]. Para obter mais informações, consulte [Depurando o fluxo de controle](../../integration-services/troubleshooting/debugging-control-flow.md).  
  
 A caixa de diálogo **Definir Pontos de Interrupção** inclui os pontos de interrupção de script. Esses pontos de interrupção aparecem na parte inferior da lista de pontos de interrupção e exibem o número de linha e o nome da função em que o ponto de interrupção aparece. Você pode excluir um ponto de interrupção de script na caixa de diálogo **Definir Pontos de Interrupção**.  
  
 No tempo de execução, os pontos de interrupção definidos em linhas de código no script são integrados com o conjunto de pontos de interrupção definidos no pacote ou nas tarefas e nos contêineres do pacote. O depurador pode ser executado a partir de um ponto de interrupção no script para um conjunto de pontos de interrupção no pacote, tarefa, contêiner e vice-versa. Por exemplo, um pacote poderia ter um conjunto de pontos de interrupção nas condições de interrupção que ocorrem quando o pacote recebe os eventos **OnPreExecute** e **OnPostExecute** e também ter uma tarefa Script com pontos de interrupção nas linhas de seu script. Nesse cenário, o pacote pode suspender a execução na condição de interrupção associada com o evento **OnPreExecute**, executado nos pontos de interrupção no script, e finalmente executar a condição de interrupção associada com o evento **OnPostExecute**.  
  
 Para obter mais informações sobre como depurar a tarefa Script e o componente Script, consulte [Codificando e depurando a tarefa Script](../../integration-services/extending-packages-scripting/task/coding-and-debugging-the-script-task.md) e [Codificando e depurando o componente Script](../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).  
  
### Para definir um ponto de interrupção no Visual Studio for Applications  
  
-   [Depurar um script definindo pontos de interrupção em uma tarefa Script e um componente Script](../../integration-services/extending-packages-scripting/debug-a-script-by-setting-breakpoints-in-a-script-task-and-script-component.md)  
  
## Consulte também  
 [Solucionando problemas de ferramentas para desenvolvimento de pacotes](../../integration-services/troubleshooting/troubleshooting-tools-for-package-development.md)  
  
  