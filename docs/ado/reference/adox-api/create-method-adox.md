---
title: "Criar método (ADOX) | Microsoft Docs"
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
- _Catalog::raw_Create
- _Catalog::Create
helpviewer_keywords:
- Create method [ADOX]
ms.assetid: 64f5c21c-b581-42d8-bdc7-c4f1bebaf105
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 81c480c08a9d214ab8d35730c4aa34465d418d27
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="create-method-adox"></a>Criar método (ADOX)
Cria um novo catálogo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
Catalog.Create ConnectString  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *ConnectString*  
 Um **cadeia de caracteres** valor usado para se conectar à fonte de dados.  
  
## <a name="remarks"></a>Remarks  
 O **criar** método cria e abre um novo ADO [Conexão](../../../ado/reference/ado-api/connection-object-ado.md) à fonte de dados especificado em *ConnectString*. Se for bem-sucedido, o novo **Conexão** objeto é atribuído para o [ActiveConnection](../../../ado/reference/adox-api/activeconnection-property-adox.md) propriedade.  
  
 Se o provedor não oferece suporte a criação de novos catálogos, ocorrerá um erro.  
  
## <a name="applies-to"></a>Aplica-se a  
 [Objeto Catalog (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>Consulte também  
 [Criar um exemplo de método (VB)](../../../ado/reference/adox-api/create-method-example-vb.md)   
 [Propriedade ActiveConnection (ADOX)](../../../ado/reference/adox-api/activeconnection-property-adox.md)
