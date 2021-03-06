---
title: MSdbms_datatype_mapping (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
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
applies_to:
- SQL Server
f1_keywords:
- MSdbms_datatype_mapping_TSQL
- MSdbms_datatype_mapping
dev_langs:
- TSQL
helpviewer_keywords:
- MSdbms_datatype_mapping system table
ms.assetid: 13289a0b-dfb0-4771-ad80-4c5f83cded99
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 75f042866d01baa0a74143d2698644148a100b43
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="msdbmsdatatypemapping-transact-sql"></a>MSdbms_datatype_mapping (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  O **MSdbms_datatype_mapping** tabela contém os mapeamentos de tipo de dados permitida do tipo de dados no sistema de gerenciamento de banco de dados (DBMS) origem para um ou mais tipos de dados específicos no DBMS de destino. Essa tabela é armazenada no **msdb** banco de dados e é usado para replicação de banco de dados heterogênea.  
  
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|**datatype_mapping_id**|**int**|Identifica cada mapeamento de tipo de dados exclusivo.|  
|**map_id**|**int**|Identifica o tipo de dados de origem.|  
|**dest_datatype_id**|**int**|Identifica o tipo de dados de destino.|  
|**dest_precision**|**bigint**|Define a precisão do tipo de dados de destino, onde um valor NULL significa que a precisão não é usada, e um valor de **-1** significa que a precisão do tipo de dados de origem é usada.|  
|**dest_scale**|**int**|Define a escala do tipo de dados de destino, onde um valor NULL significa que a escala não é usada, e um valor de **-1** significa que a escala do tipo de dados de origem é usada.|  
|**dest_length**|**bigint**|Define o comprimento do tipo de dados de destino, onde um valor NULL significa que o comprimento não é usado, e um valor de **-1** significa que o comprimento do tipo de dados de origem é usado.|  
|**dest_nullable**|**bit**|Indica se a coluna de destino no mapeamento permite valores NULL, onde um valor de NULL significa que essa definição não é exigida.|  
|**dest_createparams**|**int**|O bitmap que descreve quais as combinações de comprimento, precisão e escala são aplicáveis para cada tipo de dados, incluindo:<br /><br /> **0x1** = precisão.<br /><br /> **0x2** = escala.<br /><br /> **0x4** = comprimento.|  
  
## <a name="see-also"></a>Consulte também  
 [Replicação de banco de dados heterogênea](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Especificar mapeamentos de tipo de dados para um publicador Oracle](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [Tabelas de replicação &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Exibições de replicação &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
