---
title: "Grupos de coleção (ADOX) | Microsoft Docs"
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
- Groups
- User::Groups
- Catalog::Groups
helpviewer_keywords:
- Groups collection [ADOX]
ms.assetid: 09aa7b0a-69d5-4564-80a7-20ad8189670f
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2a19ec44a3d6bbea3477d64ff7618c6a5d4ad57c
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="groups-collection-adox"></a>Coleção de grupos (ADOX)
Contém todos os armazenados [grupo](../../../ado/reference/adox-api/group-object-adox.md) objetos de um catálogo ou usuário.  
  
## <a name="remarks"></a>Remarks  
 O **grupos** coleção de um [catálogo](../../../ado/reference/adox-api/catalog-object-adox.md) representa todas as contas de grupo do catálogo. O **grupos** coleção para um [usuário](../../../ado/reference/adox-api/user-object-adox.md) representa apenas o grupo ao qual o usuário pertence.  
  
 O [Append](../../../ado/reference/adox-api/append-method-adox-groups.md) método para um **grupos** coleção é exclusiva para ADOX. Você pode:  
  
-   Adicionar um novo grupo de segurança para a coleção com o **Append** método.  
  
 As propriedades e os métodos restantes são padrão para coleções de ADO. Você pode:  
  
-   Acessar um grupo na coleção com o [Item](../../../ado/reference/ado-api/item-property-ado.md) propriedade.  
  
-   Retorna o número de grupos contidos na coleção com o [contagem](../../../ado/reference/ado-api/count-property-ado.md) propriedade.  
  
-   Remover um grupo de coleção com o [excluir](../../../ado/reference/adox-api/delete-method-adox-collections.md) método.  
  
-   Atualizar os objetos na coleção para refletir o esquema de banco de dados atual com o [atualização](../../../ado/reference/ado-api/refresh-method-ado.md) método.  
  
> [!NOTE]
>  Antes de anexar um **grupo** o objeto para o **grupos** coleção de um **usuário** objeto, um **grupo** objeto com o mesmo [ Nome](../../../ado/reference/adox-api/name-property-adox.md) como um a ser acrescentada já deve existir no **grupos** coleção do **catálogo**.  
  
 Esta seção contém o tópico a seguir.  
  
-   [Propriedades, Métodos e Eventos da coleção Groups](../../../ado/reference/adox-api/groups-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Consulte também  
 [Objeto de catálogo (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Objeto Group (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)
