---
title: "Catálogo de objeto (ADOX) | Microsoft Docs"
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
- Catalog
helpviewer_keywords:
- Catalog object [ADOX]
ms.assetid: bb651639-a488-4e38-b6de-0ed99fa4dd92
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5d8f47b63022f481c5ed102bcc9e97f5fa563aea
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="catalog-object-adox"></a>Objeto de catálogo (ADOX)
Contém coleções ([tabelas](../../../ado/reference/adox-api/tables-collection-adox.md), [exibições](../../../ado/reference/adox-api/views-collection-adox.md), [usuários](../../../ado/reference/adox-api/users-collection-adox.md), [grupos](../../../ado/reference/adox-api/groups-collection-adox.md), e [procedimentos](../../../ado/reference/adox-api/procedures-collection-adox.md)) que Descreva o catálogo de esquema de uma fonte de dados.  
  
## <a name="remarks"></a>Remarks  
 Você pode modificar o **catálogo** objeto adicionando ou removendo objetos ou modificando os objetos existentes. Alguns provedores podem não dar suporte a todos os **catálogo** suporte somente para exibir informações de esquema ou objetos.  
  
 Com as propriedades e métodos de um **catálogo** do objeto, você pode:  
  
-   Abra o catálogo, definindo o [ActiveConnection](../../../ado/reference/adox-api/activeconnection-property-adox.md) propriedade ADO [Conexão](../../../ado/reference/ado-api/connection-object-ado.md) objeto ou uma cadeia de caracteres de conexão válido.  
  
-   Criar um novo catálogo com o [criar](../../../ado/reference/adox-api/create-method-adox.md) método.  
  
-   Determinar os proprietários de objetos em um **catálogo** com o [GetObjectOwner](../../../ado/reference/adox-api/getobjectowner-method-adox.md) e [SetObjectOwner](../../../ado/reference/adox-api/setobjectowner-method.md) métodos.  
  
 Esta seção contém o tópico a seguir.  
  
-   [Propriedades, Métodos e Eventos do objeto Catalog](../../../ado/reference/adox-api/catalog-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Consulte também  
 [Exemplo de propriedade ActiveConnection do catálogo (VB)](../../../ado/reference/adox-api/catalog-activeconnection-property-example-vb.md)   
 [Exemplo de propriedades de CommandText (VB) e comando](../../../ado/reference/adox-api/command-and-commandtext-properties-example-vb.md)   
 [Método Close da Conexão, exemplo de propriedade de tipo de tabela (VB)](../../../ado/reference/adox-api/connection-close-method-table-type-property-example-vb.md)   
 [Criar um exemplo de método (VB)](../../../ado/reference/adox-api/create-method-example-vb.md)   
 [Chaves de acrescentar o método, tipo de chave, RelatedColumn, RelatedTable e exemplo de propriedades de UpdateRule (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Coleção de parâmetros, o exemplo de comando de propriedade (VB)](../../../ado/reference/adox-api/parameters-collection-command-property-example-vb.md)   
 [Exemplo de propriedade ParentCatalog (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Procedimentos de acrescentar o exemplo de método (VB)](../../../ado/reference/adox-api/procedures-append-method-example-vb.md)   
 [Procedimentos de exemplo de método (VB)-excluir](../../../ado/reference/adox-api/procedures-delete-method-example-vb.md)   
 [Procedimentos de atualização de exemplo do método (VB)](../../../ado/reference/adox-api/procedures-refresh-method-example-vb.md)   
 [Exemplo de coleções de campos (VB) e modos de exibição](../../../ado/reference/adox-api/views-and-fields-collections-example-vb.md)   
 [Exibições de acrescentar o exemplo de método (VB)](../../../ado/reference/adox-api/views-append-method-example-vb.md)   
 [Coleção de modos de exibição, o exemplo da propriedade CommandText (VB)](../../../ado/reference/adox-api/views-collection-commandtext-property-example-vb.md)   
 [Exemplo de método (VB)-excluir exibições](../../../ado/reference/adox-api/views-delete-method-example-vb.md)   
 [Exemplo de método (VB) de atualização de modos de exibição](../../../ado/reference/adox-api/views-refresh-method-example-vb.md)   
 [Coleção de grupos (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)   
 [Coleção de procedimentos (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)   
 [Coleção de tabelas (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)   
 [Coleção de usuários (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)   
 [Coleção Views (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)
