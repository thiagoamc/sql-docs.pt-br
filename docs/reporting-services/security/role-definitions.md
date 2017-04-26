---
title: "Defini&#231;&#245;es de fun&#231;&#227;o | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "funções [Reporting Services], criando"
  - "funções [Reporting Services], segurança"
  - "segurança [Reporting Services], definições de função"
  - "segurança baseada em função [Reporting Services], definições de função"
ms.assetid: d1b8dbf0-4462-402e-92dd-0e4835002b6e
caps.latest.revision: 44
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 44
---
# Defini&#231;&#245;es de fun&#231;&#227;o
  No [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], uma *definição* de *função* é uma coleção nomeada de tarefas que definem as operações disponíveis em um servidor de relatório. As definições de função fornecem as regras usadas pelo servidor de relatório para impor a segurança. Quando um usuário tenta executar uma tarefa, como publicar um relatório, o servidor de relatório verifica a atribuição de função de relatório do usuário para determinar se a tarefa está incluída em sua definição de função. Se a tarefa estiver incluída na definição de função, a solicitação será enviada.  
  
## Usando funções para autorizar o acesso a um servidor de relatório  
 Uma função só se torna operacional quando usada em uma atribuição de função. Para obter mais informações sobre como as funções fornecem segurança, consulte [Atribuições de Função](../../reporting-services/security/role-assignments.md).  
  
## Tipos de definições de função  
 Definições de função são definições em nível de item ou de sistema. Uma *definição de função de nível de item* descreve as tarefas relacionadas aos itens armazenados e gerenciados em um servidor de relatório, como relatórios, pastas e modelos. Gerenciar relatórios, Exibir pastas e Gerenciar assinaturas individuais são exemplos de tarefas que você pode incluir nas definições de função de nível de item. Uma *definição de função de sistema* inclui tarefas que se aplicam ao site como um todo. Exibir as propriedades do servidor de relatório é um exemplo de uma tarefa que você pode incluir em uma função de sistema.  
  
## Funções predefinidas  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] inclui funções predefinidas que correspondem a níveis diferentes de interação com o usuário. A seguinte lista contém as funções predefinidas que você pode usar:  
  
-   Gerenciador de Conteúdo, Publicador, Navegador, Construtor de Relatórios e Meus Relatórios são definições de função de nível de item que você pode usar ao criar atribuições de função para acessar conteúdo de servidor de relatório.  
  
-   Administrador de Sistema e Usuário do Sistema são definições de função em nível de sistema que você pode usar para autorizar o acesso a operações de site.  
  
 Para obter mais informações, consulte [Funções Predefinidas](../../reporting-services/security/predefined-roles.md).  
  
## Criando uma definição de função  
 Para criar uma função, use o Management Studio para especificar um nome e as tarefas que ela contém. Você deve criar uma definição de função separada para tarefas de item e de sistema. As funções podem incluir tarefas em nível de item ou de sistema, mas não ambas. A criação de uma definição de função consiste em fornecer um nome e escolher um conjunto de tarefas para a definição. Para criar uma definição de função, você deve ter permissão para fazer isso. A tarefa "Definir segurança para itens individuais" fornece essas permissões. Por padrão, administradores e usuários atribuídos à função **Gerenciador de Conteúdo** predefinida podem executar essa tarefa.  
  
 Uma função deve ter um nome exclusivo. Para ser válida, a definição de função deve conter pelo menos uma tarefa. Para obter mais informações, consulte [Tarefas e Permissões](../../reporting-services/security/tasks-and-permissions.md).  
  
 Para criar uma definição de função, use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Para obter mais informações, consulte [Criar, excluir ou modificar uma função &#40;Management Studio&#41;](../../reporting-services/security/create-delete-or-modify-a-role-management-studio.md).  
  
 Após criar uma definição de função, você poderá usá-la selecionando-a em uma atribuição de função. Para obter mais informações, consulte [Conceder acesso ao usuário a um servidor de relatório &#40;Gerenciador de Relatórios&#41;](../../reporting-services/security/grant-user-access-to-a-report-server-report-manager.md).  
  
## Personalizar ou excluir uma definição de função  
 Funções predefinidas podem ser modificadas ou substituídas por funções personalizadas. Para modificar uma função, adicione ou remova tarefas da definição de função. Não é possível renomear uma função. Qualquer alteração feita será imediatamente aplicada a todas as atribuições de função que contenham a definição de função.  
  
 Você poderá excluir uma definição de função se já não estiver mais a utilizando. Não será possível excluir a definição de função selecionada para o recurso Meus Relatórios se esse recurso estiver habilitado. Antes de excluir a definição de função usada por Meus Relatórios, desabilite o recurso ou selecione outra definição de função para usar com ele.  
  
## Consulte também  
 [Tarefas e permissões](../../reporting-services/security/tasks-and-permissions.md)   
 [Concedendo permissões em um servidor de relatório no modo nativo](../../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md)   
 [Criar, excluir ou modificar uma função &#40;Management Studio&#41;](../../reporting-services/security/create-delete-or-modify-a-role-management-studio.md)   
 [Conceder acesso ao usuário a um servidor de relatório &#40;Gerenciador de Relatórios&#41;](../../reporting-services/security/grant-user-access-to-a-report-server-report-manager.md)   
 [Modificar ou excluir uma atribuição de função &#40;Gerenciador de Relatórios&#41;](../../reporting-services/security/modify-or-delete-a-role-assignment-report-manager.md)   
 [Definir permissões para itens do Servidor de Relatório em um site do SharePoint &#40;Reporting Services no modo integrado do SharePoint&#41;](../../reporting-services/security/set permissions for report server items on a sharepoint site.md)  
  
  