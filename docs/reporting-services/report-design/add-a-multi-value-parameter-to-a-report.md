---
title: "Adicionar um par&#226;metro com v&#225;rios valores a um relat&#243;rio | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 12ad0e77-4c28-4bbb-ab11-473ae89ec9f1
caps.latest.revision: 7
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 7
---
# Adicionar um par&#226;metro com v&#225;rios valores a um relat&#243;rio
  É possível adicionar um parâmetro a um relatório que permite ao usuário selecionar mais de um valor para o parâmetro.  
  
 Você pode passar vários valores de parâmetro para o relatório na URL de relatório. Para um exemplo de URL que inclui um parâmetro com vários valores, consulte [Passar um parâmetro de relatório em uma URL](../../reporting-services/pass-a-report-parameter-within-a-url.md).  
  
 Para obter informações sobre como passar vários valores de parâmetro para um procedimento armazenado, consulte [Trabalhando com parâmetros de seleções múltiplas para relatórios SSRS](http://go.microsoft.com/fwlink/?LinkId=321529) em mssqltips.com.  
  
## Para adicionar um parâmetro com vários valores  
  
1.  No Construtor de Relatórios, abra o relatório no qual você deseja adicionar o parâmetro com vários valores.  
  
2.  Clique com o botão direito do mouse no conjunto de dados do relatório e clique em **Propriedades do Conjunto de Dados**  
  
3.  Adicione uma variável à consulta do conjunto de dados editando o texto da consulta na caixa **Consulta** , ou adicionando um filtro através do designer de consulta. Para obter mais informações, consulte [Criar uma consulta no Designer de Consultas Relacionais &#40;Construtor de Relatórios e SSRS&#41;](../../reporting-services/report-data/build-a-query-in-the-relational-query-designer-report-builder-and-ssrs.md).  
  
    ```  
    WHERE  
      Production.ProductInventory.ProductID IN (@ProductID)  
    ```  
  
    > [!IMPORTANT]  
    > *  O texto da consulta não deve incluir uma instrução DECLARE para a variável de consulta.  
    > *  O texto da variável de consulta deve incluir o operador **IN**, como mostrado no exemplo acima.  
    > *  Lembre-se de incluir os parênteses delimitando a variável, conforme mostrado acima. Caso contrário, o relatório não será renderizado e o erro “É necessário declarar a variável escalar” será exibido.  
  
    Um parâmetro de conjunto de dados para um conjunto de dados inserido ou um conjunto de dados compartilhado é criado automaticamente para a variável de consulta. Um parâmetro de relatório é criado automaticamente para o parâmetro de conjunto de dados.  
  
4.  No painel **Dados do Relatório**, expanda o nó **Parâmetros**, clique com o botão direito do mouse no parâmetro de relatório criado automaticamente para o parâmetro do conjunto de dados e clique em **Propriedades do Parâmetro**.  
  
5.  Na guia **Geral** , selecione **Permitir vários valores** para permitir que um usuário selecione mais de um valor para o parâmetro.  
  
6.  (Opcionalmente) Na guia **Valores disponíveis**, especifique uma lista de valores disponíveis a serem exibidos para o usuário.  
  
     Uma lista de valores disponíveis limita as escolhas do usuário aos valores válidos para o parâmetro. No caso de diversos valores, a lista começa com um recurso **Selecionar Tudo** , através do qual o usuário pode selecionar ou desmarcar todos os valores com um só clique. Se você optar por obter os valores disponíveis para o parâmetro de relatório de uma consulta de conjunto de dados, selecione um conjunto de dados que não contenha a variável de consulta que está associada ao mesmo parâmetro de relatório.  
  
     Para obter mais informações, consulte [Adicionar, alterar ou excluir valores disponíveis de um parâmetro de relatório &#40;Construtor de Relatórios e SSRS&#41;](../../reporting-services/report-design/add, change, or delete available values for a report parameter.md).  
  
## Para adicionar um parâmetro com vários valores  
  
1.  No Construtor de Relatórios, abra o relatório no qual você deseja adicionar o parâmetro com vários valores.  
  
2.  Clique com o botão direito do mouse no conjunto de dados do relatório e clique em **Propriedades do Conjunto de Dados**  
  
3.  Adicione uma variável à consulta do conjunto de dados editando o texto da consulta na caixa **Consulta** , ou adicionando um filtro através do designer de consulta. Para obter mais informações, consulte [Criar uma consulta no Designer de Consultas Relacionais &#40;Construtor de Relatórios e SSRS&#41;](../../reporting-services/report-data/build-a-query-in-the-relational-query-designer-report-builder-and-ssrs.md).  
  
     ```  
    WHERE  
      Production.ProductInventory.ProductID IN (@ProductID)  
    ```  
  
    > [!IMPORTANT]  
    > *  O texto da consulta não deve incluir uma instrução DECLARE para a variável de consulta.  
    > *  O texto da variável de consulta deve incluir o operador **IN**, como mostrado no exemplo acima.  
    > *  Lembre-se de incluir os parênteses delimitando a variável, conforme mostrado acima. Caso contrário, o relatório não será renderizado e o erro “É necessário declarar a variável escalar” será exibido  
      
    Um parâmetro de conjunto de dados para um conjunto de dados inserido ou um conjunto de dados compartilhado é criado automaticamente para a variável de consulta. Um parâmetro de relatório é criado automaticamente para o parâmetro de conjunto de dados.  
  
4.  No painel **Dados do Relatório**, expanda o nó **Parâmetros**, clique com o botão direito do mouse no parâmetro de relatório criado automaticamente para o parâmetro do conjunto de dados e clique em **Propriedades do Parâmetro**.  
  
5.  Na guia **Geral** , selecione **Permitir vários valores** para permitir que um usuário selecione mais de um valor para o parâmetro.  
  
6.  (Opcionalmente) Na guia **Valores disponíveis**, especifique uma lista de valores disponíveis a serem exibidos para o usuário.  
  
     Uma lista de valores disponíveis limita as escolhas do usuário aos valores válidos para o parâmetro. No caso de diversos valores, a lista começa com um recurso **Selecionar Tudo** , através do qual o usuário pode selecionar ou desmarcar todos os valores com um só clique. Se você optar por obter os valores disponíveis para o parâmetro de relatório de uma consulta de conjunto de dados, selecione um conjunto de dados que não contenha a variável de consulta que está associada ao mesmo parâmetro de relatório.  
  
     Para obter mais informações, consulte [Adicionar, alterar ou excluir valores disponíveis de um parâmetro de relatório &#40;Construtor de Relatórios e SSRS&#41;](../../reporting-services/report-design/add, change, or delete available values for a report parameter.md).  
  
## Consulte também  
 [Adicionar parâmetros em cascata a um relatório &#40;Construtor de Relatórios e SSRS&#41;](../../reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs.md)   
 [Adicionar, alterar ou excluir um parâmetro de relatório &#40;Construtor de Relatórios e SSRS&#41;](../../reporting-services/report-design/add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md)  
  
  