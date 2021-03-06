---
title: srv_senddone (API de Procedimento Armazenado Estendido) | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
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
- srv_senddone
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_senddone
ms.assetid: 1fc4f1d5-56d4-43f6-b5e4-0c0cc295cba3
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5f45177df0d252f3bd33475c20c60383f71f7ae7
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="srvsenddone-extended-stored-procedure-api"></a>srv_senddone (API de procedimento armazenado estendido)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Use a integração CLR em vez disso.  
  
 Envia uma mensagem de conclusão de resultado para o cliente.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
int srv_senddone (  
SRV_PROC *  
srvproc  
,  
DBUSMALLINT   
status  
,  
DBUSMALLINT  
info  
,  
DBINT  
count   
);  
  
```  
  
## <a name="arguments"></a>Argumentos  
 *srvproc*  
 É um ponteiro para a estrutura SRV_PROC que é o identificador de uma conexão de cliente específica (neste caso, o identificador que recebeu a solicitação de linguagem). A estrutura contém informações que a biblioteca de APIs de procedimento armazenado estendido usa para gerenciar a comunicação e os dados entre o aplicativo e o cliente.  
  
 *status*  
 É um campo de 2 bytes para vários sinalizadores *status* . Vários sinalizadores podem ser definidos usando os operadores lógicos AND e OR com valores de sinalizador *status* . A seguinte tabela lista os possíveis sinalizadores *status* .  
  
|Sinalizador de status|Description|  
|-----------------|-----------------|  
|SRV_DONE_COUNT|O parâmetro *count* contém uma contagem válida.|  
|SRV_DONE_ERROR|O comando do cliente atual recebeu um erro.|  
  
 *info*  
 É um campo reservado de 2 bytes. Defina o valor como 0.  
  
 *contagem*  
 É um campo de 4 bytes usado para indicar uma contagem do conjunto de resultados atual. Se o sinalizador SRV_DONE_COUNT for definido no campo *status* , *count* manterá uma contagem válida.  
  
## <a name="returns"></a>Retorna  
 SUCCEED ou FAIL  
  
## <a name="remarks"></a>Remarks  
 Uma solicitação do cliente pode fazer com que o servidor execute vários comandos e retorne vários conjuntos de resultados. Para cada conjunto de resultados, **srv_senddone** deve retornar uma mensagem de conclusão de resultado para o cliente.  
  
 O campo *count* indica o número de linhas afetadas por um comando. Se o campo *count* contiver uma contagem, o sinalizador SRV_DONE_COUNT deverá ser definido no campo *status* . Essa configuração permite ao cliente distinguir entre um valor *count* igual a 0 e um campo não usado *count* .  
  
 Não chame **srv_senddone** no manipulador SRV_CONNECT.  
  
> [!IMPORTANT]  
>  Você deve examinar totalmente o código-fonte de procedimentos armazenados estendidos e deve testar as DLLs compiladas antes de instalá-las em um servidor de produção. Para obter informações sobre revisão e testes de segurança, consulte este [site da Microsoft](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
  
