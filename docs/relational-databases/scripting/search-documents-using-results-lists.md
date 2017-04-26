---
title: "Pesquisar documentos usando listas de resultados | Microsoft Docs"
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
  - "pesquisas [SQL Server Management Studio], listas de resultados"
  - "pesquisas na lista de resultados [SQL Server Management Studio]"
  - "pesquisas [SQL Server Management Studio], vários arquivos"
  - "Editor de Consultas [SQL Server Management Studio], pesquisar vários arquivos"
ms.assetid: 275e1b6c-fbd0-4408-af77-35903f90657c
caps.latest.revision: 22
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 22
---
# Pesquisar documentos usando listas de resultados
  Usando a caixa de diálogo **Localizar e Substituir** , você pode pesquisar e substituir texto em todos os arquivos de um projeto ou solução, ou em uma pasta do sistema de arquivos, mesmo quando eles não estiverem abertos no [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Correspondências de pesquisas executadas com a caixa de diálogo **Localizar e Substituir** são exibidas nas janelas Localizar Resultados 1 e Localizar Resultados 2, que permitem a exibição do texto exato da linha que contém a correspondência.  
  
### Para executar pesquisas em vários arquivos  
  
1.  No menu **Editar** , aponte para **Localizar e Substituir** e depois clique em **Localizar nos Arquivos**.  
  
2.  Na caixa de texto **Localizar** , digite o texto da pesquisa.  
  
3.  Na lista **Examinar** , clique em **Todos os Documentos Abertos**, **Projeto Atual**, **Solução Inteira**ou digite um caminho de diretório.  
  
4.  Na lista **Tipos de arquivo** , selecione um dos conjuntos relacionados de extensões de arquivo ou digite as extensões dos tipos de arquivo a serem pesquisados, separados por ponto-e-vírgula. Use \*.\* para pesquisar todos os arquivos no diretório relacionados na lista suspensa **Examinar**.  
  
5.  Selecione uma opção dentre as opções restantes para melhorar a precisão da pesquisa.  
  
6.  Clique em **Localizar** para começar a pesquisa.  
  
 As correspondências da pesquisa são exibidas na janela Localizar Resultados 1 por padrão. Você pode navegar pelos resultados da pesquisa clicando duas vezes em cada entrada na janela Localizar Resultados 1. Para exibir os resultados da pesquisa em uma janela nova, selecione **Exibir em Localizar 2.**  
  
#### Para efetuar uma substituição em vários arquivos ou pastas  
  
1.  No menu **Editar** , aponte para **Localizar e Substituir** e depois clique em **Substituir nos Arquivos**.  
  
2.  Na caixa de texto **Localizar** , digite o texto da pesquisa.  
  
3.  Na caixa **Substituir por** , digite o texto para substituir o texto de pesquisa.  
  
4.  Na lista **Examinar** , clique em **Todos os Documentos Abertos**, **Projeto Atual**, **Solução Inteira**ou digite um caminho de diretório.  
  
5.  Clique em **Substituir** para substituir a correspondência da pesquisa atual pelo texto da caixa **Substituir por** . Você pode passar para a próxima correspondência clicando em **Localizar Próximo** ou passar para o próximo arquivo clicando em **Ignorar Arquivo**.  
  
     \- ou –  
  
     Selecione **Substituir tudo** para substituir todas as correspondências pelo texto da caixa **Substituir por** . Selecione **Manter arquivos modificados abertos após Substituir Tudo** se você quiser desfazer algumas das substituições em outro momento.  
  
    > [!NOTE]  
    >  **Substituir tudo** substitui todas as correspondências da pesquisa, inclusive aquelas nos arquivos ignorados com **Ignorar Arquivo** ou **Localizar Próximo**. Você só pode usar **Desfazer** para substituições feitas em arquivos que tenham permanecido abertos depois da operação de substituição.  
  
 As informações de substituição são exibidas na janela Localizar Resultados 1 por padrão. Você pode navegar pelas substituições clicando duas vezes em cada entrada na janela Localizar Resultados 1.  
  
## Consulte também  
 [Pesquisar e substituir](../../relational-databases/scripting/search-and-replace.md)   
 [Pesquisar documentos interativamente](../../relational-databases/scripting/search-documents-interactively.md)   
 [Pesquisar texto com curingas](../../relational-databases/scripting/search-text-with-wildcards.md)   
 [Pesquisar texto com expressões regulares](../../relational-databases/scripting/search-text-with-regular-expressions.md)  
  
  