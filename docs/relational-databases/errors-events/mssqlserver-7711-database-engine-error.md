---
title: MSSQLSERVER_7711 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 7711 (Database Engine error)
ms.assetid: a5c7cd6e-18d6-47ef-902b-db9dd64bba34
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: da817a514d1c472010d87a71819ad8f1206d0546
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver7711"></a>MSSQLSERVER_7711
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Detalhes  
  
|||  
|-|-|  
|Nome do produto|SQL Server|  
|ID do evento|7711|  
|Origem do evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbólico|PRT_RANGE_OVERLAP|  
|Texto da mensagem|A opção DATA_COMPRESSION foi especificada mais de uma vez para a tabela ou o índice ou para uma de suas partições.|  
  
## <a name="explanation"></a>Explicação  
Ocorreu um erro na opção DATA_COMPRESSION em uma das seguintes instruções:  
  
-   CREATE TABLE  
  
-   ALTER TABLE  
  
-   CREATE INDEX  
  
-   ALTER INDEX  
  
Se a tabela ou o índice citado for particionado, a opção DATA_COMPRESSION foi listada mais de uma vez para pelo menos uma das partições. Se a tabela ou o índice não for particionado, a opção DATA_COMPRESSION foi citada mais de uma vez.  
  
## <a name="user-action"></a>Ação do usuário  
Para uma tabela ou um índice particionado, verifique se a opção DATA_COMPRESSION está especificada somente uma vez para cada partição. Para uma tabela ou um índice não particionado, use a opção DATA_COMPRESSION somente uma vez na instrução.  
  
