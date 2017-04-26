---
title: "Administra&#231;&#227;o e configura&#231;&#227;o de servidor do Power Pivot na Administra&#231;&#227;o Central | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2cdbfdc5-45a9-4000-a03d-318cc7ac8fe9
caps.latest.revision: 29
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 27
---
# Administra&#231;&#227;o e configura&#231;&#227;o de servidor do Power Pivot na Administra&#231;&#227;o Central
  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] são realizadas por administradores de aplicativo de serviço do SharePoint, usando a Administração Central do SharePoint.  
  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] para SharePoint deve ser configurado antes de ser usado. Após instalar o [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] para SharePoint usando a Instalação do SQL Server, você poderá configurá-lo usando uma das seguintes abordagens:  
  
-   [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ou Ferramenta de Configuração do [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] para SharePoint 2013  
  
-   Administração Central do SharePoint  
  
-   Cmdlets do PowerShell  
  
 Todas as três abordagens entregam um servidor completamente configurado.  
  
 Esta seção inclui tarefas para configurar o software usando a Administração Central. Execute pelo menos as três tarefas da configuração exigidas anotadas na lista abaixo.  
  
> [!IMPORTANT]  
>  Para o SharePoint 2010, o SharePoint 2010 Service Pack 1 (SP1) deve ser instalado antes da configuração do [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] para SharePoint ou de um farm do SharePoint que usa um servidor de banco de dados do [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. Se você ainda não instalou o service pack; faça isso agora, antes de começar a configurar o servidor.  
  
## Benefícios de configurar o Power Pivot para SharePoint usando a Administração Central  
 A Administração Central do SharePoint é o aplicativo administrativo de um farm do SharePoint. Se você for administrador de farm, pode preferir usar uma ferramenta familiar ao adicionar uma instância do [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] para SharePoint a seu farm.  
  
 Em contraste com as Ferramentas de Configuração do [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ou cmdlets PowerShell, a Administração Central fornece páginas que especificam completamente todas as opções que você pode definir ao configurar um aplicativo ou servidor. Outras abordagens condensam o fluxo de trabalho de configuração em um número menor de etapas ou exigem conhecimento prévio de como configurar um servidor do SharePoint usando PowerShell.  
  
## Conteúdo relacionado  
 [Configuração do Power Pivot usando o Windows PowerShell](../../analysis-services/power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell.md)  
  
 [Ferramentas de Configuração do Power Pivot](../../analysis-services/power-pivot-sharepoint/power-pivot-configuration-tools.md)  
  
## Tarefas relacionadas  
  
|Link|Tipo|Descrição da tarefa|  
|----------|----------|----------------------|  
|[Implantar soluções Power Pivot para SharePoint](../../analysis-services/power-pivot-sharepoint/deploy-power-pivot-solutions-to-sharepoint.md)|Required|Esta etapa instala os arquivos da solução que adicionam arquivos de programa e páginas de aplicativo ao farm e às coleções de sites.|  
|[Criar e configurar um aplicativo de serviço do Power Pivot na Administração Central](../../analysis-services/power-pivot-sharepoint/create-and-configure-power-pivot-service-application-in-ca.md)|Required|Esta etapa provisiona o Serviço de Sistema do [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .|  
|[Ativar a Integração de Recursos do Power Pivot para as Coleções de Sites na Administração Central](../../analysis-services/power-pivot-sharepoint/activate power pivot integration for site collections in ca.md)|Required|Esta etapa ativa os recursos do [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] no nível de conjunto de sites.|  
|[Adicionar MSOLAP.5 como um provedor de dados confiável em Serviços do Excel](../../analysis-services/power-pivot-sharepoint/add-msolap-5-as-a-trusted-data-provider-in-excel-services.md)|Required|Esta etapa adiciona o provedor OLE DB do Analysis Services como um provedor de confiança em Serviços do Excel.|  
|[Atualização de dados do Power Pivot com o SharePoint 2010](http://msdn.microsoft.com/pt-br/01b54e6f-66e5-485c-acaa-3f9aa53119c9)|Recomendado|A atualização de dados é opcional, porém recomendada. Ela permite programar atualizações autônomas ao dados do [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] em pastas de trabalho do Excel publicadas.|  
|[Configurar a conta da atualização de dados autônoma Power Pivot (Power Pivot para SharePoint)](http://msdn.microsoft.com/pt-br/81401eac-c619-4fad-ad3e-599e7a6f8493)|Recomendado|Esta etapa provisiona uma conta com finalidade especial que pode ser usada para executar trabalhos de atualização de dados no servidor.|  
|[Configurar a coleta de dados de uso para o &#40;Power Pivot para SharePoint](../../analysis-services/power-pivot-sharepoint/configure-usage-data-collection-for-power-pivot-for-sharepoint.md)|Opcional|A coleta de dados de uso é configurada por padrão. Você pode usar essas etapas para modificar as configurações padrão.|  
|[Configurar o processamento dedicado de atualização de dados ou de somente consulta (Power Pivot para SharePoint)](http://msdn.microsoft.com/pt-br/5e027605-1086-4941-bb01-f315df8f829b)|Opcional|Uma instância do [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pode ser dedicada somente para trabalhos de atualização de dados ou consultas. Além disso, você pode modificar as configurações padrão para trabalhos de atualização de dados paralelos.|  
|[Configurar contas de serviço Power Pivot](../../analysis-services/power-pivot-sharepoint/configure-power-pivot-service-accounts.md)|Opcional|Explica como atualizar senhas ou alterar contas de serviço.|  
|[Conectar um aplicativo de serviço do Power Pivot a um aplicativo Web do SharePoint na Administração Central](../../analysis-services/power-pivot-sharepoint/connect power pivot service app to sharepoint web app in ca.md)|Opcional|Explica como modificar associações de serviço.|  
|[Criar um local confiável para sites do Power Pivot na Administração Central](../../analysis-services/power-pivot-sharepoint/create-a-trusted-location-for-power-pivot-sites-in-central-administration.md)|Opcional|Explica como adicionar a Galeria do [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] como um local confiável.|  
|[Configurar e exibir arquivos de log do SharePoint e registro em log de diagnóstico &#40;Power Pivot para SharePoint&#41;](../Topic/Configure%20and%20View%20SharePoint%20Log%20Files%20%20and%20Diagnostic%20Logging%20\(Power%20Pivot%20for%20SharePoint\).md)|Opcional|O log de eventos está configurado por padrão. Você pode usar essas etapas para modificar as configurações padrão.|  
|[Configurar regras de integridade do Power Pivot](../../analysis-services/power-pivot-sharepoint/configure-power-pivot-health-rules.md)|Opcional|As regras de integridade do servidor são configuradas por padrão. Você pode usar essas etapas para modificar algumas das configurações padrão.|  
|[Criar e personalizar a galeria do Power Pivot](../../analysis-services/power-pivot-sharepoint/create-and-customize-power-pivot-gallery.md)|Opcional|Para instalações que você está configurando manualmente, este procedimento explica como criar uma biblioteca da Galeria do [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] que mostra miniaturas de imagem das pastas de trabalho do [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] que ela contém.|  
|[Adicionar um tipo de conteúdo de conexão de modelo semântico de BI a uma biblioteca &#40;Power Pivot para SharePoint&#41;](../../analysis-services/power-pivot-sharepoint/add bi semantic model connection content type to library.md)|Opcional|Explica como estender uma biblioteca de documentos para dar suporte à criação de arquivos de conexão de modelo semântico de BI.|  
  
## Consulte também  
 [Instalação do Power Pivot para SharePoint 2010](http://msdn.microsoft.com/pt-br/8d47dde7-c941-4280-a934-e2fe3f9a938f)   
 [Referência de parâmetro de configuração &#40;Power Pivot para SharePoint&#41;](../../analysis-services/power-pivot-sharepoint/configuration-setting-reference-power-pivot-for-sharepoint.md)   
 [Recuperação de Desastres do Power Pivot para SharePoint](http://go.microsoft.com/fwlink/p/?LinkId=389570)  
  
  