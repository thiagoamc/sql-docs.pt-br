---
title: "Designer SSIS | Microsoft Docs"
ms.custom: ""
ms.date: "08/31/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.controlflowwindow.f1"
  - "sql13.dts.designer.dataflowwindow.f1"
  - "sql13.dts.designer.eventhandlerwindow.f1"
  - "sql13.dts.designer.treeview.f1"
  - "sql13.dts.designer.progress.f1"
  - "sql13.dts.designer.connectionstray.f1"
helpviewer_keywords: 
  - "SQL Server Integration Services, Designer SSIS"
  - "Business Intelligence Development Studio, Integration Services em"
  - "ferramentas [Integration Services], Designer SSIS"
  - "SSIS, Designer SSIS"
  - "Designer SSIS, sobre o Designer SSIS"
  - "Integration Services, Designer SSIS"
ms.assetid: 006d68ea-1b5c-4c1e-8079-3910288e012c
caps.latest.revision: 59
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 58
---
# Designer SSIS
  [!INCLUDE[ssIS](../includes/ssis-md.md)] é uma ferramenta gráfica que pode ser usada para criar e manter pacotes do [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . [!INCLUDE[ssIS](../includes/ssis-md.md)] está disponível no [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] como parte de um projeto do [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
 Você pode utilizar o Designer [!INCLUDE[ssIS](../includes/ssis-md.md)] para executar as seguintes tarefas:  
  
-   Criar o fluxo de controle em um pacote.  
  
-   Criar o fluxo de dados em um pacote.  
  
-   Adicionar manipuladores de eventos ao pacote e a objetos do pacote.  
  
-   Exibir o conteúdo do pacote.  
  
-   Em tempo de execução, exibir o progresso da execução do pacote.  
  
 O diagrama a seguir exibe o [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer e a janela **Caixa de Ferramentas** .  
  
 ![Instantâneo do designer de SSIS e da caixa de ferramentas](../integration-services/media/denali-designerandtoolbox.gif "Instantâneo do designer de SSIS e da caixa de ferramentas")  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] inclui caixas de diálogo e janelas adicionais para proporcionar maior funcionalidade aos pacotes e o [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] fornece janelas e caixas de diálogo para configurar o ambiente de desenvolvimento e trabalhar com pacotes. Para obter mais informações, consulte [Interface do usuário do Integration Services](../integration-services/integration-services-user-interface.md).  
  
 [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer não tem dependência do serviço [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , o serviço que gerencia e monitora pacotes, e não é necessário que o serviço esteja sendo executado para criar ou modificar pacotes no [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer. Entretanto, se você parar o serviço enquanto o [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer estiver aberto, não poderá mais abrir as caixas de diálogo que o [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer fornece e poderá receber a mensagem de erro "RPC server is unavailable". Para redefinir o [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer e continuar a trabalhar com o pacote, você deve fechar o designer, sair do [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]e reabrir o [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], o projeto do [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] e o pacote.  
  
## Desfazer e refazer  
 É possível desfazer e refazer até 20 ações no [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer. Para um pacote, a opção desfazer/refazer está disponível nas guias **Fluxo de Controle**, **Fluxo de Dados**, **Manipuladores de Eventos** e **Parâmetros**, bem como na janela **Variáveis**. Para um projeto, a opção desfazer/refazer está disponível na janela **Parâmetros do Projeto**.  
  
 Não é possível desfazer/refazer alterações na nova **Caixa de Ferramentas do SSIS**.  
  
 Quando você fizer alterações em um componente usando o editor de componente, desfaz e refaz as alterações como um conjunto em vez de desfazer e refazer alterações individuais. O conjunto de alterações aparece como uma única ação na lista suspensa de desfazer e refazer.  
  
 Para desfazer uma ação, clique no botão desfazer de barra de ferramentas, item de menu **Editar/Desfazer** ou pressione CTRL+Z. Para refazer uma ação, clique no botão refazer da barra de ferramentas, item de menu **Editar/Refazer** ou pressione CTRL+Y. Você pode desfazer e refazer várias ações, clicando na seta ao lado do botão de barra de ferramentas, realçando várias ações na lista suspensa e clicando na lista.  
  
## Partes do Designer SSIS  
 [!INCLUDE[ssIS](../includes/ssis-md.md)] tem cinco guias permanentes: para a criação de fluxos de controle de pacotes, de fluxos de dados, de parâmetros e de manipuladores de eventos e uma guia para a exibição do conteúdo de um pacote. Em tempo de execução, será mostrada uma sexta guia que exibe o progresso da execução de um pacote enquanto ele é executado, bem como os resultados da execução após o término.  
  
 Além disso, o [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer inclui a área Gerenciadores de Conexões para adicionar e configurar os gerenciadores de conexões usados por um pacote para se conectar com os dados.  
  
### Guia Fluxo de Controle  
 Você pode criar o fluxo de controle em um pacote na superfície de design da guia **Fluxo de Controle** . Arraste itens da **Caixa de Ferramentas** para a superfície de design e conecte-os em um fluxo de controle clicando no ícone do item e arrastando a seta de um item para outro.  
  
 Para obter mais informações, consulte [Control Flow](../integration-services/control-flow/control-flow.md).  
  
### Guia Fluxo de Dados  
 Se um pacote contém uma tarefa de fluxo de dados, você pode adicionar fluxos de dados a ele. Você pode criar fluxos de dados em um pacote na superfície de design da guia **Fluxo de Dados** . Arraste itens da **Caixa de Ferramentas** para a superfície de design e conecte-os em um fluxo de dados clicando no ícone do item e arrastando a seta de um item para outro.  
  
 Para obter mais informações, consulte [Data Flow](../integration-services/data-flow/data-flow.md).  
  
### Guia Parâmetros  
 Os parâmetros do Integration Services (SSIS) permitem atribuir valores às propriedades nos pacotes em tempo de execução do pacote. Você pode criar parâmetros de projeto em nível de projeto e parâmetros de pacote em nível de pacote. Os parâmetros do projeto são usados para fornecer uma entrada externa que o projeto recebe para um ou mais pacotes no projeto. Os parâmetros do pacote permitem modificar a execução do pacote sem a necessidade de editar e reimplantar o pacote. Esta guia permite gerenciar parâmetros de pacote.  
  
 Para obter mais informações sobre parâmetros, consulte [Parâmetros do SSIS (Integration Services)](https://msdn.microsoft.com/library/hh213214.aspx).  
  
> **IMPORTANTE:**  Os parâmetros estão disponíveis apenas para projetos desenvolvidos para o modelo de implantação de projeto. Portanto, você só verá a guia Parâmetros para pacotes que fazem parte de um projeto configurado para usar o modelo de implantação de projeto.  
  
### Guia Manipuladores de Eventos  
 Você pode criar os eventos em um pacote na superfície de design da guia **Manipuladores de Eventos** . Na guia **Manipuladores de Eventos** , selecione o pacote ou o objeto do pacote para o qual deseja criar um manipulador de eventos e selecione o evento a ser associado ao manipulador de eventos. Um manipulador de eventos tem um fluxo de controle e fluxos de dados opcionais.  
  
 Para obter mais informações, consulte [Add an Event Handler to a Package](../Topic/Add%20an%20Event%20Handler%20to%20a%20Package.md).  
  
### Guia Explorador de Pacotes  
 Os pacotes podem ser complexos, incluindo muitas tarefas, gerenciadores de conexões, variáveis e outros elementos. A exibição do explorador do pacote permite que você visualize uma lista completa de elementos de pacote.  
  
 Para obter mais informações, consulte [Exibir objetos do pacote](../integration-services/view-package-objects.md).  
  
#### Guias Resultado da Execução/Progresso  
 Enquanto um pacote é executado, a guia **Progresso** exibe o progresso da execução do pacote. Depois que o pacote termina de ser executado, os resultados da execução continuam disponíveis na guia **Resultados da Execução** .  
  
> **OBSERVAÇÃO:** para habilitar ou desabilitar a exibição de mensagens na guia **Progresso**, marque ou desmarque a opção **Depurar Relatório do Progresso** no menu **SSIS**.  
  
##### Área Gerenciadores de Conexões  
 Você adiciona e modifica os gerenciadores de conexões que um pacote usa na área **Gerenciadores de conexões** . [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] inclui gerenciadores de conexões para conexão a várias fontes de dados, como arquivos de texto, bancos de dados OLE DB e provedores .NET.  
  
 Para obter mais informações, consulte [Conexões do Integration Services &#40;SSIS&#41;](../integration-services/connection-manager/integration-services-ssis-connections.md) e [Criar gerenciadores de conexões](../Topic/Create%20Connection%20Managers.md).  
  
## Tarefas relacionadas  
  
-   [Copiar pacotes nas Ferramentas de Dados do SQL Server](../integration-services/create-packages-in-sql-server-data-tools.md)  
  
## Consulte também  
 [Interface do usuário do Integration Services](../integration-services/integration-services-user-interface.md)  
  
  