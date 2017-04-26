---
title: "Extens&#245;es de processamento de dados e provedores de dados do .NET Framework (SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "relatórios [Reporting Services], dados"
  - "extensões de processamento de dados [Reporting Services]"
  - "provedores de dados [Reporting Services]"
  - "recuperação de dados [Reporting Services]"
  - "Reporting Services, fontes de dados"
  - "dados do relatório [Construtor de Relatórios], acessando"
ms.assetid: 42a5afb5-f4c8-4957-b1fd-77bf39afa5be
caps.latest.revision: 19
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 19
---
# Extens&#245;es de processamento de dados e provedores de dados do .NET Framework (SSRS)
  Uma extensão de processamento de dados [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] é um componente instalado com [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], projetado para recuperar dados de um tipo específico de fonte de dados e para fornecer funcionalidade adicional para oferecer suporte ao design de relatórios e processamento de relatórios. Um provedor de dados do [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] é um componente disponível do [!INCLUDE[msCoName](../../includes/msconame-md.md)] ou de fontes de terceiros que dá suporte às interfaces <xref:System.Data> que permitem que você recupere e modifique dados de um tipo específico de fonte de dados.  
  
## Entendendo uma extensão de processamento de dados  
 Uma extensão de processamento de dados do [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dá suporte a um subconjunto das interfaces <xref:System.Data>. As extensões de processamento de dados exigem apenas o acesso somente leitura a uma fonte de dados para que as interfaces para gravação e atualização não sejam implementadas. Cada extensão de processamento de dados pode fornecer recursos personalizados para dar suporte ao processamento de relatório. Por exemplo, uma extensão de processamento de dados pode oferecer suporte aos seguintes tipos de recursos:  
  
-   Gerenciamento de credenciais separadamente da cadeia de conexão  
  
-   Suportando parâmetros de vários valores  
  
-   Recuperação de agregações de servidor, que são calculadas na fonte de dados  
  
-   Recuperando propriedades de dados bem como valores de dados da fonte de dados  
  
## Entendendo um provedor de dados  
 Um provedor de dados do [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] (às vezes, conhecido como um driver) dá suporte a um conjunto padrão de interfaces <xref:System.Data> para ler, gravar e atualizar dados em uma fonte de dados. Um provedor de dados pode ser usado quando não houver nenhuma extensão de processamento de dados disponível para um tipo específico de fonte de dados. Muitos provedores de dados [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] padrão de terceiros estão disponíveis.  
  
 Uma vez que [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] tem uma arquitetura de provedor de dados extensível, você pode criar uma extensão de processamento de dados personalizada para incluir a funcionalidade extra fornecida pelas extensões de processamento de dados do [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Para obter mais informações, consulte [Implementing a Data Processing Extension](../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md). Para as extensões de processamento de dados de terceiros, consulte a documentação que acompanha a extensão de processamento de dados de terceiros.  
  
> [!NOTE]  
>  Um provedor de dados [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] ou uma extensão de processamento de dados personalizada deve ser instalada e registrada antes de ser usada para acessar dados de uma fonte de dados. A extensão de processamento de dados deve ser instalada e registrada tanto no cliente de relatório para criá-lo quanto no servidor de relatórios para exibir o relatório publicado. Nem todos os provedores de dados se destinam a funcionar em um ambiente de servidor. Para obter mais informações, consulte [Registrar um provedor de dados padrão do .NET Framework &#40;SSRS&#41;](../../reporting-services/report-data/register-a-standard-net-framework-data-provider-ssrs.md) e [Implantando uma extensão de processamento de dados](../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension.md).  
  
## Consulte também  
 [Visão geral das extensões de processamento de dados](../../reporting-services/extensions/data-processing/data-processing-extensions-overview.md)   
 [Conjuntos de dados inseridos e compartilhados de relatório &#40;Construtor de Relatórios e SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
  
  