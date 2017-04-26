---
title: "Li&#231;&#227;o 3: Criar o relat&#243;rio pai usando o Assistente de Relat&#243;rio | Microsoft Docs"
ms.custom: ""
ms.date: "05/18/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 2f69dcd3-cd6d-45a9-a62a-ba6f5f3179d8
caps.latest.revision: 9
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 9
---
# Li&#231;&#227;o 3: Criar o relat&#243;rio pai usando o Assistente de Relat&#243;rio
Após criar uma conexão de dados e uma tabela de dados para o relatório pai, a próxima etapa será criar o relatório pai usando o Assistente de Relatório no Designer de Relatórios. Para obter mais informações sobre o Designer de Relatórios, consulte [Criar relatórios com o Designer de Relatórios &#40;SSRS&#41;](../reporting-services/tools/design-reports-with-report-designer-ssrs.md).  
  
### Para criar o relatório pai usando o Assistente de Relatório  
  
1.  Verifique se esse site de nível superior está selecionado no **Gerenciador de Soluções**.  
  
2.  Clique com o botão direito do mouse no site e selecione **Adicionar Novo Item**.  
  
3.  Na caixa de diálogo **Adicionar Novo Item**, selecione **Assistente de Relatório**, insira um nome para o arquivo de relatório e selecione **Adicionar**.  
  
    Isso iniciará o Assistente de Relatório.  
  
4.  Na página **Propriedades do Conjunto de Dados**, na caixa **Fonte de dados**, selecione o **DataSet1** criado na [Lição 2: Definir uma conexão de dados e uma tabela de dados para o relatório pai](../reporting-services/lesson-2-define-a-data-connection-and-data-table-for-parent-report.md).  
  
    A caixa **Conjuntos de dados disponíveis** é atualizada automaticamente com a **DataTable** criada acima.  
  
5.  Selecione **Avançar**.  
  
6.  Na página **Organizar campos**, faça o seguinte:  
  
    1.  Arraste **ProductID**, **Name**, **ProductNumber**, **SafetyStockLevel** e **ReorderLevel** de **Campos disponíveis** até a caixa **Valores**.  
  
    2.  Clique na seta ao lado de **Sum(ProductID)**, **Sum(SafetyStockLevel)**, **Sum(ReorderLevel)** e desmarque a seleção **Sum**.  
  
7.  Selecione **Avançar** duas vezes e **Concluir** para fechar o **Assistente de Relatório**.  
  
    Agora você criou o arquivo .rdlc. O arquivo é aberto no Designer de Relatórios. Agora, o tablix que você criou será exibido na superfície de design.  
  
8.  Salve o arquivo .rdlc.  
  
## Próxima tarefa  
Você criou o relatório pai com êxito usando o Assistente de Relatório. Em seguida, você criará uma conexão de dados e uma tabela de dados para o relatório filho. Consulte [Lição 4: Definir uma conexão de dados e uma tabela de dados para o relatório filho](../reporting-services/lesson-4-define-a-data-connection-and-data-table-for-child-report.md).  
  
  
  