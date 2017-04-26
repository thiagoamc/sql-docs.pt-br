---
title: "Configura&#231;&#227;o da &#193;rea de Superf&#237;cie | Microsoft Docs"
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
  - "reduzindo área da superfície atacável"
  - "atualizando o SQL Server, segurança"
  - "configuração da área da superfície [SQL Server]"
  - "configuração da área de superfície [SQL Server], sobre a configuração da área de superfície"
  - "área da superfície atacável [SQL Server]"
  - "instalando o SQL Server, segurança"
ms.assetid: f741169c-1453-4ad2-830b-bf2be27d712f
caps.latest.revision: 79
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 79
---
# Configura&#231;&#227;o da &#193;rea de Superf&#237;cie
  Na configuração padrão de novas instalações do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], muitos recursos não estão habilitados. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instala e inicia seletivamente somente os serviços e recursos principais, para reduzir o número de recursos que podem ser atacados por um usuário mal-intencionado. Um administrador de sistema pode alterar esses padrões no momento da instalação e também seletivamente habilitar ou desabilitar recursos de uma instância em execução do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Além disso, alguns componentes podem não estar disponíveis ao estabelecer conexão a partir de outros computadores até que os protocolos sejam configurados.  
  
> [!NOTE]  
>  Ao contrário das novas instalações, nenhum serviço ou recurso existente é desativado durante uma atualização, mas as opções adicionais de configuração da área da superfície poderão ser aplicadas após a conclusão da atualização.  
  
## Protocolos, conexão e opções de inicialização  
 Use o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager para iniciar e interromper serviços, configurar opções de inicialização e habilitar protocolos e outras opções de conexão.  
  
#### Para iniciar o SQL Server Configuration Manager  
  
1.  No menu **Iniciar** , aponte para **Todos os Programas**, aponte para [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], aponte para **Ferramentas de Configuração**e clique em **SQL Server Configuration Manager**.  
  
    -   Use a área **Serviços do SQL Server** para iniciar componentes e configurar as opções de inicialização automática.  
  
    -   Use a área **Configuração de Rede do SQL Server** para habilitar protocolos de conexão e opções de conexão, como portas TCP/IP fixas, ou forçar a criptografia.  
  
 Para obter mais informações, consulte [SQL Server Configuration Manager](../../relational-databases/sql-server-configuration-manager.md). A conectividade remota também pode depender da configuração correta de um firewall. Para obter mais informações sobre como fazer isso, veja [Configurar o Firewall do Windows para permitir acesso ao SQL Server](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).  
  
## Habilitando e desabilitando recursos  
 A habilitação e desabilitação de recursos do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] podem ser configuradas usando as facetas no [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
#### Para configurar área da superfície usando as facetas  
  
1.  No [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], conecte-se ao componente do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  No Pesquisador de Objetos, clique com o botão direito do mouse no servidor e clique em **Facetas**.  
  
3.  Na caixa de diálogo **Exibir Facetas**, expanda a lista **Faceta** e selecione a faceta **Configuração da Área da Superfície** apropriada (**Configuração da Área da Superfície**, **Configuração da Área da Superfície para o Analysis Services** ou **Configuração da Área da Superfície para o Reporting Services**).  
  
4.  Na área **Propriedades da faceta**, selecione os valores desejados para cada propriedade.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 Para verificar a configuração de uma faceta periodicamente, use o Gerenciamento Baseado em Política. Para obter mais informações sobre o gerenciamento baseado em políticas, veja [Administrar servidores usando o gerenciamento baseado em políticas](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md).  
  
 Você também pode definir opções do [!INCLUDE[ssDE](../../includes/ssde-md.md)] usando o procedimento armazenado **sp_configure**. Para obter mais informações, consulte [Opções de configuração do servidor &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
 Para alterar a propriedade **EnableIntegrated Security** do [!INCLUDE[ssRS](../../includes/ssrs-md.md)], use as configurações de propriedades no [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Para alterar as propriedades **Eventos de agendamento e entrega de relatório** e **Serviço Web e acesso HTTP**, edite o arquivo de configuração **RSReportServer.config**.  
  
## Opções do prompt de comando  
 Use o cmdlet **Invoke-PolicyEvaluation**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] do PowerShell para invocar as Políticas de Configuração da Área da Superfície. Para obter mais informações, veja [Usar os cmdlets do Mecanismo de Banco de Dados](../../relational-databases/scripting/use-the-database-engine-cmdlets.md).  
  
## Pontos de extremidade SOAP e do Service Broker  
 Para desabilitar os pontos de extremidade, use o Gerenciamento Baseado em Política. Para criar e alterar as propriedades de pontos de extremidade, use [CREATE ENDPOINT &#40;Transact-SQL&#41;](../../t-sql/statements/create-endpoint-transact-sql.md) e [ALTER ENDPOINT &#40;Transact-SQL&#41;](../../t-sql/statements/alter-endpoint-transact-sql.md).  
  
## Conteúdo relacionado  
 [Central de segurança do Mecanismo de Banco de Dados do SQL Server e Banco de Dados SQL do Azure](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  