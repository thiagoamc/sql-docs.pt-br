---
title: MScached_peer_lsns (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- MScached_peer_lsns_TSQL
- MScached_peer_lsns
dev_langs:
- TSQL
helpviewer_keywords:
- MScached_peer_lsns system table
ms.assetid: f8b6089a-0230-45f9-8c34-9fe0d2a3a74e
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 93c1c8600541f1f5710cc9dc2fe4675d1433fa92
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="mscachedpeerlsns-transact-sql"></a>MScached_peer_lsns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  O **MScached_peer_lsns** tabela é usada para controlar valores LSN no log de transações que são usados para determinar quais comandos para retornar a um determinado assinante em replicação ponto a ponto. Esta tabela é armazenada no banco de dados de distribuição.  
  
## <a name="definition"></a>Definição  
  
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|**agent_id**|**int**|A ID do Distribution Agent.|  
|**originador**|**sysname**|O nome do Publicador de origem.|  
|**originator_db**|**sysname**|O nome do banco de dados de publicação de origem.|  
|**originator_publication_id**|**int**|Identifica a publicação de origem.|  
|**originator_db_version**|**int**|Identifica o número da versão do banco de dados de origem.|  
|**originator_lsn**|**varbinary (16)**|O LSN da transação de origem.|  
  
## <a name="remarks"></a>Comentários  
 Valores LSN só são usados imediatamente após a inserção e não têm nenhum significado duradouro no sistema.  
  
## <a name="see-also"></a>Consulte também  
 [Tabelas de replicação &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Exibições de replicação &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
