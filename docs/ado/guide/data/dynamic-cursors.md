---
title: "Cursores dinâmicos | Microsoft Docs"
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
- cursors [ADO], dynamic
- dynamic cursors [ADO]
ms.assetid: 00460f30-8cf7-494e-82df-41012f40ae51
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: dbeb8f40cf6d1ad91a59fa9719410f26386953d4
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="dynamic-cursors"></a>Cursores dinâmicos
Cursores dinâmicos detectam todas as alterações feitas nas linhas no conjunto de resultados, independentemente se ocorrerem as alterações de dentro do cursor ou por outros usuários fora do cursor. Todos os insert, update e instruções delete feitas por todos os usuários são visíveis pelo cursor. O cursor dinâmico pode detectar todas as alterações feitas com as linhas, a ordem e a valores no conjunto de resultados depois que o cursor é aberto. As atualizações feitas fora do cursor não são visíveis até serem confirmadas (a menos que o nível de isolamento de transação do cursor é definido como "").  
  
 Por exemplo, suponha que um cursor dinâmico busca duas linhas e o outro aplicativo e, em seguida, atualiza uma dessas linhas e exclui a outra. Se o cursor dinâmico, em seguida, agrupa essas linhas, ele não encontrar a linha excluída, mas ele exibirá os novos valores para a linha atualizada.  
  
 O cursor dinâmico é uma boa opção se seu aplicativo deve detectar todas as atualizações simultâneas feitas por outros usuários. Use o **adOpenDynamic CursorTypeEnum** para indicar que você deseja usar um cursor dinâmico no ADO.  
  
## <a name="see-also"></a>Consulte também  
 [Cursores de somente avanço](../../../ado/guide/data/forward-only-cursors.md)   
 [Cursores estáticos](../../../ado/guide/data/static-cursors.md)   
 [Cursores do conjunto de chaves](../../../ado/guide/data/keyset-cursors.md)
