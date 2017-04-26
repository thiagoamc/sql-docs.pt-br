---
title: "Caixa de di&#225;logo Propriedades do Conjunto de Dados, Op&#231;&#245;es (Construtor de Relat&#243;rios) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "10020"
  - "sql13.rtp.rptdesigner.datasetproperties.options.f1"
  - "10130"
ms.assetid: 43e50133-45ef-47a2-b575-34dfcc28ec98
caps.latest.revision: 15
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 15
---
# Caixa de di&#225;logo Propriedades do Conjunto de Dados, Op&#231;&#245;es (Construtor de Relat&#243;rios)
  Selecione **Opções** na caixa de diálogo **Propriedades do Conjunto de Dados** para alterar as opções dos dados, como as opções de agrupamento e tratar os subtotais como dados detalhados, para a consulta. Para obter mais informações sobre agrupamentos, consulte [Agrupamento e suporte a Unicode](../../relational-databases/collations/collation-and-unicode-support.md) nos [Manuais Online do SQL Server](http://go.microsoft.com/fwlink/?linkid=98335).  
  
 Opções de dados que fazem parte de uma definição de conjunto de dados compartilhado no servidor de relatório afetam todos os relatórios que usam o conjunto de dados compartilhado. Você pode substituir opções para o banco de dados compartilhado depois de adicioná-lo ao relatório. Estas alterações afetam somente o relatório no qual são definidas.  
  
 As opções de dados de um conjunto de dados inserido afetam apenas o relatório no qual são definidas.  
  
 Para obter mais informações, consulte [Conjuntos de dados inseridos e compartilhados de relatório &#40;Construtor de Relatórios e SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).  
  
## Opções  
 **Agrupamento**  
 Selecione uma localidade que determina a sequência de agrupamento a ser usada para classificar os dados. **Padrão** indica que o servidor de relatórios deve tentar derivar o valor a partir do provedor de dados quando o relatório é executado. Se o valor não puder ser derivado, o valor padrão será derivado da configuração de localidade do computador.  
  
 **Diferenciação de maiúsculas e minúsculas**  
 Selecione um valor que determina a diferenciação de maiúsculas e minúsculas. Esta opção indica se os dados são maiúsculas e minúsculas. Você pode definir a **Distinção de maiúsculas e minúsculas** como **Verdadeiro**, **Falso**ou **Automático**. O valor padrão, **Auto**, indica que o servidor de relatórios deve tentar derivar o valor a partir do provedor de dados quando o relatório é executado. Se o provedor de dados não der suporte ao tipo de diferenciação de maiúsculas e minúsculas, o relatório será executado como se o valor fosse **False**. Se souber o valor e souber que ele tem suporte, escolha **Verdadeiro**.  
  
 **Distinção de acentos **  
 Selecione um valor que determina a sensibilidade de acentuação. A**Sensibilidade de acentuação** indica se os dados são sensíveis à acentuação e podem ser definidos para **Verdadeiro**, **Falso**ou **Automático**. O valor padrão, **Auto**, indica que o servidor de relatórios deve tentar derivar o valor a partir do provedor de dados quando o relatório é executado. Se o provedor de dados não der suporte o tipo de sensibilidade de acentuação, o relatório executará como se o valor fosse **Falso**. Se souber o valor e souber que ele tem suporte, escolha **Verdadeiro**.  
  
 **Sensibilidade de Kanatype**  
 Selecione um valor que determina sensibilidade de kanatype. Esta opção indica se os dados são sensíveis ao kanatype; pode ser definido como **Verdadeiro**, **Falso**ou **Automático**. O valor padrão, **Auto**, indica que o servidor de relatórios deve tentar derivar o valor a partir do provedor de dados quando o relatório é executado. Se o provedor de dados não der suporte ao tipo de sensibilidade de kanatype, o relatório executará como se o valor fosse **Falso**. Se souber o valor e souber que ele tem suporte, escolha **Verdadeiro**.  
  
 **Distinção de largura**  
 Selecione um valor que determina distinção de largura. Esta opção indica se os dados são sensíveis à largura e pode ser definida como **True**, **False** ou **Auto**. O valor padrão, **Auto**, indica que o servidor de relatórios deve tentar derivar o valor a partir do provedor de dados quando o relatório é executado. Se o provedor de dados não der suporte ao tipo de distinção de largura, o relatório executará como se o valor fosse **Falso**. Se souber o valor e souber que ele tem suporte, escolha **Verdadeiro**.  
  
 **Interprete subtotais como linhas de detalhe**  
 Selecione um valor que indica se deseja que linhas de subtotais sejam interpretadas como linhas de detalhes ao invés de linhas de agregação. O valor padrão, **Auto**, indica que as linhas de subtotais deverão ser tratadas como linhas de detalhes se o relatório não usar a função **Aggregate**() para acessar os campos em um conjunto de dados. Se quiser que as linhas de subtotais sejam interpretadas como linhas de agregação, selecione **Falso**. Se quiser que as linhas de subtotal sejam interpretadas como linhas de detalhes e você souber que elas não usam a função **Aggregate**(), selecione **True**.  
  
## Consulte também  
 [Ajuda do Construtor de Relatórios para caixas de diálogo, painéis e assistentes](http://msdn.microsoft.com/pt-br/2da24891-0b6d-4d3c-8b18-81b98752642f)   
 [Função Aggregate &#40;Construtor de Relatórios e SSRS&#41;](../../reporting-services/report-design/aggregate-function-report-builder-and-ssrs.md)   
 [Filtrar, agrupar e classificar dados &#40;Construtor de Relatórios e SSRS&#41;](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Conjuntos de dados inseridos e compartilhados de relatório &#40;Construtor de Relatórios e SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [Caixa de diálogo Propriedades do Conjunto de Dados, Consulta &#40;Construtor de Relatórios&#41;](../../reporting-services/report-data/dataset-properties-dialog-box-query-report-builder.md)  
  
  