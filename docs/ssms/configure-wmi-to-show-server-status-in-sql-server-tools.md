---
title: Configurar o WMI para mostrar o status do servidor nas ferramentas do SQL Server | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms
ms.reviewer: 
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WMI Provider for Server Events, setting permissions
- WMI permissions [SQL Server]
ms.assetid: 7e97197b-ed4d-40d1-9a52-9ab1d92401d7
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 654dfff830fa18a1a38a3ecb3454cfa824e097c9
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/23/2018
---
# <a name="configure-wmi-to-show-server-status-in-sql-server-tools"></a>Configurar o WMI para mostrar o status do servidor nas ferramentas do SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Este tópico descreve como configurar o WMI para mostrar o status de servidor nas ferramentas do SQL Server no [!INCLUDE[ssCurrent](../includes/sscurrent_md.md)]. Na conexão com servidores, os componentes Servidores Registrados e Pesquisador de Objetos do [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)], assim como o [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] Configuration Manager, usam o Windows Management Instrumentation (WMI) para obter o status dos serviços do [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] (MSSQLSERVER) e do [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] Agent (MSSQLSERVER). Para exibir o status do serviço, o usuário deve ter direitos para acessar o objeto WMI remotamente. O servidor deve ter o WMI instalado para que essa permissão possa ser configurada.  
  
## <a name="SSMSProcedure"></a>Para configurar a permissão de WMI  
  
1.  No menu **Iniciar** no servidor remoto, clique em **Executar**.  
  
2.  Na caixa **Abrir** , digite **wmimgmt.msc**e clique em **OK**.  
  
3.  No programa **Windows Management Infrastructure** , clique com o botão direito do mouse em **Controle WMI (Local)**e clique em **Propriedades**.  
  
4.  Na caixa de diálogo **Propriedades do Controle WMI (Local)** , na guia **Segurança** , expanda **Raiz**e clique em **CIMV2**.  
  
5.  Clique em **Segurança** para abrir a caixa de diálogo **Segurança de ROOT\CIMV2** .  
  
6.  Adicione um grupo ou usuário à caixa **Nomes de grupo ou de usuário** e selecione-o.  
  
7.  Na caixa **Permissões do***<group or user>*, selecione a coluna **Permitir** da permissão **Habilitação Remota** para os usuários que desejam detectar remotamente o status do serviço.  
  
## <a name="see-also"></a>Consulte Também  
[Iniciar, parar ou pausar o serviço do SQL Server Agent](../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)  
  
