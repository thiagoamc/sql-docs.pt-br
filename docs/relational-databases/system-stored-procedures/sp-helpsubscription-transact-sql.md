---
title: sp_helpsubscription (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_helpsubscription_TSQL
- sp_helpsubscription
helpviewer_keywords:
- sp_helpsubscription
ms.assetid: ff96bcbf-e2b9-4da8-8515-d80d4ce86c16
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 201a7c412fbf01ca2600d3c9dc233eadfa33710b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="sphelpsubscription-transact-sql"></a>sp_helpsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Lista informações de assinatura associadas a uma publicação, um artigo, Assinante ou conjunto de assinaturas específico. Esse procedimento armazenado é executado no Publicador, em um banco de dados de publicação.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Convenções da sintaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
sp_helpsubscription [ [ @publication = ] 'publication' ]   
    [ , [ @article = ] 'article' ]  
    [ , [ @subscriber = ] 'subscriber' ]  
    [ , [ @destination_db = ] 'destination_db' ]   
    [ , [ @found=] found OUTPUT ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Argumentos  
 [  **@publication =** ] **'***publicação***'**  
 É o nome da publicação associada. *publicação* é **sysname**, com um padrão de  **%** , que retorna todas as informações de assinatura para esse servidor.  
  
 [  **@article=** ] **'***artigo***'**  
 É o nome do artigo. *artigo* é **sysname**, com um padrão de  **%** , que retorna todas as informações de assinatura para as publicações e assinantes selecionados. Se **todos os**, apenas uma entrada é retornada para a assinatura completa em uma publicação.  
  
 [  **@subscriber=** ] **'***assinante***'**  
 É o nome do Assinante no qual obter informações de assinaturas. *assinante* é **sysname**, com um padrão de  **%** , que retorna todas as informações de assinatura para as publicações e assinantes selecionados.  
  
 [  **@destination_db=** ] **'***destination_db***'**  
 É o nome do banco de dados de destino. *destination_db* é **sysname**, com um padrão de  **%** .  
  
 [  **@found=** ] **'***encontrado***'**saída  
 É um sinalizador para indicar linhas de retorno. *encontrado*é **int** e um parâmetro de saída, com um padrão de 23456.  
  
 **1** indica que a publicação foi localizada.  
  
 **0** indica a publicação não foi encontrada.  
  
 [  **@publisher** =] **'***publicador***'**  
 É o nome do Publicador. *publicador* é **sysname**e o padrão é o nome do servidor atual.  
  
> [!NOTE]  
>  *publicador* não deve ser especificado, exceto quando ele for um editor Oracle.  
  
## <a name="result-sets"></a>Conjuntos de resultados  
  
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|**Assinante**|**sysname**|Nome do Assinante.|  
|**publicação**|**sysname**|Nome da publicação.|  
|**artigo**|**sysname**|Nome do artigo.|  
|**banco de dados de destino**|**sysname**|Nome do banco de dados de destino no qual os dados replicados são colocados.|  
|**status da assinatura**|**tinyint**|O status da assinatura:<br /><br /> **0** = inativo<br /><br /> **1** = assinado<br /><br /> **2** = ativo|  
|**tipo de sincronização**|**tinyint**|O tipo de sincronização da assinatura:<br /><br /> **1** = automático<br /><br /> **2** = nenhum|  
|**tipo de assinatura**|**int**|O tipo de assinatura:<br /><br /> **0** = push<br /><br /> **1** = pull<br /><br /> **2** = anônimo|  
|**assinatura completa**|**bit**|Se a assinatura é para todos os artigos na publicação:<br /><br /> **0** = não<br /><br /> **1** = Sim|  
|**nome da assinatura**|**nvarchar(255)**|O nome da assinatura.|  
|**modo de atualização**|**int**|**0** = somente leitura<br /><br /> **1** = assinatura de atualização imediata|  
|**id do trabalho de distribuição**|**binário (16)**|A ID de trabalho do Distribution Agent.|  
|**loopback_detection**|**bit**|A detecção de loopback determina se o Distribution Agent envia transações originadas no Assinante de volta para o Assinante:<br /><br /> **0** = envia de volta.<br /><br /> **1** = não envia de volta.<br /><br /> Usado com replicação transacional bidirecional. Para obter mais informações, consulte [Bidirectional Transactional Replication](../../relational-databases/replication/transactional/bidirectional-transactional-replication.md).|  
|**offload_enabled**|**bit**|Especifica se execução de descarga de um agente de replicação foi definida para executar no Assinante.<br /><br /> Se **0**, agent é executado no publicador.<br /><br /> Se **1**, agent é executado no assinante.|  
|**offload_server**|**sysname**|Nome do servidor habilitado para ativação de agente remota. Se for NULL, então o offload_server atual listado em [MSdistribution_agents](../../relational-databases/system-tables/msdistribution-agents-transact-sql.md) tabela é usada.|  
|**dts_package_name**|**sysname**|Especifica o nome do pacote DTS (Data Transformation Services).|  
|**dts_package_location**|**int**|Local do pacote DTS, se um estiver atribuído à assinatura. Se houver um pacote, um valor de **0** Especifica o local do pacote no **distribuidor**. Um valor de **1** Especifica o **assinante**.|  
|**subscriber_security_mode**|**smallint**|É o modo de segurança no assinante, onde **1** significa autenticação do Windows e **0** significa [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] autenticação.|  
|**subscriber_login**|**sysname**|É o nome de logon no Assinante.|  
|**subscriber_password**||A senha do Assinante atual nunca é retornada. O resultado é mascarado por um "**\*\*\*\*\*\***" cadeia de caracteres.|  
|**job_login**|**sysname**|Nome da conta do Windows na qual o Distribution Agent é executado.|  
|**job_password**||A senha de trabalho atual nunca é retornada. O resultado é mascarado por um "**\*\*\*\*\*\***" cadeia de caracteres.|  
|**distrib_agent_name**|**nvarchar (100)**|Nome do trabalho de agente que sincroniza a assinatura.|  
|**subscriber_type**|**tinyint**|Tipo do Assinante, que pode ser um dos seguintes:<br /><br /> **0** = assinante do SQL Server<br /><br /> **1** = servidor de fonte de dados ODBC<br /><br /> **2** = banco de dados do Microsoft JET (preterido)<br /><br /> **3** = provedor OLE DB|  
|**subscriber_provider**|**sysname**|PROGID (identificador programático) exclusivo com o qual o provedor OLE DB para fonte de dados não SQL Server é registrado.|  
|**subscriber_datasource**|**nvarchar(4000)**|Nome da fonte de dados conforme entendido pelo provedor OLE DB.|  
|**subscriber_providerstring**|**nvarchar(4000)**|Cadeia de conexão específica de provedor OLE DB que identifica a fonte de dados.|  
|**subscriber_location**|**nvarchar(4000)**|Local do banco de dados conforme entendido pelo provedor OLE DB|  
|**subscriber_catalog**|**sysname**|Catálogo a ser usado ao fazer uma conexão com o provedor OLE DB.|  
  
## <a name="return-code-values"></a>Valores do código de retorno  
 **0** (êxito) ou **1** (falha)  
  
## <a name="remarks"></a>Comentários  
 **sp_helpsubscription** é usado em replicação de instantâneo e transacional.  
  
## <a name="permissions"></a>Permissões  
 As permissões de execução têm como padrão a função **public** . Só são retornadas informações aos usuários sobre assinaturas criadas por eles. Informações sobre todas as assinaturas são retornadas aos membros do **sysadmin** a função de servidor fixa no publicador ou membros do **db_owner** função de banco de dados fixa no banco de dados de publicação.  
  
## <a name="see-also"></a>Consulte também  
 [sp_addsubscription &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)   
 [sp_changesubstatus &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-changesubstatus-transact-sql.md)   
 [sp_dropsubscription &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)   
 [Procedimentos armazenados do sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
