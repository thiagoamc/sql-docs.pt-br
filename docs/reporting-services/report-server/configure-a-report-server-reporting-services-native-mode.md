---
title: "Configurar um servidor de relat&#243;rios (modo nativo do Reporting Services) | Microsoft Docs"
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
  - "configuração do servidor de relatórios"
  - "servidores de relatório [Reporting Services], configurando"
ms.assetid: ef84ce9d-9156-48e9-8073-7e0535476932
caps.latest.revision: 17
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 17
---
# Configurar um servidor de relat&#243;rios (modo nativo do Reporting Services)
  Dependendo das opções selecionadas durante a instalação, o Servidor de Relatórios possivelmente exigir uma configuração adicional para que você possa usá-lo. A configuração de um servidor de relatório é formada no mínimo por estes itens:  
  
-   Uma conta do serviço Servidor de Relatórios (configurada durante a instalação).  
  
-   Uma URL de serviço Web que dá acesso ao servidor de relatório.  
  
-   Um banco de dados de servidor de relatório que armazena dados de aplicativo, relatórios e outros itens.  
  
 A Instalação define as configurações mínimas quando você seleciona uma das seguintes opções: configuração padrão do modo Nativo ou configuração padrão do modo integrado do SharePoint. Se você tiver instalado o servidor de relatório no modo somente arquivos (a opção **Instalar, mas não configurar** do assistente de Instalação), será configurada apenas a conta de serviço. A URL do serviço Web e o banco de dados do servidor de relatório devem ser configurados após o término da instalação.  
  
 O Gerenciador de Relatórios é um recurso opcional para um servidor de relatório no modo nativo, mas é recomendável configurá-lo de forma que você possa conceder acesso ao servidor de relatório ao usuário e gerenciar o conteúdo do servidor de relatório. Se você implantar um servidor de relatório no modo integrado do SharePoint, use o front-end da Web de um servidor SharePoint para conceder acesso.  
  
 Recursos adicionais, como e-mail de servidor de relatório e a conta de execução autônoma, podem ser configurados conforme necessário. Para obter mais informações, consulte [Gerenciar um servidor de relatório de modo nativo do Reporting Services](../../reporting-services/report-server/manage-a-reporting-services-native-mode-report-server.md).  
  
 Para configurar um servidor de relatório, use a ferramenta Configuração do Reporting Services.  
  
### Para definir a configuração mínima de uma instalação de servidor de relatório  
  
1.  Inicie a ferramenta Configuração do Reporting Services e conecte-se à instância do servidor de relatório. Para obter instruções, veja [Reporting Services Configuration Manager &#40;Modo Nativo&#41;](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md).  
  
2.  Clique em **URL do Serviço da Web** para abrir a página e configurar uma URL para o servidor de relatório. Para obter instruções sobre como definir a URL, veja [Configurar uma URL &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md).  
  
3.  Clique em **Banco de Dados** para criar o banco de dados do servidor de relatório. Para obter instruções, veja [Criar um banco de dados de servidor de relatório do modo nativo &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/create-a-native-mode-report-server-database-ssrs-configuration-manager.md).  
  
4.  Volte à página **URL do Serviço da Web** e clique na URL para verificar se ela está funcionando.  
  
5.  Siga as instruções descritas em "Próximas etapas" para concluir a implantação.  
  
## Próximas etapas  
 Para concluir a implantação, configure o Gerenciador de Relatórios ou a integração com o SharePoint. Para obter mais informações, consulte [Configurar o Gerenciador de Relatórios &#40;Modo Nativo&#41;](../../reporting-services/report-server/configure-report-manager-native-mode.md).  
  
 Se o Firewall do Windows estiver ativado, a porta que o servidor de relatório está configurado para usar provavelmente estará fechada. Uma indicação de que uma porta pode estar fechada é uma página em branco quando você tenta abrir o Gerenciador de Relatórios em um computador cliente remoto. Para obter informações sobre como configurar o firewall, consulte [Configure a Firewall for Report Server Access](../../reporting-services/report-server/configure-a-firewall-for-report-server-access.md).  
  
 Se estiver usando o Windows Vista ou o Windows Server 2008, etapas adicionais serão necessárias para abrir o Gerenciador de Relatórios localmente. Para obter mais informações, veja [Configurar um servidor de relatório no modo nativo para a Administração Local &#40;SSRS&#41;](../../reporting-services/report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).  
  
 Verifique a instalação criando pastas, carregando itens e executando relatórios. Siga as instruções em [Verificar uma instalação do Reporting Services](../../reporting-services/install-windows/verify-a-reporting-services-installation.md) para verificar a instalação.  
  
## Consulte também  
 [Gerenciar um servidor de relatórios de modo nativo do Reporting Services](../../reporting-services/report-server/manage-a-reporting-services-native-mode-report-server.md)   
 [Configurar um firewall para acesso ao servidor de relatório](../../reporting-services/report-server/configure-a-firewall-for-report-server-access.md)   
 [Configurar um servidor de relatório no modo nativo para a Administração Local &#40;SSRS&#41;](../../reporting-services/report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md)   
 [Configurar um servidor de relatório para administração remota](../../reporting-services/report-server/configure-a-report-server-for-remote-administration.md)   
 [Reporting Services Configuration Manager &#40;Modo Nativo&#41;](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md)  
  
  