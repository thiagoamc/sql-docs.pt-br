---
title: "Tipos de dados de integração de CLR e agrupamento | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- data types [CLR integration]
- parameter collation [CLR integration]
- collations [CLR integration]
ms.assetid: 6ebaed8e-2e2b-4f6d-bf4b-bc25452de441
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ab94a6397d8b070af754fa5fd8dd47f9bd553630
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="collation-and-clr-integration-data-types"></a>Tipos de dados de integração CLR e agrupamento
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
No [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], o **CompareInfo** agrupamentos alças do objeto. O [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] aplicativo usar interfaces de programação (APIs) da cadeia de caracteres de **CompareInfo** propriedade associada a **CultureInfo** objeto do thread atual para executar comparações de cadeia de caracteres. A configuração padrão da **CultureInfo** objeto se baseia o [!INCLUDE[msCoName](../../includes/msconame-md.md)] configuração de localidade do Windows para o computador no qual [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] está em execução. Isso determina a semântica de comparação padrão, se não explícita **CultureInfo** for especificado, para comparações de **System. String** valores. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]não altera explicitamente o **CompareInfo** propriedade para o agrupamento de banco de dados ou servidor. Se necessário, os usuários devem definir apropriada **CompareInfo** propriedade em suas rotinas.  
  
## <a name="parameter-collation"></a>Agrupamento de parâmetros  
 Quando você criar uma rotina do common language runtime (CLR) e um parâmetro de um método CLR associado à rotina é do tipo **SQLString**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cria uma instância do parâmetro com o agrupamento padrão do banco de dados que contém a rotina de chamada. Se um parâmetro não é um **SqlType** (por exemplo, **cadeia de caracteres** em vez de **SQLString**), as informações de agrupamento do banco de dados não estão associadas com o parâmetro.  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de dados do SQL Server no .NET Framework](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
