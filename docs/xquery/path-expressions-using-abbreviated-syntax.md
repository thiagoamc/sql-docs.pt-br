---
title: "Usando a sintaxe em uma expressão de caminho abreviação | Microsoft Docs"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- axis step [XQuery]
- abbreviated syntax [XQuery]
ms.assetid: f83c2e41-5722-47c3-b5b8-bf0f8cbe05d3
caps.latest.revision: 23
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: cd4ed101bc96fb8c5c417ec1c47063d747af29df
ms.contentlocale: pt-br
ms.lasthandoff: 09/01/2017

---
# <a name="path-expressions---using-abbreviated-syntax"></a>Expressões de caminho - usando a sintaxe abreviada
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Todos os exemplos [Noções básicas sobre expressões de caminho no XQuery](../xquery/path-expressions-xquery.md) usam sintaxe não abreviada para expressões de caminho. A sintaxe não abreviada para uma etapa de eixo em uma expressão de caminho inclui o nome de eixo e teste de nó, separados por dois-pontos duplos e seguidos por zero ou mais qualificadores de etapa.  
  
 Por exemplo:  
  
```  
child::ProductDescription[attribute::ProductModelID=19]  
```  
  
 O XQuery oferece suporte para as abreviações a seguir para uso em expressões de caminho:  
  
-   O **filho** eixo é o eixo padrão. Portanto, o **filho::** eixo pode ser omitido de uma etapa em uma expressão. Por exemplo, `/child::ProductDescription/child::Summary` pode ser escrito como `/ProductDescription/Summary`.  
  
-   Um **atributo** eixo pode ser abreviado como @. Por exemplo, `/child::ProductDescription[attribute::ProductModelID=10]` pode ser escrito como `/ProudctDescription[@ProductModelID=10]`.  
  
-   Um **descendant-or-self::node()/** pode ser abreviado como / /. Por exemplo, `/descendant-or-self::node()/child::act:telephoneNumber` pode ser escrito como `//act:telephoneNumber`.  
  
     A consulta anterior recupera todos os números de telefone armazenados na coluna AdditionalContactInfo na tabela Contact. O esquema para AdditionalContactInfo é definido de forma que um \<telephoneNumber > elemento pode aparecer em qualquer lugar no documento. Então, para recuperar todos os números de telefone, você deve pesquisar cada nó no documento. A pesquisa inicia na raiz do documento e continua por todos os nós descendentes.  
  
     A consulta a seguir recupera todos os números de telefone de um contato de cliente específico:  
  
    ```  
    SELECT AdditionalContactInfo.query('             
                declare namespace act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";             
                declare namespace crm="http://schemas.adventure-works.com/Contact/Record";             
                declare namespace ci="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";             
                /descendant-or-self::node()/child::act:telephoneNumber             
                ') as result             
    FROM Person.Contact             
    WHERE ContactID=1             
    ```  
  
     Se você substituir a expressão de caminho com a sintaxe abreviada, `//act:telephoneNumber`, receberá os mesmos resultados.  
  
-   O **self:: node ()** em uma etapa pode ser abreviado como um único ponto (.). No entanto, o ponto não é equivalente nem intercambiável com o **self:: node ()**.  
  
     Por exemplo, na consulta a seguir, o uso de um ponto representa um valor e não um nó:  
  
    ```  
    ("abc", "cde")[. > "b"]  
    ```  
  
-   O **pai:: node ()** em uma etapa pode ser abreviado como um ponto duplo (.).  
  
  