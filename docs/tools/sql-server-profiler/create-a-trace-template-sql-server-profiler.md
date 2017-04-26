---
title: "Criar um modelo de rastreamento (SQL Server Profiler) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modelos [SQL Server], rastreamentos"
  - "modelos de rastreamento [SQL Server]"
  - "salvando modelo de rastreamento"
ms.assetid: 025868b0-3790-4cda-8757-5a58327bfba0
caps.latest.revision: 24
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 24
---
# Criar um modelo de rastreamento (SQL Server Profiler)
  Este tópico descreve como criar um novo modelo de rastreamento usando o [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### Para criar um modelo de rastreamento  
  
1.  No menu **Arquivo** , aponte para **Modelos**e clique em **Novo Modelo**.  
  
2.  Na caixa de diálogo **Propriedades do Modelo de Rastreamento** , selecione um tipo de servidor na lista **Selecionar tipo de servidor**.  
  
3.  Na caixa **Nome do novo modelo** , insira um nome para o modelo.  
  
4.  Opcionalmente, clique em **Basear novo modelo no existente**e selecione um modelo na lista.  
  
     Todos os eventos, colunas de dados e filtros são inicialmente definidos como especificado no modelo selecionado.  
  
5.  Opcionalmente, clique em **Usar como modelo padrão para o tipo de servidor selecionado**.  
  
6.  Na guia **Seleção de Eventos** , adicione, remova ou modifique eventos, colunas de dados ou filtros.  
  
7.  No menu **Seleção de Eventos**, use o controle da grade para adicionar ou remover eventos e colunas de dados do arquivo de rastreamento, da maneira abaixo:  
  
    -   Para adicionar um evento, expanda a categoria de evento apropriada na coluna **Eventos** e selecione o nome do evento.  
  
    -   Quando um evento é adicionado, todas as colunas de dados relevantes são incluídas, por padrão. Para remover uma coluna de dados de um evento do rastreamento, desmarque a caixa de seleção correspondente ao evento na coluna de dados.  
  
    -   Para adicionar filtros, clique no nome de coluna de dados e especifique os critérios de filtro na caixa de diálogo **Editar Filtro** . Você também pode clicar com o botão direito do mouse no nome da coluna de dados e em **Editar Filtro de Coluna** para iniciar a caixa de diálogo **Editar Filtro**. Para adicionar o filtro, clique em **OK** .  
  
8.  Clique em **Salvar**.  
  
## Consulte também  
 [Especificar eventos e colunas de dados para um arquivo de rastreamento &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)   
 [Derivar um modelo de um rastreamento em execução &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/derive-a-template-from-a-running-trace-sql-server-profiler.md)   
 [Derivar um modelo de um arquivo ou uma tabela de rastreamento &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md)   
 [Modelos e permissões do SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  