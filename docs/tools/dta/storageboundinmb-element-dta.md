---
title: Elemento StorageBoundInMB (DTA) | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: dta
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: XML
helpviewer_keywords: StorageBoundInMB element
ms.assetid: a8374910-bf68-4edb-b464-53a3a705e7f4
caps.latest.revision: "12"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e0584999dc8e98243c00f4bbd174d1bfa8b14ba2
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="storageboundinmb-element-dta"></a>Elemento StorageBoundInMB (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Especifica o espaço máximo em megabytes que podem ser consumidos pela recomendação de ajuste do Orientador de otimização do mecanismo de banco de dados (índice e conjunto de particionamento).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <StorageBoundInMB>...</ StorageBoundInMB >  
```  
  
## <a name="element-characteristics"></a>Características do elemento  
  
|Característica|Descrição|  
|--------------------|-----------------|  
|**Comprimento e tipo de dados**|**unsignedInt**, comprimento ilimitado.|  
|**Valor padrão**|Nenhuma.|  
|**Ocorrência**|Opcional. Só pode ser usado uma vez para o elemento **TuningOptions** .|  
  
## <a name="element-relationships"></a>Relações do elemento  
  
|Relação|Elementos|  
|------------------|--------------|  
|**Elemento pai**|[Elemento TuningOptions &#40; DTA &#41;](../../tools/dta/tuningoptions-element-dta.md)|  
|**Elementos filho**|Nenhuma|  
  
## <a name="remarks"></a>Comentários  
 Quando múltiplos bancos de dados são ajustados, as recomendações para todos os bancos de dados são consideradas no cálculo do espaço. Por padrão, o Orientador de Otimização do Mecanismo de Banco de Dados assume o menor dos seguintes tamanhos de armazenamento:  
  
-   Três vezes o tamanho de dados brutos atuais, o que inclui o tamanho total de heaps e índices clusterizados em tabelas.  
  
-   Os espaços livres em todas as unidades de disco anexas mais o tamanho dos dados brutos.  
  
 O tamanho de armazenamento padrão não inclui índices não clusterizados e exibições indexadas.  
  
 Se o valor especificado para o elemento **StorageBoundInMB** exceder o espaço de disco atual, o Orientador de Otimização do Mecanismo de Banco de Dados retorna um erro, mas continua o ajuste. Depois que o ajuste estiver completo, você pode acrescentar espaço de disco caso decida implementar a recomendação.  
  
## <a name="example"></a>Exemplo  
  
## <a name="description"></a>Descrição  
 O seguinte exemplo de código mostra como definir um limite de 1500 megabytes como o espaço de disco de máximo que uma recomendação de ajuste pode consumir:  
  
## <a name="code"></a>Código  
  
```  
<DTAInput>  
  <Server>...</Server>  
  <Workload>...</Workload>  
  <TuningOptions>  
    <StorageBoundInMB>1500</StorageBoundInMB>  
...code removed here...  
</DTAInput>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Referência do arquivo de entrada XML &#40;Orientador de Otimização do Mecanismo de Banco de Dados&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
