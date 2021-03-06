---
title: "Gramática de forma formal | Microsoft Docs"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shape commands [ADO], shape grammar
- data shaping [ADO], shape grammar
ms.assetid: ea691475-0f03-4abe-a785-b77e77712d1d
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f9eb99feba381701f7e590add3906cd0285b2720
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="formal-shape-grammar"></a>Gramática de forma formal
Esta é a gramática formal para a criação de qualquer comando de forma:  
  
-   Termos gramaticais necessários são cadeias de caracteres de texto delimitadas por colchetes angulares ("<>").  
  
-   Termos opcionais são delimitados por colchetes ("[]").  
  
-   Alternativas são indicadas por uma barra oblíqua ("&#124;").  
  
-   Alternativas de repetição são indicadas por um sinal de reticências ("...").  
  
-   *Alpha* indica uma cadeia de caracteres de letras em ordem alfabética.  
  
-   *Dígito* indica uma cadeia de números.  
  
-   *Dígitos Unicode* indica uma cadeia de caracteres de dígitos de unicode.  
  
 Todos os outros termos são literais.  
  
|Termo|Definição|  
|----------|----------------|  
|\<shape-command>|FORMA [\<exp tabela > [[como] \<alias >]] [\<forma de ação >]|  
|\<table-exp>|{\<provider-command-text>} &#124;<br /><br /> (\<comando forma >) &#124;<br /><br /> TABELA \<entre aspas-name > &#124;<br /><br /> \<quoted-name>|  
|\<shape-action>|ACRESCENTAR \<lista de campos de um alias > &#124;<br /><br /> COMPUTAÇÃO \<lista de campos de um alias > [BY \<lista de campos >]|  
|\<aliased-field-list>|\<aliased-field> [, \<aliased-field...>]|  
|\<aliased-field>|\<field-exp> [[AS] \<alias>]|  
|\<field-exp>|(\<relation-exp>) &#124;<br /><br /> \<calculated-exp> &#124;<br /><br /> \<aggregate-exp> &#124;<br /><br /> \<new-exp>|  
|<relation_exp>|\<table-exp> [[AS] \<alias>]<br /><br /> RELATE \<relação-condicional-list >|  
|\<relation-cond-list>|\<Relação condicional > [, \<relação condicional >...]|  
|\<relation-cond>|\<nome do campo > TO \<filho ref >|  
|\<child-ref>|\<field-name> &#124;<br /><br /> PARÂMETRO \<ref param >|  
|\<param-ref>|\<number>|  
|\<field-list>|\<field-name> [, \<field-name>]|  
|\<aggregate-exp>|SUM(\<qualified-field-name>) &#124;<br /><br /> AVG(\<qualified-field-name>) &#124;<br /><br /> MIN(\<qualified-field-name>) &#124;<br /><br /> MAX(\<qualified-field-name>) &#124;<br /><br /> COUNT(\<qualified-alias> &#124; \<qualified-name>) &#124;<br /><br /> STDEV(\<qualified-field-name>) &#124;<br /><br /> ANY(\<qualified-field-name>)|  
|\<calculated-exp>|CALC(\<expression>)|  
|\<qualified-field-name>|\<alias>.[\<alias>...]\<field-name>|  
|\<alias>|\<quoted-name>|  
|\<field-name>|\<quoted-name> [[AS] \<alias>]|  
|\<quoted-name>|"\<string>" &#124;<br /><br /> '\<string>' &#124;<br /><br /> [\<string>] &#124;<br /><br /> \<name>|  
|\<qualified-name>|alias[.alias...]|  
|\<name>|Alpha [alfa &#124; dígito &#124; _ &#124; # &#124;: &#124;...]|  
|\<number>|Dígito [dígito...]|  
|\<new-exp>|NOVO \<tipo de campo > [(\<número > [, \<número >])]|  
|\<field-type>|Um tipo de dados OLE DB ou ADO.|  
|\<string>|caractere Unicode [caractere unicode....]|  
|\<expression>|Um Visual Basic para a expressão de aplicativos cujos operandos são outras colunas não CALC na mesma linha.|  
  
## <a name="see-also"></a>Consulte também  
 [Acessar linhas em um conjunto de registros hierárquico](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md)   
 [Visão geral de modelagem de dados](../../../ado/guide/data/data-shaping-overview.md)   
 [Provedores necessários para modelagem de dados](../../../ado/guide/data/required-providers-for-data-shaping.md)   
 [Cláusula APPEND de forma](../../../ado/guide/data/shape-append-clause.md)   
 [Comandos de forma em geral](../../../ado/guide/data/shape-commands-in-general.md)   
 [Cláusula COMPUTE de forma](../../../ado/guide/data/shape-compute-clause.md)   
 [Funções do Visual Basic for Applications](../../../ado/guide/data/visual-basic-for-applications-functions.md)
