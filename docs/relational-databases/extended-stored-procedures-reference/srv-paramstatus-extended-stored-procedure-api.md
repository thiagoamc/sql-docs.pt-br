---
title: srv_paramstatus (API de Procedimento Armazenado Estendido) | Microsoft Docs
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
- srv_paramstatus
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_paramstatus
ms.assetid: 86cecd45-0b09-42e9-8152-32a12a1c2b7a
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4ca30a57ad4196eb66c6cf9b7ea262d092fe5936
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="srvparamstatus-extended-stored-procedure-api"></a>srv_paramstatus (API de procedimento armazenado estendido)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Use a integração CLR em vez disso.  
  
 Retorna o status de um parâmetro de chamada de procedimento armazenado remoto específico.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
int srv_paramstatus (  
SRV_PROC *  
srvproc  
,  
int  
n   
);  
```  
  
## <a name="arguments"></a>Argumentos  
 *srvproc*  
 É um ponteiro para a estrutura SRV_PROC que identifica uma conexão de cliente específica (nesse caso, o identificador que recebeu a chamada do procedimento armazenado remoto). A estrutura contém informações que a biblioteca de APIs de procedimento armazenado estendido usa para gerenciar a comunicação e os dados entre o aplicativo e o cliente.  
  
 *n*  
 Indica o número do parâmetro. O primeiro parâmetro equivale ao número 1.  
  
## <a name="returns"></a>Retorna  
 Um **int** que contém sinalizadores de status para o parâmetro. Atualmente, há só um sinalizador: se bit 0 for definido como 1, o parâmetro será um parâmetro de retorno. Se não existir o *n*º parâmetro ou se não houver nenhum procedimento armazenado remoto, -1 será retornado.  
  
## <a name="remarks"></a>Remarks  
 Esta rotina retorna os sinalizadores de status para um parâmetro de chamada de procedimento armazenado remoto.  
  
 Os parâmetros contêm dados passados entre os clientes e o aplicativo com procedimentos armazenados remotos. O cliente pode especificar certos parâmetros como parâmetros de retorno. Esses parâmetros de retorno podem conter valores que o aplicativo devolve ao cliente.  
  
 Atualmente, o único sinalizador de status é um que indica se o parâmetro é um parâmetro de retorno.  
  
 Quando uma chamada de procedimento armazenado remoto é feita com parâmetros, os parâmetros podem ser passados pelo nome ou pela posição (sem-nome). Se a chamada de procedimento armazenado remoto for feita com alguns parâmetros transmitidos pelo nome e outros pela posição, ocorrerá um erro. Em caso de erro, o manipulador SRV_RPC ainda será chamado, mas aparecerá como se não houvesse parâmetros e **srv_rpcparams** retornará 0.  
  
> [!IMPORTANT]  
>  Você deve examinar totalmente o código-fonte de procedimentos armazenados estendidos e deve testar as DLLs compiladas antes de instalá-las em um servidor de produção. Para obter informações sobre revisão e testes de segurança, consulte este [site da Microsoft](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>Consulte Também  
 [srv_rpcparams &#40;API de Procedimento Armazenado Estendido&#41;](../../relational-databases/extended-stored-procedures-reference/srv-rpcparams-extended-stored-procedure-api.md)  
  
  
