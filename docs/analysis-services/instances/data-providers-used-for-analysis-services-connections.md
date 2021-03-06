---
title: "Provedores de dados usados para conexões do Analysis Services | Microsoft Docs"
ms.custom: 
ms.date: 01/23/2018
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 128f6dde-409d-4c12-9820-3305bab57b75
caps.latest.revision: "19"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 816919b48f77a4462e8d0f0f04d0bb621a2d2058
ms.sourcegitcommit: 3206a31870f8febab7d1718fa59fe0590d4d45db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2018
---
# <a name="client-libraries-data-providers-used-for-analysis-services-connections"></a>Bibliotecas de cliente (provedores de dados) usadas para conexões do Analysis Services
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

O Analysis Services fornece três bibliotecas de cliente, também conhecido como **provedores de dados**, para acesso a dados de ferramentas e aplicativos cliente e servidor. Ferramentas como o SSMS SSDT e aplicativos que o Power BI Desktop e Excel se conectar ao Analysis Services usando essas bibliotecas. Duas das bibliotecas de cliente ADOMD.NET e o Analysis Services Management Objects (AMO) são bibliotecas de cliente gerenciado. O provedor OLE DB do Analysis Services (MSOLAP DLL) é uma biblioteca do native client. Bibliotecas de cliente são os mesmos para o SQL Server Analysis Services e o Azure Analysis Services.
  
##  <a name="bkmk_downloadsite"></a>Onde obter versões mais recentes  
 A versão instalada em um computador cliente deve corresponder à versão principal do servidor que fornece os dados. Se a instalação do servidor for mais recente do que a instalação dos provedores de dados existentes nas estações de trabalho da sua rede, talvez você precise instalar bibliotecas mais recentes.  

Bibliotecas de cliente incluídas em pacotes de recursos do SQL Server anteriores correspondem a essa versão do SQL; No entanto, eles não podem ter a versão mais recente. Conectar-se ao Azure Analysis Services pode exigir versões posteriores. Todas as versões são compatíveis com versões anteriores.

Para obter a versão mais recente, consulte [bibliotecas de cliente para se conectar ao Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-data-providers). 
  
## <a name="see-also"></a>Consulte também  
 [Conectar ao Analysis Services](../../analysis-services/instances/connect-to-analysis-services.md)  
  
  
