---
title: Usando modos de lote e AddNew em imediata | Microsoft Docs
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AddNew method [ADO]
- ADO, editing data
- ADO, adding data
- editing data [ADO], AddNew method
ms.assetid: ed314bb9-e188-4658-a68c-a2abc49610be
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f22ae3e595c68b52e7eca449557e647c3bedae78
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="using-addnew-in-immediate-and-batch-modes"></a>Usando modos de lote e AddNew em imediata
O comportamento do **AddNew** método depende do modo de atualização do **Recordset** objeto e se você passa o *FieldList* e *valores*argumentos.  
  
 No modo de atualização imediata (no qual o provedor grava as alterações à fonte de dados subjacente quando você chamar o **atualizar** método), chamar o **AddNew** método sem conjuntos de argumentos de  **EditMode** propriedade **adEditAdd.** O provedor armazena em cache localmente as alterações de valor de campo. Chamando o **atualização** método posta o novo registro no banco de dados e redefine o **EditMode** propriedade **adEditNone.** Se você passar o *FieldList* e *valores* argumentos, o ADO envia imediatamente o novo registro no banco de dados (sem **atualização** chamada é necessária); o **EditMode**  não altera o valor da propriedade (**adEditNone**).  
  
 No modo de atualização em lotes, chamando o **AddNew** método sem conjuntos de argumentos de **EditMode** propriedade **adEditAdd**. O provedor armazena em cache localmente as alterações de valor de campo. Chamando o **atualização** método adiciona o novo registro para o atual **registros** e redefine o **EditMode** propriedade **adEditNone**, mas o provedor não postar as alterações no banco de dados subjacentes até que você chame o **UpdateBatch** método. Se você passar o *FieldList* e *valores* argumentos, ADO envia o novo registro para o provedor de armazenamento em cache; você precisa chamar o **UpdateBatch** método para lançar o novo Registre o banco de dados subjacente. Para obter mais informações sobre **atualização** e **UpdateBatch**, consulte [atualizando e persistir dados](../../../ado/guide/data/updating-and-persisting-data.md).
