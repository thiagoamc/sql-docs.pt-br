---
title: sys.fulltext_index_fragments (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- fulltext_index_fragments
- sys.fulltext_index_fragments_TSQL
- fulltext_index_fragments_TSQL
- sys.fulltext_index_fragments
dev_langs:
- TSQL
helpviewer_keywords:
- full-text indexes [SQL Server], fragments
- full-text indexes [SQL Server], metadata
- troubleshooting [SQL Server], full-text search
- sys.fulltext_index_fragments catalog view
ms.assetid: a82e5018-5d88-45c0-9a47-c251e17a6cdb
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d131a8fc53f13c412d058d2971f9156e32c669ec
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2018
---
# <a name="sysfulltextindexfragments-transact-sql"></a>sys.fulltext_index_fragments (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Um índice de texto completo usa tabelas internas, chamadas *fragmentos de índice de texto completo* para armazenar os dados de índice invertido. Esta exibição pode ser usada para consultar os metadados sobre estes fragmentos. Esta exibição contém uma linha para cada fragmento de índice de texto completo em toda tabela que contém um índice de texto completo.  
 
  
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|table_id|**Int**|ID de objeto da tabela que contém o fragmento do índice de texto completo.|  
|fragment_object_id|**Int**|ID de objeto da tabela interna associado com o fragmento.|  
|fragment_id|**Int**|ID lógico do fragmento de índice de texto completo. Ele é exclusivo em todos os fragmentos para esta tabela.|  
|timestamp|**timestamp**|Timestamp associado com a criação do fragmento. O timestamps dos fragmentos mais recentes são maiores do que o timestamps de fragmentos mais antigos.|  
|data_size|**Int**|Tamanho lógico do fragmento em bytes.|  
|row_count|**Int**|Número de linhas individuais no fragmento.|  
|status|**Int**|Status do fragmento, um de:<br /><br /> 0 = Criado recentemente e não utilizado ainda<br /><br /> 1 = Sendo usado para inserção durante população ou mesclagem de índice de texto completo<br /><br /> 4 = Fechado. Pronto para consulta<br /><br /> 6 = Sendo usado para entrada de mesclagem e pronto para consulta<br /><br /> 8 = Marcado para exclusão. Não será usado para consulta e mesclagem de origem.<br /><br /> Um status de 4 ou 6 significa que o fragmento faz parte do índice de texto completo lógico e pode ser consultado; ou seja, ele é um *passível de consulta* fragmento.|  
  
## <a name="remarks"></a>Remarks  
 A exibição do catálogo sys.fulltext_index_fragments pode ser usada para consultar o número de fragmentos que formam um índice de texto completo. Se estiver observando um baixo desempenho de consulta de texto completo, é possível usar sys.fulltext_index_fragments para consultar o número de fragmentos que podem ser consultados (status = 4 ou 6) no índice de texto completo desta forma:   
  
```  
SELECT table_id, status FROM sys.fulltext_index_fragments  
   WHERE status=4 OR status=6;  
```  
  
 Se existirem diversos fragmentos que podem ser consultados, a Microsoft recomenda que você reorganize o catálogo de texto completo que contém um índice de texto completo para mesclar os fragmentos juntos. Para reorganizar do catálogo de texto completo use [ALTER_FULLTEXT_CATALOG](../../t-sql/statements/alter-fulltext-catalog-transact-sql.md)*catalog_name* REORGANIZE. Por exemplo, para reorganizar um catálogo de texto completo chamado banco de dados `ftCatalog` in the `AdventureWorks2012`, digite:  
  
```  
USE AdventureWorks2012;  
GO  
ALTER FULLTEXT CATALOG ftCatalog REORGANIZE;  
GO  
```  
  
## <a name="permissions"></a>Permissões  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Exibições de catálogo de objeto &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Popular índices de texto completo](../../relational-databases/search/populate-full-text-indexes.md)  
  
  
