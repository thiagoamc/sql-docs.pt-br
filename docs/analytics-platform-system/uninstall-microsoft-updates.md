---
title: "Desinstalar as atualizações da Microsoft (Analytics Platform System)"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: df61570a-210d-4154-822f-98acd721f075
caps.latest.revision: "19"
ms.openlocfilehash: 52bd212a753f4bb69c79d8b8e274664d2100cbee
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="uninstall-microsoft-updates"></a>Desinstalar as atualizações da Microsoft
Este tópico descreve como desinstalar uma atualização da Microsoft instalada anteriormente no dispositivo Analytics Platform System.  
  
## <a name="before-you-begin"></a>Antes de começar  
  
### <a name="prerequisites"></a>Prerequisites  
Para executar essas etapas, você precisará de:  
  
-   Um logon Analytics Platform System com permissões para acessar o Console de administração para monitorar o dispositivo.  
  
-   Conhecimento da conta de administrador de domínio de malha de logon para o  *<Fabric Domain>*  **-HST01** nó.  
  
## <a name="HowToUninstallMSFT"></a>Para desinstalar as atualizações da Microsoft  
  
1.  Logon para o  *<Fabric Domain>*  **-HST01** nó como o administrador de domínio de malha.  
  
2.  Para desinstalar todas as atualizações aprovadas para desinstalar o WSUS, abra uma janela de Prompt de comando e digite o seguinte comando. Substituir os itens de espaço reservado *< >* com as informações apropriadas.  
  
    ```  
    C:\pdwinst\media\setup.exe /action="RemoveMicrosoftUpdate" /DomainAdminPasswords="<password>"  
    ```  
  
## <a name="see-also"></a>Consulte Também  
[Baixe e aplique as atualizações da Microsoft &#40; Analytics Platform System &#41;](download-and-apply-microsoft-updates.md)  
[Aplicar Hotfixes do sistema de plataforma de análise &#40; Analytics Platform System &#41;](apply-analytics-platform-system-hotfixes.md)  
[Desinstalar Hotfixes do sistema de plataforma de análise &#40; Analytics Platform System &#41;](uninstall-analytics-platform-system-hotfixes.md)  
[Manutenção de software &#40; Analytics Platform System &#41;](software-servicing.md)  
  
