---
title: O objeto de procedimento (ADOX) | Microsoft Docs
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
- Procedure
helpviewer_keywords:
- Procedure object [ADOX]
ms.assetid: 927bcf3e-32f5-4a80-98d3-600779f0732e
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b9cf7c0eb98db42defaf1723a9321eef78ea5bbe
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="procedure-object-adox"></a>Objeto de procedimento (ADOX)
Representa um procedimento armazenado. Quando usado em conjunto com o ADO [comando](../../../ado/reference/ado-api/command-object-ado.md) objeto, o **procedimento** objeto pode ser usado para adicionar, excluir ou modificar procedimentos armazenados.  
  
## <a name="remarks"></a>Remarks  
 O **procedimento** objeto permite que você crie um procedimento armazenado sem a necessidade de saber ou usar a sintaxe de "CREATE PROCEDURE" do provedor.  
  
 Com as propriedades de um **procedimento** do objeto, você pode:  
  
-   Identificar o procedimento com o [nome](../../../ado/reference/adox-api/name-property-adox.md) propriedade.  
  
-   Especifique o ADO **comando** objeto que pode ser usado para criar ou executar o procedimento com o [comando](../../../ado/reference/adox-api/command-property-adox.md) propriedade.  
  
-   Retornar informações de data com o [DateCreated](../../../ado/reference/adox-api/datecreated-property-adox.md) e [DateModified](../../../ado/reference/adox-api/datemodified-property-adox.md) propriedades.  
  
 Esta seção contém o tópico a seguir.  
  
-   [Propriedades, Métodos e Eventos do objeto Procedure](../../../ado/reference/adox-api/procedure-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Consulte também  
 [Exemplo de propriedades de CommandText (VB) e comando](../../../ado/reference/adox-api/command-and-commandtext-properties-example-vb.md)   
 [Coleção de parâmetros, o exemplo de comando de propriedade (VB)](../../../ado/reference/adox-api/parameters-collection-command-property-example-vb.md)   
 [Procedimentos de acrescentar o exemplo de método (VB)](../../../ado/reference/adox-api/procedures-append-method-example-vb.md)   
 [Procedimentos de exemplo de método (VB)-excluir](../../../ado/reference/adox-api/procedures-delete-method-example-vb.md)   
 [Coleção Procedures (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)
