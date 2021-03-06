---
title: "Atualizar o método (RDS) | Microsoft Docs"
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.component: reference
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Refresh
- RDS.DataControl::Refresh
- DataControl::Refresh
helpviewer_keywords:
- Refresh method [RDS]
ms.assetid: c90a8050-0ff4-4c83-9925-261f2f2ccfe9
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 26182bb5f3ec1d60b66e5c16bf403a1f427c8b87
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="refresh-method-rds"></a>Atualizar o método (RDS)
Repete a consulta de fonte de dados especificada no [conectar](../../../ado/reference/rds-api/connect-property-rds.md) propriedade e atualizações os resultados da consulta.  
  
> [!IMPORTANT]
>  Começando com o Windows 8 e Windows Server 2012, os componentes de servidor RDS não estão mais incluídos no sistema operacional Windows (veja o Windows 8 e [manual de compatibilidade do Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) para obter mais detalhes). Componentes de cliente RDS serão removidos em uma versão futura do Windows. Evite usar esse recurso em desenvolvimentos novos e planeje modificar os aplicativos que atualmente o utilizam. Aplicativos que usam o RDS devem migrar para [WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
DataControl.Refresh  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *DataControl*  
 Uma variável de objeto que representa um [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) objeto.  
  
## <a name="remarks"></a>Remarks  
 Você deve definir o [conectar](../../../ado/reference/rds-api/connect-property-rds.md), [servidor](../../../ado/reference/rds-api/server-property-rds.md), e [SQL](../../../ado/reference/rds-api/sql-property.md) propriedades antes de usar o **atualização** método. Todos os controles de associação de dados no formulário associado com um **RDS. DataControl** objeto refletirá o novo conjunto de registros. Qualquer pré-existente [registros](../../../ado/reference/ado-api/recordset-object-ado.md) objeto é liberado, e as alterações não salvas serão descartadas. O **atualização** método automaticamente torna o primeiro registro o atual.  
  
 É uma boa ideia para chamar o **atualização** método periodicamente ao trabalhar com dados. Se você recupera dados e deixe-o em um computador cliente por um tempo, é provável que se tornem desatualizados. É possível que as alterações que você fizer falhará, porque outra pessoa pode ter alterado o registro e enviada alterações antes de você.  
  
## <a name="applies-to"></a>Aplica-se a  
 [Objeto DataControl (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Consulte também  
 [Atualizar exemplo de método (VB)](../../../ado/reference/ado-api/refresh-method-example-vb.md)   
 [Atualizar exemplo de método (VBScript)](../../../ado/reference/rds-api/refresh-method-example-vbscript.md)   
 [Botões de comando do catálogo de endereços](../../../ado/guide/remote-data-service/address-book-command-buttons.md)   
 [Método CancelUpdate (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [Atualizar o método (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)   
 [Método SubmitChanges (RDS)](../../../ado/reference/rds-api/submitchanges-method-rds.md)


