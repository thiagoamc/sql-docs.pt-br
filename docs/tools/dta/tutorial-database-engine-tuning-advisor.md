---
title: "Tutorial: Orientador de Otimiza&#231;&#227;o do Mecanismo de Banco de Dados | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
helpviewer_keywords: 
  - "Orientador de Otimização do Mecanismo de Banco de Dados [SQL Server], tutorias"
  - "tutoriais: [Orientador de Otimização do Mecanismo de Banco de Dados]"
ms.assetid: 3b54cbbe-d8c6-424d-92f1-aa58179f4da8
caps.latest.revision: 38
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 38
---
# Tutorial: Orientador de Otimiza&#231;&#227;o do Mecanismo de Banco de Dados
Bem-vindo ao tutorial do Orientador de Otimização do Mecanismo de Banco de Dados. O Orientador de Otimização do Mecanismo de Banco de Dados examina como são processadas as consultas nos bancos de dados que você especifica e recomenda meios de aprimorar o desempenho de processamento de consultas, modificando as estruturas do banco de dados, como índices, exibições indexadas e particionamento.  
  
O Orientador de Otimização do Mecanismo de Banco de Dados fornece duas interfaces do usuário: uma GUI (interface gráfica do usuário) e o utilitário de prompt de comando **dta**. A GUI facilita a exibição rápida dos resultados das sessões de ajuste, enquanto o utilitário **dta** facilita a inserção da funcionalidade Orientador de Otimização do Mecanismo de Banco de Dados em scripts para ajuste automatizado. Além disso, o Orientador de Otimização do Mecanismo de Banco de Dados aceita entrada XML, o que oferece mais controle sobre o processo de ajuste.  
  
## O que você aprenderá  
Este tutorial vai ensiná-lo a navegar na GUI do Orientador de Otimização do Mecanismo de Banco de Dados e executar algumas tarefas básicas com a GUI e o utilitário **dta**. Ele contém as seguintes lições:  
  
[Lição 1: Navegação básica no Orientador de Otimização do Mecanismo de Banco de Dados](../../tools/dta/lesson-1-basic-navigation-in-database-engine-tuning-advisor.md)  
Nessa lição, você se acostumará com a nova interface gráfica do usuário do Orientador de Otimização do Mecanismo de Banco de Dados e aprenderá a definir opções de display e layout.  
  
[Lição 2: Usando o Orientador de Otimização do Mecanismo de Banco de Dados](../../tools/dta/lesson-2-using-database-engine-tuning-advisor.md)  
Nessa lição, você aprenderá a executar tarefas básicas de ajuste com a GUI do Orientador de Otimização do Mecanismo de Banco de Dados.  
  
[Lição 3: Usando o utilitário de prompt de comando dta](../../tools/dta/lesson-3-using-the-dta-command-prompt-utility.md)  
Nesta lição, você aprenderá a iniciar o utilitário de prompt de comando **dta** e executar alguns comandos de ajuste simples.  
  
## Requisitos  
Este tutorial destina-se a administradores de banco de dados que não estão familiarizados com a GUI do Orientador de Otimização do Mecanismo de Banco de Dados nem com o utilitário de prompt de comando **dta**, mas que têm experiência com conceitos e estruturas de banco de dados, como índices e exibições indexadas.  
  
Você deve instalar o [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] (ou uma versão posterior) com o banco de dados de exemplo do [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]. Para reforçar a segurança, os bancos de dados de exemplo não são instalados por padrão. Para instalar os bancos de dados de exemplo, consulte [Instalando amostras e bancos de dados de exemplo do SQL Server](http://sqlserversamples.codeplex.com).  
  
## Depois de você concluir este tutorial  
Depois de você terminar as lições deste tutorial, recorra aos tópicos a seguir para obter mais informações sobre o Orientador de Otimização do Mecanismo de Banco de Dados:  
  
-   [Orientador de Otimização do Mecanismo de Banco de Dados](../../relational-databases/performance/database-engine-tuning-advisor.md) para obter descrições sobre como executar tarefas com essa ferramenta.  
  
-   [dta Utility](../../tools/dta/dta-utility.md) para obter material de referência sobre o utilitário de prompt de comando e o arquivo XML opcional que você pode usar para controlar a operação do utilitário.  
  
## Próxima lição  
[Lição 1: Navegação básica no Orientador de Otimização do Mecanismo de Banco de Dados](../../tools/dta/lesson-1-basic-navigation-in-database-engine-tuning-advisor.md)  
  
  
  