---
title: "Configura&#231;&#227;o de rede de cliente | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configuração de cliente [SQL Server], conexões"
  - "Mecanismo de banco de dados [SQL Server], configurações de rede"
  - "conexões [SQL Server], configuração de cliente"
  - "conexões de cliente [SQL Server], sobre conexões de rede de cliente"
  - "computadores clientes [SQL Server]"
  - "conexões de cliente [SQL Server]"
  - "conexões de rede [SQL Server], configuração de cliente"
ms.assetid: c382eacd-0a0c-40a4-958f-9b774eb2d734
caps.latest.revision: 38
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 38
---
# Configura&#231;&#227;o de rede de cliente
  O software cliente permite que computadores cliente se conectam a uma instância do [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] em uma rede. Um "cliente" é um aplicativo front-end que usa os serviços fornecidos por um servidor como o [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. O computador que hospeda esse aplicativo é denominado *computador cliente*.  
  
 No nível mais simples, um cliente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pode residir na mesma máquina que uma instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Geralmente, porém, um cliente se conecta com um ou mais servidores remotos em uma rede. A arquitetura cliente/servidor do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] permite que ele gerencie clientes vários clientes e servidores em uma rede. As configurações padrão do cliente são satisfeitas na maioria das situações.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] clientes podem incluir aplicativos de vários tipos, como:  
  
-   Consumidores de OLE DB  
  
     Esses aplicativos usam o provedor de OLE DB do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client para se conectarem a uma instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. O provedor de OLE DB atua como mediador entre o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e os aplicativos cliente que consomem dados do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] como conjuntos de linhas OLE DB. O utilitário de prompt de comando **sqlcmd** e [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] são exemplos de aplicativos OLE DB.  
  
-   aplicativos ODBC  
  
     Esses aplicativos incluem utilitários clientes instalados com as versões anteriores do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], como o utilitário de prompt de comando **osql** e outros aplicativos que usam o driver ODBC do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client para se conectarem a uma instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Clientes DB-Library  
  
     Esses aplicativos incluem o utilitário de prompt de comando **isql** do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e clientes gravados na biblioteca de banco de dados. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o suporte a aplicativos cliente que usam a DB-Library é limitado a recursos do [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0.  
  
> [!NOTE]  
>  Embora o [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ainda ofereça suporte a conexões de aplicativos existentes que usam DB-Library e APIs do SQL, não inclui os arquivos ou a documentação necessária para programar trabalho em aplicativos que usam essas APIs. Uma versão futura do [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] descartará suporte para conexões do DB-Library ou aplicativos do Embedded SQL. Não use DB-Library ou Embedded SQL para desenvolver novos aplicativos. Remova qualquer dependência no DB-Library ou no Embedded SQL ao modificar aplicativos existentes. Em vez destas APIs, use o namespace SQLClient ou uma API como OLE DB ou ODBC. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] não inclui a DLL DB-Library necessária para executar estes aplicativos. Para executar o DB-Library ou os aplicativos SQL inserindos, é necessário ter disponível o DB-Library DLL do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versão 6.5, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 ou [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].  
  
 Independentemente do tipo de aplicativo, o gerenciamento de um cliente consiste principalmente em configurar sua conexão com os componentes de servidor do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Dependendo dos requisitos do seu site, o gerenciamento do cliente pode variar desde inserir o nome do computador servidor e criar uma biblioteca de entradas de configuração personalizadas até a acomodação de um ambiente de vários servidores diversificado.  
  
 A DLL do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client contém as bibliotecas de rede e é instalada pelo programa de instalação. Os protocolos de rede não estão habilitados durante a instalação para novas instalações do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Instalações atualizadas habilitam os protocolos habilitados anteriormente. Os protocolos de rede subjacentes são instalados como parte da Instalação do Windows (ou por Redes no Painel de Controle). As ferramentas seguintes são usadas para gerenciar clientes do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager  
  
     Componentes de rede de cliente e servidor são gerenciados com o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, que combina o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Network Utility, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client Network Utility e o Service Manager de versões anteriores. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] O Configuration Manager é um snap-in do MMC ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console). Ele também é exibido como um nó no snap-in do Windows Computer Manager. As bibliotecas de rede individuais podem ser habilitadas, desabilitadas, configuradas e priorizadas com o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.  
  
-   Instalação  
  
     Execute a instalação do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para instalar os componentes de rede em um computador cliente. As bibliotecas de rede individuais podem ser habilitadas ou desabilitadas durante instalação quando a Instalação é iniciada no prompt de comando.  
  
-   Administrador de Fonte de Dados ODBC  
  
     O Administrador de Fonte de Dados ODBC permite criar e modificar fontes de dados ODBC em computadores que executam o sistema operacional Microsoft Windows.  
  
## Nesta seção  
 [Configurar protocolos de cliente](../../database-engine/configure-windows/configure-client-protocols.md)  
  
 [Criar ou excluir um alias de servidor para ser usado por um cliente &#40;SQL Server Configuration Manager&#41;](../../database-engine/configure-windows/create or delete a server alias for use by a client.md)  
  
 [Fazendo o logon no SQL Server](../../database-engine/configure-windows/logging-in-to-sql-server.md)  
  
 [Abrir o Administrador de Fonte de Dados ODBC](../../database-engine/configure-windows/open-the-odbc-data-source-administrator.md)  
  
 [Verificar a versão do driver ODBC do SQL Server &#40;Windows&#41;](../../database-engine/configure-windows/check-the-odbc-sql-server-driver-version-windows.md)  
  
## Conteúdo relacionado  
 [Configuração de rede do servidor](../../database-engine/configure-windows/server-network-configuration.md)  
  
 [Gerenciar os serviços do Mecanismo de Banco de Dados](../../database-engine/configure-windows/manage-the-database-engine-services.md)  
  
  