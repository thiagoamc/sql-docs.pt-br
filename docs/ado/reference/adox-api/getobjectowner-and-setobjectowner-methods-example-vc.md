---
title: "Exemplo de métodos de SetObjectOwner (VC + +) e GetObjectOwner | Microsoft Docs"
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
dev_langs:
- C++
helpviewer_keywords:
- SetObjectOwner method [ADOX], VC++ example
- GetObjectOwner method [ADOX], VC++ example
ms.assetid: f5f2aa4b-d790-458f-9e70-1643e3e203b2
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ee1b891dd12810e8a54ebb8532a366789f28c957
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="getobjectowner-and-setobjectowner-methods-example-vc"></a>GetObjectOwner e exemplo dos métodos SetObjectOwner (VC + +)
Este exemplo demonstra o [GetObjectOwner](../../../ado/reference/adox-api/getobjectowner-method-adox.md) e [SetObjectOwner](../../../ado/reference/adox-api/setobjectowner-method.md) métodos. Esse código supõe a existência do grupo de estatísticas (consulte o [grupos e usuários, ChangePassword métodos exemplo Append (VC + +)](../../../ado/reference/adox-api/groups-and-users-append-changepassword-methods-example-vc.md) para ver como adicionar esse grupo para o sistema). O proprietário da tabela de categorias é definido para contabilidade.  
  
```  
// BeginOwnersCpp.cpp  
// compile with: /EHsc  
#import "msadox.dll" no_namespace  
  
#include "iostream"  
using namespace std;  
  
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);};  
  
int main() {  
   if ( FAILED(::CoInitialize(NULL)) )  
      return -1;  
  
   HRESULT hr = S_OK;  
  
   // Define and initialize ADOX object pointers. These are in the ADODB namespace.  
   _TablePtr m_pTable = NULL;  
   _CatalogPtr m_pCatalog = NULL;  
  
   try {  
      TESTHR(hr = m_pCatalog.CreateInstance(__uuidof(Catalog)));  
      TESTHR(hr = m_pTable.CreateInstance(__uuidof(Table)));  
  
      // Open the Catalog.  
      m_pCatalog->PutActiveConnection("Provider='Microsoft.JET.OLEDB.4.0';data source='c:\\Northwind.mdb';jet oledb:system database='c:\\system.mdw'");  
  
      // Print the original owner of Categories  
      _bstr_t strOwner = m_pCatalog->GetObjectOwner("Categories", adPermObjTable);  
      cout << "Owner of Categories: " << strOwner << "\n" << endl;  
  
      //Create and append new group with a string.  
      m_pCatalog->Groups->Append("Accounting");  
  
      //Set the owner of Categories to Accounting.  
      m_pCatalog->SetObjectOwner("Categories", adPermObjTable, "Accounting");  
  
      _variant_t vIndex;  
      // List the owners of all tables and columns in the catalog.  
      for ( long iIndex = 0 ; iIndex < m_pCatalog->Tables->Count ; iIndex++ ) {  
         vIndex = iIndex;  
         m_pTable = m_pCatalog->Tables->GetItem(vIndex);  
         cout << "Table: " << m_pTable->Name << endl;  
         cout << "   Owner: " << m_pCatalog->GetObjectOwner(m_pTable->Name, adPermObjTable) << endl;  
      }  
  
      // Restore the original owner of Categories  
      m_pCatalog->SetObjectOwner("Categories", adPermObjTable, strOwner);  
  
      // Delete Accounting  
      m_pCatalog->Groups->Delete("Accounting");  
   }  
   catch(_com_error &e) {  
      // Notify the user of errors if any.  
      _bstr_t bstrSource(e.Source());  
      _bstr_t bstrDescription(e.Description());  
  
      printf("\n\tSource :  %s \n\tdescription : %s \n ", (LPCSTR)bstrSource, (LPCSTR)bstrDescription);  
   }  
  
   catch(...) {  
      cout << "Error occured in include files...." << endl;  
   }  
   ::CoUninitialize();  
}  
```
