---
title: "Vidas úteis de transação | Microsoft Docs"
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
- lifetimes [SQL Server]
- Transact-SQL vs. managed code
ms.assetid: cb076fda-6488-4959-a6a4-7adaccf3f25c
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f24c0e6642a01b5f1d59ae82c7c09ce9ed94e7fb
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="transaction-lifetimes"></a>Vidas úteis de transação
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Há uma diferença importante entre as transações iniciadas nos procedimentos armazenados [!INCLUDE[tsql](../../includes/tsql-md.md)] e aquelas iniciadas no código gerenciado: o código CLR (common language runtime) não pode desequilibrar o estado da transação na entrada ou saída de uma invocação CLR. Esteja ciente das seguintes implicações dessa diferença:  
  
-   Uma transação iniciada em um quadro CLR precisa ser confirmada ou revertida ou o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gerará um erro quando o quadro for fechado.  
  
-   Uma transação externa não pode ser confirmada ou revertida no código CLR.  
  
-   Uma tentativa de confirmar uma transação não iniciada no mesmo procedimento causa um erro em tempo de execução.  
  
-   Uma tentativa de reverter uma transação não iniciada no mesmo procedimento causa a paralisação da transação (impedindo a ocorrência de qualquer outra operação como efeito colateral). A transação é descontinuada até que o código CLR saia do escopo. Observe que isso pode ser útil quando você detecta um erro em seu procedimento e deseja verificar se a transação inteira é finalizada.  
  
## <a name="see-also"></a>Consulte também  
 [Integração CLR e transações](../../relational-databases/clr-integration-data-access-transactions/clr-integration-and-transactions.md)  
  
  
