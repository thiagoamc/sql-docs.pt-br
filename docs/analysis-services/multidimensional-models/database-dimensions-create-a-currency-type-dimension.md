---
title: "Criar uma dimensão de tipo de moeda | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dimensions [Analysis Services], currency
- currency [Analysis Services]
- converting currency
- currency dimensions [Analysis Services]
ms.assetid: b1f037d1-ce47-4e47-a1c2-5ec9e781cff6
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 2cb2fb0b8fc1785eb0e58a5ea0d609a6d3c1bd0c
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2018
---
# <a name="database-dimensions---create-a-currency-type-dimension"></a>Dimensões de banco de dados - criar uma dimensão de tipo de moeda
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
No [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], uma dimensão de tipo de moeda é aquela cujos atributos representam uma lista de moedas para uso em relatórios financeiros.  
  
 Uma dimensão de moeda permite a inclusão de recursos de conversão de moeda em um cubo do [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Para adicionar a conversão de moeda a um cubo, use o Assistente de Business Intelligence para definir um comando de script MDX que converte medidas monetárias nos valores apropriados para a localidade do aplicativo cliente. Para criar esse script MDX, o Assistente de Business Intelligence precisa das seguintes informações:  
  
-   Uma dimensão de moeda que representa as moedas de origem. (Essa dimensão é a dimensão de moeda de origem.)  
  
-   Um grupo de medidas que representa as taxas de câmbio que serão usadas.  
  
 Com essas informações, o Assistente de Business Intelligence criará o processo de conversão de moedas que identificará a dimensão da moeda de destino apropriada (a dimensão de moeda que representa as moedas de destino). Dependendo do número de conversões de moeda que a solução de business intelligence precisar, o Assistente de Business Intelligence pode definir várias dimensões de moeda de destino. Para obter mais informações sobre como definir conversões de moeda, consulte [Conversões de moeda &#40;Analysis Services&#41;](../../analysis-services/currency-conversions-analysis-services.md).  
  
 Para identificar uma dimensão como dimensão de moeda, defina a propriedade **Type** da dimensão como **Currency**.  
  
## <a name="dimension-structure"></a>Estrutura da Dimensão  
 Uma dimensão de moeda contém, no mínimo, um atributo de chave que identifica cada moeda da tabela de dimensões da dimensão de moeda. O valor do atributo de chave é diferente nas dimensões de moeda de origem e destino:  
  
-   Para identificar um atributo como atributo de chave de uma dimensão de moeda de origem, defina a propriedade **Type** do atributo como **CurrencySource**.  
  
-   Para identificar um atributo como dimensão da moeda de destino, defina a propriedade **Type** do atributo como **CurrencyDestination**.  
  
 Para geração de relatório, tanto a dimensão de moeda de origem como a de destino podem conter, opcionalmente, os seguintes atributos:  
  
-   Um atributo de nome da moeda.  
  
     Para identificar um atributo como nome da moeda, defina a propriedade **Type** do atributo como **CurrencyName**.  
  
-   Um atributo de origem da moeda.  
  
     Para identificar um atributo como atributo de origem da moeda, defina a propriedade **Type** do atributo como **CurrencySource**.  
  
-   Um código de moeda da Organização de Padronização Internacional (ISO).  
  
     Para identificar um atributo como atributo de código ISO da moeda, defina a propriedade **Type** do atributo como **CurrencyIsoCode**.  
  
 Para obter mais informações sobre tipos de atributos, consulte [Configurar tipos de atributo](../../analysis-services/multidimensional-models/attribute-properties-configure-attribute-types.md).  
  
## <a name="defining-account-intelligence-with-the-business-intelligence-wizard"></a>Definindo inteligência de conta com o Assistente de Business Intelligence  
 Depois de configurar a dimensão de conta e adicioná-la a um cubo, você pode usar o Assistente de Business Intelligence para adicionar à dimensão funcionalidades de inteligência de conta, como identificação e mapeamento de tipos de conta. Para obter mais informações, consulte [Adicionar inteligência de conta a uma dimensão](../../analysis-services/multidimensional-models/bi-wizard-add-account-intelligence-to-a-dimension.md).  
  
## <a name="see-also"></a>Consulte também  
 [Atributos e hierarquias de atributo](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Ajuda de F1 do Assistente do Business Intelligence](http://msdn.microsoft.com/library/155ac80c-63ae-47aa-9e86-9396e3d920eb)   
 [Tipos de dimensão](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md)  
  
  
