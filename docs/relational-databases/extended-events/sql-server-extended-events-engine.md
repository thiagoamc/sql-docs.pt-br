---
title: Mecanismo de eventos estendidos do SQL Server | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
- xevents
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- extended events [SQL Server], engine
ms.assetid: d74642a5-42b9-4a15-aa3d-f98bfe695050
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e11bf82e65be3b127ca7ee6c4f43ab2b60531b71
ms.lasthandoff: 04/11/2017

---
# <a name="sql-server-extended-events-engine"></a>Mecanismo de eventos estendidos do SQL Server
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  O mecanismo de Eventos Estendidos do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] é uma coleção de serviços e objetos que:  
  
-   Habilita a definição de eventos.  
  
-   Habilita dados de evento de processamento.  
  
-   Gerencia serviços de eventos estendidos e objetos no sistema.  
  
-   Mantenha uma lista de sessões de eventos estendidos e gerencie o acesso àquela lista.  
  
 O mecanismo de eventos estendidos não fornece qualquer evento ou ações que ocorram quando um evento é disparado. Os processos que usam o mecanismo de evento estendido definem interação com o mecanismo. Estes processos adicionam pontos de evento e fornecem ações para que ocorram em resposta ao disparo do evento.  
  
 A ilustração seguinte mostra uma exibição simplificada de uma sessão de eventos estendidos. Para obter mais informações, consulte [Sessões de eventos estendidos do SQL Server](../../relational-databases/extended-events/sql-server-extended-events-sessions.md).  
  
 ![Arquitetura detalhada de eventos estendidos](../../relational-databases/extended-events/media/xearchitecturedetailed.gif "Arquitetura detalhada de eventos estendidos")  
  
 Observe o seguinte:  
  
-   Cada processo do Windows pode ter um ou mais módulos (**processo Win32**, **módulo Win32**). Estes também são conhecidos como *binários* ou *módulos de executáveis*.  
  
-   Cada um dos módulos de processo do Windows pode conter um ou mais pacotes de eventos estendidos (**Pacote**) que contêm um ou mais objetos de eventos estendidos (**Tipo**, **Destino**, **Ação**, **Mapa**, **Predicado**e **Evento**).  
  
-   Dentro de um processo de host pode haver só uma instância do mecanismo de eventos estendidos (**Mecanismo de evento estendido**) que:  
  
    -   Gerencia alguns aspectos da sessão (por exemplo, enumerar sessões).  
  
    -   Gerencia envio (**Dispatcher**). Isso é semelhante a um pool de thread.  
  
    -   Gerencia buffers de memória (**Buffer**) para eventos. Quando os buffers estiverem cheios, eles são despachados para os destinos.  
  
-   Depois que uma sessão for criada e os eventos associados à sessão opcionalmente (**Contexto de sessão**):  
  
    -   Instâncias de destinos (**Instância de destino**) podem também ser criadas e adicionadas à sessão.  
  
    -   Quando os buffers estão cheios, aqueles buffers são despachados para os destinos.  
  
## <a name="see-also"></a>Consulte também  
 [Eventos estendidos](../../relational-databases/extended-events/extended-events.md)  
  
  