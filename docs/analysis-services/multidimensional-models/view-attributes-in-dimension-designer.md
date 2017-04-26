---
title: "Exibir atributos no Designer de Dimens&#227;o | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "exibindo atributos"
  - "atributos [Analysis Services], exibindo"
  - "exibindo atributos"
ms.assetid: ef011559-9ab9-4a19-b5da-265064fea521
caps.latest.revision: 27
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 33
---
# Exibir atributos no Designer de Dimens&#227;o
  São criados atributos nos objetos de dimensão. Você pode exibir e configurar atributos usando o Designer de Dimensão no [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. O painel **Atributos** da guia **Estrutura da Dimensão** do Designer de Dimensão lista os atributos que estão em uma dimensão. Use esse painel para adicionar, remover ou configurar atributos. Também é possível selecionar atributos para usar como um nível em uma nova hierarquia ou para adicionar a um nível de uma hierarquia existente.  
  
 Para exibir os atributos de uma dimensão, abra o Designer de Dimensão para a dimensão. O painel **Atributos** da guia **Estrutura da Dimensão**  do designer mostra os atributos que estão na dimensão. É possível alternar entre o modo de exibição de lista, árvore ou grade, basta apontar para **Mostrar Atributos em** no menu **Dimensão** do [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] e, em seguida, clicar em um dos comandos a seguir:  
  
1.  Mostrar Atributos em uma **Lista**. Exibe os atributos no formato de lista. Clique com o botão direito do mouse no atributo para excluí-lo da lista, renomeá-lo ou alterar seu uso. Use esse modo de exibição para construir hierarquias. As informações do atributo e as propriedades do membro não são visíveis.  
  
2.  Mostrar Atributos em uma **Árvore**. Exibe os atributos no formato de árvore, com a dimensão como o nó de nível superior na árvore. Expanda o atributo para exibir suas relações ou criar uma nova relação de atributo, executando um destes procedimentos:  
  
    -   Clique na dimensão, no atributo ou na propriedade do membro para exibir suas propriedades na janela **Propriedades** .  
  
    -   Clique com o botão direito do mouse no atributo ou na propriedade do membro para excluí-lo(a) da lista, renomeá-lo(a) ou alterar seu uso.  
  
     Use esse modo de exibição para exibir e criar propriedades do membro. Você também pode usá-lo para construir hierarquias.  
  
3.  Mostrar Atributos em uma **Grade**. Exibe os atributos no formato de grade. A grade exibe as seguintes colunas:  
  
    -   **Nome** mostra o valor da propriedade **Name** . Digite outro nome para alterar a configuração.  
  
    -   **Uso** especifica se este é um atributo Regular, Key, Parent ou AccountType. Clique em um valor dessa coluna selecionar uma configuração diferente.  
  
    -   **Tipo** especifica a categoria de business intelligence do atributo. Clique nessa célula para selecionar uma configuração diferente.  
  
    -   **Coluna de Chave** mostra o tipo de dados OLE DB para a propriedade **KeyColumn** do atributo. Não é possível alterar essa coluna.  
  
    -   **Coluna de Nome** indica se a configuração da propriedade **NameColumn** do atributo é a mesma coluna da configuração da propriedade **KeyColumn** . Não é possível alterar essa coluna.  
  
     Clique em qualquer linha da grade para exibir as propriedades desse atributo.  
  
     Use esse modo de exibição para criar e configurar atributos.  
  
 No [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], os ícones mostrados na tabela a seguir marcam os atributos de acordo com seu uso.  
  
|Ícone|Uso do atributo|  
|----------|---------------------|  
|![Ícone de atributo](../../analysis-services/multidimensional-models/media/as-icon-attribute.png "Ícone de atributo")|Regular ou AccountType|  
|![Ícone de atributo de chave](../../analysis-services/multidimensional-models/media/as-icon-key-attribute.png "Ícone de atributo de chave")|Chave|  
|![Ícone de atributo pai](../../analysis-services/multidimensional-models/media/as-icon-parent-attribute.png "Ícone de atributo pai")|Pai|  
  
## Consulte também  
 [Referência de propriedades de atributo de dimensão](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)  
  
  