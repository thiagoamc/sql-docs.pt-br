---
title: sp_addmergefilter (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/06/2017
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
applies_to:
- SQL Server
f1_keywords:
- sp_addmergefilter
- sp_addmergefilter_TSQL
helpviewer_keywords:
- sp_addmergefilter
ms.assetid: 4c118cb1-2008-44e2-a797-34b7dc34d6b1
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bae5cbac50c347247bba5b0488a7fb70ad8e71a3
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="spaddmergefilter-transact-sql"></a>sp_addmergefilter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Adiciona um novo filtro de mesclagem para criar uma partição com base em uma junção com outra tabela. Esse procedimento armazenado é executado no Publicador, no banco de dados publicador.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Convenções da sintaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
sp_addmergefilter [ @publication = ] 'publication'   
        , [ @article = ] 'article'   
        , [ @filtername = ] 'filtername'   
        , [ @join_articlename = ] 'join_articlename'   
        , [ @join_filterclause = ] join_filterclause  
    [ , [ @join_unique_key = ] join_unique_key ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
    [ , [ @filter_type = ] filter_type ]  
```  
  
## <a name="arguments"></a>Argumentos  
 [  **@publication=** ] **'***publicação***'**  
 É o nome da publicação na qual o filtro de mesclagem está sendo adicionado. *publicação* é **sysname**, sem padrão.  
  
 [  **@article=** ] **'***artigo***'**  
 É o nome do artigo no qual o filtro de mesclagem está sendo adicionado. *artigo* é **sysname**, sem padrão.  
  
 [  **@filtername=** ] **'***filtername***'**  
 É o nome do filtro. *FilterName* é um parâmetro obrigatório. *FilterName*é **sysname**, sem padrão.  
  
 [  **@join_articlename=** ] **'***join_articlename***'**  
 É o artigo pai ao qual o artigo filho, especificado por *artigo*, deve ser unidas usando a cláusula de junção especificada por *join_filterclause*, para determinar as linhas no artigo filho que atendem os critérios de filtro de mesclagem. *join_articlename* é **sysname**, sem padrão. O artigo deve estar na publicação fornecida por *publicação*.  
  
 [  **@join_filterclause=** ] *join_filterclause*  
 É a cláusula de junção que deve ser usada para unir o artigo filho especificado por *artigo*e o artigo pai especificado por *join_article*, para determinar as linhas qualificadas para o filtro de mesclagem. *join_filterclause* é **nvarchar (1000)**.  
  
 [  **@join_unique_key=** ] *join_unique_key*  
 Especifica se a associação entre o artigo filho *artigo*e o artigo pai *join_article*é um-para-muitos, um para um, muitos-para-um ou muitos-para-muitos. *join_unique_key* é **int**, com um padrão de 0. **0** indica uma junção muitos-para-um ou muitos-para-muitos. **1** indica uma junção um para um ou um-para-muitos. Esse valor é **1** quando as colunas de junção formam uma chave exclusiva na *join_article*, ou se *join_filterclause* entre uma chave estrangeira em *artigo* e uma chave primária em *join_article*.  
  
> [!CAUTION]  
>  Só defina este parâmetro como **1** se você tiver uma restrição na coluna de junção na tabela subjacente para o artigo pai que garanta a exclusividade. Se *join_unique_key* é definido como **1** incorretamente, poderá ocorrer não convergência de dados.  
  
 [  **@force_invalidate_snapshot=** ] *force_invalidate_snapshot*  
 Confirma que a ação tomada por esse procedimento armazenado pode invalidar um instantâneo existente. *force_invalidate_snapshot* é um **bit**, com um padrão **0**.  
  
 **0** Especifica que as alterações no artigo de mesclagem não fará com que o instantâneo seja inválido. Se o procedimento armazenado detectar que a alteração exigir um novo instantâneo, ocorrerá um erro e nenhuma alteração será feita.  
  
 **1** Especifica que as alterações no artigo de mesclagem podem invalidar o instantâneo inválido e se houver assinaturas existentes que exigem um novo instantâneo, dará permissão para que o instantâneo existente seja marcado como obsoleto e um novo instantâneo gerado.  
  
 [  **@force_reinit_subscription=** ] *force_reinit_subscription*  
 Confirma que a ação tomada por esse procedimento armazenado pode exigir que as assinaturas existentes sejam reinicializadas. *force_reinit_subscription* é um **bit**, com um padrão de 0.  
  
 **0** Especifica que as alterações no artigo de mesclagem não fará com que a assinatura ser reiniciada. Se o procedimento armazenado detectar que a alteração irá requerer que as assinaturas existentes sejam reiniciadas, ocorrerá um erro e nenhuma alteração será feita.  
  
 **1** Especifica que as alterações no artigo de mesclagem fará com que as assinaturas existentes sejam reinicializadas e dá permissão para que ocorra a reinicialização da assinatura.  
  
 [  **@filter_type=** ] *filter_type*  
 Especifica o tipo de filtro que está sendo adicionado. *filter_type* é **tinyint**, e pode ser um dos valores a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|**1**|Somente filtro de junção. Necessário para dar suporte a [!INCLUDE[ssEW](../../includes/ssew-md.md)] assinantes.|  
|**2**|Somente relação de registro lógico.|  
|**3**|Relação de filtro de junção e registro lógico.|  
  
 Para obter mais informações, consulte [Agrupar alterações a linhas relacionadas com registros lógicos](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
## <a name="return-code-values"></a>Valores do código de retorno  
 **0** (êxito) ou **1** (falha)  
  
## <a name="remarks"></a>Comentários  
 **sp_addmergefilter** é usado em replicação de mesclagem.  
  
 **sp_addmergefilter** só pode ser usado com artigos de tabela. Artigos de exibição e exibição indexada não têm suporte.  
  
 Esse procedimento também pode ser usado para adicionar uma relação lógica entre dois artigos que podem ou não ter um filtro de junção entre eles. *filter_type* é usado para especificar se o filtro de mesclagem está sendo adicionado é um filtro de junção, uma relação lógica ou ambos.  
  
 Para usar registros lógicos, a publicação e os artigos devem atender a vários requisitos. Para obter mais informações, consulte [Agrupar alterações a linhas relacionadas com registros lógicos](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
 Geralmente, essa opção é usada para um artigo que tem uma referência de chave estrangeira para uma tabela de chave primária publicada, e, a tabela da chave primária tem um filtro definido nesse artigo. O subconjunto de linhas de chave primária é usado para determinar as linhas da chave estrangeira que são replicadas para o Assinante.  
  
 Você não pode adicionar um filtro de junção entre dois artigos publicados quando as tabelas de origem de ambos os artigos compartilham o mesmo nome de objeto de tabela. Nesse caso, mesmo que ambas as tabelas sejam de propriedade de esquemas diferentes e tenham nomes de artigo exclusivos, a criação do filtro de junção irá falhar.  
  
 Quando um filtro de linha e um filtro de junção com parâmetros são usados no mesmo artigo de tabela, a replicação determinará se uma linha pertence a uma partição de Assinante. Ele faz isso avaliando a função de filtro ou o filtro de junção (usando o [OR](../../t-sql/language-elements/or-transact-sql.md) operador), em vez de avaliar a interseção de duas condições (usando o [AND](../../t-sql/language-elements/and-transact-sql.md) operador).  
  
## <a name="example"></a>Exemplo  
 [!code-sql[HowTo#sp_addmergefilter](../../relational-databases/replication/codesnippet/tsql/sp-addmergefilter-transa_1.sql)]  
  
## <a name="permissions"></a>Permissões  
 Somente membros do **sysadmin** função de servidor fixa ou **db_owner** pode executar a função de banco de dados fixa **sp_addmergefilter**.  
  
## <a name="see-also"></a>Consulte também  
 [Define an Article](../../relational-databases/replication/publish/define-an-article.md)   
 [Define and Modify a Join Filter Between Merge Articles](../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)   
 [Join Filters](../../relational-databases/replication/merge/join-filters.md)   
 [sp_changemergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergefilter-transact-sql.md)   
 [sp_dropmergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql.md)   
 [sp_helpmergefilter &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpmergefilter-transact-sql.md)   
 [Procedimentos armazenados de replicação &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
