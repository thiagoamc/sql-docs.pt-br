---
title: "&gt;= (Maior que ou igual a) (Express&#227;o SSIS) | Microsoft Docs"
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
  - "<= (operador menor que ou igual a)"
  - "maior que ou igual a (>=)"
ms.assetid: 52ad504d-2f54-44de-b5e2-620577c0e289
caps.latest.revision: 50
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 50
---
# &gt;= (Maior que ou igual a) (Express&#227;o SSIS)
  Executa uma comparação para determinar se a primeira expressão é maior que ou igual à segunda. O avaliador de expressões converte automaticamente muitos tipos de dados antes de executar a comparação.  
  
> [!NOTE]  
>  Este operador não aceita comparações que usam os tipos de dados DT_TEXT, DT_NTEXT ou DT_IMAGE.  
  
 No entanto, alguns tipos de dados requerem que a expressão inclua uma conversão explícita antes de ser avaliada com êxito. Para obter mais informações sobre conversões legais entre tipos de dados, consulte [Conversão &#40;Expressão do SSIS&#41;](../../integration-services/expressions/cast-ssis-expression.md).  
  
> [!NOTE]  
>  Não há nenhum espaço entre os dois caracteres neste operador.  
  
## Sintaxe  
  
```  
  
expression1 >= expression2  
  
```  
  
## Argumentos  
 *expression1, expression2*  
 É qualquer expressão válida.  
  
## Tipos de resultado  
 DT_BOOL  
  
## Comentários  
 Se qualquer expressão na comparação for nula, o resultado da comparação será nulo. Se ambas as expressões forem nulas, o resultado será nulo.  
  
 O conjunto de expressões, *expression1* e *expression2*, deve seguir uma destas regras:  
  
-   **Numérico** Ambas *expression1* e *expression2* devem ser um tipo de dados numérico. A intersecção dos tipos de dados deve ser um tipo de dados numérico, como especificado nas regras sobre as conversões numéricas implícitas que o avaliador de expressões executa. A interseção dos dois tipos de dados numéricos não pode ser nula. Para obter mais informações, consulte [Integration Services Data Types in Expressions](../../integration-services/expressions/integration-services-data-types-in-expressions.md).  
  
-   **Character** Tanto *expression1* quanto *expression2* devem ser avaliadas como um tipo de dados DT_STR ou DT_WSTR. As duas expressões podem ser avaliadas como tipos de dados de cadeia diferentes.  
  
    > [!NOTE]  
    >  Comparações de cadeia de caracteres diferenciam maiúsculas de minúsculas, acentuação, kana e largura.  
  
-   **Date, Time, ou Date/Time** Tanto *expression1* quanto *expression2* devem ser avaliadas como um dos seguintes tipos de dados: DT_DBDATE, DT_DATE, DT_DBTIME, DT_DBTIME2, DT_DBTIMESTAMP, DT_DBTIMESTAMP2, DT_DBTIMESTAPMOFFSET ou DT_FILETIME.  
  
    > [!NOTE]  
    >  O sistema não aceita comparações entre uma expressão que avalia um tipo de dados de hora e uma expressão que avalia um tipo de dados de data ou data/hora. O sistema gera um erro.  
  
     Ao comparar as expressões, o sistema aplica as seguintes regras de conversão na ordem listada:  
  
    -   Quando as duas expressões avaliarem o mesmo tipo de dados, uma comparação daquele tipo de dados é executada.  
  
    -   Se uma expressão for um tipo de dados DT_DBTIMESTAMPOFFSET, a outra expressão será convertida implicitamente para DT_DBTIMESTAMPOFFSET, e uma comparação de DT_DBTIMESTAMPOFFSET será executada. Para obter mais informações, consulte [Integration Services Data Types in Expressions](../../integration-services/expressions/integration-services-data-types-in-expressions.md).  
  
    -   Se uma expressão for um tipo de dados DT_DBTIMESTAMP2, a outra expressão será convertida implicitamente para DT_DBTIMESTAMP2, e uma comparação de DT_DBTIMESTAMP2 será executada.  
  
    -   Se uma expressão for um tipo de dados DT_DBTIME2, a outra expressão será convertida implicitamente para DT_DBTIME2, e uma comparação de DT_DBTIME2 será executada.  
  
    -   Se uma expressão for de um tipo diferente de DT_DBTIMESTAMPOFFSET, DT_DBTIMESTAMP2 ou DT_DBTIME2, as expressões serão convertidas para o tipo de dados DT_DBTIMESTAMP antes de serem comparadas.  
  
     Ao comparar as expressões, o sistema faz as seguintes suposições:  
  
    -   Se cada expressão for um tipo de dados que inclui segundos fracionais, o sistema assumirá que o tipo de dados com o número de dígitos mínimo para os segundos fracionais tem zeros nos dígitos restantes.  
  
    -   Se cada expressão for um tipo de dados de data, mas somente um tiver um deslocamento de fuso horário, o sistema assumirá que o tipo de dados de data sem o deslocamento de fuso horário estará em UTC (Tempo Universal Coordenado).  
  
 Para obter mais informações sobre tipos de dados, consulte [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
## Exemplos de expressões  
 Este exemplo avaliará como TRUE se a data atual for 4 de julho de 2003 ou anterior. Para obter mais informações, consulte [GETDATE &#40;Expressão SSIS&#41;](../../integration-services/expressions/getdate-ssis-expression.md).  
  
```  
"7/4/2003" >= GETDATE()  
```  
  
 Este exemplo avaliará como TRUE se o valor na coluna **ListPrice** for maior que ou igual a 500.  
  
```  
ListPrice >= 500  
```  
  
 Este exemplo usa a variável **LPrice**. Ele avaliará como TRUE se o valor de **LPrice** for maior que ou igual a 500. O tipo de dados da variável deve ser numérico para que a expressão seja analisada.  
  
```  
@LPrice >= 500  
```  
  
## Consulte também  
 [&#62; &#40;Maior que&#41; &#40;Expressão SSIS&#41;](../../integration-services/expressions/greater-than-ssis-expression.md)   
 [&#60; &#40;Menor que&#41; &#40;Expressão SSIS&#41;](../../integration-services/expressions/less-than-ssis-expression.md)   
 [&#60;= &#40;Menor que ou igual a&#41; &#40;Expressão SSIS&#41;](../../integration-services/expressions/less-than-or-equal-to-ssis-expression.md)   
 [Precedência de operador e capacidade de associação](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Operadores &#40;Expressão do SSIS&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  