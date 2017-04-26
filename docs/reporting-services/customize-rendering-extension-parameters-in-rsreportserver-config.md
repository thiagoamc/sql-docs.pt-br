---
title: "Personalizar par&#226;metros de extens&#227;o de renderiza&#231;&#227;o em RSReportServer.config | Microsoft Docs"
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
  - "opções de configuração [Reporting Services]"
  - "Configurações de DeviceInfo"
  - "extensões de renderização [Reporting Services], substituindo comportamentos"
  - "parâmetros [Reporting Services], renderização de relatório"
  - "substituindo comportamento de renderização de relatório"
  - "extensões [Reporting Services], extensões"
ms.assetid: 3bf7ab2b-70bb-41c8-acda-227994d15aed
caps.latest.revision: 31
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 31
---
# Personalizar par&#226;metros de extens&#227;o de renderiza&#231;&#227;o em RSReportServer.config
  Você pode especificar parâmetros de extensão de renderização no arquivo de configuração RSReportServer para substituir o comportamento de renderização de relatório padrão para os relatórios executados em um servidor de relatórios do [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Os parâmetros de extensão de renderização podem ser modificados com os seguintes objetivos:  
  
-   Alterar o modo de exibição do nome da extensão de renderização na lista Exportar da barra de ferramentas de relatórios (por exemplo, alterar “arquivo da Web” para “MHTML”) ou localizar o nome em um idioma diferente.  
  
-   Criar várias instâncias da mesma extensão de renderização para oferecer suporte a diferentes opções de apresentação de relatório (por exemplo, uma versão do modo retrato e paisagem da extensão de renderização Imagem).  
  
-   Alterar os parâmetros padrão da extensão de renderização para usar valores diferentes (por exemplo, a extensão de renderização Imagem usa TIFF como o formato de saída padrão; se desejar, você pode modificar os parâmetros de extensão para usar EMF).  
  
 A alteração dos parâmetros de extensão de renderização afeta somente as operações de renderização no servidor de relatórios. Não é possível substituir as configurações de extensão de renderização ao visualizar relatórios no Designer de Relatórios.  
  
 A especificação de parâmetros de extensão de renderização nos arquivos de configuração afeta as extensões de renderização globalmente. As definições dos arquivos de configuração são usadas no lugar de valores padrão sempre que uma extensão de renderização específica é usada. Se desejar definir parâmetros de extensão de renderização para um relatório ou operação de renderização específico, especifique as informações do dispositivo programaticamente usando o método <xref:ReportExecution2005.ReportExecutionService.Render%2A> ou especificando configurações de informações de dispositivo em uma URL de relatório. Para obter mais informações sobre como especificar configurações de informações de dispositivo para uma operação de renderização e como exibir a lista completa de configurações de informações de dispositivo, consulte [Como passar configurações de informações de dispositivos para extensões de renderização](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).  
  
## Localizando e modificando RSReportServer.config  
 As configurações de formatos de saída de relatório são especificadas como parâmetros de extensão de renderização no arquivo RSReportServer.config. Para especificar parâmetros de extensão de renderização nos arquivos de configuração, você deve saber como definir estruturas XML que definem parâmetros de renderização. Há duas estruturas XML que podem ser modificadas:  
  
-   O elemento **OverrideNames** define o nome para exibição e a linguagem da extensão de renderização.  
  
-   A estrutura XML **DeviceInfo** define as configurações de informações de dispositivo que são usadas por uma extensão de renderização. A maioria dos parâmetros de extensão de renderização é especificada como configurações de informações de dispositivo.  
  
 Você pode usar um editor de texto para modificar o arquivo. O arquivo RSReportServer.config pode ser localizado na pasta \Reporting Services\Report Server\Bin. Para obter mais informações sobre como modificar arquivos de configuração, consulte [Modificar um arquivo de configuração do Reporting Services &#40;RSreportserver.config&#41;](../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md).  
  
## Alterando o nome para exibição  
 O nome para exibição de uma extensão de renderização aparece na lista Exportar da barra de ferramentas de relatório. Exemplos de nomes para exibição padrão incluem arquivos da Web, TIFF e Acrobat (PDF). Você pode substituir o nome para exibição padrão por um valor personalizado especificando o elemento **OverrideNames** nos arquivos de configuração. Além disso, se duas instâncias de uma única extensão de renderização forem definidas, use o elemento **OverrideNames** para diferenciar cada instância na lista Exportar.  
  
 Como os nomes para exibição são localizados, defina o atributo **Language** se estiver substituindo o nome padrão por um valor personalizado. Caso contrário, qualquer nome especificado será ignorado. O valor de idioma definido deve ser válido para o computador do servidor de relatórios. Por exemplo, se o servidor de relatórios for executado em um sistema operacional francês, especifique "fr-FR" como o valor do atributo.  
  
 O exemplo a seguir ilustra como fornecer um nome personalizado em um servidor de relatórios em inglês:  
  
```  
<Extension Name="XML" Type="Microsoft.ReportingServices.Rendering.DataRenderer.XmlDataReport,Microsoft.ReportingServices.DataRendering">  
   <OverrideNames>  
     <Name Language="en-US">My Custom Display Name for XML Rendering</Name>  
   </OverrideNames>  
</Extension>  
```  
  
## Alterando as configurações de informações de dispositivo  
 Para modificar as configurações padrão de informações de dispositivo que são usadas por uma extensão de renderização que já está implantada no servidor de relatórios, digite a estrutura XML **DeviceInfo** nos arquivos de configuração. Todas as extensões de renderização oferecem suporte para configurações de informações de dispositivo que são exclusivas na extensão em questão. Para exibir a lista completa de informações do dispositivo, consulte [Como passar configurações de informações de dispositivos para extensões de renderização](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).  
  
 O exemplo a seguir ilustra a estrutura XML e a sintaxe que modificam as configurações padrão da extensão de renderização Imagem:  
  
```  
<Render>  
    <Extension Name="IMAGE (EMF)" Type="Microsoft.ReportingServices.Rendering.ImageRenderer.ImageRenderer,Microsoft.ReportingServices.ImageRendering">  
        <OverrideNames>  
            <Name Language="en-US">Image (EMF)</Name>  
        </OverrideNames>  
        <Configuration>  
            <DeviceInfo>  
                <ColorDepth>32</ColorDepth>  
                <DpiX>300</DpiX>  
                <DpiY>300</DpiY>  
                <OutputFormat>EMF</OutputFormat>  
            </DeviceInfo>  
        </Configuration>  
    </Extension>  
</Render>  
```  
  
## Configurando várias entradas para uma extensão de renderização  
 Você pode criar várias instâncias da mesma extensão de renderização para oferecer suporte para opções de apresentação de relatório diferentes. Cada instância definida pode ter uma combinação diferente de valores de parâmetro. Ao definir novas instâncias de uma extensão de renderização existente, faça o seguinte:  
  
-   Especifique um nome exclusivo para a extensão.  
  
     Cada instância deve ter um valor exclusivo para o atributo **Name** . O exemplo a seguir usa os nomes "IMAGE (EMF Landscape)" e "IMAGE (EMF Portrait)" para diferenciar as duas instâncias.  
  
     Tenha cuidado ao alterar o nome de uma extensão de renderização que já está implantada. Os desenvolvedores que especificam extensões de renderização programaticamente usam o nome da extensão para identificar a instância que deve ser usada em uma operação de renderização específica. Se estiver executando aplicativos personalizados do [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] no servidor de relatórios, verifique se o desenvolvedor sabe se está modificando o nome de uma extensão existente ou adicionando uma nova extensão.  
  
-   Especifique um nome para exibição exclusivo de forma que usuários possam entender as diferenças de cada formato de saída.  
  
     Se estiver configurando várias versões da mesma extensão, dê a cada versão um nome exclusivo fornecendo um valor para **OverrideNames**. Caso contrário, todas as versões da extensão parecerão ter o mesmo nome na lista opções Exportar na barra de ferramentas de relatório.  
  
 O exemplo a seguir ilustra como usar a extensão de renderização Imagem padrão (que produz a saída TIFF) para gerar EMF no modo Retrato, junto com uma segunda instância que gera relatórios em EMF no modo Paisagem. Observe que cada nome de extensão é exclusivo. Ao testar esse exemplo, escolha relatórios que não contenham recursos interativos como opções de mostrar/ocultar, matrizes ou links de detalhamentos (os recursos interativos não funcionam na extensão de renderização Imagem):  
  
```  
<Render>  
    <Extension Name="IMAGE (EMF Landscape)" Type="Microsoft.ReportingServices.Rendering.ImageRenderer.ImageRenderer,Microsoft.ReportingServices.ImageRendering">  
        <OverrideNames>  
            <Name Language="en-US">EMF in Landscape Mode</Name>  
        </OverrideNames>  
        <Configuration>  
            <DeviceInfo>  
                <OutputFormat>EMF</OutputFormat>  
                <PageHeight>8.5in</PageHeight>  
                <PageWidth>11in</PageWidth>  
            </DeviceInfo>  
        </Configuration>  
    </Extension>  
    <Extension Name="IMAGE (EMF Portrait)" Type="Microsoft.ReportingServices.Rendering.ImageRenderer.ImageRenderer,Microsoft.ReportingServices.ImageRendering">  
        <OverrideNames>  
            <Name Language="en-US">EMF in Portait Mode</Name>  
        </OverrideNames>  
        <Configuration>  
            <DeviceInfo>  
                <OutputFormat>EMF</OutputFormat>  
                <PageHeight>11in</PageHeight>  
                <PageWidth>8.5in</PageWidth>  
            </DeviceInfo>  
        </Configuration>  
    </Extension>  
</Render>  
```  
  
## Consulte também  
 [Arquivo de Configuração RsReportServer.config](../reporting-services/report-server/rsreportserver-config-configuration-file.md)   
 [Arquivo de configuração RSReportDesigner](../reporting-services/report-server/rsreportdesigner-configuration-file.md)   
 [Configurações das informações do dispositivo CSV](../reporting-services/csv-device-information-settings.md)   
 [Configurações das informações do dispositivo do Excel](../reporting-services/excel-device-information-settings.md)   
 [Configurações de informações do dispositivo HTML ](../reporting-services/html-device-information-settings.md)   
 [Configurações das informações do dispositivo do Image](../reporting-services/image-device-information-settings.md)   
 [Configurações das informações do dispositivo MHTML](../reporting-services/mhtml-device-information-settings.md)   
 [Configurações de informações do dispositivo PDF ](../reporting-services/pdf-device-information-settings.md)   
 [Configurações de informações do dispositivo XML](../reporting-services/xml-device-information-settings.md)  
  
  