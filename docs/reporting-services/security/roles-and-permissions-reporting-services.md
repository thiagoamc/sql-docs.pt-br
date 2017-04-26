---
title: "Fun&#231;&#245;es e permiss&#245;es (Reporting Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "controles de acesso [Reporting Services]"
  - "permissões [Reporting Services], sobre permissões"
  - "segurança [Reporting Services], controle de acesso e identidade"
  - "autenticação [Reporting Services]"
  - "permissões [Reporting Services]"
  - "segurança [Reporting Services], baseada em função"
  - "identidade [Reporting Services]"
ms.assetid: eea655fe-43ed-418d-8233-b288a8f4daa4
caps.latest.revision: 18
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 18
---
# Fun&#231;&#245;es e permiss&#245;es (Reporting Services)
  O Reporting Services fornece um subsistema de autenticação e modelo de autorização com base na função. Os modelos de autenticação e autorização variam, dependendo se o servidor de relatório é executado no modo nativo ou no modo do SharePoint. Se o servidor de relatório fizer parte de uma implantação do SharePoint, as permissões do SharePoint determinarão quem tem acesso ao servidor de relatório.  
  
## Controle de identidade e acesso para o modo nativo  
 A autenticação padrão se baseia na Autenticação e na segurança integrada do Windows. Você pode alterar as configurações de autenticação para permitir que o servidor de relatório responda a solicitações de autenticação diferentes, ou mesmo substitua os recursos de segurança padrão por uma extensão de autenticação personalizada fornecida por você.  
  
 A autorização se baseia em funções que você atribui a um princípio. Cada função consiste em um conjunto de tarefas relacionadas compostas, por sua vez, por operações relacionadas. Por exemplo, a tarefa **Gerenciar relatórios** concede acesso às seguintes operações de servidor de relatório: exibir relatórios, adicionar relatório, atualizar relatório, excluir relatório, agendar relatório e atualizar propriedades de relatório.  
  
## Controle de identidade e acesso no modo do SharePoint  
 No modo integrado do SharePoint, a autenticação e a autorização são manipuladas no site do SharePoint, antes da chegada das solicitações ao servidor de relatório. De acordo com o modo como você configura a autenticação, as solicitações de um site do SharePoint contêm um token de segurança ou um nome de usuário confiável. As permissões que você define para usuários e grupos do SharePoint autorizam o acesso aos itens do servidor de relatório colocados nas bibliotecas do SharePoint.  
  
## Nesta seção  
 [Concedendo permissões em um servidor de relatório no modo nativo](../../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md)  
 Descreve o modelo de autorização com base em funções que fornece acesso a conteúdo e operações.  
  
 [Concedendo permissões para itens do servidor de relatório em um site do SharePoint](../../reporting-services/security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md)  
 Explica como grupos, níveis de permissão e permissões do SharePoint são usados para controlar o acesso a um servidor de relatório.  
  
## Consulte também  
 [Autenticação com o servidor de relatório](../../reporting-services/security/authentication-with-the-report-server.md)   
 [Concedendo permissões em um servidor de relatório no modo nativo](../../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md)  
  
  