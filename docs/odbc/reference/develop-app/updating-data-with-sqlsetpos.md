---
title: Atualizando dados com SQLSetPos | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- updating data [ODBC], SQLSetPos
- data updates [ODBC], SQLSetPos
- SQLSetPos function [ODBC], updating data
ms.assetid: e9625b59-06a0-4883-b155-b932ba7528d9
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3a86647a0086c322918d8dc650d4f840b09326d6
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="updating-data-with-sqlsetpos"></a>Atualizando dados com SQLSetPos
Aplicativos podem atualizar ou excluir qualquer linha no conjunto de linhas com **SQLSetPos**. Chamando **SQLSetPos** é uma alternativa conveniente para construir e executar uma instrução SQL. Ele permite que um driver ODBC oferecem suporte a atualizações posicionadas mesmo quando a fonte de dados não dá suporte a instruções SQL posicionadas. Ele faz parte do paradigma de obter acesso completo do banco de dados por meio de chamadas de função.  
  
 **SQLSetPos** opera no conjunto de linhas atual e pode ser usado somente depois de uma chamada para **SQLFetchScroll**. O aplicativo especifica o número da linha para atualizar, excluir ou inserir, e o driver recupera os novos dados para aquela linha dos buffers de conjunto de linhas. **SQLSetPos** também pode ser usado para designar uma linha especificada como a linha atual ou para atualizar uma linha específica no conjunto de linhas da fonte de dados.  
  
 Tamanho do conjunto de linhas é definido por uma chamada para **SQLSetStmtAttr** com um *atributo* argumento de SQL_ATTR_ROW_ARRAY_SIZE. **SQLSetPos** usa um novo tamanho do conjunto de linhas, no entanto, apenas após uma chamada para **SQLFetch** ou **SQLFetchScroll**. Por exemplo, se o tamanho do conjunto de linhas for alterado, **SQLSetPos** é chamado e, em seguida, **SQLFetch** ou **SQLFetchScroll** é chamado e a chamada para **SQLSetPos** usa o tamanho do conjunto de linhas anterior ao **SQLFetch** ou **SQLFetchScroll** usa o novo tamanho do conjunto de linhas.  
  
 A primeira linha do conjunto de linhas é o número de linha 1. O *RowNumber* argumento **SQLSetPos** deve identificar uma linha no conjunto de linhas; ou seja, seu valor deve estar no intervalo entre 1 e o número de linhas buscado mais recentemente (que pode ser menor que tamanho do conjunto de linhas). Se *RowNumber* for 0, a operação se aplica a todas as linhas no conjunto de linhas.  
  
 Como a interação com a maioria dos bancos de dados relacionais é feita por meio do SQL, **SQLSetPos** não tem muito suporte. No entanto, um driver pode facilmente emulá-lo criando e executando um **atualização** ou **excluir** instrução.  
  
 Para determinar quais operações **SQLSetPos** oferece suporte, um aplicativo chama **SQLGetInfo** com SQL_DYNAMIC_CURSOR_ATTRIBUTES1 SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ ATTRIBUTES1 ou opção de informações de SQL_STATIC_CURSOR_ATTRIBUTES1 (dependendo do tipo de cursor).  
  
 Esta seção contém os tópicos a seguir.  
  
-   [Atualizando linhas no conjunto de linhas com SQLSetPos](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md)  
  
-   [Excluindo linhas no conjunto de linhas com SQLSetPos](../../../odbc/reference/develop-app/deleting-rows-in-the-rowset-with-sqlsetpos.md)
