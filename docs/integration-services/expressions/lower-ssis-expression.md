---
title: "LOWER (Express&#227;o SSIS) | Microsoft Docs"
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
  - "convertendo caracteres maiúsculos em minúsculos"
  - "função LOWER"
  - "caracteres maiúsculos [Integration Services]"
  - "caracteres minúsculos"
ms.assetid: 109328e1-5604-40ff-895e-f2e7c13fff41
caps.latest.revision: 33
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 33
---
# LOWER (Express&#227;o SSIS)
  Retorna uma expressão character depois de converter caracteres maiúsculos em minúsculos.  
  
## Sintaxe  
  
```  
  
LOWER(character_expression)  
```  
  
## Argumentos  
 *character_expression*  
 É uma expressão de caractere para converter para caracteres minúsculos.  
  
## Tipos de resultado  
 DT_WSTR  
  
## Comentários  
 LOWER só funciona com o tipo de dados DT_WSTR. Um argumento *character_expression* que é um literal de cadeia de caracteres ou uma coluna de dados com o tipo de dados DT_STR é implicitamente convertido para o tipo de dados DT_WSTR antes de LOWER executar sua operação. Outros tipos de dados devem ser explicitamente convertidos para o tipo de dados DT_WSTR. Para obter mais informações, consulte [Tipos de dados do Integration Services](../../integration-services/data-flow/integration-services-data-types.md) e [Cast &#40;Expressão SSIS&#41;](../../integration-services/expressions/cast-ssis-expression.md).  
  
 LOWER retornará um resultado nulo se o argumento for nulo.  
  
## Exemplos de expressões  
 Este exemplo converte um literal de cadeia de caracteres para caracteres minúsculos. O resultado de retorno é "Nova Iorque".  
  
```  
LOWER("New York")  
```  
  
 Este exemplo converte todos os caracteres da coluna de entrada **Color** , exceto o primeiro caractere, para caracteres minúsculos. Se Color for AMARELO, o resultado de retorno será "Amarelo". Para obter mais informações, consulte [SUBSTRING &#40;Expressão do SSIS&#41;](../../integration-services/expressions/substring-ssis-expression.md).  
  
```  
LOWER(SUBSTRING(Color, 2, 15))  
```  
  
 Este exemplo converte o valor na variável **CityName** para caracteres minúsculos.  
  
```  
LOWER(@CityName)  
```  
  
## Consulte também  
 [UPPER &#40;Expressão do SSIS&#41;](../../integration-services/expressions/upper-ssis-expression.md)   
 [Funções &#40;Expressão do SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  