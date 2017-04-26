---
title: "Web Part do Visualizador de Relat&#243;rios em um site do SharePoint | Microsoft Docs"
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
  - "integração com o SharePoint [Reporting Services], exibindo relatórios"
  - "Web Parts [Reporting Services]"
  - "integração com o SharePoint [Reporting Services], Web Parts"
  - "Web Part do Visualizador de Relatórios [Reporting Services]"
ms.assetid: b6341a73-172f-4632-a9e9-cc79fed3f36b
caps.latest.revision: 13
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 13
---
# Web Part do Visualizador de Relat&#243;rios em um site do SharePoint
  A Web Part do Visualizador de Relatórios é uma Web Part personalizada instalada pelo suplemento [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] para produtos SharePoint. Você pode usar a Web Part para exibir, navegar, imprimir e exportar relatórios em um servidor de relatório configurado para ser executado no modo integrado do SharePoint. A Web Part do Visualizador de Relatórios está associada a arquivos de definição de relatório (.rdl) processados por um servidor de relatório do [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Você não pode usar isso com outros documentos de relatório criados em outros produtos de software.  
  
 Para instalar a Web Part, você deve executar a Instalação do suplemento [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Você não deve instalar ou desinstalar a Web Part independentemente. Isso é parte do suplemento e pode ser instalado somente pelo pacote de instalação do suplemento. O nome de arquivo da Web Part do Visualizador de Relatórios é ReportViewer.dwp. Ela está localizada na pasta Arquivos de Programas\Arquivos Comuns\Microsoft Shared\web server extensions\12\template\features\reportserver e não deve ser movida para outras pastas.  
  
 Para usar a Web Part, você deve ter o instalado e configurado o suplemento [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] e configurado o servidor de relatório para a integração com o SharePoint. Você deve ter também relatórios para serem exibidos no visualizador. Só é possível abrir relatórios que estejam em uma biblioteca, pasta de bibliotecas, histórico de relatórios ou em um vínculo de uma Web Part de Biblioteca para uma Web Part do Visualizador de Relatórios. Você não pode abrir relatórios salvos como anexos de um item em uma lista personalizada.  
  
 Você pode definir propriedades na Web Part do Visualizador de Relatórios para controlar a aparência da barra de ferramentas e das áreas de exibição e para vincular a Web Part a um relatório específico. O Visualizador de Relatórios mostra um relatório vinculado de maneira explícita a ele ou mostra todos os arquivos .rdl abertos.  
  
 Não é possível vincular diversos relatórios a uma única instância do Visualizador de Relatórios, mas se quiser agrupar relatórios juntos, você pode criar um painel de controle ou uma página Web Part que insira várias instâncias Web Part do Visualizador de Relatórios em uma única página.  
  
 A Web Part inclui uma área de exibição, uma barra de ferramentas, uma área que pode ser recolhida para definir credenciais e parâmetros, e propriedades. A imagem a seguir mostra a Web Part com o relatório de exemplo Vendas da Empresa e as opções de exportação que você pode selecionar em uma barra de ferramentas.  
  
 ![Web Part do Visualizador de Relatórios](../../reporting-services/report-server-sharepoint/media/rs-sharepointrvwebpart.gif "Web Part do Visualizador de Relatórios")  
  
## Componentes da Web Part  
 A área de exibição mostra um relatório em HTML. Dependendo de como a Web Part está configurada, a área de exibição pode ser maximizada para mostrar o relatório em modo de página inteira ou pode compartilhar o espaço disponível com painéis adjacentes e uma barra de ferramentas.  
  
 A barra de ferramentas fornece recursos de navegação na página, de pesquisa, de zoom e de exportação, para que você possa exibir um relatório em outro formato de aplicativo. Ela também fornece funcionalidade de impressão opcional, oferecendo saídas impressas paginadas para relatórios HTML e a capacidade de alterar as configurações de layout de página e de margens. As opções **Abrir com o Construtor de Relatórios, Assinar**, **Exportar** e **Imprimir** são fornecidas no menu **Ações** da barra de ferramentas. Os controles de navegação de página e zoom estão diretamente na barra de ferramentas.  
  
> [!NOTE]  
>  Você não pode personalizar a barra de ferramentas a menos que escreva um código para isso, mas pode definir as propriedades para ocultar todos ou alguns controles.  
  
### Ação Exportar na barra de ferramentas Relatório  
 **Exportar** no menu **Ações** mostra formatos de aplicativo associados a extensões de renderização implantadas em um servidor de relatório. Para determinar a disponibilidade de um formato específico, você pode adicionar ou remover uma extensão de renderização no servidor de relatórios ou pode modificar definições de configuração para remover um formato de exportação específico da lista. Você também pode especificar definições de configuração no servidor de relatórios para controlar os formatos disponíveis. Você pode modificar o comportamento padrão de um formato específico adicionando e modificando definições de configuração para essa extensão de renderização.  
  
### Ação Imprimir na barra de ferramentas Relatório  
 **Imprimir** no menu **Ações** é a funcionalidade de impressão personalizada fornecida por [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Ao clicar em **Imprimir**, um controle de impressão ActiveX do cliente é baixado na o computador cliente. Na maioria dos casos, o usuário que clica em **Imprimir** deve ter permissões de Administrador no computador local. É uma prática comum restringir downloads de controles ActiveX apenas aos usuários com permissões de Administrador. Você pode usar a Administração Central do SharePoint para habilitar ou desabilitar o download do controle de impressão do cliente.  
  
### Ação Localizar na barra de ferramentas Relatório  
 **Localizar** no menu **Ações** fornece um modo de passar a um local de destino no relatório. Você pode procurar conteúdo em um relatório digitando uma palavra ou frase que você quer localizar. O valor máximo de um termo de pesquisa é de 256 caracteres. Quando sua pesquisa localiza um valor correspondente no relatório, o foco é movido para a parte do relatório que contém esse valor.  
  
 Ao digitar um valor de pesquisa, digite-o como você espera que ele apareça no relatório. Não digite uma pergunta, por exemplo, "qual é o lucro médio deste mês", a menos que espere que cada palavra da frase esteja no relatório.  
  
 Você só pode procurar um termo ou valor de cada vez. Não é possível usar operadores de pesquisa (por exemplo, **AND** ou **OR**) ou símbolos e caracteres curinga. Você não pode realizar uma pesquisa em uma seção cruzada dos dados (por exemplo, procurando as vendas líquidas de um determinado produto em um dado mês). Para esse tipo de análise, use o Construtor de Relatórios para criar relatórios de clickthrough.  
  
 As configurações de segurança de modelo e banco de dados que restringem o acesso aos dados do relatório se aplicam às operações de pesquisa. Se você estiver procurando um valor em um relatório de clickthrough que use um modelo como fonte de dados e não tiver acesso a uma parte do modelo, os dados representados por essa parte do modelo serão excluídos da pesquisa.  
  
### Painéis para especificar credenciais e parâmetros  
 **Credenciais** e **Parâmetros** são painéis que aparecem ao lado da área de exibição. O painel **Credenciais** aparece quando a conexão da fonte de dados do relatório é configurada para solicitar ao usuário uma conta e senha com direitos de acesso à fonte de dados. O painel **Parâmetros** aparece quando o relatório aceita que o usuário insira parâmetros definidos no relatório.  
  
### Configurando propriedades na Web Part do Visualizador de Relatórios  
 As propriedades na Web Part incluem as propriedades personalizadas específicas ao Visualizador de Relatórios e propriedades gerais que você pode definir para qualquer Web Part. Para obter mais informações, consulte [Personalizar a Web Part do Visualizador de Relatórios](../../reporting-services/report-server-sharepoint/customize-the-report-viewer-web-part.md).  
  
 Os relatórios são abertos em modo de página inteira por padrão. O modo de página inteira mostra a barra de ferramentas, que fornece funcionalidades de navegação de página e pesquisa, entre outras. Você pode personalizar a Web Part para alterar sua aparência ou seu comportamento padrão.  
  
## Consulte também  
 [Instalar ou desinstalar o suplemento Reporting Services para SharePoint](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)   
 [Adicionar a Web Part do Visualizador de Relatórios a uma página da Web &#40;Reporting Services no modo integrado do SharePoint&#41;](../../reporting-services/report-server-sharepoint/add the report viewer web part to a web page.md)  
  
  