---
title: "Número de propriedade (ADO) | Microsoft Docs"
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
- Error::Number
- Error::GetNumber
- Error::get_Number
helpviewer_keywords:
- number property [ADO]
ms.assetid: f92323c5-dd11-4a63-a505-d9014a0f067f
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f6a98f38098d936ea6c2eee03b28d969f1c0e506
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="number-property-ado"></a>Propriedade de número (ADO)
Indica o número que identifica exclusivamente um [erro](../../../ado/reference/ado-api/error-object.md) objeto.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna um **longo** valor pode corresponder a uma da [ErrorValueEnum](../../../ado/reference/ado-api/errorvalueenum.md) constantes.  
  
## <a name="remarks"></a>Remarks  
 Use o **número** propriedade para determinar qual erro ocorreu. O valor da propriedade é um número exclusivo que corresponde à condição de erro.  
  
 O [erros](../../../ado/reference/ado-api/errors-collection-ado.md) coleção retorna um HRESULT em formato hexadecimal (por exemplo, 0x80004005) ou valor longo (por exemplo, 2147467259). Esses HRESULTs podem ser gerados por componentes subjacentes, como OLE DB ou até mesmo OLE em si. Para obter mais informações sobre esses números, consulte [erros (OLE DB)](http://msdn.microsoft.com/en-us/ed74e62d-4948-4eeb-a7c9-fd7ad46af7fd) no [referência do programador de DB OLE](http://msdn.microsoft.com/en-us/3c5e2dd5-35e5-4a93-ac3a-3818bb43bbf8)*.*  
  
## <a name="applies-to"></a>Aplica-se a  
 [Objeto Error](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>Consulte também  
 [Descrição, HelpContext, HelpFile, NativeError, número, fonte e exemplo de propriedades de SQLState (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Descrição, HelpContext, HelpFile, NativeError, número, fonte e exemplo de propriedades de SQLState (VC + +)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Propriedade Description](../../../ado/reference/ado-api/description-property.md)   
 [Propriedades HelpContext e HelpFile](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)   
 [Propriedade Source (Erro ADO)](../../../ado/reference/ado-api/source-property-ado-error.md)
