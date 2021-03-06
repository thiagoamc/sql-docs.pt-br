---
title: sys.dm_db_xtp_checkpoint_files (Transact-SQL) | Microsoft Docs
ms.date: 03/20/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.custom: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_db_xtp_checkpoint_files
- sys.dm_db_xtp_checkpoint_files_TSQL
- dm_db_xtp_checkpoint_files_TSQL
- sys.dm_db_xtp_checkpoint_files
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_xtp_checkpoint_files dynamic management view
ms.assetid: ac8e6333-7a9f-478a-b446-5602283e81c9
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fff8a7cff566b555c0cc28ff6e60c67815956738
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmdbxtpcheckpointfiles-transact-sql"></a>sys.dm_db_xtp_checkpoint_files (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  Exibe informações sobre os arquivos de ponto de verificação, incluindo o tamanho do arquivo, o local físico e a ID da transação.  
  
> **Observação:** para o ponto de verificação atual que não foi fechado, a coluna de estado de s`ys.dm_db_xtp_checkpoint_files` estará em construção para novos arquivos. Um ponto de verificação será fechada automaticamente quando não há suficiente crescimento do log de transações desde o último ponto de verificação, ou se você emitir o `CHECKPOINT` comando ([CHECKPOINT &#40; Transact-SQL &#41; ](../../t-sql/language-elements/checkpoint-transact-sql.md)).  
  
 Um grupo de arquivos com otimização de memória usa internamente arquivos somente de acréscimo para armazenar linhas inseridas e excluídas para tabelas na memória. Existem dois tipos de arquivos. Um arquivo de dados contém linhas inseridas, enquanto um arquivo delta contém referências às linhas excluídas. 
  
 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] é significativamente diferente de versões mais recentes e é discutido mais baixa no tópico em [SQL Server 2014](#bkmk_2014).  
  
 Para obter mais informações, consulte [criando e gerenciando armazenamento para objetos com otimização de memória](../../relational-databases/in-memory-oltp/creating-and-managing-storage-for-memory-optimized-objects.md).  
  
##  <a name="bkmk_2016"></a>[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] e posterior  
 A tabela a seguir descreve as colunas para `sys.dm_db_xtp_checkpoint_files`, começando com  **[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]** .  
  
|Nome da coluna|Tipo|Description|  
|-----------------|----------|-----------------|  
|container_id|**Int**|A ID do contêiner (representado como um arquivo com o tipo FILESTREAM em sys.database_files) da qual fazem parte os dados ou o arquivo delta. Junções com file_id em [sys. database_files &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md).|  
|container_guid|**uniqueidentifier**|GUID do contêiner, o raiz, dados ou arquivo delta é parte do. Junções com file_guid na tabela sys. database_files.|  
|checkpoint_file_id|**uniqueidentifier**|GUID do arquivo de ponto de verificação.|  
|relative_file_path|**nvarchar(256)**|Caminho do arquivo relativo ao contêiner para que é mapeada.|  
|file_type|**smallint**|-1 para livre<br /><br /> 0 para o arquivo de dados.<br /><br /> 1 para o arquivo DELTA.<br /><br /> 2 para o arquivo raiz<br /><br /> 3 para o arquivo de dados grandes|  
|file_type_desc|**nvarchar(60)**|Arquivos de tudo livre mantidos como livre estão disponíveis para alocação. Arquivos livres podem variar em tamanho, dependendo de necessidades antecipadas pelo sistema. O tamanho máximo é de 1GB.<br /><br /> DADOS - arquivos de dados contêm linhas que foram inseridas em tabelas com otimização de memória.<br /><br /> DELTA - os arquivos Delta contêm referências às linhas em arquivos de dados que foram excluídos.<br /><br /> RAIZ - arquivos raiz contém metadados do sistema para objetos com otimização de memória e compilados nativamente.<br /><br /> DADOS grandes - grandes arquivos de dados contêm valores inseridos (colunas varchar e varbinary (max), bem como segmentos de coluna que fazem parte de índices columnstore em tabelas com otimização de memória.|  
|internal_storage_slot|**Int**|O índice do arquivo na matriz de armazenamento interna. NULL para a raiz ou para um estado diferente de 1.|  
|checkpoint_pair_file_id|**uniqueidentifier**|Os dados correspondentes ou arquivo DELTA. NULL para a raiz.|  
|file_size_in_bytes|**bigint**|Tamanho do arquivo no disco.|  
|file_size_used_in_bytes|**bigint**|Para os pares de arquivos de ponto de verificação que ainda estão sendo populados, essa coluna será atualizada após o próximo ponto de verificação.|  
|logical_row_count|**bigint**|Para dados, o número de linhas inseridas.<br /><br /> Delta, número de linhas excluídas depois de descarte de tabela.<br /><br /> Para raiz, NULL.|  
|state|**smallint**|0 – PRÉ-CRIADO<br /><br /> 1 - EM CONSTRUÇÃO<br /><br /> 2 - ATIVO<br /><br /> 3 – MESCLAR DESTINO<br /><br /> 8 – AGUARDANDO O TRUNCAMENTO DE LOG|  
|state_desc|**nvarchar(60)**|Pré-criado – um número de arquivos de ponto de verificação é pré-alocados para minimizar ou eliminar qualquer espera para alocar novos arquivos conforme as transações estão sendo executadas. Elas pré-criados arquivos podem variar em tamanho, dependendo das necessidades estimados da carga de trabalho, mas eles não contêm nenhum dado. Isso é uma sobrecarga de armazenamento em bancos de dados com um grupo de arquivos MEMORY_OPTIMIZED_DATA.<br /><br /> EM construção - esses arquivos de ponto de verificação estão em construção, que significa que eles estão sendo preenchidos com base nos registros de log gerados pelo banco de dados e ainda não fazem parte de um ponto de verificação.<br /><br /> ATIVO - esses contêm linhas inseridas/excluídas de verificação fechados anteriores. Elas contêm o conteúdo das tabelas de área lidos na memória antes de aplicar a parte ativa do log de transações na reinicialização do banco de dados. Esperamos que esse tamanho desses arquivos de ponto de verificação seja aproximadamente 2x do tamanho de memória das tabelas com otimização de memória, supondo que a operação de mesclagem está acompanhando a carga de trabalho transacional.<br /><br /> Mesclar destino – o destino das operações de mesclagem - esses arquivos de ponto de verificação de armazenar as linhas de dados consolidados dos arquivos de origem que foram identificados pela política de mesclagem. Assim que a mesclagem for instalada, a opção MESCLAR DESTINO entrará no estado ATIVO.<br /><br /> AGUARDANDO o TRUNCAMENTO de LOG – após a mesclagem foi instalada e o CFP mesclar destino faz parte do ponto de verificação durável, a transição de arquivos de ponto de verificação de fonte mesclagem nesse estado. Arquivos nesse estado são necessários para exatidão operacional do banco de dados com a tabela com otimização de memória.  Por exemplo, restaurar de um ponto de verificação durável para voltar no tempo.|  
|lower_bound_tsn|**bigint**|Limite inferior da transação no arquivo. NULL se o estado não está em (1, 3).|  
|upper_bound_tsn|**bigint**|Limite superior da transação no arquivo. NULL se o estado não está em (1, 3).|  
|begin_checkpoint_id|**bigint**|ID do ponto de verificação inicial.|  
|end_checkpoint_id|**bigint**|ID do ponto de verificação final.|  
|last_updated_checkpoint_id|**bigint**|ID do último ponto de verificação que este arquivo atualizado.|  
|encryption_status|**smallint**|0, 1, 2|  
|encryption_status_desc|**nvarchar(60)**|0 = > UNENCRTPTED<br /><br /> 1 = > CRIPTOGRAFADA COM A CHAVE 1<br /><br /> 2 = > CRIPTOGRAFADA COM A CHAVE 2. Válido somente para arquivos ativos.|  
  
##  <a name="bkmk_2014"></a> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
 A tabela a seguir descreve as colunas para `sys.dm_db_xtp_checkpoint_files`, para  **[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]** .  
  
|Nome da coluna|Tipo|Description|  
|-----------------|----------|-----------------|  
|container_id|**Int**|A ID do contêiner (representado como um arquivo com o tipo FILESTREAM em sys.database_files) da qual fazem parte os dados ou o arquivo delta. Junções com file_id em [sys. database_files &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md).|  
|container_guid|**uniqueidentifier**|O GUID do contêiner do qual fazem parte os dados ou o arquivo delta.|  
|checkpoint_file_id|**GUID**|ID dos dados ou arquivo delta.|  
|relative_file_path|**nvarchar(256)**|Caminho para os dados ou arquivo delta, relativo ao local do contêiner.|  
|file_type|**tinyint**|0 para arquivo de dados.<br /><br /> 1 para arquivo delta.<br /><br /> NULL se a coluna de estado estiver definida como 7.|  
|file_type_desc|**nvarchar(60)**|O tipo de arquivo: DATA_FILE, DELTA_FILE ou nulo se a coluna de estado é definida como 7.|  
|internal_storage_slot|**Int**|O índice do arquivo na matriz de armazenamento interna. NULL se a coluna de estado não estiver definida como 2 ou 3.|  
|checkpoint_pair_file_id|**uniqueidentifier**|Os dados ou arquivo delta correspondentes.|  
|file_size_in_bytes|**bigint**|Tamanho do arquivo usado. NULL se a coluna de estado estiver definida como 5, 6 ou 7.|  
|file_size_used_in_bytes|**bigint**|Tamanho utilizado do arquivo que está sendo usado NULL se a coluna de estado estiver definida como 5, 6 ou 7.<br /><br /> Para os pares de arquivos de ponto de verificação que ainda estão sendo populados, essa coluna será atualizada após o próximo ponto de verificação.|  
|inserted_row_count|**bigint**|Número de linhas no arquivo de dados.|  
|deleted_row_count|**bigint**|Número de linhas excluídas no arquivo delta.|  
|drop_table_deleted_row_count|**bigint**|O número de linhas nos arquivos de dados afetados por uma tabela. Aplica-se aos arquivos de dados quando o estado da coluna for igual a 1.<br /><br /> Mostra as contagens de linhas excluídas das tabelas removidas. As estatísticas drop_table_deleted_row_count são compiladas depois que a coleta de lixo de memória das linhas nas tabelas removidas é concluída e um ponto de verificação é realizado. Se você reiniciar o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] antes que as estatísticas de tabelas removidas apareçam nessa coluna, as estatísticas serão atualizadas como parte da recuperação. O processo de recuperação não carrega linhas das tabelas removidas. As estatísticas das tabelas removidas são compiladas durante a fase de carregamento e relatadas nessa coluna quando a recuperação é concluída.|  
|state|**Int**|0 – PRÉ-CRIADO<br /><br /> 1 – EM CONSTRUÇÃO<br /><br /> 2 - ATIVO<br /><br /> 3 – MESCLAR DESTINO<br /><br /> 4 – ORIGEM MESCLADA<br /><br /> 5 – NECESSÁRIO PARA BACKUP/AD<br /><br /> 6 – EM TRANSIÇÃO PARA MARCA DE EXCLUSÃO<br /><br /> 7 – MARCA DE EXCLUSÃO|  
|state_desc|**nvarchar(60)**|PRÉ-CRIADO – Um conjunto pequeno de pares de arquivos delta, também conhecido como pares (CFPs) de arquivos de ponto de verificação, é mantido pré-atribuído para minimizar ou eliminar todas as esperas para atribuir novos arquivos enquanto as transações estão sendo executadas. Eles são totalmente utilizados com um tamanho de arquivo de dados de 128 MB e tamanho de arquivo delta de 8 MB, mas não contêm dados. O número de CFPs é calculado como o número de processadores lógicos ou de agendadores (um por núcleo, sem número máximo) com um mínimo de 8. Essa é uma sobrecarga de armazenamento fixa em bancos de dados com tabelas com otimização de memória.<br /><br /> EM CONSTRUÇÃO – Conjunto de CFPs que armazenam linhas de dados recentemente inseridas e possivelmente excluídas desde o último ponto de verificação.<br /><br /> ATIVO - Esses contêm as linhas inseridas e excluídas dos pontos de verificação fechados anteriores. Esses CFPs contêm todas as linhas inseridas e excluídas necessárias antes da aplicação da parte ativa do log de transações na reinicialização do banco de dados. O tamanho dessas CFPs será aproximadamente 2 vezes o tamanho das tabelas com otimização de memória na memória, supondo que a operação de mesclagem esteja atualmente com a carga de trabalho transacional.<br /><br /> MESCLAR DESTINO – O CFP armazena as linhas de dados consolidadas dos CFPs que foram identificados pela política de mesclagem. Assim que a mesclagem for instalada, a opção MESCLAR DESTINO entrará no estado ATIVO.<br /><br /> ORIGEM MESCLADA – Assim que a operação de mesclagem for instalada, os CFPs de origem serão marcados como ORIGEM MESCLADA. Observe que, o avaliador de política de mesclagem pode identificar várias mesclagens, mas um CFP só pode participar de uma operação de mesclagem.<br /><br /> NECESSÁRIO PARA BACKUP/AD – Assim que a mesclagem for instalada e o CFP MESCLAR DESTINO fizer parte do ponto de verificação durável, os CFPs de origem de mesclagem entram nesse estado. Os CFPs nesse estado são necessários para exatidão operacional do banco de dados da tabela com otimização de memória.  Por exemplo, restaurar de um ponto de verificação durável para voltar no tempo. Um CFP pode ser marcado para coleta de lixo depois que o ponto de truncamento do log passar de seu intervalo de transações.<br /><br /> EM TRANSIÇÃO PARA MARCA DE EXCLUSÃO – Esses CFPs não são necessários pelo mecanismo de OLTP em memória e podem ser coletados como lixo. Esse estado indica que esses CFPs estão aguardando o thread em segundo plano para fazer a transição deles para o próximo estado, que é MARCA DE EXCLUSÃO.<br /><br /> MARCA DE EXCLUSÃO – Esses CFPs estão esperando para serem coletados como lixo pelo coletor de lixo do fluxo de arquivos. ([sp_filestream_force_garbage_collection &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/filestream-and-filetable-sp-filestream-force-garbage-collection.md))|  
|lower_bound_tsn|**bigint**|O limite inferior de transações contidas no arquivo. Nulo se a coluna de estado for diferente de 2, 3 ou 4.|  
|upper_bound_tsn|**bigint**|O limite superior de transações contidas no arquivo. Nulo se a coluna de estado for diferente de 2, 3 ou 4.|  
|last_backup_page_count|**Int**|Contagem de página lógica que é determinada no último backup. Aplica-se quando a coluna de estado estiver definida como 2, 3, 4 ou 5. NULL se a contagem de páginas não for conhecida.|  
|delta_watermark_tsn|**Int**|A transação do último ponto de verificação que gravou neste arquivo delta. Essa é a marca d'água do arquivo delta.|  
|last_checkpoint_recovery_lsn|**nvarchar(23)**|Número de sequência do log de recuperação do último ponto de verificação que ainda precisa do arquivo.|  
|tombstone_operation_lsn|**nvarchar(23)**|O arquivo será excluído uma vez que tombstone_operation_lsn ir para trás do número de sequência de log de truncamento do registro.|  
|logical_deletion_log_block_id|**bigint**|Aplica-se somente ao estado 5.|  
  
## <a name="permissions"></a>Permissões  
 Requer a permissão `VIEW DATABASE STATE` no servidor.  
  
## <a name="use-cases"></a>Casos de uso  
 Você pode estimar o armazenamento usado pelo OLTP na memória da seguinte maneira:  
  
```  
-- total storage used by In-Memory OLTP  
SELECT SUM (file_size_in_bytes)/(1024*1024) as file_size_in_MB  
FROM sys.dm_db_xtp_checkpoint_files  
```  
  
  
Para ver uma análise da utilização de armazenamento por estado e tipo de arquivo execute a seguinte consulta:
  
```  
SELECT state_desc  
 , file_type_desc  
 , COUNT(*) AS [count]  
 , SUM(file_size_in_bytes) / 1024 / 1024 AS [on-disk size MB]   
FROM sys.dm_db_xtp_checkpoint_files  
GROUP BY state, state_desc, file_type, file_type_desc  
ORDER BY state, file_type  
```  
  

  
## <a name="see-also"></a>Consulte também  
 [Exibições de gerenciamento dinâmico de tabela com otimização de memória &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
