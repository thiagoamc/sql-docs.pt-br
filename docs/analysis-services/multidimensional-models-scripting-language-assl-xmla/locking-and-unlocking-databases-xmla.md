---
title: Bloqueando e desbloqueando bancos de dados (XMLA) | Microsoft Docs
ms.custom: 
ms.date: 02/14/2018
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- locking [XML for Analysis]
- XML for Analysis, locking
- XMLA, locking
- unlocking objects
ms.assetid: 451afa58-ce03-4ecc-8dd3-9e7e8559b5f1
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 05a2627f13306e59a6369e2bafa206f82977c186
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2018
---
# <a name="locking-and-unlocking-databases-xmla"></a>Bloqueando e desbloqueando bancos de dados (XMLA)
  Você pode bloquear e desbloquear bancos de dados usando, respectivamente, o [bloqueio](../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md) e [Unlock](../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md) comandos em XML for Analysis (XMLA). Normalmente, outros comandos do XMLA bloqueiam e desbloqueiam objetos automaticamente quando necessário para concluir o comando durante a execução. Explicitamente, você pode bloquear ou desbloquear um banco de dados para executar vários comandos em uma única transação, como um [lote](../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md) comando, enquanto impede que outros aplicativos confirmem uma transação de gravação no banco de dados.  
  
## <a name="locking-databases"></a>Bloqueando bancos de dados  
 O **bloqueio** comando bloqueia um objeto, para uso compartilhado ou exclusivo dentro do contexto da transação ativa no momento. Um bloqueio em um objeto impede a confirmação de transações até que o bloqueio seja removido. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] oferece suporte a dois tipos de bloqueios, bloqueios compartilhados e bloqueios exclusivos. Para obter mais informações sobre os tipos de bloqueio suportados pelo [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], consulte [elemento Mode &#40; XMLA &#41; ](../../analysis-services/xmla/xml-elements-properties/mode-element-xmla.md).  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] permite que somente bancos de dados a ser bloqueada. O [objeto](../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md) elemento deve conter uma referência de objeto para um [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] banco de dados. Se o **objeto** elemento não for especificado ou se o **objeto** elemento se refere a um objeto diferente de um banco de dados, ocorrerá um erro.  
  
> [!IMPORTANT]  
>  Apenas administradores de banco de dados ou servidor podem emitir explicitamente um **bloqueio** comando.  
  
 Outros comandos implicitamente problema um **bloqueio** comando um [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] banco de dados. Qualquer operação que leia dados ou metadados de um banco de dados, como qualquer [Discover](../../analysis-services/xmla/xml-elements-methods-discover.md) método ou um [Execute](../../analysis-services/xmla/xml-elements-methods-execute.md) método executando um [instrução](../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md) command, emite implicitamente um compartilhado bloqueio no banco de dados. Qualquer transação que confirme alterações em dados ou metadados para um objeto em um [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] banco de dados, como um **Execute** método executando um [Alter](../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md) command, emite implicitamente um bloqueio exclusivo no banco de dados.  
  
## <a name="unlocking-objects"></a>Desbloqueando objetos  
 O comando **Unlock** remove um bloqueio estabelecido dentro do contexto da transação ativa no momento.  
  
> [!IMPORTANT]  
>  Apenas administradores de banco de dados ou de servidor podem emitir um comando **Unlock** explicitamente.  
  
 Todos os bloqueios são mantidos no contexto da transação atual. Quando a transação atual é confirmada ou revertida, todos os bloqueios definidos dentro da transação são liberados automaticamente.  
  
## <a name="see-also"></a>Consulte também  
 [Elemento lock &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md)   
 [Desbloquear elemento &#40; XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md)   
 [Desenvolvendo com XMLA no Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
