---
title: MSSQL_ENG003724 | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSSQL_ENG003724 error
ms.assetid: 10cb119d-92df-4124-b85d-cd2f2666c99c
caps.latest.revision: 13
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d97300f400557643da18e81201136649d629b681
ms.lasthandoff: 04/11/2017

---
# <a name="mssqleng003724"></a>MSSQL_ENG003724
    
## <a name="message-details"></a>Detalhes da mensagem  
  
|||  
|-|-|  
|Nome do produto|SQL Server|  
|ID do evento|3724|  
|Origem do evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nome simbólico||  
|Texto da mensagem|Não é possível %S_MSG o %S_MSG '%.*ls' porque está sendo usado para replicação.|  
  
## <a name="explanation"></a>Explicação  
 Quando os objetos em um banco de dados são replicados, são marcados como replicados na tabela do sistema **sysarticles** (para publicações de instantâneo e transacionais) ou **sysmergearticles** (para publicações de mesclagem). Se tentar descartar um objeto replicado, ocorrerá esse erro.  
  
## <a name="user-action"></a>Ação do usuário  
 Certifique-se de que o objeto de banco de dados não está replicado antes de tentar descartá-lo. Por exemplo:  
  
-   Se o erro ocorrer no banco de dados de publicação, descarte o artigo da publicação antes de descartar o objeto. Para obter mais informações, consulte [Add Articles to and Drop Articles from Existing Publications](../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md) (Adicionar e remover artigos para/de publicações existentes).  
  
-   Se o erro ocorrer no banco de dados de assinatura, descarte a assinatura antes de descartar o objeto. Para obter mais informações, consulte [Subscribe to Publications](../../relational-databases/replication/subscribe-to-publications.md) (Assinar publicações). Para assinaturas de publicações transacionais, é possível descartar a assinatura de um artigo individual em vez de toda a publicação. Para obter mais informações, consulte [sp_dropsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md).  
  
 Se esse erro ocorrer em um banco de dados não replicado, execute [sp_removedbreplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) para garantir que os objetos nos bancos de dados não são marcados como replicados.  
  
## <a name="see-also"></a>Consulte também  
 [Referência de erros e eventos &#40;Replicação&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  