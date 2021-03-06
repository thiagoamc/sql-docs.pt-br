---
title: "Enviar comentários de telemetria à Microsoft (SQL Server PDW)"
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
ms.assetid: 40a994f0-7eff-4db9-9572-401d6e1187a0
caps.latest.revision: "18"
ms.openlocfilehash: f78a9e7c1e66085dd84ba71e8e7b5f517131e18a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="send-telemetry-feedback-to-microsoft"></a>Enviar comentários de telemetria à Microsoft
Analytics Platform System tem um recurso de telemetria opcional que envia dados de Console de administração para a Microsoft. Recomendamos que você habilite esta opção para nos ajudar a melhorar o produto.  
  
> [!NOTE]  
> Nesta versão, Microsoft não está monitorando ativamente os dados de telemetria. O dado está sendo coletado para apenas para fins de análise.  
  
## <a name="privacy"></a>Privacidade  
Para fornecer a proteção de privacidade máximo, APS é fornecido sem habilitar a telemetria. Antes de habilitar esse recurso, primeiro examine o [declaração de privacidade do Microsoft Analytics Platform System](http://go.microsoft.com/fwlink/?LinkId=400902). Em seguida, para aceitar execute o script do PowerShell descrito abaixo.  
  
## <a name="enable"></a>Habilite a Telemetria  
**Encaminhamento de DNS:** enviar dados de telemetria à Microsoft requer Analytics Platform System para se conectar à internet através de um encaminhador DNS. Para habilitar esse recurso, você deve habilitar o encaminhamento em todos os hosts e VMs de carga de trabalho DNS. Invocar o `Enable-RemoteMonitoring` com o `SetupDnsForwarder` opção para configurar o encaminhamento de DNS e habilite a telemetria corretamente. Invocar o `Enable-RemoteMonitoring` comando sem o `SetupDnsForwarder` opção quando o encaminhamento de DNS já está configurado e você deseja habilitar o monitoramento de pulsação.  
  
> [!IMPORTANT]  
> Habilitar o encaminhamento de DNS abre a conexão de internet para todos os hosts e VMs de carga de trabalho.  
  
#### <a name="to-enable-feedback"></a>Para habilitar comentários  
  
1.  Usando uma conta de administrador de domínio do dispositivo, conecte-se ao nó de controle (***appliance_domain*-CTL01**) e abra um prompt de comando usando suas credenciais de administrador do Windows.  
  
2.  Navegue até o seguinte diretório: `C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100`.  
  
3.  Importe o módulo`Configure-RemoteMonitoring.ps1`  
  
    > [!NOTE]  
    > Para importar, você deve usar dois pontos no comando.  
  
    **Exemplo:**  
  
    ```  
    PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> . .\Configure-RemoteMonitoring.ps1  
    ```  
  
4.  Invocar o `Enable-RemoteMonitoring` comando.  
  
    > [!NOTE]  
    > O script assume que a conexão de internet está funcionando corretamente e não valida a conexão de internet.  
  
    1.  Na primeira vez que você habilite a telemetria, use o comando a seguir para garantir que todos os encaminhadores de DNS estão configurados corretamente. Neste exemplo, substitua o endereço IP do DNS encaminhado `xx.xx.xx.xx` com o endereço IP do encaminhador de DNS em seu ambiente.  
  
        ```  
        PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> Enable-RemoteMonitoring -SetupDnsForwarder -DnsForwarderIp xx.xx.xx.xx  
        ```  
  
    2.  Quando os encaminhadores DNS já estiverem configurados, como reabilitar desabilitada anteriormente telemetria, use o comando a seguir para habilitar a telemetria sem configurar o encaminhamento de DNS.  
  
        ```  
        PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> Enable-RemoteMonitoring  
        ```  
  
5.  Você será solicitado para ler e confirmar que o APS coletará informações sobre o dispositivo. Haverá um link para a declaração de privacidade de pontos de acesso que você pode copiar e colar em qualquer navegador da internet para revisão.  
  
6.  Digite **Y** para aceitar e optar por comentários ou digite **N** para não aceitar.  
  
7.  Se você digitou **Y** haverá uma série de comandos que serão executados e que permitem a telemetria (e opcionalmente o encaminhador de DNS) recursos em sua aplicação. Se você vir quaisquer erros ou informações que levam você acreditar que o comando não foi bem-sucedida entre em contato com o CSS para obter assistência.  
  
Se você digitou **N**, nenhum comando será executado e o recurso não será habilitado e não há nada mais para que você faça.  
  
Não há nenhum problema em execução o `Enable-RemoteMonitoring` comando várias vezes. Se o encaminhador DNS já estiver definido, você obterá uma mensagem de aviso que indica que é o caso.  
  
## <a name="disable"></a>Desabilitar a Telemetria  
Desativando a telemetria interromperá todas as operações que se comunicam informações sobre o estado do dispositivo para pontos de acesso de monitoramento de serviço na nuvem.  
  
> [!IMPORTANT]  
> Executar esta operação não desabilitará o encaminhador de DNS ou conexão de internet que pode estar em uso por outros recursos no dispositivo.  
  
#### <a name="to-disable-telemetry"></a>Para desabilitar a Telemetria  
  
1.  Usando uma conta de administrador de domínio do dispositivo, conecte-se ao nó de controle (***appliance_domain*-CTL01**) e abra uma janela do PowerShell com privilégios de administrador.  
  
2.  Navegue até o seguinte diretório: `C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100`.  
  
3.  Importe o módulo`Configure-RemoteMonitoring.ps1`  
  
    > [!NOTE]  
    > Para importar, você deve usar dois pontos no comando.  
  
    **Exemplo:**  
  
    ```  
    PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> . .\Configure-RemoteMonitoring.ps1  
    ```  
  
4.  Invocar o `Disable-RemoteMonitoring` comando sem parâmetros. Esse comando irá parar de enviar comentários. (Isso não afetará o monitoramento local.) No entanto, o comando será não desabilitar o encaminhador de DNS e/ou desabilitar qualquer conectividade com a internet. Isso deve ser feito manualmente depois de desabilitar os comentários com êxito.  
  
    **Exemplo:**  
  
    ```  
    PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> Disable-RemoteMonitoring  
    ```  
  
Se você vir quaisquer erros ou informações que levam você acreditar que o comando não foi bem-sucedida entre em contato com o CSS para obter assistência.  
  
Não há nenhum problema em execução o `Disable-RemoteMonitoring` comando várias vezes.  
  
## <a name="see-also"></a>Consulte Também  
[Monitorar o dispositivo usando o Console de administração &#40; Analytics Platform System &#41;](monitor-the-appliance-by-using-the-admin-console.md)  
[Monitorar o dispositivo por meio de exibições do sistema &#40; Analytics Platform System &#41;](monitor-the-appliance-by-using-system-views.md)  
[Monitorar o dispositivo usando o System Center Operations Manager &#40; Analytics Platform System &#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)  
[Use um encaminhador DNS para resolver nomes DNS de dispositivo não &#40; Analytics Platform System &#41;](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md)  
  
