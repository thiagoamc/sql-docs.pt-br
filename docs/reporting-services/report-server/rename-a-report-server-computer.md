---
title: "Renomear um computador de servidor de relat&#243;rio | Microsoft Docs"
ms.custom: ""
ms.date: "03/20/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "renomeando servidores de relatório"
ms.assetid: 82fc4ba2-291a-4939-a025-271b8d687c54
caps.latest.revision: 45
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 45
---
# Renomear um computador de servidor de relat&#243;rio
  A renomeação de um computador provoca uma alteração de nome correspondente para o servidor Web e a instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (se estiver no mesmo computador). Em alguns casos, o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] talvez não possa ser acessado após uma alteração de nome do computador. Use as etapas fornecidas neste tópico para reconfigurar um servidor de relatório depois de uma alteração de nome do computador.  
  
## Renomeando um Mecanismo de Banco de Dados do SQL Server  
 Se você renomear a instância do  [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] que executa o banco de dados do servidor de relatório, faça o seguinte:  
  
1.  Inicie a ferramenta Configuração do Reporting Services e conecte-se ao servidor de relatório que usa o banco de dados do servidor de relatório no servidor renomeado.  
  
2.  Abra a página Configuração do Banco de Dados.  
  
3.  Em **Nome do Servidor**, digite ou selecione o nome do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e, em seguida, clique em **Conectar**.  
  
4.  Clique em **Aplicar**.  
  
 Se o servidor de relatório estiver usando uma instância local do [!INCLUDE[ssDE](../../includes/ssde-md.md)], use *(local)* ou *(local)\nomedainstância* para especificar o servidor. Se você usar *(local)* para fazer referência ao servidor, poderá renomear o servidor e as conexões continuarão funcionando. Caso esteja usando um servidor remoto ou o [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] seja configurado com o nome do servidor, atualize as informações de conexão do banco de dados sempre que o nome do servidor for alterado.  
  
## Renomeando um computador de servidor de relatório  
 Se você renomear um computador que executa um servidor de relatório, faça o seguinte:  
  
1.  Abra RSReportServer.config em um editor de texto e modifique a configuração **UrlRoot** para refletir o novo nome do servidor. A configuração **UrlRoot** é usada pelas extensões de entrega para compor o URL usado para acessar itens armazenados no servidor de relatório. A alteração do endereço URL do servidor de relatório requer a atualização da configuração **UrlRoot** para que as assinaturas continuem a entregar os relatórios conforme o esperado.  
  
2.  No mesmo arquivo, se estiver definida, modifique a configuração **ReportServerUrl** para refletir o novo nome do servidor. Esta configuração não é usada em todas as instalações. Se estiver vazio, não faça nada.  
  
    > [!NOTE]  
    >  Se estiver usando o WINS (Windows Internet Naming Service) na rede corporativa, o servidor de relatório e o Gerenciador de Relatórios podem continuar disponíveis com o nome anterior por um período de tempo. O WINS mapeia um endereço IP para cada computador ao qual oferece suporte. Quando o WINS atualiza o endereço IP do computador renomeado, o nome antigo do computador não pode ser mais usado para acessar um servidor de relatório ou Gerenciador de Relatórios.  
  
## Consulte também  
 [Arquivo de Configuração RsReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)   
 [Reporting Services Configuration Manager &#40;Modo Nativo&#41;](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md)   
 [Servidor de relatório do Reporting Services &#40;Modo Nativo&#41;](../../reporting-services/report-server/reporting-services-report-server-native-mode.md)   
 [Iniciar e parar o serviço Servidor de Relatório](../../reporting-services/report-server/start-and-stop-the-report-server-service.md)   
 [Utilitário rsconfig &#40;SSRS&#41;](../../reporting-services/tools/rsconfig-utility-ssrs.md)  
  
  