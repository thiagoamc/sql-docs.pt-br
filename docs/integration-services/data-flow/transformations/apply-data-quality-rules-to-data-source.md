---
title: "Aplicar regras de qualidade de dados &#224; fonte de dados | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a965e8f2-004d-4ccc-8523-a185b35b26e2
caps.latest.revision: 8
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 8
---
# Aplicar regras de qualidade de dados &#224; fonte de dados
  Você pode usar o DQS (Data Quality Services) para corrigir dados no fluxo de dados de pacote conectando a transformação de limpeza DQS à fonte de dados. Para obter mais informações sobre DQS, consulte [Data Quality Services Concepts](../../../data-quality-services/data-quality-services-concepts.md). Para obter mais informações sobre a transformação, consulte [DQS Cleansing Transformation](../../../integration-services/data-flow/transformations/dqs-cleansing-transformation.md).  
  
 Quando você processar dados com a transformação de limpeza DQS, um projeto de qualidade de dados é criado no Data Quality Server. Você usa o Cliente Data Quality para gerenciar o projeto. Para obter mais informações, consulte [Abrir, desbloquear, renomear e excluir um projeto de qualidade de dados](https://msdn.microsoft.com/library/hh510417.aspx).  
  
### Para corrigir dados no fluxo de dados  
  
1.  Criar um pacote.  
  
2.  Adicione e configure a transformação Limpeza DQS. Para obter mais informações, consulte [DQS Cleansing Transformation Editor Dialog Box](../../../integration-services/data-flow/transformations/dqs-cleansing-transformation-editor-dialog-box.md).  
  
3.  Conecte a transformação Limpeza DQS a uma fonte de dados.  
  
  