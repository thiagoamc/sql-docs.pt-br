---
title: 'C para SQL: data | Microsoft Docs'
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- date data type [ODBC]
- converting data from c to SQL types [ODBC], date
- data conversions from C to SQL types [ODBC], date
ms.assetid: bea087d3-911f-418b-b483-d2b5b334da19
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ba2869a8fb8272251f6a23df0808b12e68ec5a59
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="c-to-sql-date"></a>C para SQL: data
O identificador para o tipo de dados do ODBC C data é:  
  
 SQL_C_TYPE_DATE  
  
 A tabela a seguir mostra o ODBC SQL tipos de dados ao qual o data C dados pode ser convertida. Para obter uma explicação das colunas e os termos na tabela, consulte [converter dados de C para tipos de dados SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Identificador de tipo SQL|Teste|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Comprimento de bytes da coluna > = 10<br /><br /> Coluna de comprimento de byte < 10<br /><br /> Valor de dados não é uma data válida|n/d<br /><br /> 22001<br /><br /> 22008|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Comprimento de caracteres da coluna > = 10<br /><br /> Coluna de tamanho < 10 caracteres<br /><br /> Valor de dados não é uma data válida|n/d<br /><br /> 22001<br /><br /> 22008|  
|SQL_TYPE_DATE|Valor de dados é uma data válida<br /><br /> Valor de dados não é uma data válida|n/d<br /><br /> 22007|  
|SQL_TYPE_TIMESTAMP|Valor de dados é uma data válida [a]<br /><br /> Valor de dados não é uma data válida|n/d<br /><br /> 22007|  
  
 [a] a parte de hora do carimbo de hora é definida como zero.  
  
 Para obter informações sobre quais valores são válidos em uma estrutura SQL_C_TYPE_DATE, consulte [tipos de dados C](../../../odbc/reference/appendixes/c-data-types.md), anteriormente neste apêndice.  
  
 Quando dados de data C são convertidos em dados de SQL de caractere, os dados de caracteres resultante estão no "*aaaa*-*mm*-*dd*" formato.  
  
 O driver ignora o valor de comprimento/indicador ao converter dados de tipo de dados date C e pressupõe que o tamanho do buffer de dados é o tamanho do tipo de dados de data C. O valor de comprimento/indicador é passado a *StrLen_or_Ind* argumento **SQLPutData** e no buffer especificado com o *StrLen_or_IndPtr* argumento **SQLBindParameter**. O buffer de dados é especificado com o *DataPtr* argumento na **SQLPutData** e *ParameterValuePtr* argumento **SQLBindParameter**.
