---
title: Novidades no SQL Server vNext | Microsoft Docs
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-vnext
ms.reviewer: 
ms.suite: 
ms.technology:
- server-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b57f375-9242-4bb2-9d4b-c560d5a93524
caps.latest.revision: 71
author: craigg-msft
ms.author: craigg
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f4a9065cccb31a8ee71e142aeba054addd6c4a5d
ms.lasthandoff: 04/11/2017

---
# <a name="what39s-new-in-sql-server-vnext"></a>Novidades no SQL Server vNext
O SQL Server vNext representa um passo importante para a transformação do SQL Server em uma plataforma que fornece opções de linguagens de desenvolvimento, tipos de dados, local e na nuvem e entre sistemas operacionais, levando a potência do SQL Server para o Linux, contêineres do Docker baseados em Linux e Windows.

Este tópico é um resumo das novidades da versão mais recente do CTP (Community Technical Preview) e fornece links para informações mais detalhadas sobre as novidades em áreas de recurso específicas.

![info_tip](../sql-server/media/info-tip.png) Execute o SQL Server no Linux! Para obter mais informações, consulte:
-  [Novidades do SQL Server vNext no Linux](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-whats-new)
-  [Documentação de SQL Server no Linux](https://docs.microsoft.com/en-us/sql/linux/)


**Experimente:**    
   -   [![Download from Evaluation Center](../analysis-services/media/download.png)](http://go.microsoft.com/fwlink/?LinkID=829477) **[Download the SQL Server vNext Community Technology Preview](http://go.microsoft.com/fwlink/?LinkID=829477)**

## <a name="whats-new-in-sql-server-vnext-ctp-14-march-2017"></a>Novidades do SQL Server vNext CTP 1.4 (março de 2017)
### <a name="sql-server-database-engine"></a>Mecanismo de Banco de Dados do SQL Server
- Não há nenhum recurso novo do Mecanismo de Banco de Dados neste CTP.
- Este CTP contém correções de bugs para o Mecanismo do Banco de Dados.
- Para obter uma lista detalhada das melhorias do vNext CTP em versões anteriores do CTP, veja [Novidades do SQL Server vNext (Mecanismo de Banco de Dados)](../database-engine/configure-windows/what-s-new-in-sql-server-vnext-database-engine.md).

### <a name="sql-server-r-services"></a>SQL Server R Services
- Não há recursos novos do R Services neste CTP.
- Para obter informações mais detalhadas sobre as novidades do R Services, incluindo detalhes de CTPs anteriores, consulte [Novidades do SQL Server R Services](../advanced-analytics/r-services/what-s-new-in-sql-server-r-services.md).  

### <a name="sql-server-reporting-services-ssrs"></a>SQL Server Reporting Services (SSRS)
- Não há novos recursos do SSRS neste CTP.
- Para obter informações mais detalhadas sobre as novidades do SSRS, incluindo detalhes de versões anteriores, veja [Novidades do Reporting Services](../reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md). 

### <a name="sql-server-analysis-services-ssas"></a>SSAS (SQL Server Analysis Services)
- Não há recursos novos do SSAS neste CTP.  
- Para obter mais detalhes, incluindo novidades para o Analysis Services nas visualizações mais recentes do SSDT e SSMS, consulte [Novidades novo no Analysis Services vNext](../analysis-services/what-s-new-in-sql-server-analysis-services-vnext.md).  

### <a name="sql-server-integration-services-ssis"></a>SQL Server Integration Services (SSIS)
- Não há recursos novos do SSIS neste CTP.
- Para obter informações mais detalhadas sobre as novidades do SSIS, incluindo detalhes de CTPs anteriores, consulte [Novidades do Integration Services vNext](../integration-services/what-s-new-in-integration-services-in-sql-server-vnext.md).  

### <a name="master-data-services-mds"></a>Master Data Services (MDS)
- Não há recursos novos do Master Data Services neste CTP.

![horizontal_bar](../sql-server/media/horizontal-bar.png)

## <a name="whats-new-in-sql-server-vnext-ctp-13-february-2017"></a>Novidades do SQL Server vNext CTP 1.3 (fevereiro de 2017)
### <a name="sql-server-database-engine"></a>Mecanismo de Banco de Dados do SQL Server
- Melhorias indiretas de desempenho do ponto de verificação.
- Suporte a grupos de disponibilidade sem cluster adicionado.
- Configuração de Grupos de Disponibilidade de Confirmação de Réplica Mínima adicionada.
- Os Grupos de Disponibilidade agora podem trabalhar no Windows-Linux para permitir as migrações e testes entre sistemas operacionais.
- Suporte à Política de Retenção de Tabelas Temporais adicionado,
- Novo DMV SYS.DM_DB_STATS_HISTOGRAM
- Suporte à criação e recriação de índice de columnstore não clusterizado online adicionado
- Cinco novas exibições de gerenciamento dinâmico para retornar informações sobre o processo do Linux. Para saber mais, veja [Exibições de Gerenciamento Dinâmico de Processos do Linux](../relational-databases/system-dynamic-management-views/linux-process-dynamic-management-views-transact-sql.md).   
- [sys.dm_db_stats_histogram (Transact-SQL)](../relational-databases/system-dynamic-management-views/sys-dm-db-stats-histogram-transact-sql.md) é adicionado para análise de estatísticas.

### <a name="sql-server-analysis-services-ssas-ctp-13"></a>SQL Server Analysis Services (SSAS) (CTP 1.3)
- Dicas de codificação - um recurso avançado usado para otimizar o processamento (atualização de dados) de grandes modelos de tabela na memória. Para saber mais, veja [Novidades no SQL Server Analysis Services vNext](../analysis-services/what-s-new-in-sql-server-analysis-services-vnext.md). 


![horizontal_bar](../sql-server/media/horizontal-bar.png)

##  <a name="infotipsql-servermediainfo-tippng-engage-with-the-sql-server-engineering-team"></a>![info_tip](../sql-server/media/info-tip.png) Entre em contato com a equipe de engenharia do SQL Server 
- [Stack Overflow (marcação sql-server)](http://stackoverflow.com/questions/tagged/sql-server)
- [Fóruns do MSDN](https://social.msdn.microsoft.com/Forums/en-US/home?category=sqlserver)
- [Microsoft Connect – relatar bugs e solicitar recursos](https://connect.microsoft.com/SQLServer/Feedback)
- [Reddit – discussão geral sobre R](https://www.reddit.com/r/SQLServer/)

## <a name="see-also"></a>Consulte também    
 + [![Notas de versão](../analysis-services/instances/install-windows/media/ssrs-fyi-note.png)] [Notas de versão do SQL Server VNext](../sql-server/sql-server-vnext-release-notes.md). 
+ [Recursos com suporte por Edição](https://msdn.microsoft.com/library/cc645993.aspx)
 + [Requisitos de instalação de hardware e software](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)
 + [Assistente de Instalação](../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)
 
 + [Configuração e instalação de manutenção](http://msdn.microsoft.com/library/6df72a78-6b36-4bc1-948e-04b4ebe46094)
 
 ![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png)


