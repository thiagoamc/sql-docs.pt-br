---
title: "Método GetCurrentCertificate (classe SInstance) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
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
- GetCurrentCertificate Method (SInstance Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- GetCurrentCertificate method
ms.assetid: 9d2b72df-cb21-414a-abef-917f13d4de62
caps.latest.revision: 
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 950bbea868c04a0c7efc1e0ab1e842a51cb17c46
ms.sourcegitcommit: 0d904c23663cebafc48609671156c5ccd8521315
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2018
---
# <a name="getcurrentcertificate-method-sinstance-class"></a>Método GetCurrentCertificate (classe SInstance)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Obtém o certificado de segurança atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
object.GetCurrentCertificate(SHA)  
```  
  
## <a name="parts"></a>Partes  
 *objeto*  
 Um objeto da [classe SInstance](../../../relational-databases/wmi-provider-configuration-classes/sinstance-class/sinstance-class.md) que representa as configurações de servidor em uma instância do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
#### <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Description|  
|---------------|-----------------|  
|*SHA*|Um valor de objeto da cadeia de caracteres (parâmetro de saída) que especifica o certificado de segurança atual depois que o método é concluído.|  
  
## <a name="property-valuereturn-value"></a>Valor da propriedade/Valor do retorno  
 Um valor **uint32** , que é 0 se o serviço tiver sido modificado com êxito, 1 se a solicitação não tiver suporte e qualquer outro número para indicar um erro.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>Consulte também  
 [Configurando protocolos de rede do servidor e bibliotecas de rede](http://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
