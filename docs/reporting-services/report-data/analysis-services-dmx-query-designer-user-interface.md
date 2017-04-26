---
title: "Interface de usu&#225;rio do Designer de Consulta DMX do Analysis Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "10012"
  - "sql13.rtp.rptdesigner.dataview.asquerydesigner.f1"
helpviewer_keywords: 
  - "Analysis Services [DMX]"
  - "DMX [Analysis Services], interface do usuário"
  - "designers de consulta [DMX]"
ms.assetid: 5fd726a4-aed7-4e6c-9404-ccb2db66cf26
caps.latest.revision: 35
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 35
---
# Interface de usu&#225;rio do Designer de Consulta DMX do Analysis Services
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] oferece designers de consultas gráficas que permitem criar consultas DMX (extensões DMX) e MDX (Multidimensional Expression) para uma fonte de dados do [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Este tópico descreve o designer de consulta DMX. Para obter mais informações, consulte [Interface do usuário do Designer de Consulta MDX do Analysis Services](../../reporting-services/report-data/analysis-services-mdx-query-designer-user-interface.md).  
  
 O designer de consultas gráficas DMX tem três modos: Design, Consulta e Resultado. Para alternar entre os modos, clique com o botão direito do mouse no painel Design da Consulta e selecione o modo desejado. Cada modo contém um painel Metadados, do qual é possível arrastar membros dos cubos selecionados para criar uma consulta DMX que recupere dados de um conjunto de dados quando o relatório for processado.  
  
## Barra de ferramentas do designer de consultas DMX gráficas  
 A barra de ferramentas do designer de consulta fornece botões para ajudá-lo a criar consultas DMX por meio da interface gráfica. A tabela a seguir descreve os botões e as respectivas funções.  
  
|Botão|Description|  
|------------|-----------------|  
|**Editar como Texto**|Desabilitado para este tipo de fonte de dados.|  
|**Importar**|Importa uma consulta existente de um arquivo de definição de relatório (.rdl) no sistema de arquivos. Para obter mais informações, consulte [Conjuntos de dados inseridos e compartilhados de relatório &#40;Construtor de Relatórios e SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).|  
|![Change to MDX query view](../../reporting-services/report-data/media/rsqdicon-commandtypemdx.gif "Change to MDX query view")|Alterne para o modo do designer de consulta MDX.|  
|![Alterar para a exibição de linguagem de consulta DMX](../../reporting-services/report-data/media/rsqdicon-commandtypedmx.png "Alterar para a exibição de linguagem de consulta DMX")|Alterne para o modo do designer de consulta DMX.|  
|![Refresh result data](../../reporting-services/report-data/media/rsqdicon-refresh.gif "Refresh result data")|Atualiza metadados na fonte de dados.|  
|![Excluir](../../reporting-services/report-data/media/rsqdicon-delete.png "Excluir")|Exclui da consulta a coluna selecionada no painel Dados.|  
|![Ícone da caixa de diálogo Parâmetros de Consulta](../../reporting-services/report-data/media/iconqueryparameter.png "Ícone da caixa de diálogo Parâmetros de Consulta")|Exiba a caixa de diálogo **Parâmetros de Consulta** . Quando você atribui um valor padrão a uma variável, um parâmetro de relatório correspondente é criado no momento em que você alterna para o modo de Layout do Designer de Relatórios.|  
|![Executar a consulta](../../reporting-services/report-data/media/rsqdicon-run.png "Executar a consulta")|Prepara a consulta.|  
|![Alternar para o modo de Design](../../reporting-services/media/rsqdicon-designmode.png "Alternar para o modo de Design")|Alterna entre o modo Design e o modo Consulta. Para mudar para a exibição de resultado, clique com o botão direito do mouse no painel Design e escolha **Resultado**.|  
  
## Designer de consultas DMX gráficas no modo de Design  
 Quando você edita um conjunto de dados que usa uma fonte de dados do [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sem cubos válidos, mas com modelos de mineração válidos, o designer de consultas gráficas é aberto no modo de Design. A figura a seguir mostra os painéis do modo Design.  
  
 ![Designer de consulta DMX do Analysis Services, modo de design](../../reporting-services/report-data/media/rsqd-dsawas-dmx-designmode.gif "Designer de consulta DMX do Analysis Services, modo de design")  
  
 A tabela a seguir descreve a função de cada painel.  
  
|Painel|Função|  
|----------|--------------|  
|Painel Designer da Consulta|Use as caixas de diálogo **Modelo de Mineração** e **Selecionar Tabela de Entrada** para criar a consulta DMX.|  
|Painel Grade|Para cada linha da grade, use a lista suspensa **Origem** para selecionar uma função ou expressão e escolha campos, grupos e critérios ou argumentos a serem usados na consulta DMX. Para ver o texto da consulta DMX gerado pelas seleções que você fez, clique no botão **Modo de Design** na barra de ferramentas.|  
  
 Para executar a consulta DMX e mostrar os resultados no painel Resultado, clique com o botão direito do mouse no painel Design da Consulta e selecione **Resultado**.  
  
## Designer de consultas DMX gráficas no modo de Consulta  
 Para mudar o designer de consultas gráficas para o modo de Consulta, clique no botão **Modo de Design** da barra de ferramentas ou clique com o botão direito do mouse na superfície de design de consulta e, no menu de atalho, escolha **Consulta**. Use este modo para inserir o texto DMX diretamente no painel Consulta.  
  
 A figura a seguir mostra os painéis do modo Consulta.  
  
 ![Designer de consulta DMX do Analysis Services, exibição de consulta](../../reporting-services/report-data/media/rsqd-dsawas-dmx-querymode.gif "Designer de consulta DMX do Analysis Services, exibição de consulta")  
  
 A tabela a seguir descreve a função de cada painel.  
  
|Painel|Função|  
|----------|--------------|  
|Painel Designer da Consulta|Use as caixas de diálogo **Modelo de Mineração** e **Selecionar Tabela de Entrada** para criar a consulta DMX.|  
|Painel Consulta|Exiba ou edite o texto da consulta DMX diretamente no painel. As alterações feitas no texto da consulta DMX não serão mantidas se você voltar para o modo de **Design**.|  
  
 Para executar a consulta DMX e mostrar os resultados no painel Resultado, clique com o botão direito do mouse no painel Design da Consulta e selecione **Resultado**.  
  
## Designer de consultas DMX gráficas no modo de Resultado  
 Para exibir o modo Resultado, clique com o botão direito do mouse na superfície de design de consulta e escolha **Resultado** no menu de atalho. Quando você alternar para o modo de Resultado, a consulta DMX será executada automaticamente.  
  
 A figura a seguir mostra o designer de consulta no modo Resultado.  
  
 ![Designer de consulta DMX do Analysis Services, exibição de resultado](../../reporting-services/report-data/media/rsqd-dsawas-dmx-resultmode.gif "Designer de consulta DMX do Analysis Services, exibição de resultado")  
  
 Para voltar aos modos de Design ou de Consulta, clique com o botão direito do mouse no painel Resultado e selecione **Design** ou **Consulta**.  
  
## Consulte também  
 [Definir parâmetros no Designer de Consulta MDX do Analysis Services &#40;Construtor de Relatórios e SSRS&#41;](../../reporting-services/report-data/define parameters in the mdx query designer for analysis services.md)   
 [Criar um conjunto de dados compartilhado ou um conjunto de dados inserido &#40;Construtor de Relatórios e SSRS&#41;](../../reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)   
 [Tipo de conexão Analysis Services para DMX &#40;SSRS&#41;](../../reporting-services/report-data/analysis-services-connection-type-for-dmx-ssrs.md)   
 [Recuperar dados de um modelo de Data Mining &#40;DMX&#41; &#40;SSRS&#41;](../../reporting-services/report-data/retrieve-data-from-a-data-mining-model-dmx-ssrs.md)   
 [Arquivo de configuração RSReportDesigner](../../reporting-services/report-server/rsreportdesigner-configuration-file.md)   
 [Tipo de conexão Analysis Services para MDX &#40;SSRS&#41;](../../reporting-services/report-data/analysis-services-connection-type-for-mdx-ssrs.md)   
 [Tipo de conexão Analysis Services para DMX &#40;SSRS&#41;](../../reporting-services/report-data/analysis-services-connection-type-for-dmx-ssrs.md)  
  
  