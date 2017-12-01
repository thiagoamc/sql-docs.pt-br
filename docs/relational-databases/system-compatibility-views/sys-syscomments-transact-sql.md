---
title: sys. syscomments (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-compatibility-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.syscomments_TSQL
- syscomments
- syscomments_TSQL
- sys.syscomments
dev_langs: TSQL
helpviewer_keywords:
- sys.syscomments compatibility view
- syscomments system table
ms.assetid: 767dd410-6bc9-4c4a-ab0f-6d2cf6163426
caps.latest.revision: "53"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 5c9b5a5269025f6ed9c3bed493b71a6be557dc25
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/27/2017
---
# <a name="syssyscomments-transact-sql"></a>sys.syscomments (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contém entradas para cada exibição, regra, padrão, gatilho, restrição CHECK, restrição DEFAULT e procedimento armazenado no banco de dados. O **texto** coluna contém as instruções de definição originais do SQL.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] É recomendável usar sys.sql_modules. Para obter mais informações, consulte [sys. sql_modules &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md).  
  
|Nome da coluna|Tipo de dados|Descrição|  
|-----------------|---------------|-----------------|  
|**id**|**int**|ID do objeto ao qual esse texto se aplica.|  
|**número**|**smallint**|Número no agrupamento do procedimento, se agrupado.<br /><br /> 0 = Entradas não são procedimentos.|  
|**colid**|**smallint**|Número de sequência de linha para definições de objeto superiores a 4.000 caracteres.|  
|**status**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**ctext**|**varbinary (8000)**|Os bytes brutos da instrução de definição SQL.|  
|**texto: digite**|**smallint**|0 = Comentário fornecido pelo usuário<br /><br /> 1 = Comentário fornecido pelo sistema<br /><br /> 4 = Comentário criptografado|  
|**idioma**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**criptografado**|**bit**|Indica se a definição de procedimento é ofuscada.<br /><br /> 0 = Não ofuscado<br /><br /> 1 = Ofuscado<br /><br /> **\*\*Importante \* \***  para ofuscar definições de procedimento armazenado, use CREATE PROCEDURE com a palavra-chave de criptografia.|  
|**compactado**|**bit**|Sempre retorna 0. Isso indica se o procedimento é compactado.|  
|**texto**|**nvarchar(4000)**|Texto real da instrução de definição SQL.<br /><br /> A semântica da expressão decodificada equivale ao texto original; porém, não há nenhuma garantia sintática. Por exemplo, espaços em branco são removidos da expressão decodificada.<br /><br /> Isso [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]-exibição compatível obtém informações de atual [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] estruturas e pode retornar mais caracteres do que o **nvarchar (4000)** definição. **sp_help** retorna **nvarchar (4000)** como o tipo de dados da coluna de texto. Ao trabalhar com **syscomments** considere o uso de **nvarchar (max)**. Para novos desenvolvimentos, não use **syscomments**.|  
  
## <a name="see-also"></a>Consulte também  
 [Mapeando tabelas do sistema para exibições do sistema &#40; Transact-SQL &#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Exibições de compatibilidade &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  