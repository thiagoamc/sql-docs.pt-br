---
title: "Derivar valores de coluna por meio da transforma&#231;&#227;o Coluna Derivada | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "colunas [Integration Services]"
  - "colunas derivadas"
  - "colunas [Integration Services], valores"
  - "transformação Coluna Derivada"
ms.assetid: 28b07746-fc6f-42b2-b741-9de6fac3f29c
caps.latest.revision: 48
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 48
---
# Derivar valores de coluna por meio da transforma&#231;&#227;o Coluna Derivada
  Para adicionar e configurar uma transformação Coluna Derivada, o pacote já deve incluir pelo menos uma tarefa de Fluxo de Dados e uma origem.  
  
 A transformação de Coluna Derivada usa expressões para atualizar os valores de colunas existentes ou adicionar valores a novas colunas. Ao optar por adicionar valores a novas colunas, a caixa de diálogo **Editor de Transformação Coluna Derivada** avalia a expressão e define apropriadamente os metadados das colunas. Por exemplo, se uma expressão concatena duas colunas—cada uma com o tipo de dados DT_WSTR e um comprimento de 50—com um espaço entre os dois valores de coluna, a nova coluna terá o tipo de dados DT_WSTR e um comprimento de 101. É possível atualizar o tipo de dados de colunas novas. O único requisito é que o tipo de dados seja compatível com os dados inseridos. Por exemplo, a caixa de diálogo **Editor de Transformação Coluna Derivada** gera um erro de validação ao atribuir um valor de dados a uma coluna com um tipo de dados Integer. Dependendo do tipo de dados selecionado, é possível especificar o comprimento, a precisão, a escala e a página de código da coluna.  
  
### Para derivar valores de coluna  
  
1.  No [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], abra o projeto do [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] que contém o pacote desejado.  
  
2.  No Gerenciador de Soluções, clique duas vezes no pacote para abri-lo.  
  
3.  Clique na guia **Fluxo de Dados** e, na **Caixa de Ferramentas**, arraste a transformação Coluna Derivada para a superfície de design.  
  
4.  Conecte a transformação de Coluna Derivada ao fluxo de dados arrastando um conector da fonte ou da transformação anterior para a transformação de Coluna Derivada.  
  
5.  Clique duas vezes na transformação de Coluna Derivada.  
  
6.  Na caixa de diálogo **Editor de Transformação Coluna Derivada**, crie as expressões para usar como condições arrastando variáveis, colunas, funções e operadores para a coluna **Expressão** na grade. Como alternativa, é possível digitar a expressão na coluna **Expressão**.  
  
    > [!NOTE]  
    >  Se a expressão não for válida, o texto da expressão será realçado e uma Dica de Ferramenta na coluna descreverá os erros.  
  
7.  Na lista **Coluna Derivada**, selecione **\<adicionar como uma nova coluna>** para gravar o resultado da avaliação da expressão em uma nova coluna ou selecione uma coluna existente para atualizar com o resultado da avaliação.  
  
     Se você optar por usar uma nova coluna, a caixa de diálogo **Editor de Transformação Coluna Derivada** avaliará a expressão e atribuirá um tipo de dados à coluna, dependendo do tipo de dados, tamanho, precisões, escala e página de código.  
  
8.  Se estiver usando uma nova coluna, selecione um tipo de dados na lista **Tipo de Dados**. Dependendo do tipo de dados selecionado, atualize, opcionalmente, os valores nas colunas **Tamanho**, **Precisão**, **Escala** e **Página de Código**. Metadados de colunas existentes não podem ser alterados.  
  
9. Opcionalmente, modifique os valores na coluna **Nome da Coluna Derivada**.  
  
10. Para configurar a saída de erro, clique em **Configurar Saída de Erro**. Para obter mais informações, consulte [Configurar uma saída de erro em um componente de fluxo de dados](../../../integration-services/troubleshooting/configure-an-error-output-in-a-data-flow-component.md).  
  
11. Clique em **OK**.  
  
12. Para salvar o pacote atualizado, clique em **Salvar Itens Selecionados** no menu **Arquivo** .  
  
## Consulte também  
 [Transformação Coluna Derivada](../../../integration-services/data-flow/transformations/derived-column-transformation.md)   
 [Tipos de dados do Integration Services](../../../integration-services/data-flow/integration-services-data-types.md)   
 [Transformações do Integration Services](../../../integration-services/data-flow/transformations/integration-services-transformations.md)   
 [Caminhos do Integration Services](../../../integration-services/data-flow/integration-services-paths.md)   
 [Tarefa de Fluxo de Dados](../../../integration-services/control-flow/data-flow-task.md)   
 [Expressões do Integration Services &#40;SSIS&#41;](../../../integration-services/expressions/integration-services-ssis-expressions.md)  
  
  