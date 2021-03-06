---
title: ADORecordConstruction Interface | Microsoft Docs
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
apitype: COM
f1_keywords:
- ADORecordConstruction
helpviewer_keywords:
- ADORecordConstruction interface [ADO]
ms.assetid: 52a5429e-5829-455e-be3b-31f05cbecf2d
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7bfe02588a73f6c896b8947298483766c6a8a01e
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="adorecordconstruction-interface"></a>ADORecordConstruction Interface
O **ADORecordConstruction**interface é usada para construir um ADO **registro** objeto a partir de um banco de dados OLE **linha** objeto em um aplicativo C/C++.  
  
 Esta interface suporta as seguintes propriedades:  
  
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|[ParentRow](../../../ado/reference/ado-api/parentrow-property-ado.md)|Somente gravação.<br />Define o contêiner do OLE DB **linha** objeto este ADO **registro** objeto.|  
|[Linha](../../../ado/reference/ado-api/row-property-ado.md)|Leitura/gravação.<br />Obtém/define um banco de dados OLE **linha** objeto de/esse ADO **registro** objeto.|  
  
## <a name="methods"></a>Métodos  
 Nenhuma.  
  
## <a name="events"></a>Eventos  
 Nenhuma.  
  
## <a name="remarks"></a>Remarks  
 Dado um OLE DB **linha** objeto (`pRow`), a construção de ADO **registro** objeto (`adoR`), valores para as três operações básicas a seguir:  
  
1.  Criar um ADO **registro** objeto:  
  
    ```  
    _RecordPtr adoR;  
    adoRs.CreateInstance(__uuidof(_Record));  
    ```  
  
2.  Consulta o **IADORecordConstruction** interface no **registro** objeto:  
  
    ```  
    adoRecordConstructionPtr adoRConstruct=NULL;  
    adoR->QueryInterface(__uuidof(ADORecordConstruction),  
                        (void**)&adoRConstruct);  
    ```  
  
3.  Chamar o **IADORecordConstruction::put_Row** método de propriedade para definir o OLE DB **linha** objeto ADO **registro** objeto:  
  
    ```  
    IUnknown *pUnk=NULL;  
    pRow->QueryInterface(IID_IUnknown, (void**)&pUnk);  
    adoRConstruct->put_Row(pUnk);  
    ```  
  
 O RSoP **objeto adoR** objeto agora representa o ADO **registro** objeto construído a partir do OLE DB **linha** objeto.  
  
 ADO **registro** objeto também pode ser construído do contêiner do OLE DB **linha** objeto.  
  
## <a name="requirements"></a>Requisitos  
 **Versão:** ADO 2.0 e posterior  
  
 **Library:** msado15.dll  
  
 **UUID:** 00000567-0000-0010-8000-00AA006D2EA4
