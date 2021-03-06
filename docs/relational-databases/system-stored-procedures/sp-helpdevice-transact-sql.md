---
title: sp_helpdevice (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_helpdevice
- sp_helpdevice_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpdevice
ms.assetid: 1a5eafa7-384e-4691-ba05-978eb73bbefb
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 08b996fa7f68bd028a73766a100c16858770cd45
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2018
---
# <a name="sphelpdevice-transact-sql"></a>sp_helpdevice (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Relata informações sobre dispositivos de backup do Microsoft® SQL Server™.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Recomendamos que você use o [backup_devices](../../relational-databases/system-catalog-views/sys-backup-devices-transact-sql.md) exibição do catálogo  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Convenções da sintaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
sp_helpdevice [ [ @devname = ] 'name' ]  
```  
  
## <a name="arguments"></a>Argumentos  
 [ **@devname =** ] **'***name***'**  
 É o nome do dispositivo de backup ao qual as informações são reportadas. O valor de *nome* é sempre **sysname**.  
  
## <a name="return-code-values"></a>Valores do código de retorno  
 0 (êxito) ou 1 (falha)  
  
## <a name="result-sets"></a>Conjuntos de resultados  
  
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|**device_name**|**sysname**|Nome do dispositivo lógico.|  
|**physical_name**|**nvarchar(260)**|Nome do arquivo físico.|  
|**description**|**nvarchar(255)**|A descrição do dispositivo.|  
|**status**|**Int**|Um número que corresponde a descrição do status do **descrição** coluna.|  
|**cntrltype**|**smallint**|Tipo de controlador do dispositivo:<br /><br /> 2 = Dispositivo de disco<br /><br /> 5 = Dispositivo de fita|  
|**size**|**Int**|Tamanho do dispositivo em páginas de 2 KB.|  
  
## <a name="remarks"></a>Remarks  
 Se *nome* for especificado, **sp_helpdevice** exibe informações sobre o dispositivo de despejo especificado. Se *nome* não for especificado, **sp_helpdevice** exibe informações sobre todos os dispositivos de despejo no **backup_devices** exibição do catálogo.  
  
 Dispositivos de despejo são adicionados ao sistema usando **sp_addumpdevice**.  
  
## <a name="permissions"></a>Permissões  
 Requer associação à função **pública** .  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir relata informações sobre todos os dispositivos de despejo em uma instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
EXEC sp_helpdevice;  
```  
  
## <a name="see-also"></a>Consulte também  
 [sp_addumpdevice &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md)   
 [sp_dropdevice &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdevice-transact-sql.md)   
 [Mecanismo de banco de dados armazenados procedimentos &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Procedimentos armazenados do sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
