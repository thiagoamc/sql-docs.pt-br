---
title: "Método (Java.IO. Reader, long) updateCharacterStream | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e5e177c-7ed7-4d0c-8fa8-0e13daf46f4b
caps.latest.revision: "19"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a4f8c19e87773499fa731d933370c04dcdb8a5e6
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2017
---
# <a name="updatecharacterstream-method-javalangstring-javaioreader-long"></a>Método updateCharacterStream (java.lang.String, java.io.Reader, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Atualiza a coluna designada com um valor de fluxo de caracteres que terá o número de caracteres especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public void updateCharacterStream(java.lang.String columnLabel,  
                                  java.io.Reader reader,  
                                  long length)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *columnLabel*  
  
 Um **cadeia de caracteres** que contém o rótulo da coluna.  
  
 *leitor*  
  
 Um objeto do leitor.  
  
 *length*  
  
 O comprimento do fluxo.  
  
## <a name="exceptions"></a>Exceções  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentários  
 Esse método updateCharacterStream é especificado pelo método updateCharacterStream na interface Java.SQL. resultset.  
  
 Esse método passa caracteres Unicode de um objeto do leitor de texto selecionado e de colunas binárias. Isto inclui todas as colunas de texto e colunas binary, varbinary, varbinary(max), image e XML, mas não colunas UDT.  
  
 Se o comprimento do fluxo for diferente do especificado no *comprimento* parâmetro, o driver JDBC lançará uma exceção quando a linha for atualizada ou inserida.  
  
 Se o comprimento do fluxo for desconhecido, o *comprimento* parâmetro pode ser definido como -1 para indicar que o driver deve aceitar o fluxo independentemente de seu tamanho. Com sqljdbc4.jar, é recomendável que você use o método do JDBC 4.0 [updateCharacterStream método &#40;java.lang.String, Java.IO. Reader &#41;](../../../connect/jdbc/reference/updatecharacterstream-method-java-lang-string-java-io-reader.md) quando o aplicativo quiser atualizar a coluna de um fluxo cujo comprimento é desconhecido.  
  
## <a name="see-also"></a>Consulte também  
 [Método updateCharacterStream &#40; SQLServerResultSet &#41;](../../../connect/jdbc/reference/updatecharacterstream-method-sqlserverresultset.md)   
 [Membros de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
