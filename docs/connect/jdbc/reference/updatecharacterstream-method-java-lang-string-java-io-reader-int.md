---
title: "Método updateCharacterStream (Java.IO. Reader, int) | Microsoft Docs"
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
apiname: SQLServerResultSet.updateCharacterStream (java.lang.String, java.io.Reader, int)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 08cfc4e0-83f0-4f2f-ac55-b381f34fe67f
caps.latest.revision: "22"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 32cfd203e7b0d97a4141399b4ada12ad5c790c60
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2017
---
# <a name="updatecharacterstream-method-javalangstring-javaioreader-int"></a>Método updateCharacterStream (java.lang.String, java.io.Reader, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Atualiza a coluna designada com um valor de fluxo de caracteres que terá o número de caracteres especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public void updateCharacterStream(java.lang.String columnName,  
                                  java.io.Reader readerValue,  
                                  int length)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *columnName*  
  
 Um **cadeia de caracteres** que contém o nome da coluna.  
  
 *readerValue*  
  
 Um objeto do leitor.  
  
 *length*  
  
 Um **int** que indica o comprimento do fluxo.  
  
## <a name="exceptions"></a>Exceções  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentários  
 Esse método updateCharacterStream é especificado pelo método updateCharacterStream na interface Java.SQL. resultset.  
  
 Esse método passa caracteres Unicode de um objeto do leitor de texto selecionado e de colunas binárias. Isso inclui todas as colunas de texto e **binário**, **varbinary**, **varbinary (max)**, **imagem**, e **xml**colunas, mas não **udt** colunas.  
  
 Se o comprimento do fluxo for diferente do especificado no *comprimento* parâmetro, o driver JDBC lançará uma exceção quando a linha for atualizada ou inserida.  
  
 Se o comprimento do fluxo for desconhecido, o *comprimento* parâmetro pode ser definido como -1 para indicar que o driver deve aceitar o fluxo independentemente de seu tamanho. Com sqljdbc4.jar, é recomendável que você use o método do JDBC 4.0 [updateCharacterStream método &#40;java.lang.String, Java.IO. Reader &#41;](../../../connect/jdbc/reference/updatecharacterstream-method-java-lang-string-java-io-reader.md) quando o aplicativo quiser atualizar a coluna de um fluxo cujo comprimento é desconhecido.  
  
## <a name="see-also"></a>Consulte também  
 [Método updateCharacterStream &#40; SQLServerResultSet &#41;](../../../connect/jdbc/reference/updatecharacterstream-method-sqlserverresultset.md)   
 [Membros de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
