---
title: Propriedade PageSize (ADO) | Microsoft Docs
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
- Recordset15::PageSize
helpviewer_keywords:
- PageSize property [ADO]
ms.assetid: e57930a6-46c4-4a17-a3b6-f79e94d5c9c7
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3f611c47acb81b661e7c99422a785d6fb1c0d489
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="pagesize-property-ado"></a>Propriedade PageSize (ADO)
Indica o número de registros constituem uma página no [registros](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="settings-and-return-values"></a>Configurações e valores de retorno  
 Define ou retorna um **longo** valor que indica o número de registros em uma página. O padrão é **10**.  
  
## <a name="remarks"></a>Remarks  
 Use o **PageSize** propriedade para determinar quantos registros compõem uma página lógica dos dados. Estabelecer um tamanho de página permite que você use o [AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md) propriedade para mover para o primeiro registro de uma determinada página. Isso é útil em cenários de servidor Web quando você deseja permitir que o usuário para página de dados, exibindo um determinado número de registros por vez.  
  
 Essa propriedade pode ser definida a qualquer momento, e seu valor será usado para calcular a localização do primeiro registro de uma determinada página.  
  
## <a name="applies-to"></a>Aplica-se a  
 [Objeto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Consulte também  
 [Exemplo de propriedades de PageSize (VB), PageCount e AbsolutePage](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vb.md)   
 [AbsolutePage, PageCount e exemplo de propriedades de PageSize (VC + +)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vc.md)   
 [Propriedade AbsolutePage (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)   
 [Propriedade PageCount (ADO)](../../../ado/reference/ado-api/pagecount-property-ado.md)
