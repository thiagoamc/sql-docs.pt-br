---
title: "Opera&#231;&#245;es de backup e restaura&#231;&#227;o para o Reporting Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/18/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
  - "reporting-services-sharepoint"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "bancos de dados [Reporting Services], fazendo backup"
  - "bancos de dados [Reporting Services], restaurando"
  - "bancos de dados [Reporting Services], movendo"
  - "fazendo backup de bancos de dados [Reporting Services]"
  - "movendo bancos de dados"
  - "restaurando bancos de dados [Reporting Services]"
  - "arquivos [Reporting Services], restaurando"
  - "arquivos [Reporting Services], fazendo backup"
ms.assetid: 157bc376-ab72-4c99-8bde-7b12db70843a
caps.latest.revision: 43
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 43
---
# Opera&#231;&#245;es de backup e restaura&#231;&#227;o para o Reporting Services
  Este tópico fornece uma visão geral de todos os arquivos de dados usados em uma instalação do [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] e descreve quando e como você deve fazer backup dos arquivos. O desenvolvimento de um plano de backup e restauração para os arquivos do banco de dados do servidor de relatório é a parte mais importante de uma estratégia de recuperação. No entanto, uma estratégia de recuperação mais abrangente inclui backups de chaves de criptografia, assemblies ou extensões personalizados, arquivos de configuração e arquivos de origem para relatórios e modelos.  
  
 Modo nativo do **[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] | Modo do SharePoint do [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
 As operações de backup e restauração são usadas com frequência para mover todo ou parte de uma instalação do [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]:  
  
-   Se estiver movendo apenas os bancos de dados do servidor de relatório, poderá usar o backup e restauração ou anexar e desanexar para realocar os bancos de dados em uma instância diferente do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Para obter mais informações, consulte [Movendo os bancos de dados do servidor de relatório para outro computador &#40;modo nativo do SSRS&#41;](../../reporting-services/report-server/moving-the-report-server-databases-to-another-computer-ssrs-native-mode.md).  
  
-   Mover uma instalação do [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] para um computador novo é chamado de migração. Quando você migra uma instalação, o Programa de Instalação é executado para instalar uma nova instância do servidor de relatório e, em seguida, os dados da instância são copiados para o novo computador. Para obter mais informações sobre como migrar uma instalação do [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], consulte os seguintes tópicos:  
  
    -   [Atualizar e migrar o Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)  
  
    -   [Migrar uma instalação do Reporting Services &#40;modo do SharePoint&#41;](../../reporting-services/install-windows/migrate-a-reporting-services-installation-sharepoint-mode.md)  
  
    -   [Migrar uma instalação do Reporting Services &#40;modo nativo&#41;](../../reporting-services/install-windows/migrate-a-reporting-services-installation-native-mode.md)  
  
## Fazendo backup dos bancos de dados do servidor de relatório  
 Uma vez que um servidor de relatório é um servidor sem monitoração de estado, os dados de todos os aplicativos são armazenados nos bancos de dados **reportserver** e **reportservertempdb** que são executados em uma instância do [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] . Você pode fazer backup dos bancos de dados **reportserver** e **reportservertempdb** que usam um dos métodos com suporte para fazer backup dos bancos de dados do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . As recomendações específicas para os bancos de dados do servidor de relatório incluem:  
  
-   Use o modelo de recuperação completo para fazer backup do banco de dados **reportserver** .  
  
-   Use o modelo de recuperação simples para fazer backup do banco de dados **reportservertempdb** .  
  
-   Você pode usar agendas de backup diferentes para cada banco de dados. O único motivo para fazer backup do **reportservertempdb** é evitar ter que recriá-lo se houver uma falha de hardware. No caso de uma falha de hardware, não é necessário recuperar os dados no **reportservertempdb**, mas você precisará da estrutura da tabela. Se você perder o **reportservertempdb**, o único modo de reverter isso é recriar o banco de dados de servidor de relatório. Se você recriar o **reportservertempdb**, é importante que você tenha o mesmo nome que o banco de dados do servidor de relatório primário.  
  
 Para obter mais informações sobre backup e recuperação dos [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bancos de dados relacionais [Fazer backup e restaurar bancos de dados do SQL Server](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).  
  
> [!IMPORTANT]  
>  Se seu servidor de relatório do [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] estiver em modo do SharePoint, haverá bancos de dados adicionais com os quais se preocupar, inclusive bancos de dados de configuração do SharePoint e o banco de dados de alertas do [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. No modo do SharePoint, três bancos de dados são criados para cada aplicativo de serviço do [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Os bancos de dados **reportserver**, **reportservertempdb**e **dataalerting** . Para obter mais informações, consulte [Aplicativos de serviço SharePoint de backup e restauração do Reporting Services](../../reporting-services/report-server-sharepoint/backup-and-restore-reporting-services-sharepoint-service-applications.md)  
  
## Fazendo backup das chaves de criptografia  
 Você deve fazer backup das chaves de criptografia ao configurar uma instalação do [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pela primeira vez. Você também deve fazer backup das chaves sempre que alterar a identidade das contas de serviço ou renomear o computador. Para saber mais, confira [Back Up and Restore Reporting Services Encryption Keys](../../reporting-services/install-windows/back-up-and-restore-reporting-services-encryption-keys.md). Para servidores de relatório do modo do SharePoint, consulte a seção “Gerenciamento de chaves” de [Manage a Reporting Services SharePoint Service Application](../../reporting-services/report-server-sharepoint/manage-a-reporting-services-sharepoint-service-application.md) (Gerenciar um aplicativo de serviço SharePoint do Reporting Services).  
  
## Fazendo backup dos arquivos de configuração  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] usa arquivos de configuração para armazenar as configurações do aplicativo. Você deve fazer backup dos arquivos quando configurar o servidor pela primeira vez e depois de implantar qualquer extensão personalizada. Os arquivos dos quais deve ser feito backup incluem:  
  
-   Rsreportserver.config  
  
-   Rssvrpolicy.config  
  
-   Rsmgrpolicy.config  
  
-   Reportingservicesservice.exe.config  
  
-   Web.config para os aplicativos Servidor de Relatório e Gerenciador de Relatórios do [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]  
  
-   Machine.config para [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]  
  
## Fazendo backup de arquivos de dados  
 Faça backup dos arquivos criados e mantidos no Designer de Relatórios e Designer de Modelos. Eles incluem arquivos de definição de relatórios (.rdl), arquivos de modelo de relatórios (.smdl), arquivos de fontes de dados compartilhadas (.rds), arquivos de exibição de dados (.dv), arquivos de fonte de dados (.ds), arquivos de projeto do servidor de relatório (.rptproj) e arquivos de solução de relatórios (.sln).  
  
 Lembre-se de fazer backup de qualquer arquivo de script (.rss) criado para as tarefas de administração ou implantação.  
  
 Verifique se você tem uma cópia de backup de todas as extensões e assemblies personalizados que você está usando.  
  
## Consulte também  
 [Banco de dados do servidor de relatório &#40;modo nativo do SSRS&#41;](../../reporting-services/report-server/report-server-database-ssrs-native-mode.md)   
 [Arquivos de configuração do Reporting Services](../../reporting-services/report-server/reporting-services-configuration-files.md)   
 [Utilitário rskeymgmt &#40;SSRS&#41;](../../reporting-services/tools/rskeymgmt-utility-ssrs.md)   
 [Copiar bancos de dados com backup e restauração](../../relational-databases/databases/copy-databases-with-backup-and-restore.md)   
 [Administrar um banco de dados de servidor de relatório &#40;modo nativo do SSRS&#41;](../../reporting-services/report-server/administer-a-report-server-database-ssrs-native-mode.md)   
 [Configurar e gerenciar chaves de criptografia &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/configure-and-manage-encryption-keys-ssrs-configuration-manager.md)  
  
  