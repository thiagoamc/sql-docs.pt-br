---
title: "Tutorial: Gravando instru&#231;&#245;es Transact-SQL | Microsoft Docs"
ms.custom: ""
ms.date: "08/03/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
helpviewer_keywords: 
  - "instruções Transact-SQL, tutoriais"
  - "tutoriais do Transact-SQL"
  - "tutoriais [Transact-SQL]"
ms.assetid: 2addc9be-67d0-423d-a457-192fe9d7d058
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# Tutorial: Gravando instru&#231;&#245;es Transact-SQL
Bem-vindo ao tutorial Escrevendo Instruções [!INCLUDE[tsql](../includes/tsql-md.md)]. Esse tutorial foi planejado para usuários que desconhecem como escrever instruções SQL. Ele irá ajudar usuários iniciantes revisando algumas das instruções básicas sobre como criar tabelas e inserir dados. Este tutorial usa a [!INCLUDE[tsql](../includes/tsql-md.md)], a implementação [!INCLUDE[msCoName](../includes/msconame-md.md)] do SQL standard. Esse tutorial foi planejado como uma rápida introdução à linguagem [!INCLUDE[tsql](../includes/tsql-md.md)], e não como substituição para uma classe [!INCLUDE[tsql](../includes/tsql-md.md)]. As instruções nesse tutorial são intencionalmente simples, e não tem a intenção de representar a complexidade encontrada em um banco de dados de produção típico.  
  
>**OBSERVAÇÃO:** se você for um iniciante, talvez seja mais fácil usar o [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] em vez de escrever instruções [!INCLUDE[tsql](../includes/tsql-md.md)].  
  
## Descobrindo mais informações  
Para encontrar mais informações sobre uma instrução específica, pesquise a instrução pelo nome nos Manuais Online do SQL Server ou use o Conteúdo para navegar pelos 1.800 elementos de linguagem listados em ordem alfabética em [Referência do Transact-SQL &#40;Mecanismo de Banco de Dados&#41;](../t-sql/transact-sql-reference-database-engine.md). Outra boa estratégia para obter informações é pesquisar palavras-chave relacionadas ao assunto do seu interesse. Por exemplo, se quiser saber como retornar uma parte de uma data (como o mês), pesquise **datas [SQL Server]** no índice e selecione **dateparts**. Isso o levará ao tópico [DATEPART &#40;Transact-SQL&#41;](../t-sql/functions/datepart-transact-sql.md). Como outro exemplo, para descobrir como trabalhar com cadeias de caracteres, pesquise **funções de cadeia de caracteres**. Isso o levará ao tópico [Funções de cadeia de caracteres &#40;Transact-SQL&#41;](../t-sql/functions/string-functions-transact-sql.md).  
  
## O que você aprenderá  
Este tutorial lhe mostrará como criar um banco de dados, criar uma tabela no banco de dados, inserir dados numa tabela, atualizar dados, ler dados, excluir dados e, por fim, excluir a tabela. Você criará exibições e procedimentos armazenados e configurará um usuário ao banco de dados e aos dados.  
  
Este tutorial divide-se em três lições:  
  
[Lição 1: Criando objetos de banco de dados](../t-sql/lesson-1-creating-database-objects.md)  
Nesta lição, você irá criar um banco de dados; criar uma tabela no banco de dados; inserir dados em uma tabela; atualizar e ler dados.  
  
[Lição 2: Configurando permissões em objetos de banco de dados](../t-sql/lesson-2-configuring-permissions-on-database-objects.md)  
Nesta lição, você criará um logon e um usuário. Você também criará uma exibição e um procedimento armazenado e, então, concederá a permissão de usuário ao procedimento armazenado.  
  
[Lição 3: Excluindo objetos de banco de dados](../t-sql/lesson-3-deleting-database-objects.md)  
Nesta lição, você removerá o acesso aos dados; excluirá dados de uma tabela; deletará a tabela e, por fim, excluirá o banco de dados.  
  
## Requisitos  
Para completar este tutorial, não é necessário conhecer a linguagem SQL, mas você precisa dominar conceitos básicos de banco de dados, como tabelas. Durante esse tutorial, você criará um banco de dados e criará um usuário do Windows. Essas tarefas requerem um nível alto de permissões; assim, faça seu logon no computador como um administrador.  
  
O sistema deverá ter o seguinte instalado:  
  
-   Qualquer edição do [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-  [SQL Server Management Studio](https://msdn.microsoft.com/library/mt238290.aspx)  
  

 
  
  
  