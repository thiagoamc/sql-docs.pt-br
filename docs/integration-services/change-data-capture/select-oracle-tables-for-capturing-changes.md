---
title: "Selecionar as tabelas Oracle para capturar alterações | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: change-data-capture
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- selOraTabDia
ms.assetid: 2e295dc8-999d-4c4d-96cc-1519674b47a4
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 983338ce51799c8a2d36cc87404f4b6f477e590c
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2018
---
# <a name="select-oracle-tables-for-capturing-changes"></a>Selecionar as tabelas Oracle para capturar alterações
  Use esta caixa de diálogo para selecionar as tabelas incluídas na instância CDC. As tabelas selecionadas são adicionadas à lista na página **Selecionar Tabelas e Colunas** do Assistente de Nova Instância. É possível fazer o seguinte nesta caixa de diálogo.  
  
 Por padrão, nenhuma tabela está incluída na lista de tabelas nesta caixa de diálogo. Você pode marcar a caixa de seleção na parte superior da coluna de caixa de seleção para selecionar todas as tabelas ou procurar tabelas específicas.  
  
 **Para pesquisar tabelas específicas**  
 Insira os critérios de pesquisa da seguinte maneira e clique em **Pesquisar**:  
  
-   **Esquema**: selecione um esquema de banco de dados da lista. Somente tabelas que têm esquema serão incluídas na lista.  
  
-   **Padrão de Nome de Tabela**: insira qualquer cadeia de caracteres. Somente tabelas que incluem a cadeia de caracteres inserida serão exibidas.  
  
> [!NOTE]  
>  Você pode inserir critérios em um ou ambos os campos.  
  
-   **Exibir as 1000 primeiras tabelas correspondentes**: por padrão, esta caixa de seleção está marcada. Limita o vídeo às primeiras 1000 tabelas compatíveis. Se você desmarcar a caixa de seleção, todas as tabelas que correspondem aos critérios serão exibidas. Se houver um número grande de tabelas, poderá levar muito tempo para exibir a lista.  
  
 **Para selecionar tabelas a serem incluídas na instância CDC**  
 Clique na caixa de seleção ao lado de qualquer uma das tabelas que você quer incluir e clique em **Adicionar**. As tabelas são adicionadas à lista na página **Selecionar Tabelas e Colunas** do Assistente de Nova Instância.  
  
 Clique em **Fechar** para fechar a caixa de diálogo sem adicionar tabelas.  
  
> [!NOTE]  
>  Se você selecionar uma tabela que inclui um tipo de dados sem suporte, verá uma mensagem de erro e a tabela não será incluída.  
  
## <a name="see-also"></a>Consulte Também  
 [Como criar a instância de banco de dados de alteração do SQL Server](../../integration-services/change-data-capture/how-to-create-the-sql-server-change-database-instance.md)   
 [Selecionar tabelas e colunas Oracle](../../integration-services/change-data-capture/select-oracle-tables-and-columns.md)  
  
  
