---
title: sp_special_columns_100 (SQL Data Warehouse) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 5774fadc-77cc-46f8-8f9f-a0f9efe95e21
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 64aafbee1cae4cbdf8a2d43c7367fdbae6e40b27
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2018
---
# <a name="spspecialcolumns100-sql-data-warehouse"></a>sp_special_columns_100 (SQL Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Retorna o conjunto ideal de colunas que identificam, de forma exclusiva, uma linha na tabela. Também retorna colunas atualizadas automaticamente quando qualquer valor na linha for atualizado por uma transação.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "ícone de link do tópico") [convenções de sintaxe do Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_special_columns_100 [ @table_name = ] 'table_name'     
     [ , [ @table_owner = ] 'table_owner' ]   
     [ , [ @qualifier = ] 'qualifier' ]   
     [ , [ @col_type = ] 'col_type' ]   
     [ , [ @scope = ] 'scope' ]  
     [ , [ @nullable = ] 'nullable' ]   
     [ , [ @ODBCVer = ] 'ODBCVer' ]   
[ ; ]  
```  
  
## <a name="arguments"></a>Argumentos  
 [ @table_name=] '*table_name*'  
 É o nome da tabela usada para retornar informações do catálogo. *nome* é **sysname**, sem padrão. Não há suporte para a correspondência de padrão curinga.  
  
 [ @table_owner=] '*table_owner*'  
 É o proprietário da tabela da tabela usada para retornar informações de catálogo. *proprietário* é **sysname**, com um padrão NULL. Não há suporte para a correspondência de padrão curinga. Se *proprietário* não for especificado, serão aplicadas as regras de visibilidade de tabela padrão do DBMS subjacente.  
  
 Em [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], se o usuário atual possuir uma tabela com o nome especificado, as colunas dessa tabela serão retornadas. Se *proprietário* não for especificado e o usuário atual não possuir uma tabela especificada *nome*, esse procedimento procurará uma tabela especificada *nome* o banco de dados de propriedade proprietário. Se a tabela existir, suas colunas serão retornadas.  
  
 [ @qualifier=] '*qualifier*'  
 É o nome do qualificador da tabela. *qualificador* é **sysname**, com um padrão NULL. Vários produtos DBMS dão suporte à nomenclatura de três partes para tabelas (*qualificador*). No [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], essa coluna representa o nome do banco de dados. Em alguns produtos, representa o nome do servidor do ambiente de banco de dados da tabela.  
  
 [ @col_type=] '*col_type*'  
 É o tipo da coluna. *col_type* é **char (**1**)**, com um padrão de R. o tipo R retorna a coluna ou conjunto ideal de colunas que, pela recuperação de valores de coluna ou colunas, permite que qualquer linha especificada tabela a ser identificado exclusivamente. A coluna pode ser uma pseudocoluna especificamente projetada para esta finalidade ou a coluna ou colunas de qualquer índice exclusivo da tabela. O tipo V retorna a coluna ou as colunas da tabela especificada, se houver, que são automaticamente atualizadas pela fonte de dados quando qualquer valor na linha é atualizado por qualquer transação.  
  
 [ @scope=] '*escopo*'  
 É o escopo mínimo necessário de ROWID. *escopo* é **char (**1**)**, com um padrão T. o escopo C Especifica que a ROWID é válida somente quando posicionada nessa linha. O escopo T especifica que a ROWID é válida para a transação.  
  
 [ @nullable=] '*anulável*'  
 Indica se as colunas especiais podem aceitar um valor nulo. *anulável* é **char (**1**)**, com um padrão de U. O Especifica colunas especiais que não permitem valores nulos. U especifica colunas que permitem valor parcialmente nulo.  
  
 [ @ODBCVer=] '*ODBCVer*'  
 É a versão do ODBC que está sendo utilizada. *ODBCVer* é **int (**4**)**, com um padrão de 2. Isso indica o ODBC versão 2.0. Para obter mais informações sobre a diferença entre ODBC versão 2.0 e ODBC versão 3.0, consulte a especificação de ODBC SQLSpecialColumns para ODBC versão 3.0.  
  
## <a name="return-code-values"></a>Valores do código de retorno  
 Nenhuma  
  
## <a name="result-sets"></a>Conjuntos de resultados  
  
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|SCOPE|**smallint**|Escopo real da ID da linha. Pode ser 0, 1 ou 2. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]sempre retorna 0. Esse campo sempre retorna um valor.<br /><br /> 0 = SQL_SCOPE_CURROW. A ID da linha tem a garantia de ser válida somente quando posicionada nessa linha. Uma nova seleção posterior que utilize a ID da linha talvez não retorne uma linha se a linha foi atualizada ou excluída por outra transação.<br /><br /> 1 = SQL_SCOPE_TRANSACTION. A ID da linha tem a garantia de ser válida durante a transação atual.<br /><br /> 2 = SQL_SCOPE_SESSION. A ID da linha tem a garantia de ser válida durante a sessão (dentro dos limites da transação).|  
|COLUMN_NAME|**sysname**|Nome de coluna para cada coluna do *tabela*retornado. Esse campo sempre retorna um valor.|  
|DATA_TYPE|**smallint**|Tipo de dados SQL ODBC.|  
|TYPE_NAME|**sysname**|Nome do tipo de dados dependente da fonte de dados; Por exemplo, **char**, **varchar**, **money**, ou **texto**.|  
|PRECISION|**Int**|Precisão da coluna na fonte de dados. Esse campo sempre retorna um valor.|  
|LENGTH|**Int**|Comprimento em bytes, necessário para o tipo de dados em seu formato binário na fonte de dados, por exemplo, 10 para **char (**10**)**, 4 para **inteiro**e 2 para **smallint** .|  
|SCALE|**smallint**|Escala da coluna na fonte de dados. NULL é retornado para os tipos de dados para os quais a escala não é aplicável.|  
|PSEUDO_COLUMN|**smallint**|Indica se a coluna é uma pseudocoluna. O [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sempre retorna 1:<br /><br /> 0 = SQL_PC_UNKNOWN<br /><br /> 1 = SQL_PC_NOT_PSEUDO<br /><br /> 2 = SQL_PC_PSEUDO|  
  
## <a name="remarks"></a>Remarks  
 sp_special_columns é equivalente a SQLSpecialColumns no ODBC. Os resultados retornados são ordenados por SCOPE.  
  
## <a name="permissions"></a>Permissões  
 Requer a permissão SELECT no esquema.  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemplos: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 O exemplo a seguir retorna informações sobre a coluna que identifica linhas de forma exclusiva na tabela `FactFinance`.  
  
```  
-- Uses AdventureWorks  
  
EXEC sp_special_columns_100 @table_name = 'FactFinance';  
```  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos armazenados do SQL Data Warehouse](../../relational-databases/system-stored-procedures/sql-data-warehouse-stored-procedures.md)  
  
  

