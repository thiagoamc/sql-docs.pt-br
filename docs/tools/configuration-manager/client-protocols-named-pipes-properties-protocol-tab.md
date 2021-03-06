---
title: "Protocolos de cliente – propriedades de Pipes (guia protocolo) com nome | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: configuration-manager
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipes [SQL Server], connecting to
- Named Pipes [SQL Server], default pipe
- client protocols [SQL Server]
ms.assetid: 30fbae62-2f2e-4d36-9c6e-3444fff68781
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 67a401a8edf4c6818899b755d9444edd09165972
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2018
---
# <a name="client-protocols---named-pipes-properties-protocol-tab"></a>Protocolos de Cliente – Propriedades de Pipes Nomeados (guia Protocolo)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
No [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, use a guia **Protocolo** na caixa de diálogo **Propriedades de Pipes Nomeados** para exibir ou modificar a descrição do pipe padrão. Para se conectar a um pipe diferente, digite o pipe na caixa **Pipe Padrão** . Para obter mais informações sobre cadeias de conexão, consulte [Creating a Valid Connection String Using Named Pipes](http://msdn.microsoft.com/library/90930ff2-143b-4651-8ae3-297103600e4f).  
  
## <a name="options"></a>Opções  
 **Pipe Padrão**  
 Especifica o pipe padrão que a biblioteca de rede Pipes Nomeados usará para tentar se conectar à instância de destino do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Por padrão, o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] escuta em: `\\.\pipe\sql\query`  
  
 Para se conectar ao pipe padrão, digite `sql\query`  
  
 **Ativado**  
 Os valores possíveis são **Sim** e **Não**.  
  
## <a name="see-also"></a>Consulte também  
 [Escolhendo um protocolo de rede](http://msdn.microsoft.com/library/6565fb7d-b076-4447-be90-e10d0dec359a)  
  
  
