---
title: "Propriedades do gerenciador de bloqueio | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "propriedades do gerenciador de bloqueio [Analysis Services]"
  - "propriedade LockWaitGranularityMS"
  - "propriedade DefaultLockTimeoutMS"
  - "propriedade DeadlockDetectionGranularityMS"
ms.assetid: 15fe9ead-825b-4ac3-9191-7a07caa2861b
caps.latest.revision: 16
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 16
---
# Propriedades do gerenciador de bloqueio
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] oferece suporte às propriedades do servidor do gerenciador de bloqueio, listadas na tabela a seguir. Para obter mais informações sobre propriedades adicionais do servidor e como defini-las, consulte [Propriedades do servidor do Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md).  
  
 **Aplica-se a:** modo de servidor multidimensional e tabular  
  
## Propriedades  
 **DefaultLockTimeoutMS**  
 Uma propriedade de inteiro de 32 bits assinada que define o tempo limite de bloqueio padrão em milissegundos para solicitações de bloqueio internas.  
  
 O valor padrão para essa propriedade é -1, o que indica que não há nenhum tempo limite para solicitações de bloqueio interno.  
  
 **LockWaitGranularityMS**  
 Uma propriedade avançada que não deve ser alterada, exceto sob orientação do suporte da [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **DeadlockDetectionGranularityMS**  
 Uma propriedade avançada que não deve ser alterada, exceto sob orientação do suporte da [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## Consulte também  
 [Propriedades do servidor do Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
 [Determina o Modo de Servidor de uma instância do Analysis Services.](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  