---
title: "Gera&#231;&#227;o de scripts do mecanismo de banco de dados | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "scripts [SQL Server], PowerShell"
  - "scripts [SQL Server]"
  - "gerando scripts [Mecanismo de Banco de Dados do SQL Server]"
  - "gerando scripts [Mecanismo de Banco de Dados do SQL Server], PowerShell"
ms.assetid: 9978a884-59a2-4e7f-a82a-335149f3a261
caps.latest.revision: 23
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 23
---
# Gera&#231;&#227;o de scripts do mecanismo de banco de dados
  O [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] oferece suporte ao ambiente de script do [!INCLUDE[msCoName](../../includes/msconame-md.md)] PowerShell para gerenciar instâncias do [!INCLUDE[ssDE](../../includes/ssde-md.md)] e os objetos nas instâncias. Também é possível criar e executar consultas do [!INCLUDE[ssDE](../../includes/ssde-md.md)] que contêm [!INCLUDE[tsql](../../includes/tsql-md.md)] e XQuery em ambientes muito semelhantes aos ambientes de script.  
  
## SQL Server PowerShell  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] inclui dois snap-ins do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell que implementam:  
  
-   Um provedor do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell que expõe as hierarquias de modelos de objeto de gerenciamento do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] como caminhos do PowerShell que são semelhantes aos caminhos do sistema de arquivos. É possível usar as classes de modelo de objeto de gerenciamento do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para gerenciar os objetos representados em cada nó do caminho.  
  
-   Um conjunto de cmdlets do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que implementa comandos do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Um dos cmdlets é **Invoke-Sqlcmd**. Ele é usado para executar scripts de consulta do [!INCLUDE[ssDE](../../includes/ssde-md.md)] a serem executados com o utilitário **sqlcmd** .  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fornece estes recursos para execução do PowerShell:  
  
-   O módulo **sqlps** do PowerShell que pode ser importado para uma sessão do PowerShell; em seguida, o módulo carrega os snap-ins do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. É possível executar interativamente comandos do PowerShell ad hoc. É possível executar arquivos de script usando um comando como .\MyFolder\MyScript.ps1.  
  
-   Os arquivos de script do PowerShell podem ser usados como entrada para etapas de trabalho do PowerShell do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent que executam os scripts em intervalos agendados ou em resposta a eventos do sistema.  
  
-   O utilitário **sqlps** que inicia o PowerShell e importa o módulo do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Em seguida, você pode executar todas as ações com suporte no módulo. É possível iniciar o utilitário **sqlps** em um prompt de comando ou clicando com o botão direito do mouse nos nós da árvore do Pesquisador de Objetos do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio e selecionando **Iniciar PowerShell**.  
  
## Consultas do mecanismo de banco de dados  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] contêm três tipos de elementos:  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
-   Instruções de linguagem XQuery  
  
-   Comandos e variáveis do utilitário **sqlcmd** .  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fornece três ambientes para criar e executar consultas do [!INCLUDE[ssDE](../../includes/ssde-md.md)] :  
  
-   É possível executar e depurar consultas do [!INCLUDE[ssDE](../../includes/ssde-md.md)] interativamente no Editor de Consultas do [!INCLUDE[ssDE](../../includes/ssde-md.md)] no [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. É possível codificar e depurar várias instruções em uma sessão e, em seguida, salvar todas as instruções em um único arquivo de script.  
  
-   O utilitário de prompt de comando do **sqlcmd** permite executar interativamente consultas do [!INCLUDE[ssDE](../../includes/ssde-md.md)] e também arquivos de script de consulta do [!INCLUDE[ssDE](../../includes/ssde-md.md)] existentes.  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] normalmente são codificados interativamente no [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] usando o Editor de Consultas do [!INCLUDE[ssDE](../../includes/ssde-md.md)] . O arquivo pode ser aberto posteriormente em um destes ambientes:  
  
-   Use o menu **Arquivo**/**Abrir** do [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] para abrir o arquivo em uma nova janela do Editor de Consultas do [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
-   Use o parâmetro **-i***input_file* para executar o arquivo com o utilitário **sqlcmd**.  
  
-   Use o parâmetro **-QueryFromFile** para executar o arquivo com o cmdlet **Invoke-Sqlcmd** em scripts do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell.  
  
-   Use etapas de trabalho do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent [!INCLUDE[tsql](../../includes/tsql-md.md)] para executar os scripts em intervalos agendados ou em resposta a eventos do sistema.  
  
 Além disso, você pode usar o Assistente para Gerar Scripts do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para gerar scripts [!INCLUDE[tsql](../../includes/tsql-md.md)] . Você pode clicar com o botão direito do mouse no Pesquisador de Objetos do [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] e selecionar o item de menu **Gerar Script**. A opção**Gerar Script** inicia o assistente que fornece instruções para o processo de criação de um script.  
  
## Tarefas de scripts do mecanismo de banco de dados  
  
|Descrição da tarefa|Tópico|  
|----------------------|-----------|  
|Descreve como usar código e editores de texto no [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] para desenvolver, depurar e executar interativamente scripts [!INCLUDE[tsql](../../includes/tsql-md.md)].|[Editores de consultas e de texto &#40;SQL Server Management Studio&#41;](../../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md)|  
|Descreve como usar o utilitário **sqlcmd** para executar scripts [!INCLUDE[tsql](../../includes/tsql-md.md)] do prompt de comando, incluindo a capacidade de desenvolver scripts de maneira interativa.|[Tópicos de informações práticas sobre sqlcmd](../Topic/sqlcmd%20How-to%20Topics.md)|  
|Descreve como integrar os componentes do SQL Server em um ambiente do Windows PowerShell e, então, compilar scripts do PowerShell para gerenciar instâncias e objetos do SQL Server.|[SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)|  
|Descreve como usar o assistente para **Gerar e Publicar Scripts** para criar scripts [!INCLUDE[tsql](../../includes/tsql-md.md)] que recriam um ou mais dos objetos de um banco de dados.|[Gerar scripts &#40;SQL Server Management Studio&#41;](../../relational-databases/scripting/generate-scripts-sql-server-management-studio.md)|  
  
## Consulte também  
 [Utilitário sqlcmd](../../tools/sqlcmd-utility.md)   
 [Tutorial: Gravando instruções Transact-SQL](../../t-sql/tutorial-writing-transact-sql-statements.md)  
  
  