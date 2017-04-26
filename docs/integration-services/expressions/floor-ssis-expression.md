---
title: "FLOOR (Express&#227;o SSIS) | Microsoft Docs"
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
  - "maior número inteiro menor que ou igual à expressão"
  - "função FLOOR [SSIS]"
ms.assetid: 168084db-badd-40f2-87b4-1f5bc45c3e24
caps.latest.revision: 33
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 33
---
# FLOOR (Express&#227;o SSIS)
  Retorna o maior inteiro que é menor que ou igual a uma expressão numérica.  
  
## Sintaxe  
  
```  
  
FLOOR(numeric_expression)  
```  
  
## Argumentos  
 *numeric_expression*  
 É uma expressão numérica válida.  
  
## Tipos de resultado  
 O tipo de dados numérico da expressão do argumento. O resultado é a parte inteira do valor calculado no mesmo tipo de dados que *numeric_expression.*  
  
## Comentários  
 FLOOR retornará um resultado nulo se o argumento for nulo.  
  
## Exemplos de expressões  
 Estes exemplos aplicam a função FLOOR aos valores positivos, negativos e zerados.  
  
```  
FLOOR(123.45)  
```  
  
 Retorna 123.00  
  
```  
FLOOR(-123.45)  
```  
  
 Retorna -124.00  
  
```  
FLOOR(0.00)  
```  
  
 Retorna 0.00  
  
## Consulte também  
 [CEILING &#40;Expressão do SSIS&#41;](../../integration-services/expressions/ceiling-ssis-expression.md)   
 [Funções &#40;Expressão do SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  