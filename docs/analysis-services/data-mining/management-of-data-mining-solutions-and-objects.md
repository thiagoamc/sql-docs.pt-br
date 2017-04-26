---
title: "Gerenciamento de solu&#231;&#245;es de minera&#231;&#227;o de dados e objetos | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "mineração de dados [Analysis Services], gerenciando"
  - "gerenciando modelos de mineração"
ms.assetid: 06fc61dd-925c-4347-8677-7046ee5d2f6f
caps.latest.revision: 26
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 26
---
# Gerenciamento de solu&#231;&#245;es de minera&#231;&#227;o de dados e objetos
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] fornece ferramentas de cliente que você pode usar para gerenciar estruturas de mineração e modelos de mineração existentes. Esta seção descreve as operações de gerenciamento que você pode executar usando cada ambiente.  
  
 Além dessas ferramentas, você pode gerenciar objetos de mineração de dados programaticamente, usando AMO, ou usar outros clientes que se conectam a um banco de dados do [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], como os Suplementos de Mineração de Dados para [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 2007.  
  
## Nesta seção  
 [Movendo objetos de mineração de dados](../../analysis-services/data-mining/moving-data-mining-objects.md)  
  
 [Requisitos e considerações de processamento &#40;Mineração de dados&#41;](../../analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
 [Usando o SQL Server Profiler para monitorar a mineração de dados &#40;Analysis Services – Mineração de dados&#41;](../../analysis-services/data-mining/using-sql-server-profiler-to-monitor-data-mining-analysis-services-data-mining.md)  
  
## Localização de objetos de mineração de dados  
 As estruturas e os modelos de mineração que foram processados são armazenados em uma instância do [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 Se você criar uma conexão com um banco de dados do [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] no modo **Imediato** quando desenvolver seus objetos de mineração de dados, qualquer objeto que for criado será adicionado imediatamente ao servidor como trabalho. Entretanto, se você criar objetos de mineração de dados no modo **Offline** , que é o padrão quando trabalha no [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], os objetos de mineração criados serão apenas contêineres de metadados, até serem implantados em uma instância do [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Assim, sempre que você fizer uma alteração em um objeto, deverá reimplantar o objeto no servidor [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Para obter mais informações sobre a arquitetura de mineração de dados, consulte [Arquitetura física &#40;Analysis Services – Mineração de dados&#41;](../../analysis-services/data-mining/physical-architecture-analysis-services-data-mining.md).  
  
> [!NOTE]  
>  Alguns clientes, como os Suplementos de Mineração de Dados para [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 2007, também permitem criar modelos e estruturas de mineração de sessão que usam uma conexão com uma instância, mas armazenam a estrutura e os modelos de mineração no servidor somente durante a sessão. Também é possível gerenciar esses modelos através do cliente, da mesma forma que estruturas e modelos armazenados no banco de dados [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , porém os objetos não persistem depois de desconectar da instância do [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
## Gerenciando objetos de mineração de dados em Ferramentas de Dados do SQL Server  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] oferece recursos que permitem criar, navegar e editar objetos de mineração de dados com facilidade.  
  
 Os links a seguir fornecem informações sobre como modificar objetos de mineração de dados usando o [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]:  
  
-   [Editar a exibição da fonte de dados usada para a Estrutura de Mineração](../../analysis-services/data-mining/edit-the-data-source-view-used-for-a-mining-structure.md)  
  
-   [Alterar as propriedades de uma estrutura de mineração](../../analysis-services/data-mining/change-the-properties-of-a-mining-structure.md)  
  
-   [Alterar as propriedades de um modelo de mineração](../../analysis-services/data-mining/change-the-properties-of-a-mining-model.md)  
  
-   [Exibir ou alterar sinalizadores de modelagem &#40;Mineração de dados&#41;](../../analysis-services/data-mining/view-or-change-modeling-flags-data-mining.md)  
  
-   [Exibir ou alterar parâmetros do algoritmo](../../analysis-services/data-mining/view-or-change-algorithm-parameters.md)  
  
 Normalmente você usará o [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] como uma ferramenta para desenvolver novos projetos e adicionar a projetos existentes e, em seguida, gerenciar projetos e objetos que foram implantados usando ferramentas como o [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 No entanto, você pode modificar diretamente objetos que já estão implantados em uma instância do ssASnoversion usando a opção **Immediate** e conectando ao servidor em modo Online. Para obter mais informações, consulte [Connect in Online Mode to an Analysis Services Database](../../analysis-services/multidimensional-models/connect-in-online-mode-to-an-analysis-services-database.md).  
  
> [!WARNING]  
>  Todas as alterações em uma estrutura ou um modelo de mineração, inclusive alterações em metadados como um nome ou uma descrição, requerem que a estrutura ou o modelo sejam reprocessados.  
  
 Se você não tiver o arquivo de solução que foi usado para criar o projeto ou objetos de mineração de dados, poderá importar o projeto existente do servidor usando o Assistente de Importação do Analysis Services, fazer modificações nos objetos e, em seguida, reimplantar usando a opção **Incremental** . Para obter mais informações, consulte [Importar um projeto de mineração de dados usando o Assistente de Importação do Analysis Services](../../analysis-services/data-mining/import-a-data-mining-project-using-the-analysis-services-import-wizard.md).  
  
## Gerenciando objetos de mineração de dados no SQL Server Management Studio  
 No [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], é possível fazer scripts, processar ou excluir estruturas e modelos de mineração. Você pode exibir apenas um conjunto limitado de propriedades usando o Pesquisador de Objetos; entretanto, é possível exibir metadados adicionais sobre modelos de mineração abrindo a janela **Consultas DMX** e selecionando uma estrutura de mineração.  
  
-   [Criar uma consulta DMX no SQL Server Management Studio](../../analysis-services/data-mining/create-a-dmx-query-in-sql-server-management-studio.md)  
  
## Gerenciando programaticamente objetos de mineração de dados  
 Você pode criar, alterar, processar e excluir objetos de mineração de dados usando as linguagens de programação a seguir. Cada linguagem é designada para tarefas diferentes e, por isso, pode haver restrições no tipo de operações que você pode executar. Por exemplo, algumas propriedades dos objetos de mineração de dados não podem ser alteradas com o uso de extensões DMX; você deve utilizar XMLA ou AMO.  
  
### Objetos de Gerenciamento de Análise (AMO)  
 AMO (Objetos de Gerenciamento de Análise) é um modelo de objeto criado com base em XMLA que lhe proporciona o controle total sobre objetos de mineração de dados. Usando o AMO, você pode criar, implantar e monitorar estruturas e modelos de mineração  
  
-   [Conceitos e modelo de objeto AMO](../../analysis-services/multidimensional-models/analysis-management-objects/amo-concepts-and-object-model.md)  
  
-   <xref:Microsoft.AnalysisServices>  
  
 **Restrições:** nenhuma.  
  
### Extensões DMX  
 Extensões DMX podem ser usadas com outras interfaces de comando como [!INCLUDE[vstecado](../../includes/vstecado-md.md)] ou ADOMD.Net para criar, excluir e consultar estruturas e modelos de mineração.  
  
-   [Instruções de definição de dados de extensões DMX &#40;extensões DMX&#41;](../Topic/Data%20Mining%20Extensions%20\(DMX\)%20Data%20Definition%20Statements.md)  
  
 **Restrições:** algumas propriedades não podem ser alteradas usando DMX.  
  
### XML for Analysis (XMLA)  
 XML for Analysis (XMLA) é a linguagem de definição de dados para todos os Analysis Services. O XMLA dá a você o controle sobre a maioria dos objetos de mineração de dados e operações de servidor. Todas as operações de gerenciamento entre o cliente e o servidor podem ser executadas com o uso de XMLA. Para sua conveniência, é possível usar a ASSL ([!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Scripting Linguagem) para encapsular o XML.  
  
 **Restrições:** [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] gera algumas instruções XMLA que têm suporte apenas para uso interno e não podem ser usadas em scripts XML DDL.  
  
## Consulte também  
 [Documentação do desenvolvedor do Analysis Services](../../analysis-services/analysis-services-developer-documentation.md)  
  
  