---
title: sys. fulltext_languages (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.fulltext_languages
- sys.fulltext_languages_TSQL
- fulltext_languages
- fulltext_languages_TSQL
dev_langs: TSQL
helpviewer_keywords:
- languages [full-text search]
- sys.fulltext_languages catalog view
ms.assetid: 2ed6b53d-1cf2-4763-9d58-36ea24a610ef
caps.latest.revision: "54"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5e128525420e741af2ddca0c2584f55a950d98c2
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2017
---
# <a name="sysfulltextlanguages-transact-sql"></a>sys.fulltext_languages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Esta exibição do catálogo contém uma linha por idioma cujos separadores de palavras estão registrados no [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cada linha exibe o LCID e o nome do idioma. Quando há separadores de palavras registrados para um idioma, seus outros recursos linguísticos, como lematizadores, palavras de ruído (palavras irrelevantes) e arquivos de dicionário de sinônimos, ficam disponíveis para operações de indexação/consulta de texto completo. O valor de **nome** ou **lcid** pode ser especificado no índice de texto completo e consultas de texto completo [!INCLUDE[tsql](../../includes/tsql-md.md)] instruções.  
   
|Coluna|Data type|Description|  
|------------|---------------|-----------------|  
|**LCID**|**int**|O LCID (identificador de localidade) do [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows relativo ao idioma.|  
|**name**|**sysname**|É o valor do alias em [sys. syslanguages](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md) correspondente ao valor de **lcid** ou a representação de cadeia de caracteres do LCID numérico.|  
  
## <a name="values-returned-for-default-languages"></a>Valores retornados para idiomas padrão  
 A tabela a seguir mostra valores para idiomas cujos separadores de palavras são registrados por padrão.  
  
|Language|LCID|  
|--------------|----------|  
|Árabe|1025|  
|Bengali (Índia)|1093|  
|Inglês britânico|2057|  
|Búlgaro|1026|  
|Catalão|1027|  
|Chinês (RAE de Hong Kong, RPC)|3076|  
|Chinês (RAE de Macau)|5124|  
|Chinês (Cingapura)|4100|  
|Croata|1050|  
|Tcheco|1029|  
|Danish|1030|  
|Holandês|1043|  
|Inglês|1046|  
|Francês|1036|  
|Alemão|1031|  
|**Aplica-se a**: do [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ao [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Grego|1032|  
|Guzerati|1095|  
|Hebraico|1037|  
|Híndi|1081|  
|Islandês|1039|  
|Indonésio|1057|  
|Italiano|1040|  
|Japonês|1041|  
|Kannada|1099|  
|Coreano|1042|  
|Letão|1062|  
|Lituano|1063|  
|Malaio - Malásia|1086|  
|Malaiala|1100|  
|Marati|1102|  
|Neutro|0|  
|Norwegian (Bokmål)|1044|  
|**Aplica-se a**: do [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ao [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Polonês|1045|  
|Portuguese (Brazil)|1046|  
|Portuguese (Portugal)|2070|  
|Punjabi|1094|  
|Romeno|1048|  
|Russo|1049|  
|Sérvio (Cirílico)|3098|  
|Sérvio (latino)|2074|  
|Chinês simplificado|2052|  
|Eslovaco|1051|  
|Esloveno|1060|  
|Espanhol|3082|  
|Sueco|1053|  
|Tâmil|1097|  
|Télugo|1098|  
|Tailandês|1054|  
|Chinês tradicional|1028|  
|**Aplica-se a**: do [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ao [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Turco|1055|  
|Ucraniano|1058|  
|Urdu|1056|  
|Vietnamita|1066|  
  
## <a name="remarks"></a>Comentários  
 Para atualizar a lista de idiomas registrados na pesquisa de texto completo, use [sp_fulltext_service](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md)'**update_languages**'.  
  
## <a name="permissions"></a>Permissões  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [sp_fulltext_load_thesaurus_file &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-fulltext-load-thesaurus-file-transact-sql.md)   
 [sp_fulltext_service &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md)   
 [Configurar e gerenciar separadores de palavras e lematizadores de pesquisa](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)   
 [Configurar e gerenciar arquivos de dicionário de sinônimos para pesquisa de texto completo](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md)   
 [Configurar e gerenciar palavras irrelevantes e listas de palavras irrelevantes para pesquisa de texto completo](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)   
 [Atualizar pesquisa de texto completo](../../relational-databases/search/upgrade-full-text-search.md)  
  
  