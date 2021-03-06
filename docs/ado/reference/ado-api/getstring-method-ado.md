---
title: "Método GetString (ADO) | Microsoft Docs"
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
apitype: COM
f1_keywords:
- Recordset20::raw_GetString
- Recordset20::GetString
helpviewer_keywords:
- GetString method [ADO]
ms.assetid: 92452940-b2a7-456e-94fc-3780c71da33c
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 03449fb395e9c4448f7111728adb392facae9921
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="getstring-method-ado"></a>Método GetString (ADO)
Retorna o [registros](../../../ado/reference/ado-api/recordset-object-ado.md) como uma cadeia de caracteres.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
Variant = recordset.GetString(StringFormat, NumRows, ColumnDelimiter, RowDelimiter, NullExpr)  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna o **registros** como um valor de cadeia de caracteres **Variant** (BSTR).  
  
#### <a name="parameters"></a>Parâmetros  
 *StringFormat*  
 Um [StringFormatEnum](../../../ado/reference/ado-api/stringformatenum.md) valor que especifica como o **registros** devem ser convertidas em uma cadeia de caracteres. O *RowDelimiter*, *ColumnDelimiter*, e *NullExpr* parâmetros são usados apenas com uma *StringFormat* de  **adClipString**.  
  
 *NumRows*  
 Opcional. O número de linhas a ser convertido no **registros**. Se *NumRows* não for especificado, ou se for maior que o número total de linhas no **Recordset**, em seguida, todas as linhas a **Recordset** são convertidos.  
  
 *ColumnDelimiter*  
 Opcional. Um delimitador usado entre colunas, se especificado, caso contrário, o caractere de tabulação.  
  
 *RowDelimiter*  
 Opcional. Um delimitador usado entre linhas, se especificado, caso contrário, o caractere de retorno de CARRO.  
  
 *NullExpr*  
 Opcional. Uma expressão usada no lugar de um valor nulo, se especificado, caso contrário, a cadeia de caracteres vazia.  
  
## <a name="remarks"></a>Remarks  
 Dados de linha, mas nenhum dado de esquema, é salvo para a cadeia de caracteres. Portanto, um **registros** não pode ser reaberto usando essa cadeia de caracteres.  
  
 Esse método é equivalente a RDO **GetClipString** método.  
  
## <a name="applies-to"></a>Aplica-se a  
 [Objeto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Consulte também  
 [Exemplo do método GetString (VB)](../../../ado/reference/ado-api/getstring-method-example-vb.md)
