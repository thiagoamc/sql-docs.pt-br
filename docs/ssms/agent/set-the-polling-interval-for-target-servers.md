---
title: Definir o intervalo de sondagem para servidores de destino | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- interval for polling [SQL Server]
- target servers [SQL Server], polling interval
- polling interval [SQL Server]
ms.assetid: 4ffbbefa-77fb-442e-a77c-cb8c6cab9f3c
caps.latest.revision: ''
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 05a68e2b631265d0a66fdc9aea23f30e96699048
ms.sourcegitcommit: 34766933e3832ca36181641db4493a0d2f4d05c6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2018
---
# <a name="set-the-polling-interval-for-target-servers"></a>Set the Polling Interval for Target Servers
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> No momento, na [Instância Gerenciada do Banco de Dados SQL do Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), a maioria dos recursos do SQL Server Agent é compatível, mas não todos. Consulte [Azure SQL Database Managed Instance T-SQL differences from SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent) (Diferenças entre o T-SQL da Instância Gerenciada do Banco de Dados SQL do Azure e o SQL Server) para obter detalhes.

Este tópico descreve como definir a frequência com que o [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent atualiza as informações do servidor mestre para os servidores de destino. Um trabalho é uma série especificada de ações que o [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent executa. Um trabalho multisservidor é um trabalho executado por um servidor mestre em um ou mais servidores de destino.  
  
-   **Antes de começar:**  [Segurança](#Security)  
  
-   **Para definir o intervalo de sondagem para servidores de destino usando:** [SQL Server Management Studio](#SSMS), [Transact-SQL](#TSQL)  
  
## <a name="BeforeYouBegin"></a>Antes de começar  
Cada servidor de destino pode executar uma instância do mesmo trabalho ao mesmo tempo. Cada servidor de destino sonda o servidor mestre periodicamente, baixa uma cópia dos eventuais trabalhos novos a ele atribuídos e, em seguida, desconecta-se. O servidor de destino executa o trabalho localmente e, depois, reconecta-se ao servidor mestre para carregar o status do resultado do trabalho.  
  
> [!NOTE]  
> Se o servidor mestre não estiver acessível quando o servidor de destino tentar carregar o status do trabalho, este será colocado em spool até que o servidor mestre esteja novamente acessível.  
  
### <a name="Security"></a>Segurança  
Para obter informações detalhadas, consulte [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md) e [Choose the Right SQL Server Agent Service Account for Multiserver Environments](../../ssms/agent/choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md).  
  
## <a name="SSMS"></a>Usando o SQL Server Management Studio  
**Para definir o intervalo de sondagem de servidores de destino**  
  
1.  No **Pesquisador de Objetos** , conecte-se a uma instância do [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]e a expanda.  
  
2.  Clique com o botão direito do mouse em **SQL Server Agent**, aponte para **Administração Multisservidor**e clique em **Gerenciar Servidores de Destino**.  
  
3.  Na guia **Status do Servidor de Destino** , clique em **Postar Instruções**.  
  
4.  Na lista **Tipo de instrução** , selecione **Definir intervalo de sondagem**.  
  
5.  Na caixa **Intervalo de sondagem** , insira o número de segundos, de 10 a 28.800, a decorrer entre uma sondagem e outra do servidor mestre pelo servidor de destino.  
  
6.  Em **Destinatários**, siga um destes procedimentos:  
  
    1.  Clique em **Todos os servidores de destino** se todos os servidores de destino compartilharem o mesmo intervalo de sondagem.  
  
    2.  Clique em **Estes servidores de destino** se nem todos os servidores de destino compartilharem o mesmo intervalo de sondagem, e selecione cada servidor de destino que usará o intervalo de sondagem que está sendo definido.  
  
## <a name="TSQL"></a>Usando Transact-SQL  
**Para definir o intervalo de sondagem de servidores de destino**  
  
1.  No Pesquisador de Objetos, conecte-se a uma instância do Mecanismo de Banco de Dados e expanda-a.  
  
2.  Na barra de ferramentas, clique em **Nova Consulta**.  
  
3.  Na janela de consulta, use o procedimento armazenado de sistema [sp_post_msx_operation (Transact-SQL)](http://msdn.microsoft.com/en-us/085deef8-2709-4da9-bb97-9ab32effdacf) para definir o intervalo de sondagem para servidores de destino.  
  
## <a name="see-also"></a>Consulte Também  
[sysdownloadlist](http://msdn.microsoft.com/en-us/71087a4c-e829-488e-aa7d-a9476e2b4779)  
  
