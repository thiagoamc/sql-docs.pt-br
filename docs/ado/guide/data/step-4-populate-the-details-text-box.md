---
title: 'Etapa 4: Preencher a caixa de texto de detalhes | Microsoft Docs'
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
ms.assetid: cb4273e2-c907-4a86-a621-3bf110088228
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 78f0c3e899400e1bf56a9b00ce1521a23b638189
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="step-4-populate-the-details-text-box"></a>Etapa 4: Preencher a caixa de texto de detalhes
Para preencher a caixa de texto de detalhes, criar uma nova sub-rotina denominada **recFields** e insira o código a seguir:  
  
```  
Sub recFields(r As Record, l As ListBox, t As TextBox)  
    Dim f As Field  
    Dim s As Stream  
    Set s = New Stream  
    Dim str As String  
  
    For Each f In r.Fields  
        l.AddItem f.Name & ": " & f.Value  
    Next  
    t.Text = ""  
    If r!RESOURCE_CONTENTCLASS = "text/plain" Then  
        s.Open r, adModeRead, adOpenStreamFromRecord  
        str = s.ReadText(1)  
        s.Position = 0  
        If Asc(Mid(str, 1, 1)) = 63 Then '//63 = "?"  
            s.Charset = "ascii"  
            s.Type = adTypeText  
        End If  
        t.Text = s.ReadText(adReadAll)  
    End If  
End Sub  
```  
  
 Esse código preenche `lstDetails` com os campos e valores do registro simple passado para `recFields`. Se o recurso é um arquivo de texto, um fluxo de texto é aberto do registro de recurso. O código determina se o conjunto de caracteres é ASCII e copia o conteúdo de fluxo em `txtDetails`.  
  
## <a name="see-also"></a>Consulte também  
 [Cenário de publicação na Internet](../../../ado/guide/data/internet-publishing-scenario.md)   
 [Etapa 3: Preencher a caixa de listagem de campos](../../../ado/guide/data/step-3-populate-the-fields-list-box.md)
