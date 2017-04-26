---
title: "Ativar o recurso de sincroniza&#231;&#227;o de relat&#243;rio do Servidor de Relat&#243;rio na Administra&#231;&#227;o Central do SharePoint | Microsoft Docs"
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
ms.assetid: 32d1988d-07e7-41c2-b636-e65ecfae4677
caps.latest.revision: 9
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 9
---
# Ativar o recurso de sincroniza&#231;&#227;o de relat&#243;rio do Servidor de Relat&#243;rio na Administra&#231;&#227;o Central do SharePoint
  O recurso Sincronização de arquivos do Servidor de Relatório do [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] utiliza manipuladores de eventos do SharePoint para sincronizar o catálogo do servidor de relatório com itens em bibliotecas de documentos. Esse recurso é benéfico quando os usuários carregam com frequência itens de relatórios publicados diretamente nas bibliotecas de documentos do SharePoint. Se o recurso de Sincronização de arquivo não estiver ativado, o conteúdo ainda será sincronizado, mas não tão frequentemente.  
  
 O recurso Sincronização de Arquivos pode ser ativado na Administração de Site do SharePoint depois que você instala o Suplemento [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] para produtos do SharePoint.  
  
 Esse recurso pode ser ativado e desativado manualmente por site, mas não no nível de conjunto de sites.  
  
## Pré-requisitos  
 O Suplemento [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] para o SharePoint deve ser instalado. Se o suplemento não estiver instalado, o recurso de sincronização de arquivos não estará visível na lista de recursos do site.  
  
 Para verificar a instalação, exiba a lista de aplicativos instalados no [!INCLUDE[msCoName](../../includes/msconame-md.md)] Painel de Controle **do**Windows. Se o Suplemento [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] estiver instalado, siga as instruções deste tópico para ativar o recurso Sincronização de arquivos do servidor de relatório.  
  
### Para ativar ou desativar o recurso Sincronização de arquivos do Reporting Services em um site  
  
1.  Na página principal do site, clique no menu **Ações do Site** e clique em **Configurações do Site**.  
  
2.  Em **Ações de Site** , clique em **Gerenciar Recursos de Site**.  
  
3.  Localize **Sincronização de arquivos do Servidor de Relatório** na lista.  
  
4.  Clique em **Ativar**.  
  
> [!NOTE]  
>  Para desativar o recurso Sincronização de arquivos do Servidor de Relatório, é possível usar o mesmo procedimento, mas clique em **Desativar**.  
  
## Consulte também  
 [Solução de problemas de partes de relatório (Construtor de Relatórios e SSRS)](http://msdn.microsoft.com/pt-br/d9fe1932-46e7-421b-a8a9-4c54d9576e94)   
 [Ativar o servidor de relatório e os recursos de integração do Power View no SharePoint](../../reporting-services/report-server-sharepoint/activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)   
 [Instalar ou desinstalar o suplemento Reporting Services para SharePoint](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)   
 [Instalar ou desinstalar o suplemento Reporting Services para SharePoint](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  