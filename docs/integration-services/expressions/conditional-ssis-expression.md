---
title: "? : (Condicional) (Express&#227;o SSIS) | Microsoft Docs"
ms.custom: 
  - "ssisdev020617"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "operador condicional (?:)"
  - "?: (operador condicional)"
ms.assetid: d38e6890-7338-4ce0-a837-2dbb41823a37
caps.latest.revision: 49
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 49
---
# ? : (Condicional) (Express&#227;o SSIS)
  Retorna uma de duas expressões baseadas na avaliação de uma expressão booliana. Se a expressão Booleana for avaliada como TRUE, a primeira expressão será avaliada e o resultado será o resultado da expressão. Se a expressão Booleana for avaliada como FALSE, a segunda expressão será avaliada e seu resultado será o resultado da expressão.  
  
## Sintaxe  
  
```  
  
boolean_expression?expression1:expression2  
  
```  
  
## Argumentos  
 *boolean_expression*  
 É qualquer expressão válida que é avaliada como TRUE, FALSE ou NULL.  
  
 *expression1*  
 É qualquer expressão válida.  
  
 *expression2*  
 É qualquer expressão válida.  
  
## Tipos de resultado  
 O tipo de dados de *expression1* ou *expression2*.  
  
## Comentários  
 Se *boolean_expression* for avaliada como NULL, o resultado da expressão será NULL. Se uma expressão selecionada, *expression1* ou *expression2* for NULL, o resultado será NULL. Se uma expressão selecionada não for NULL, mas aquela não selecionada for NULL, o resultado será o valor da expressão selecionada.  
  
 Se *expression1* e *expression2* tiverem o mesmo tipo de dados, o resultado será aquele tipo de dados. As regras adicionais a seguir se aplicam aos tipos de resultado:  
  
-   O tipo de dados DT_TEXT requer que *expression1* e *expression2* tenham a mesma página de código.  
  
-   O comprimento de um resultado com o tipo de dados DT_BYTES é o comprimento do argumento mais longo.  
  
 O conjunto de expressão, *expression1* e *expression2*, deve ser avaliado como os tipos de dados válidos e seguir um destas regras:  
  
-   **Numérico** Ambas *expression1* e *expression2* devem ser um tipo de dados numérico. A intersecção dos tipos de dados deve ser um tipo de dados numérico, como especificado nas regras sobre as conversões numéricas implícitas que o avaliador de expressões executa. A interseção dos dois tipos de dados numéricos não pode ser nula. Para obter mais informações, consulte [Integration Services Data Types in Expressions](../../integration-services/expressions/integration-services-data-types-in-expressions.md).  
  
-   **Cadeia de caracteres** Ambas as *expression1* e *expression2* devem ser um tipo de dados String: DT_STR ou DT_WSTR. As duas expressões podem ser avaliadas como tipos de dados de cadeia diferentes. O resultado tem o tipo de dados DT_WSTR com um comprimento do argumento mais longo.  
  
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
 Este exemplo mostra uma expressão que condicionalmente é avaliada como `savannah` ou `unknown`.  
  
```  
@AnimalName == "Elephant"? "savannah": "unknown"  
```  
  
 Este exemplo mostra uma expressão que faz referências a uma coluna **ListPrice**. **ListPrice** tem o tipo de dados DT_CY. A expressão multiplica **ListPrice** condicionalmente por .2 ou .1.  
  
```  
ListPrice < 350.00 ? ListPrice * .2 : ListPrice * .1  
```  
  
## Consulte também  
 [Precedência de operador e capacidade de associação](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Operadores &#40;Expressão do SSIS&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  