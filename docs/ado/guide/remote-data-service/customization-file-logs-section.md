---
title: "Arquivo de personalização Logs seção | Microsoft Docs"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- logs section in RDS [ADO]
- customization file in RDS [ADO]
ms.assetid: a368e264-865c-41ee-be00-d9097255c2ea
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 10f6e47bcf8cede8c59a406fef4951a11cbd56bd
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="customization-file-logs-section"></a>Seção de Logs do arquivo de personalização
O **logs** seção contém uma entrada de arquivo de log, que especifica o nome de um arquivo que registra erros durante a operação do **DataFactory**.  
  
> [!IMPORTANT]
>  Começando com o Windows 8 e Windows Server 2012, os componentes de servidor RDS não estão mais incluídos no sistema operacional Windows (veja o Windows 8 e [manual de compatibilidade do Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) para obter mais detalhes). Componentes de cliente RDS serão removidos em uma versão futura do Windows. Evite usar esse recurso em desenvolvimentos novos e planeje modificar os aplicativos que atualmente o utilizam. Aplicativos que usam o RDS devem migrar para [WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintaxe  
 É uma entrada de arquivo de log do formulário:  
  
```  
  
err=  
FileName  
  
```  
  
## <a name="remarks"></a>Remarks  
  
|Parte|Description|  
|----------|-----------------|  
|**err**|Uma cadeia de caracteres literal que indica que isso é uma entrada de arquivo de log.|  
|*FileName*|Um nome de arquivo e caminho completo. O nome de arquivo comum é **c:\msdfmap.log**.|  
  
 O arquivo de log conterá o nome de usuário, o HRESULT, a data e a hora de cada erro.  
  
## <a name="see-also"></a>Consulte também  
 [Arquivo de personalização de conectar-se a seção](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [Seção SQL do arquivo de personalização](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [Seção do arquivo UserList de personalização](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [Personalização do DataFactory](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Configurações de cliente necessárias](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Noções básicas sobre o arquivo de personalização](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)   
 [Escrevendo seu próprio manipulador personalizado](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)


