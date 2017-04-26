---
title: "Adicionar, editar e atualizar campos no painel de dados do relat&#243;rio (Construtor de Relat&#243;rios e SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2e36f0fe-8100-4513-b169-14d611646f81
caps.latest.revision: 7
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 7
---
# Adicionar, editar e atualizar campos no painel de dados do relat&#243;rio (Construtor de Relat&#243;rios e SSRS)
  Campos do conjunto de dados são a coleção interna de nomes de campos que representam os dados retornados quando uma consulta de conjunto de dados é executado em uma fonte de dados externa.  
  
 Para um conjunto de dados interno, os campos do conjunto de dados são os campos criados após a conclusão da criação de uma consulta e o fechamento do painel Designer de Consulta, e campos calculados criados por você.  
  
 Para um conjunto de dados compartilhado, os campos do conjunto de dados são os campos da definição do conjunto de dados compartilhado depois que você o adicionou ao relatório. Embora a consulta do conjunto de dados compartilhado no servidor de relatório sempre seja usada quando você executa o relatório, a lista de campos do conjunto de dados no relatório é estática.  
  
 Use **Atualizar Campos** para atualizar a lista de campos no relatório para corresponder à lista atual de campos da consulta do conjunto de dados compartilhado. A atualização da lista de campos não afeta os campos calculados definidos no relatório.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### Para adicionar um campo de consulta  
  
1.  No painel de dados do relatório, clique com o botão direito do mouse no conjunto de dados e clique em **Adicionar Campo de Consulta**.  
  
    > [!NOTE]  
    >  Se não conseguir ver o painel de dados do relatório, no menu **Exibir**, clique em **Dados do Relatório**.  
  
2.  Na página **Campos** da caixa de diálogo **Propriedades do Conjunto de Dados** , clique em **Adicionar**e em **Campo de Consulta**. Uma linha nova é adicionada ao final da grade.  
  
3.  Na caixa de texto **Nome do Campo** , digite o nome para o campo.  
  
    > [!NOTE]  
    >  Os nomes devem ser exclusivos no conjunto de dados.  
  
4.  Na caixa de texto **Origem do Campo** , digite o nome de um campo existente na fonte de dados.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### Para adicionar um campo calculado  
  
1.  No painel de dados do relatório, clique com o botão direito do mouse no conjunto de dados e clique em **Adicionar Campo Calculado**.  
  
2.  Na página **Campos** da caixa de diálogo **Propriedades do Conjunto de Dados** , clique em **Adicionar**e em **Campo Calculado**. Uma linha nova é adicionada ao final da grade.  
  
3.  Na caixa de texto **Nome do Campo** , digite o nome para o campo.  
  
    > [!NOTE]  
    >  Os nomes devem ser exclusivos no conjunto de dados.  
  
4.  Na caixa de texto **Origem do Campo** , digite a expressão para o campo. Clique no botão de expressão (**fx**) para criar uma expressão.  
  
    > [!NOTE]  
    >  A expressão de um campo calculado não pode conter agregações ou referências a itens de relatório.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### Para editar um campo de consulta ou de conjunto de dados  
  
1.  No painel de dados do relatório, clique com o botão direito do mouse no campo e clique em **Propriedades do Campo**.  
  
2.  Na página **Campos** da caixa de diálogo **Propriedades do Conjunto de Dados** , clique em um campo existente para selecionar a linha.  
  
3.  Altere o nome ou o valor do campo.  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### Para excluir um campo de consulta ou um campo calculado  
  
1.  No painel de dados do relatório, expanda o conjunto de dados para exibir a coleção de campos.  
  
2.  Clique com o botão direito do mouse no campo que você deseja remover e clique em **Excluir**.  
  
### Para atualizar a coleção de campos no Painel Dados do Relatório para um conjunto de dados compartilhado  
  
1.  No painel Dados do Relatório, clique com o botão direito do mouse no conjunto de dados e clique em **Consulta**.  
  
2.  Clique em **Atualizar Campos**.  
  
     No servidor de relatório, a consulta do banco de dados compartilhado é executada e retorna a coleção de campos atual.  
  
## Consulte também  
 [Coleção de campos de conjuntos de dados &#40;Construtor de Relatórios e SSRS&#41;](../../reporting-services/report-data/dataset-fields-collection-report-builder-and-ssrs.md)   
 [Conjuntos de dados de relatório &#40;SSRS&#41;](../../reporting-services/report-data/report-datasets-ssrs.md)   
 [Conjuntos de dados inseridos e compartilhados de relatório &#40;Construtor de Relatórios e SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [Designers de Consulta do Reporting Services](../Topic/Reporting%20Services%20Query%20Designers.md)   
 [Designers de Consultas &#40;Construtor de Relatórios&#41;](../Topic/Query%20Designers%20\(Report%20Builder\).md)  
  
  