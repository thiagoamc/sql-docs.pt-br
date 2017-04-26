---
title: "Visualizador de Conflitos de Replica&#231;&#227;o da Microsoft (replica&#231;&#227;o transacional) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.replconflictviewer.cvqueued.f1"
ms.assetid: eec59d8e-cadb-4623-a31f-9f42ec09c97f
caps.latest.revision: 22
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 22
---
# Visualizador de Conflitos de Replica&#231;&#227;o da Microsoft (replica&#231;&#227;o transacional)
  O Visualizador de Conflitos de Replicação permite exibir conflitos que ocorreram durante a sincronização para uma replicação transacional ponto a ponto de uma replicação transacional com assinaturas de atualização enfileiradas. Para obter mais informações, consulte [Exibir conflitos de dados para publicações transacionais e 40; SQL Server Management Studio e 41;](../../relational-databases/replication/view-data-conflicts-for-transactional-publications-sql-server-management-studio.md).  
  
> [!NOTE]  
>  O Visualizador de Conflitos de Replicação exibe conflitos que ocorrem em replicação de mesclagem e em replicação transacional. Para replicação transacional, você pode usar o Visualizador de Conflitos de Replicação para exibir dados de conflito, mas não pode escolher uma solução diferente para o conflito.  
  
## Opções  
 O Visualizador de Conflitos de Replicação é dividido em duas seções. A seção superior da caixa de diálogo mostra a lista de conflitos para a tabela selecionada. Quando você clica em um item na lista de conflitos, os detalhes do conflito são exibidos na seção inferior da caixa de diálogo.  
  
 Os dados de conflito na seção inferior são exibidos em duas colunas correspondentes (**vencedor do conflito** e **perdedor de conflito**). Se o conflito estiver entre os dados atualizados e excluídos, talvez não haja dados a serem exibidos no lado excluído do conflito. Nesse caso, o Visualizador de Conflitos de Replicação exibe uma mensagem em uma das colunas, indicando que a linha foi excluída em um local e atualizada em outro. Também indica a resolução sugerida.  
  
 **Banco de dados**  
 Escolha um banco de dados que inclua publicações com conflitos.  
  
 **Publicação**  
 Escolha uma publicação que inclua tabelas com conflitos.  
  
 **Table**  
 Escolha uma tabela que inclua conflitos.  
  
 **Definir Filtro**  
 Clique para abrir o **definir filtros** caixa de diálogo.  
  
 **Aplicar ou Remover Filtro**  
 Clique para aplicar ou remover um filtro que foi definido no **definir filtros** caixa de diálogo.  
  
 **Selecionar Tudo**  
 Clique para selecionar todos os conflitos listados na grade.  
  
 **Selecionar Nenhum**  
 Clique para desmarcar a seleção de todos os conflitos listados na grade.  
  
 **Remover**  
 Clique para remover conflitos selecionados do visualizador e seus metadados associados das tabelas do sistema de replicação.  
  
 **Mostrar todas as colunas**  
 Selecione para mostrar todas as colunas da tabela.  
  
 **Mostrar as primeiras cinco colunas e outras colunas com dados conflitantes**  
 Selecione para exibir as primeiras cinco colunas e qualquer coluna com conflitos. Isso é útil quando a tabela tem um grande número de colunas, mas você quer ver apenas as mais relevantes para resolver o conflito. As primeiras cinco colunas sempre são incluídas nessa exibição, como campos que identificam uma linha, como chave primária ou campo de nomes, estão sempre entre as primeiras colunas da tabela.  
  
 **Exibir informações da coluna** (**...**)  
 Clique para exibir informações de coluna: **nome de tabela**, **nome de coluna**, **tipo de dados**, e **o valor da coluna**.  
  
 **Registrar em log os detalhes do conflito**  
 Marque essa caixa para registrar em log os detalhes do conflito em um arquivo. Para especificar um local para o arquivo, aponte para o **exibição** menu e clique em **opções**. Insira um valor ou clique no botão Procurar (**...**) e navegue até o arquivo apropriado. Clique em **OK** para sair da caixa de diálogo **Opções** .  
  
## Consulte também  
 [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/conflict-detection-in-peer-to-peer-replication.md)   
 [Exibir conflitos de dados para publicações transacionais e 40; SQL Server Management Studio e 41;](../../relational-databases/replication/view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)  
  
  