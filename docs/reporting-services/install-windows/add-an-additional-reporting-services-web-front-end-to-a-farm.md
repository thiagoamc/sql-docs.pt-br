---
title: "Adicionar um front-end da Web do Reporting Services a um farm | Microsoft Docs"
ms.custom: ""
ms.date: "06/03/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d7a11bda-ae26-49ac-b071-37d83cae5afe
caps.latest.revision: 11
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 11
---
# Adicionar um front-end da Web do Reporting Services a um farm
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] O modo SharePoint inclui componentes necessários para servidores de aplicativos e WFE (servidores de front-end da Web). Este tópico aborda a instalação de componentes do [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] necessárias para um servidor de WFE, inclusive as páginas de aplicativo usadas por recursos do [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] como assinaturas, alertas de dados e [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]. A instalação primária do [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] necessária para um WFE é instalar o suplemento do [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] para produtos do SharePoint 2016.  
  
## Pré-requisitos  
  
-   Você deve ser um administrador local para executar a Instalação do SQL Server.  
  
-   O computador deve ser unido a um domínio.  
  
-   Você precisa saber o nome do servidor de banco de dados existente que está hospedando a configuração do SharePoint e os bancos de dados de conteúdo.  
  
-   O servidor de banco de dados deve ser configurado para permitir conexões de bancos de dados remotos.  Se não, você não poderá unir o novo servidor ao farm porque o novo servidor não poderá fazer uma conexão com os bancos de dados de configuração do SharePoint.  
  
-   O novo servidor precisará ter a mesma versão de SharePoint instalado que os servidores de farm atuais estão executando. Por exemplo, se o farm já tiver o SharePoint 2013 Service Pack 1 (SP1) instalado, você também precisará instalar o SP1 no novo servidor antes de unir o farm.  
  
## Etapas  
 As etapas neste tópico pressupõem que um administrador de farm do SharePoint esteja instalando e configurando o servidor. O diagrama mostra um ambiente típico de três camadas e os itens numerados no diagrama são descritos na lista a seguir:  
  
-   (1) Vários servidores de front-end da Web (WFE). Os servidores WFE exigem o suplemento [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] para SharePoint 2010. As etapas a seguir adicionam um segundo servidor de aplicativos a esta camada.  
  
-   (2) Dois servidores de aplicativos que executam o [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] e sites, por exemplo a Administração Central.  
  
-   (3) Dois servidores de banco de dados do SQL Server.  
  
-   (4) Representa uma solução de software ou hardware de NLB (balanceamento de carga de rede)  
  
 ![Add SSRS to a new SharePoint WFE](../../reporting-services/install-windows/media/rs-sharepointscale-wfe.gif "Add SSRS to a new SharePoint WFE")  
  
 As etapas a seguir pressupõem que um administrador esteja instalando e configurando o servidor.  
  
|Etapa|Descrição e link|  
|----------|--------------------------|  
|Adicione um servidor do SharePoint a um farm.|Você precisará instalar o SharePoint para implantar outro aplicativo do Reporting Services.<br/><br/>Para o SharePoint 2013, consulte [Adicionar o SharePoint Server a um farm no SharePoint Server 2013](https://technet.microsoft.com/library/cc261752(v=office.15).aspx).<br/><br/>Para o SharePoint 2016, consulte [Adicionar o SharePoint Server a um farm no SharePoint Server 2016](https://technet.microsoft.com/library/cc261752(v=office.16).aspx).|  
|Instale o suplemento [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] para produtos do SharePoint 2016.|Há vários métodos para instalar o suplemento. As seguintes etapas usam o assistente de instalação do [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Para obter mais informações sobre como instalar o suplemento, consulte [Instalar ou desinstalar o suplemento Reporting Services para SharePoint](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)<br /><br /> 1) Execute a instalação do [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> 2) Na página **Função de instalação**, selecione **Instalação de recurso do SQL Server**<br /><br /> 3) Na página **Seleção de Recursos**, selecione **Suplemento do Reporting Services para produtos SharePoint**<br /><br /> 4) Clique em **Avançar** nas próximas várias páginas para concluir as opções de instalação.<br /><br/>Para obter mais informações sobre a instalação do [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], consulte [Instalar o Primeiro Servidor de Relatório no Modo do SharePoint](http://msdn.microsoft.com/pt-br/b29d0f45-0068-4c84-bd7e-5b8a9cd1b538)|  
|Verifique se o novo servidor está operacional.|1) Na Administração Central do SharePoint, clique em **Gerenciar servidores neste farm** no grupo **Configurações do Sistema**.<br /><br /> 2) Verifique se o novo servidor está na lista.|  
|Atualize sua solução de NLB.|Se apropriado, atualize seu ambiente de hardware ou software NLB para incluir o novo servidor.|  
  
## Consulte também  
[Adicionar o SharePoint Server a um farm no SharePoint Server 2016](https://technet.microsoft.com/library/cc261752(v=office.16).aspx)  
[Adicionar o SharePoint Server a um farm no SharePoint Server 2013](https://technet.microsoft.com/library/cc261752(v=office.15).aspx)
  
  