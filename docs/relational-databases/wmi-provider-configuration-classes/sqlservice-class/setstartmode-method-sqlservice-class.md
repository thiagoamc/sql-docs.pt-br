---
title: "Método SetStartMode (classe SqlService) | Microsoft Docs"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: wmi
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- SetStartMode Method (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetStartMode method
ms.assetid: f6f198b4-f9a4-468c-8977-76462ef06e61
caps.latest.revision: 
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2012cfe7e91e20e7a92088712e01a3b9fdc26158
ms.sourcegitcommit: 0d904c23663cebafc48609671156c5ccd8521315
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2018
---
# <a name="setstartmode-method-sqlservice-class"></a>Método SetStartMode (classe SqlService)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Modifica o modo de início da instância do serviço.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
object.SetStartMode(StartMode)  
```  
  
## <a name="parts"></a>Partes  
 *objeto*  
 Um objeto da [classe SqlService](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) que representa o serviço.  
  
#### <a name="parameters"></a>Parâmetros  
 *StartMode*  
 Um valor **uint32** que especifica o modo de início da instância do serviço.  
  
 Os valores válidos são os seguintes:  
  
 Valor = 0. Inicializar – o driver do dispositivo é iniciado pelo carregador do sistema operacional. Esse valor só é válido para serviços do driver.  
  
 Valor = 1. Sistema - driver de dispositivo iniciado pelo método **IoInitSystem** . Esse valor só é válido para serviços do driver.  
  
 Valor = 2. Automático - serviço a ser iniciado automaticamente pelo gerenciador de controle de serviço durante a inicialização do sistema.  
  
 Valor = 3. Manual - serviço a ser iniciado pelo Gerenciador de Computador quando um processo chamar o método **StartService** .  
  
 Valor = 4. Desabilitado - serviço não pode mais ser iniciado.  
  
## <a name="property-valuereturn-value"></a>Valor da propriedade/Valor do retorno  
 Um valor **uint32** , que é 0 se o serviço tiver sido modificado com êxito ou 1 se a solicitação não tiver suporte. Qualquer outro número indica um erro.  
  
## <a name="remarks"></a>Comentários  
  
## <a name="see-also"></a>Consulte também  
 [Iniciando e parando serviços](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
