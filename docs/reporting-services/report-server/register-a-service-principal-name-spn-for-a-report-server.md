---
title: "Registrar um SPN (Nome da Entidade de Serviço) para um servidor de relatório | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: report-server
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dda91d4f-77cc-4898-ad03-810ece5f8e74
caps.latest.revision: "7"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: d8f339aea53a9da7ee183bb2a6efee25bc603c13
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2018
---
# <a name="register-a-service-principal-name-spn-for-a-report-server"></a>Registrar um SPN (Nome da Entidade de Serviço) para um servidor de relatório
  Se estiver implantando o [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] em uma rede que use o protocolo Kerberos para autenticação mútua, você deverá criar um SPN (Nome da Entidade de Serviço) para o serviço Servidor de Relatório se configurá-lo para execução como uma conta de usuário do domínio.  
  
## <a name="about-spns"></a>Sobre SPNs  
 Um SPN é um identificador exclusivo para um serviço em uma rede que usa autenticação Kerberos. Consiste em uma classe de serviço, um nome de host e uma porta. Em uma rede que usa autenticação Kerberos, deve ser registrado um SPN para o servidor em uma conta interna do computador (como NetworkService ou LocalSystem) ou uma conta de usuário. Os SPNs são automaticamente registrados para contas internas. Entretanto, quando executar um serviço em uma conta de usuário do domínio, você deverá registrar manualmente o SPN para a conta que deseja usar.  
  
 Para criar um SPN, você pode usar o utilitário de linha de comando **SetSPN** . Para obter mais informações, consulte o seguinte:  
  
-   [Setspn](http://technet.microsoft.com/library/cc731241\(WS.10\).aspx) (http://technet.microsoft.com/library/cc731241(WS.10).aspx).  
  
-   [SPNs (Nomes da Entidade de Serviço) e Sintaxe SetSPN(Setspn.exe)](http://social.technet.microsoft.com/wiki/contents/articles/717.service-principal-names-spns-setspn-syntax-setspn-exe.aspx) (http://social.technet.microsoft.com/wiki/contents/articles/717.service-principal-names-spns-setspn-syntax-setspn-exe.aspx).  
  
 Você deve ser um administrador de domínio para executar o utilitário no controlador de domínio.  
  
## <a name="syntax"></a>Sintaxe  
 A sintaxe de comando para usar o utilitário SetSPN e criar um SPN para o servidor de relatório se assemelha ao seguinte:  
  
```  
Setspn -s http/<computername>.<domainname>:<port> <domain-user-account>  
```  
  
 **SetSPN** está disponível no Windows Server. O argumento de **-s** adiciona um SPN depois de não validar nenhuma duplicata. **OBSERVAÇÃO: -s** está disponível no Windows Server a partir do Windows Server 2008.  
  
 **HTTP** é a classe de serviço. O serviço Web Servidor de Relatórios é executado em HTTP.SYS. Uma criação por produto de um SPN para HTTP significa que todos os aplicativos Web no mesmo computador que são executados em HTTP.SYS (incluindo aplicativos hospedados no IIS) receberão tíquetes com base na conta de usuário do domínio. Se esses serviços forem executados em uma conta diferente, ocorrerá falha nas solicitações de autenticação. Para evitar esse problema, configure todos os aplicativos HTTP para que sejam executados na mesma conta ou considere a criação de cabeçalhos de host para cada aplicativo e, depois, a criação de SPNs separados para cada cabeçalho de host. Quando você configura cabeçalhos de host, é necessário fazer alterações de DNS, independentemente da configuração do [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 Os valores especificados para \<*computername*>, \<*domainname*> e \<*port*> identificam o endereço de rede exclusivo do computador que hospeda o servidor de relatório. Pode ser um nome de host local ou um nome de domínio totalmente qualificado (FQDN). Se você tiver somente um domínio e estiver usando a porta 80, poderá omitir \<*domainname*> e \<*port*> da linha de comando. \<*domain-user-account*> é a conta de usuário na qual o serviço Servidor de Relatório é executado e na qual o SPN deve ser registrado.  
  
## <a name="register-an-spn-for-domain-user-account"></a>Registrar um SPN para a conta de usuário do domínio  
  
#### <a name="to-register-an-spn-for-a-report-server-service-running-as-a-domain-user"></a>Para registrar um SPN para um serviço Servidor de Relatório que esteja em execução como um usuário do domínio  
  
1.  Instale o [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] e configure o serviço Servidor de Relatório para ser executado como uma conta de usuário do domínio. Observe que os usuários não poderão se conectar ao servidor de relatório até que você conclua as etapas a seguir.  
  
2.  Faça logon no controlador de domínio como administrador de domínio.  
  
3.  Abra uma janela do prompt de comando.  
  
4.  Copie o seguinte comando, substituindo os valores de espaço reservado por valores reais que sejam válidos para sua rede:  
  
    ```  
    Setspn -s http/<computer-name>.<domain-name>:<port> <domain-user-account>  
    ```  
  
     Por exemplo: `Setspn -s http/MyReportServer.MyDomain.com:80 MyDomainUser`  
  
5.  Execute o comando.  
  
6.  Abra o arquivo **RsReportServer.config** e localize a seção `<AuthenticationTypes>` .  
  
7.  Adicione `<RSWindowsNegotiate/>` como a primeira entrada desta seção para habilitar NTLM.  
  
## <a name="see-also"></a>Consulte Também  
 [Configurar uma conta de serviço &#40;SSRS Configuration Manager&#41;](http://msdn.microsoft.com/library/25000ad5-3f80-4210-8331-d4754dc217e0)   
 [Configurar a conta de serviço do servidor de relatório &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Gerenciar um servidor de relatórios de Modo Nativo do Reporting Services](../../reporting-services/report-server/manage-a-reporting-services-native-mode-report-server.md)  
  
  
