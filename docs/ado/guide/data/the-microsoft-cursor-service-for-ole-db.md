---
title: "O serviço de Cursor do Microsoft OLE DB | Microsoft Docs"
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
helpviewer_keywords:
- cursor service for ole db [ADO]
- cursors [ADO], cursor service for OLE DB
ms.assetid: 1ac3bd9b-2d45-4cc8-88ec-bd8a218cfb49
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5dd9f4b279bd38028bb529dcdd0a49f32ffd7cc7
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="the-microsoft-cursor-service-for-ole-db"></a>O serviço Microsoft Cursor para OLE DB
Quando você seleciona um cursor do lado do cliente, ou defina o **CursorLocation** propriedade **adUseClient**, você está invocando o serviço de Cursor da Microsoft para OLE DB. Você também poderá ver referências para o "cliente Cursor mecanismo", que é essencialmente o mesmo significado no contexto do ADO. Esse serviço complementa as funções de suporte de cursor de provedores de dados. Como resultado, você pode perceber funcionalidade relativamente uniforme de todos os provedores de dados.  
  
 O serviço de Cursor do OLE DB disponibiliza propriedades dinâmicas e aprimora o comportamento de certos métodos. Por exemplo, o **otimizar** propriedade dinâmica permite a criação de índices temporários para facilitar a determinadas operações, como o **localizar** método.  
  
 O serviço de Cursor habilita o suporte para atualização em lotes em todos os casos. Ele também simula mais compatíveis com tipos de cursor, como cursores dinâmicos, quando um provedor de dados pode fornecer apenas cursores menor capacidade, como Cursores estáticos.  
  
## <a name="see-also"></a>Consulte também  
 [Serviço Microsoft Cursor para OLE DB (componente de serviço do ADO)](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md)
