---
title: "Habilitar um servidor de relat&#243;rios para acesso ao Power BI M&#243;vel | Microsoft Docs"
ms.date: "12/17/2015"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c1a71522-394b-46a7-b9ec-f964bdd81d82
caps.latest.revision: 7
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 7
---
# Habilitar um servidor de relat&#243;rios para acesso ao Power BI M&#243;vel
Você pode usar o aplicativo Power BI Móvel para consumir relatórios móveis. Há algumas coisas que você precisa configurar para permitir que o aplicativo Power BI Móvel conecte-se ao Reporting Services.  
  
-   [Relatórios móveis requerem o modo nativo do Reporting Services](#nativemode)  
-   [ Habilitar a autenticação básica no Reporting Services](#basicauth) (para CTP 3.2)  
-   [Recomendado para habilitar HTTPS junto com um certificado confiável válido para o dispositivo cliente](#https)  
-   [Analisar as configurações de firewall](#firewall)  
  
<a name="nativemode"/>  
## O modo nativo do Reporting Services é necessário  
Relatórios móveis são um recurso do modo nativo. Eles não estão disponíveis no modo integrado do SharePoint. O aplicativo Power BI Móvel só funcionará com uma instância do modo nativo.  
  
<a name="basicauth"/>  
## Habilite a autenticação básica  
O aplicativo Power BI Móvel do iOS requer a autenticação básica para se conectar e consumir relatórios móveis. O Reporting Services não está configurado com autenticação básica habilitada por padrão. Para obter informações sobre como configurar a autenticação básica, consulte [Configurar autenticação básica no Servidor de Relatório](../../reporting-services/security/configure-windows-authentication-on-the-report-server.md).  
  
Você também precisará ter a autenticação do Windows habilitada para permitir que o aplicativo publicador publique o relatório móvel.  
  
<a name="https"/>  
## Habilitar HTTPS  
É recomendável que você habilite HTTPS no Reporting Services se habilitar a autenticação básica. Se você habilitar o HTTPS, verifique se os certificados usados podem ser confiáveis nos dispositivos cliente que executam o aplicativo Power BI Móvel do iOS. Isso significa que a cadeia de certificação deve ser válida e disponível ao dispositivo cliente.  
  
Se você precisar usar um certificado autoassinado para fins de desenvolvimento ou avaliação, pode exportar o certificado do servidor de relatórios e instalá-lo no dispositivo móvel. Consulte a documentação do dispositivo sobre como instalá-lo naquele dispositivo.  
  
Para obter mais informações sobre como habilitar o SSL, consulte [Configurar conexões SSL em um servidor de relatórios do modo nativo](../../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md).  
  
<a name="firewall"/>  
## Analisar as configurações de firewall  
É recomendável que você revise suas configurações de firewall para garantir que todos os dispositivos possam se conectar com êxito ao Reporting Services.   
  
Para obter mais informações sobre como configurar o Firewall do Windows, consulte [Configurar um firewall para acesso ao servidor de relatórios](../../reporting-services/report-server/configure-a-firewall-for-report-server-access.md).  
  
## Consulte também  
  
[Configurar a autenticação Básica no servidor de relatório](../../reporting-services/security/configure-windows-authentication-on-the-report-server.md)  
[Configurar conexões SSL em um servidor de relatórios de modo nativo](../../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md)  
[Configurar um firewall para acesso ao servidor de relatório](../../reporting-services/report-server/configure-a-firewall-for-report-server-access.md)  
  
  
  
  
  
  