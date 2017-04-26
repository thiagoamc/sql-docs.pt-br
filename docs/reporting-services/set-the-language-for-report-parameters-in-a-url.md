---
title: "Definir o idioma dos par&#226;metros do relat&#243;rio em uma URL | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "substituindo as definições de idioma do relatório"
  - "servidores de relatório [Reporting Services], configurações de linguagem"
  - "linguagens [Reporting Services]"
  - "acesso de URL [Reporting Services], substituições de linguagem"
  - "considerações internacionais [Reporting Services]"
  - "considerações globais [Reporting Services]"
ms.assetid: e1ccf22f-80d6-45bc-aae0-f5f263275092
caps.latest.revision: 29
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 29
---
# Definir o idioma dos par&#226;metros do relat&#243;rio em uma URL
  O parâmetro de acesso de URL *rs:ParameterLanguage* reduz o problema de os parâmetros de relatório sensíveis a cultura, como datas, horas, moeda e números serem interpretados por meio do idioma do navegador. Com o *rs:ParameterLanguage*, a URL agora é interpretada independentemente do navegador. Por exemplo, se o servidor de relatório for definido como uma configuração regional do alemão, mas um usuário estiver acessando um relatório via uma URL usando um navegador definido com inglês norte-americano, os valores do parâmetro que são transmitidos para um servidor de relatório serão interpretados incorretamente.  
  
 Considere a URL a seguir para um relatório:  
  
```  
http://myrshost/Reportserver?/SampleReports/Product+Line+Sales&rs:Command=Render&StartDate=4/10/2008&EndDate=11/10/2008  
```  
  
 No caso acima, o servidor, executado em uma cultura de "de-de", gera uma URL por meio de uma assinatura de e-mail ou um hiperlink. O hyperlink indica que o relatório deve ser parametrizado pela data de início de 04 de outubro de 2008 e uma data de término de 11 de outubro de 2008 de acordo com os padrões de data/hora alemães. Entretanto, um usuário que está acessando a URL por meio de um navegador definido como "en-us" força o servidor a interpretar os valores como 10 de abril de 2008 e 10 de novembro de 2008 de acordo com os padrões de data/hora do inglês norte-americano. Para corrigir o problema, o *rs:ParameterLanguage* pode ser usado para substituir o idioma do navegador para interpretação de parâmetro:  
  
```  
http://myrshost/Reportserver?/SampleReports/Product+Line+Sales&rs:Command=Render&StartDate=4/10/2008&EndDate=11/10/2008&rs:ParameterLanguage=de-DE  
```  
  
 Além de um valor **true** e **false** para o parâmetro de acesso da URL *rc:Parameters*, agora você pode transmitir um valor de **Recolhido**. Ao usar *rc:Parameters*=**Recolhido** em uma URL, a área de prompt do parâmetro do visualizador de HTML será recolhida, mas ainda poderá ser alternada pelo usuário. Um valor igual a **false** remove a área de prompt de parâmetro da barra de ferramentas do visualizador de HTML e a torna indisponível para o usuário final.  
  
## Consulte também  
 [Acesso à URL &#40;SSRS&#41;](../reporting-services/url-access-ssrs.md)   
 [Referência de parâmetro de acesso de URL](../reporting-services/url-access-parameter-reference.md)  
  
  