---
title: "Gerenciador de Conexões WMI | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: connection-manager
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.wmiconnection.f1
helpviewer_keywords:
- connections [Integration Services], WMI
- connection managers [Integration Services], WMI
- WMI connection manager [Integration Services]
ms.assetid: fbfa4ba7-3d0d-4d6b-94ad-50741a88d03d
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d432432905afd9a1ef2355e16540cc5caa64e0a2
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2018
---
# <a name="wmi-connection-manager"></a>Gerenciador de conexões WMI
  Um gerenciador de conexões WMI permite que um pacote use o WMI (Instrumentação de Gerenciamento do Windows, Windows Management Instrumentation) para gerenciar informações em um ambiente corporativo. A tarefa Serviço Web que o [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] inclui usa um gerenciador de conexões WMI.  
  
 Quando você adiciona um gerenciador de conexões WMI a um pacote, o [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] cria um gerenciador de conexões que resolve uma conexão WMI no tempo de execução, define as propriedades do gerenciador de conexões e adiciona o gerenciador de conexões à coleção **Conexões** no pacote. A propriedade **ConnectionManagerType** do gerenciador de conexões está definida como **WMI**.  
  
## <a name="configuration-of-the-wmi-connection-manager"></a>Configuração do gerenciador de conexões WMI  
 Você pode configurar um gerenciador de conexões WMI das seguintes maneiras:  
  
-   Especifique o nome de um servidor.  
  
-   Especifique um namespace no servidor.  
  
-   Selecione o modo de autenticação para a conexão com o servidor.  
  
 Você pode definir propriedades pelo Designer do [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou programaticamente.  
  
 Para obter mais informações sobre as propriedades que podem ser definidas no [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, consulte [Editor do Gerenciador de Conexões WMI](../../integration-services/connection-manager/wmi-connection-manager-editor.md).  
  
 Para obter informações sobre como configurar um gerenciador de conexões programaticamente, consulte <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> e [Adicionando conexões programaticamente](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="wmi-connection-manager-editor"></a>Editor do Gerenciador de Conexões WMI
  Use a caixa de diálogo **Gerenciador de Conexões WMI** para especificar uma conexão WMI (Instrumentação de Gerenciamento do Windows) da Microsoft com um servidor.  
  
 Para obter mais informações sobre o gerenciador de conexões WMI, consulte [WMI Connection Manager](../../integration-services/connection-manager/wmi-connection-manager.md).  
  
### <a name="options"></a>Opções  
 **Nome**  
 Forneça um nome exclusivo para o gerenciador de conexões.  
  
 **Descrição**  
 Descreva o gerenciador de conexões. Como prática recomendável, descreva o gerenciador de conexões em termos de objetivo, para tornar os pacotes autodocumentados e mais fáceis de manter.  
  
 **Nome do servidor**  
 Forneça o nome do servidor com o qual deseja fazer a conexão WMI.  
  
 **Namespace**  
 Especifique o namespace WMI.  
  
 **Usar a autenticação do Windows**  
 Selecione para usar Autenticação do Windows. Se usar Autenticação do Windows, não será preciso fornecer um nome de usuário nem senha para a conexão.  
  
 **User name**  
 Se não usar Autenticação do Windows, será preciso fornecer um nome de usuário para a conexão.  
  
 **Senha**  
 Se não usar Autenticação do Windows, será preciso fornecer uma senha para a conexão.  
  
 **Testar**  
 Teste as configurações do gerenciador de conexões.  
  
## <a name="see-also"></a>Consulte Também  
 [Tarefa Serviços Web](../../integration-services/control-flow/web-service-task.md)   
 [Conexões do SSIS &#40;Integration Services&#41;](../../integration-services/connection-manager/integration-services-ssis-connections.md)  
