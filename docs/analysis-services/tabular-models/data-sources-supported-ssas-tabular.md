---
title: "Fontes de dados com suporte (SSAS tabular) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d6c2b1b3-91fc-4175-af25-509946dc7f24
caps.latest.revision: 28
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 28
---
# Fontes de dados com suporte (SSAS tabular)
  Este tópico descreve os tipos de fonte de dados que podem ser usados com modelos tabulares.  
  
##  <a name="bkmk_supported_ds"></a> Fontes de dados com suporte para modelos na memória  
 Você pode importar dados das fontes de dados na tabela a seguir: Quando você instalar o [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], a instalação não instala os provedores listados para cada fonte de dados. Alguns deles podem já estar instalados com outros aplicativos no computador; em outros casos, você precisará baixar e instalar o provedor.  
  
|||||  
|-|-|-|-|  
|Origem|Versões|Tipo de arquivo|Provedores|  
|Bancos de dados do Access|Microsoft Access 2010 e posterior.|.accdb ou .mdb|Provedor OLE DB ACE 14|  
|Bancos de dados relacionais do SQL Server|Microsoft SQL Server 2008 e posterior, Microsoft Data Warehouse 2008 e posterior, Banco de Dados SQL do Microsoft Azure, Microsoft Analytics Platform System (APS)<br /><br /> <br /><br /> Observe que o APS (Analytics Platform System) era anteriormente conhecido como SQL PDW (Server Parallel Datawarehouse). Originalmente, conectar o PDW a partir do Analysis Services exigia um provedor de dados especial. Esse provedor foi substituído no SQL Server 2012. A partir do SQL Server 2012, o cliente nativo do SQL Server é usado para as conexões com o PDW/APS. Para saber mais sobre o APS, acesse o site [Microsoft Analytics Platform System](http://www.microsoft.com/en-us/server-cloud/products/analytics-platform-system/resources.aspx).|(não se aplica)|Provedor OLE DB para SQL Server<br /><br /> Provedor OLE DB do SQL Server Native Client<br /><br /> Provedor OLE DB do SQL Server Native 10.0 Client<br /><br /> Provedor de dados .NET Framework para SQL Client|  
|Bancos de dados relacionais da Oracle|Oracle 9i e posterior.|(não se aplica)|Provedor OLE DB Oracle<br /><br /> Provedor de Dados .NET Framework para Cliente Oracle<br /><br /> Provedor de dados do .NET Framework para SQL Server<br /><br /> OraOLEDB<br /><br /> MSDASQL|  
|Bancos de dados relacionais do Teradata|Teradata V2R6 e posterior|(não se aplica)|Provedor OLE DB TDOLEDB<br /><br /> Provedor de .NET Data para Teradata|  
|Bancos de dados relacionais do Informix||(não se aplica)|Provedor OLE DB para Informix|  
|Bancos de dados relacionais IBM DB2|8.1|(não se aplica)|DB2OLEDB|  
|Bancos de dados relacionais do Sybase Adaptive Server Enterprise (ASE)|15.0.2|(não se aplica)|Provedor OLE DB para Sybase|  
|Outros bancos de dados relacionais|(não se aplica)|(não se aplica)|Provedor OLE DB para driver ODBC|  
|Arquivos de texto|(não se aplica)|.txt, .tab, .csv|Provedor OLE DB ACE 14 para Microsoft Access|  
|Arquivos do Microsoft Excel|Excel 2010 e posterior|.xlsx, xlsm, .xlsb, .xltx, .xltm|Provedor OLE DB ACE 14|  
|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pasta de trabalho|Microsoft SQL Server 2008 Analysis Services e posterior|xlsx, xlsm, .xlsb, .xltx, .xltm|ASOLEDB 10.5<br /><br /> (usado apenas com pastas de trabalho do [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] publicadas em farms do SharePoint com o [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] instalado)|  
|Cubo do Analysis Services|Microsoft SQL Server 2008 Analysis Services e posterior|(não se aplica)|ASOLEDB 10|  
|Alimentações de dados<br /><br /> (usado para importar dados de relatórios do Reporting Services, documentos do serviço Atom, Microsoft Azure Marketplace DataMarket e feed de dados único)|Formato Atom 1.0<br /><br /> Qualquer banco de dados ou documento exposto como um Serviço de dados do WCF (Windows Communication Foundation) (antes ADO.NET Data Services).|.atomsvc para um documento de serviço que define uma ou mais alimentações<br /><br /> .atom para um documento de feed da Web do Atom|Provedor de Feed de Dados Microsoft para [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]<br /><br /> Provedor de dados do feed de dados do .NET Framework para [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]|  
|Arquivos de conexão de banco de dados do Office||.odc||  
  
  
##  <a name="bkmk_supported_ds_dq"></a> Fontes de dados com suporte para modelos DirectQuery  
 O DirectQuery é uma alternativa para o modo de armazenamento na memória, roteando consultas e retornando os resultados diretamente em sistemas de dados de back-end em vez de armazenar todos os dados dentro do modelo (e na RAM depois que o modelo é carregado). Como o Analysis Services tem que formular consultas na sintaxe da consulta de banco de dados nativo, um subconjunto menor de fontes de dados tem suporte para esse modo.  
  
Fonte de dados   |Versões  |Provedores
---------|---------|---------
Microsoft SQL Server    |  2008 e posterior      |       Provedor OLE DB para SQL Server, Provedor OLE DB para SQL Server Native Client, Provedor de Dados .NET Framework para SQL Client  
Banco de Dados SQL do Microsoft Azure    |   Todos      |  Provedor OLE DB para SQL Server, Provedor OLE DB para SQL Server Native Client, Provedor de Dados .NET Framework para SQL Client            
SQL Data Warehouse do Microsoft Azure     |   Todos     |  Provedor OLE DB para SQL Server Native Client, Provedor de Dados .NET Framework para SQL Client       
Microsoft SQL APS (Analytics Platform System)     |   Todos      |  Provedor OLE DB para SQL Server, Provedor OLE DB para SQL Server Native Client, Provedor de Dados .NET Framework para SQL Client       
Bancos de dados relacionais da Oracle     |  Oracle 9i e posterior       |  Provedor OLE DB Oracle       
Bancos de dados relacionais do Teradata    |  Teradata V2R6 e posterior     | Provedor de .NET Data para Teradata    

  
##  <a name="bkmk_tips"></a> Dicas para escolher fontes de dados  
  
A importação de tabelas de bancos de dados relacionais elimina etapas pois são usadas relações de *chave estrangeira* durante a importação para criar relações entre as tabelas no designer de modelos.  
  
Você também pode eliminar etapas com a importação de várias tabelas e a exclusão das tabelas desnecessárias. Se você importar uma tabela de cada vez, talvez ainda precise criar relações manualmente entre tabelas.  
  
Colunas que contêm dados semelhantes em fontes de dados diferentes são a base para criar relações dentro do designer de modelos. Ao usar fontes de dados heterogêneos, escolha tabelas com colunas que possam ser mapeadas para tabelas em outras fontes de dados que contêm dados idênticos ou semelhantes.  
  
Os provedores OLE DB às vezes podem oferecer desempenho mais rápido para dados em grande escala. Ao escolher entre diferentes provedores para a mesma fonte de dados, experimente primeiro o provedor OLE DB.  
  
## Consulte também  
 [Fontes de dados &#40;SSAS de Tabela&#41;](../../analysis-services/tabular-models/data-sources-ssas-tabular.md)   
 [Importar dados &#40;SSAS de Tabela&#41;](../Topic/Import%20Data%20\(SSAS%20Tabular\).md)  
  
  