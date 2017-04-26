---
title: "Truncamento de dados (SSIS) | Microsoft Docs"
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
  - "dados truncados"
  - "truncamento de dados [Integration Services]"
  - "expressões [Integration Services], truncamento de dados"
  - "opções de truncamento [Integration Services]"
ms.assetid: 02461e15-49ca-445b-abb3-5c369c283ec2
caps.latest.revision: 37
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 37
---
# Truncamento de dados (SSIS)
  Converter os valores de um tipo de dados para outro pode fazer com que os valores sejam truncados.  
  
 O truncamento pode ocorrer ao:  
  
-   A conversão de dados da cadeia de caracteres de um *DT_WSTR* para um *DT_STR* com o mesmo tamanho, caso a cadeia de caracteres original contenha caracteres de byte duplo.  
  
-   Na conversão de um inteiro de um *DT_I4* para um *DT_I2*, pode haver perda de dígitos significativos.  
  
-   Converter um inteiro sem sinal em um inteiro com sinal, os dígitos significativos podem ser perdidos.  
  
-   Na conversão de um número real de um *DT_R8* para um *DT_R4*, pode haver perda dígitos não significativos  
  
-   Na conversão de um inteiro de um *DT_I4* para um *DT_R4*, pode haver perda dígitos não significativos.  
  
 O avaliador de expressão identifica conversões explícitas que podem causar truncamento e emite um aviso quando a expressão é analisada. Por exemplo, o avaliador de expressão o advertirá se uma cadeia de 30 caracteres for convertida em uma cadeia de 20 caracteres.  
  
 No entanto, o truncamento não é verificado no tempo de execução. Na execução, os dados são truncados sem aviso. Porém, a maioria dos adaptadores de dados e transformações oferece suporte para as saídas de erro que podem lidar com a disposição das linhas de erro.  
  
 Para obter mais informações sobre como tratar o truncamento de dados, consulte [Tratamento de erros em dados](../../integration-services/data-flow/error-handling-in-data.md)  
  
  