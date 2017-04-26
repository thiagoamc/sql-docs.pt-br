---
title: "Esta pasta de trabalho cont&#233;m uma ou mais consultas que atualizam dados externos. | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: aa65c992-eb41-4032-9e11-a9ba871b6a3c
caps.latest.revision: 8
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 7
---
# Esta pasta de trabalho cont&#233;m uma ou mais consultas que atualizam dados externos.
  Para pastas de trabalho do Excel que contêm dados [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], os Serviços do Excel mostram este aviso quando detectam informações de conexão e solicitam que você habilite ou desabilite consultas para essa pasta de trabalho.  
  
## Detalhes  
  
|||  
|-|-|  
|Nome do produto|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] para SharePoint|  
|Versão do Produto|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Causa|Os Serviços do Excel são configurados para avisar na atualização de dados.|  
|Texto da mensagem|Esta pasta de trabalho contém uma ou mais consultas que atualizam dados externos. Um usuário mal-intencionado pode criar uma consulta para acessar informações confidenciais e distribuí-las a outros usuários ou pode executar outras ações prejudiciais.<br /><br /> Se você confiar na origem dessa pasta de trabalho, clique em Sim para habilitar consultas a dados externos nessa pasta de trabalho. Se você não tiver certeza, clique em Não para que as alterações não sejam aplicados em sua pasta de trabalho.<br /><br /> Você deseja habilitar consultas a dados externos nesta pasta de trabalho?|  
  
## Explicação  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] As pastas de trabalho contêm cadeias de conexão de dados incorporadas usadas pelo Excel para se comunicar com um servidor externo [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] que carrega e calcula os dados. Quando o aviso na atualização de dados estiver habilitado, o Serviços do Excel detectará essa cadeia de conexão e avisará o usuário.  
  
 Para filtrar e dividir dados [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] na pasta de trabalho, as consultas devem ser habilitadas. Certifique-se de habilitar consultas apenas para as pastas de trabalho [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] nas quais você confia.  
  
## Ação do usuário  
 Clique em **Sim** para habilitar consultas.  
  
 Você também pode alterar os parâmetros de configuração para que o aviso na atualização não ocorra mais:  
  
1.  Na Administração Central, em Gerenciamento de Aplicativo, clique em **Gerenciar aplicativos de serviço**.  
  
2.  Clique em **Aplicativo dos Serviços do Excel**.  
  
3.  Clique em **Local de Arquivo Confiável**.  
  
4.  Clique em **http://** ou no local que você deseja configurar.  
  
5.  Em Dados Externos, desmarque a caixa de seleção para **Avisar na atualização de dados**.  
  
6.  Clique em **OK**.  
  
 Como alternativa, você pode criar um novo local confiável para sites que contenham pastas de trabalho do [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] e, em seguida, modificar as definições de configuração apenas para esse site. Para obter mais informações, consulte [Create a trusted location for Power Pivot sites in Central Administration](../../analysis-services/power-pivot-sharepoint/create-a-trusted-location-for-power-pivot-sites-in-central-administration.md).  
  
  