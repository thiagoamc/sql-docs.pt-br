---
title: Grupo de objeto (ADOX) | Microsoft Docs
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
- Group
helpviewer_keywords:
- group object [ADOX]
ms.assetid: 55ef0ade-68ea-4da5-8aa5-4cd27d1f6d1e
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 89733cc0f4533320e07d701f6645e64dac224fe3
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="group-object-adox"></a>Objeto de grupo (ADOX)
Representa uma conta de grupo que tenha permissões de acesso dentro de um banco de dados protegido.  
  
## <a name="remarks"></a>Remarks  
 O [grupos](../../../ado/reference/adox-api/groups-collection-adox.md) coleção de um [catálogo](../../../ado/reference/adox-api/catalog-object-adox.md) representa as contas de grupo Todos do catálogo. O **grupos** coleção para um [usuário](../../../ado/reference/adox-api/user-object-adox.md) representa apenas o grupo ao qual o usuário pertence.  
  
 Com as propriedades, coleções e métodos de um **grupo** do objeto, você pode:  
  
-   Identificar o grupo com o [nome](../../../ado/reference/adox-api/name-property-adox.md) propriedade.  
  
-   Determinar se um grupo tem de leitura, gravação ou exclusão de permissões com a [GetPermissions](../../../ado/reference/adox-api/getpermissions-method-adox.md) e [SetPermissions](../../../ado/reference/adox-api/setpermissions-method-adox.md) métodos.  
  
-   Acessar as contas de usuário que possuem membros no grupo com o [usuários](../../../ado/reference/adox-api/users-collection-adox.md) coleção.  
  
-   Acessar as propriedades específicas do provedor com o [propriedades](../../../ado/reference/ado-api/properties-collection-ado.md) coleção.  
  
 Esta seção contém o tópico a seguir.  
  
-   [Propriedades, Métodos e Eventos do objeto Group](../../../ado/reference/adox-api/group-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Consulte também  
 [Coleção de grupos (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)   
 [Coleção Users (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)
