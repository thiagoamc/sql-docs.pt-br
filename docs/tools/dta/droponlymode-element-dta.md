---
title: "Elemento DropOnlyMode (DTA) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "XML"
helpviewer_keywords: 
  - "Elemento DropOnlyMode"
ms.assetid: 80960676-7581-4074-889b-80ee665963dd
caps.latest.revision: 14
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 14
---
# Elemento DropOnlyMode (DTA)
  Especifica que o Orientador de Otimização do Mecanismo de Banco de Dados deve apenas considerar descartar índices, exibições indexadas ou partições existentes durante a sessão de ajuste. Nenhuma nova estrutura de design físico é considerada quando esta opção de ajuste é especificada.  
  
## Sintaxe  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <DropOnlyMode>...</DropOnlyMode>  
```  
  
## Características do elemento  
 **Comprimento e tipo de dados**  
  
 **Valor padrão**  
  
 **Ocorrência**: opcional. Pode-se usar apenas uma vez para cada elemento **TuningOptions**. Não poderá ser usado se os elementos seguintes forem especificados no elemento de **TuningOptions** :  
  
-   [Elemento FeatureSet &#40;DTA&#41;](../../tools/dta/featureset-element-dta.md)  
  
-   [Elemento Partitioning &#40;DTA&#41;](../../tools/dta/partitioning-element-dta.md)  
  
-   O [Elemento KeepExisting &#40;DTA&#41;](../../tools/dta/keepexisting-element-dta.md) é definido como **ALL**  
  
## Relações do elemento  
 **Elemento pai**: [elemento TuningOptions &#40;DTA&#41;](../../tools/dta/tuningoptions-element-dta.md)  
  
 **Elementos filho**  
  
## Exemplo  
 O exemplo seguinte mostra a seção **TuningOptions** de um arquivo de entrada do Orientador de Otimização do Mecanismo de Banco de Dados XML onde o **DropOnlyMode** é especificado. Nesse exemplo a hora de ajuste é limitada a 24 horas (1440 minutos) e todos os índices clusterizados e não clusterizados existentes serão considerados para o descarte:  
  
```xml  
<TuningOptions  
  <TuningTimeInMin>1440</Name>  
  <KeepExisting>ALIGNED</KeepExisting>  
  <DropOnlyMode />  
</TuningOptions>  
```  
  
## Consulte também  
 [Referência do arquivo de entrada XML &#40;Orientador de Otimização do Mecanismo de Banco de Dados&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  