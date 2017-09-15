---
title: Elemento Subscribe (XMLA) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Subscribe Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Subscribe
- microsoft.xml.analysis.subscribe
- http://schemas.microsoft.com/analysisservices/2003/engine#Subscribe
helpviewer_keywords:
- Subscribe command
ms.assetid: aad50dd7-44d4-4d83-a973-187f9aed35ec
caps.latest.revision: 14
author: jeannt
ms.author: jeannt
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d0af4762aec4d048f19ee47f8d07445aa5e7a8b3
ms.contentlocale: pt-br
ms.lasthandoff: 09/01/2017

---
# <a name="subscribe-element-xmla"></a>Elemento Subscribe (XMLA)
  Assina um rastreamento e retorna um conjunto de linhas que contém os eventos de rastreamento de um [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instância.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
  
<Command>  
   <Subscribe>  
      <Object>...</Object>  
   </Subscribe>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Características do elemento  
  
|Característica|Descrição|  
|--------------------|-----------------|  
|Comprimento e tipo de dados|Nenhuma|  
|Valor padrão|Nenhuma|  
|Cardinalidade|0-n: Elemento opcional que pode ocorrer mais de uma vez.|  
  
## <a name="element-relationships"></a>Relações do elemento  
  
|Relação|Elemento|  
|------------------|-------------|  
|Elementos pai|[Comando](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Elementos filho|[Objeto](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)|  
  
## <a name="remarks"></a>Comentários  
 O **assinar** comando assina e devolve um conjunto de linhas de um rastreamento especificado em um [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instância. Se um objeto que não seja um rastreamento for especificado no elemento **Object** , ocorrerá um erro.  
  
 Se o **objeto** elemento não for especificado, um rastreamento de sessão é definido e assinado na [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instância. O rastreamento de sessão retorna um conjunto fixo de eventos de rastreamento da sessão atual.  
  
 O fluxo do conjunto de linhas retornado por este comando será finalizado se o aplicativo cliente fecha a conexão para o [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instância, ou se a sessão na qual o **assinar** comando é executado é encerrada.  
  
## <a name="see-also"></a>Consulte também  
 [Comandos &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  