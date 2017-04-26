---
title: "REPLACE (Express&#227;o SSIS) | Microsoft Docs"
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
  - "substituindo expressão de cadeia de caracteres"
  - "função REPLACE"
ms.assetid: a6837043-ea70-4c6a-9c7a-6868b02b2adc
caps.latest.revision: 41
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 41
---
# REPLACE (Express&#227;o SSIS)
  Retorna uma expressão de caractere depois de substituir uma cadeia de caracteres na expressão por uma cadeia diferente ou vazia.  
  
> [!NOTE]  
>  A função REPLACE geralmente usa cadeias de caracteres longos. As consequências do truncamento podem ser controladas muito bem ou causam um aviso ou um erro. Para obter mais informações, consulte [Sintaxe &#40;SSIS&#41;](../../integration-services/expressions/syntax-ssis.md).  
  
## Sintaxe  
  
```  
  
REPLACE(character_expression,searchstring,replacementstring)  
```  
  
## Argumentos  
 *character_expression*  
 É uma expressão de caractere válida que a função pesquisa.  
  
 *searchstring*  
 É uma expressão de caractere válida que a função tenta localizar.  
  
 *replacementstring*  
 É uma expressão de caractere válida que é a expressão de substituição.  
  
## Tipos de resultado  
 DT_WSTR  
  
## Comentários  
 O comprimento de *searchstring* não deve ser zero.  
  
 O comprimento de *replacementstring* pode ser zero.  
  
 Os argumentos *searchstring* e *replacementstring* podem usar variáveis e colunas.  
  
 REPLICATE funciona apenas com o tipo de dados DT_WSTR. Os argumentos *character_expression1, character_expression2,* e *character_expression3*, que são literais de cadeia de caracteres ou colunas de dados com o tipo de dados DT_STR, são implicitamente convertidos para o tipo de dados DT_WSTR antes de REPLACE executar sua operação. Outros tipos de dados devem ser explicitamente convertidos para o tipo de dados DT_WSTR. Para obter mais informações, consulte [Cast &#40;Expressão do SSIS&#41;](../../integration-services/expressions/cast-ssis-expression.md).  
  
 REPLACE retornará um resultado nulo se qualquer argumento for nulo.  
  
## Exemplos de expressões  
 Este exemplo usa um literal de cadeia de caracteres. O resultado de retorno é “Toda Bicicleta de Terreno”.  
  
```  
REPLACE("Mountain Bike", "Mountain","All Terrain")  
```  
  
 Este exemplo remove a cadeia de caracteres "Bike" da coluna **Product**.  
  
```  
REPLACE(Product, "Bike","")  
```  
  
 Este exemplo substitui valores na coluna **DaysToManufacture**. A coluna tem um tipo de dados Integer e a expressão inclui conversão de **DaysToManufacture** para o tipo de dados DT_WSTR.  
  
```  
REPLACE((DT_WSTR,8)DaysToManufacture,"6","5")  
```  
  
## Consulte também  
 [SUBSTRING &#40;Expressão SSIS&#41;](../../integration-services/expressions/substring-ssis-expression.md)   
 [Funções &#40;Expressão do SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  