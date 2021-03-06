---
title: sys.DM os_buffer_descriptors (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 08/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_os_buffer_descriptors_TSQL
- dm_os_buffer_descriptors_TSQL
- sys.dm_os_buffer_descriptors
- dm_os_buffer_descriptors
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_buffer_descriptors dynamic management view
ms.assetid: 012aab95-8888-4f35-9ea3-b5dff6e3f60f
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1c03bbdbe271500ecf417fe3b5c125304001a05e
ms.sourcegitcommit: 6b1618aa3b24bf6759b00a820e09c52c4996ca10
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2018
---
# <a name="sysdmosbufferdescriptors-transact-sql"></a>sys.dm_os_buffer_descriptors (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retorna informações sobre todas as páginas de dados atualmente no pool de buffer do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. A saída dessa exibição pode ser usada para determinar a distribuição de páginas de bancos de dados no pool de buffer de acordo com o banco de dados, objeto ou tipo. No [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], essa exibição de gerenciamento dinâmico também retorna informações sobre as páginas de dados no arquivo de extensão do pool de buffers. Para obter mais informações, consulte [extensão do Pool de buffers](../../database-engine/configure-windows/buffer-pool-extension.md).  
  
 Quando uma página de dados é lida a partir do disco, a página é copiada para o pool de buffer do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e armazenada em cache para reutilização. Cada página de dados tem um descritor de buffer. Descritores de buffer que identificam exclusivamente cada página de dados armazenada em cache no momento em uma instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. sys.dm_os_buffer_descriptors retorna páginas armazenadas em cache para todos os usuários e bancos de dados do sistema. Isso inclui páginas que estão associadas ao banco de dados de Recursos.  
  
> **Observação:** chamá-la de [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] ou [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], use o nome **sys.dm_pdw_nodes_os_buffer_descriptors**.  

|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|database_id|**Int**|Identificação do banco de dados associada à página no pool de buffer. Permite valor nulo.|  
|file_id|**Int**|Identificação do arquivo que armazena a imagem persistida da página. Permite valor nulo.|  
|page_id|**Int**|Identificação da página no arquivo. Permite valor nulo.|  
|page_level|**Int**|Nível de índice da página. Permite valor nulo.|  
|allocation_unit_id|**bigint**|ID da unidade de alocação da página. Esse valor pode ser usado para unir sys.allocation_units. Permite valor nulo.|  
|page_type|**nvarchar(60)**|Tipo da página, como: página de Dados ou página de Índice. Permite valor nulo.|  
|row_count|**Int**|Número de linhas na página. Permite valor nulo.|  
|free_space_in_bytes|**Int**|Quantidade de espaço livre disponível, em bytes, na página. Permite valor nulo.|  
|is_modified|**bit**|1 = A página foi modificada depois de lida no disco. Permite valor nulo.|  
|numa_node|**Int**|Nó de acesso à memória não uniforme do buffer. Permite valor nulo.|  
|read_microsec|**bigint**|A hora real (em microssegundos) necessária para ler a página no buffer. Este número é redefinido quando o buffer é reutilizado. Permite valor nulo.|  
|is_in_bpool_extension|**bit**|1 = página está na extensão do pool de buffers. Permite valor nulo.|  
|pdw_node_id|**Int**|**Aplica-se a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> O identificador para o nó que essa distribuição é no.|  
  
## <a name="permissions"></a>Permissões  
Em [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], requer `VIEW SERVER STATE` permissão.   
Em [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] camadas Premium, requer o `VIEW DATABASE STATE` no banco de dados. Em [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] camadas Standard e Basic, requer o **administrador do servidor** ou um **administrador do Active Directory do Azure** conta.  
  
## <a name="remarks"></a>Remarks  
 sys.DM os_buffer_descriptors retorna páginas que estão sendo usadas pelo banco de dados do recurso. sys.DM os_buffer_descriptors não retorna informações sobre páginas livres ou roubadas ou sobre páginas que apresentaram erros quando foram lidas.  
  
|De|Para|Em|Relação|  
|----------|--------|--------|------------------|  
|sys.dm_os_buffer_descriptors|sys.databases|database_id|muitos para um|  
|sys.dm_os_buffer_descriptors|\<userdb>.sys.allocation_units|allocation_unit_id|muitos para um|  
|sys.dm_os_buffer_descriptors|\<userdb>.sys.database_files|file_id|muitos para um|  
|sys.dm_os_buffer_descriptors|sys.dm_os_buffer_pool_extension_configuration|file_id|muitos para um|  
  
## <a name="examples"></a>Exemplos  
  
### <a name="a-returning-cached-page-count-for-each-database"></a>A. Retornando a contagem de páginas armazenadas em cache para cada banco de dados  
 O exemplo a seguir retorna a contagem de páginas carregadas em cada banco de dados.  
  
```  
SELECT COUNT(*)AS cached_pages_count  
    ,CASE database_id   
        WHEN 32767 THEN 'ResourceDb'   
        ELSE db_name(database_id)   
        END AS database_name  
FROM sys.dm_os_buffer_descriptors  
GROUP BY DB_NAME(database_id) ,database_id  
ORDER BY cached_pages_count DESC;  
```  
  
### <a name="b-returning-cached-page-count-for-each-object-in-the-current-database"></a>B. Retorno de contagem de páginas para cada objeto no banco de dados atual  
 O exemplo a seguir retorna a contagem de páginas carregada em cada objeto no banco de dados atual.  
  
```  
SELECT COUNT(*)AS cached_pages_count   
    ,name ,index_id   
FROM sys.dm_os_buffer_descriptors AS bd   
    INNER JOIN   
    (  
        SELECT object_name(object_id) AS name   
            ,index_id ,allocation_unit_id  
        FROM sys.allocation_units AS au  
            INNER JOIN sys.partitions AS p   
                ON au.container_id = p.hobt_id   
                    AND (au.type = 1 OR au.type = 3)  
        UNION ALL  
        SELECT object_name(object_id) AS name     
            ,index_id, allocation_unit_id  
        FROM sys.allocation_units AS au  
            INNER JOIN sys.partitions AS p   
                ON au.container_id = p.partition_id   
                    AND au.type = 2  
    ) AS obj   
        ON bd.allocation_unit_id = obj.allocation_unit_id  
WHERE database_id = DB_ID()  
GROUP BY name, index_id   
ORDER BY cached_pages_count DESC;  
```  
  
## <a name="see-also"></a>Consulte também  
 [sys.allocation_units &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-allocation-units-transact-sql.md)   
 
 [Sistema operacional SQL Server relacionadas exibições de gerenciamento dinâmico &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)   
 [Banco de dados de recursos](../../relational-databases/databases/resource-database.md)   
 [sys.DM os_buffer_pool_extension_configuration &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-buffer-pool-extension-configuration-transact-sql.md)  
  
  


