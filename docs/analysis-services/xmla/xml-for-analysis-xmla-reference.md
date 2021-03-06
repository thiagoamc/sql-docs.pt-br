---
title: "XML for Analysis (XMLA) referência | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- XML for Analysis, reference
- XMLA, reference
ms.assetid: 88045e05-ce47-4e28-999b-7f9c74af9faf
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: a8f79164c48c388ca55fbd39b45aa572f01d0a1b
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2018
---
# <a name="xml-for-analysis--xmla-reference"></a>XML for Analysis (XMLA) referência
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)][!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] usa o protocolo XML for Analysis (XMLA) para lidar com todas as comunicações entre aplicativos cliente e uma instância do Analysis Services. No seu nível mais básico, outras bibliotecas de cliente como o ADOMD.NET e AMO constroem solicitações e decodificam respostas no XMLA, servindo como um intermediário a uma instância do Analysis Services, que usa XMLA exclusivamente.  
  
 Para dar suporte à descoberta e manipulação de dados nos formatos multidimensionais e tabulares, a especificação XMLA define dois métodos geralmente acessíveis, [Discover](../../analysis-services/xmla/xml-elements-methods-discover.md) e [Execute](../../analysis-services/xmla/xml-elements-methods-execute.md)e um coleção de tipos de dados e elementos XML. Uma vez que o XML permite uma arquitetura de cliente e servidor livremente acoplada, ambos os métodos controlam as informações de entrada e saída no formato XML. O Analysis Services é compatível com a especificação XMLA 1.1, especificação, mas também estende-o para incluir a capacidade de definição e manipulação de dados, implementada como anotações no **Discover** e **Execute** métodos. A sintaxe de XML estendida é chamada de ASSL (Analysis Services Scripting Language). O ASSL baseia-se na especificação de XMLA sem quebrá-la. A interoperabilidade baseada em XMLA é assegurada se você usar somente XMLA, ou XMLA e ASSL juntos.  
  
 Como programador, você poderá usar o XMLA como uma interface de programação se os requisitos de solução especificarem protocolos padrão, como XML, SOAP e HTTP. Os programadores e administradores também podem usar XMLA de maneira ad hoc para recuperar informações dos comandos de servidor ou execução.  
  
## <a name="in-this-section"></a>Nesta seção  
  
|Tópico|Description|  
|-----------|-----------------|  
|[Elementos XML &#40; XMLA &#41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)|Descreve elementos na especificação XMLA.|  
|[Tipos de dados XML &#40; XMLA &#41;](../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)|Descreve tipos de dados na especificação XMLA.|  
|[XML for Analysis conformidade &#40; XMLA &#41;](../../analysis-services/xmla/xml-for-analysis-compliance-xmla.md)|Descreve o nível de conformidade com a especificação do XMLA 1.1.|  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Desenvolvendo com ASSL &#40;linguagem de script do Analysis Services&#41;](../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)  
  
 [Conjunto de linhas de esquema do XML](../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
 [Desenvolvendo com ADOMD.NET](../../analysis-services/multidimensional-models/adomd-net/developing-with-adomd-net.md)  
  
 [Desenvolvendo com AMO &#40;Objetos de Gerenciamento de Análise&#41;](../../analysis-services/multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md)  
  
## <a name="see-also"></a>Consulte Também  
 [Noções básicas sobre a arquitetura do Microsoft OLAP](../../analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-architecture.md)  
  
  
