---
title: srv_got_attention (API de Procedimento Armazenado Estendido) | Microsoft Docs
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: extended-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- srv_got_attention
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_got_attention
ms.assetid: 805e68e1-d17f-41bd-8b9f-a27283bb6fbe
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 541d9ebe6bb7752a9025f65f1570df28f253bb88
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="srvgotattention-extended-stored-procedure-api"></a>srv_got_attention (API do procedimento armazenado estendido)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Use a integração CLR em vez disso.  
  
 Verifica se a tarefa ou a conexão atual precisa ser anulada e retorna TRUE se a conexão for interrompida ou se o lote for anulado  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
BOOL srv_got_attention (SRV_PROC *   
srvproc  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *srvproc*  
 Ponteiro que identifica uma conexão de banco de dados.  
  
## <a name="return-value"></a>Valor de retorno  
 TRUE se a conexão for interrompida ou se o lote for anulado. FALSE se a conexão ou o lote estiverem ativos.  
  
## <a name="remarks"></a>Remarks  
 Um procedimento armazenado estendido de execução longa deve verificar a atenção do servidor chamando **srv_got_attention** periodicamente, de forma que o procedimento possa ser encerrado quando a conexão for interrompida ou o lote for anulado.  
  
> [!IMPORTANT]  
>  Você deve examinar totalmente o código-fonte de procedimentos armazenados estendidos e deve testar as DLLs compiladas antes de instalá-las em um servidor de produção. Para obter informações sobre revisão e testes de segurança, consulte este [site da Microsoft](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
  
