---
title: "Exemplo de URL de Conexão | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96fabc42-59d1-4cc0-93c5-db00cbe55e95
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9bbb062925c0c0ee1c14c0f2190101c8967d0c65
ms.contentlocale: pt-br
ms.lasthandoff: 09/09/2017

---
# <a name="connection-url-sample"></a>Exemplo de URL de conexão
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Isso [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] aplicativo de exemplo demonstra como se conectar a um [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] banco de dados usando uma URL de conexão. Ele também demonstra como recuperar dados de um [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] banco de dados usando uma instrução SQL.  
  
 O arquivo de código desse exemplo chama-se connectURL.java e pode ser encontrado neste local:  
  
 \<*diretório de instalação*> \sqljdbc_\<*versão*>\\<*idioma*> \samples\connections  
  
## <a name="requirements"></a>Requisitos  
 Para executar este aplicativo de exemplo, será necessário definir o classpath para incluir o arquivo sqljdbc.jar ou o arquivo sqljdbc4.jar. Se no classpath faltar uma entrada para sqljdbc.jar ou sqljdbc4.jar, o aplicativo de exemplo lançará a exceção comum "Class not found". Você também precisará acessar o [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] banco de dados de exemplo. Para obter mais informações sobre como definir o classpath, consulte [usando o Driver JDBC](../../../connect/jdbc/using-the-jdbc-driver.md).  
  
> [!NOTE]  
>  O [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] fornece sqljdbc.jar e sqljdbc4.jar os arquivos de biblioteca de classes a serem usados dependendo das suas configurações preferidas do Java Runtime Environment (JRE). Para obter mais informações sobre qual arquivo JAR escolher, consulte [requisitos do sistema para o Driver JDBC](../../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, o código de exemplo define várias propriedades de conexão na URL de conexão e, em seguida, chama o método getConnection da classe DriverManager para retornar um [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) objeto.  
  
 Em seguida, o código de exemplo usa o [createStatement](../../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md) método do objeto SQLServerConnection para criar um [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) objeto e, em seguida, o [executeQuery](../../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) método é chamado para executar a instrução SQL.  
  
 Por fim, o exemplo usa o [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objeto retornado do método executeQuery para iterar pelos resultados retornados pela instrução SQL.  
  
```java  
import java.sql.*;  
  
public class connectURL {  
  
   public static void main(String[] args) {  
  
      // Create a variable for the connection string.  
      String connectionUrl = "jdbc:sqlserver://localhost:1433;" +  
         "databaseName=AdventureWorks;user=UserName;password=*****";  
  
      // Declare the JDBC objects.  
      Connection con = null;  
      Statement stmt = null;  
      ResultSet rs = null;  
  
      try {  
         // Establish the connection.  
         Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
         con = DriverManager.getConnection(connectionUrl);  
  
         // Create and execute an SQL statement that returns some data.  
         String SQL = "SELECT TOP 10 * FROM Person.Contact";  
         stmt = con.createStatement();  
         rs = stmt.executeQuery(SQL);  
  
         // Iterate through the data in the result set and display it.  
         while (rs.next()) {  
            System.out.println(rs.getString(4) + " " + rs.getString(6));  
         }  
      }  
  
      // Handle any errors that may have occurred.  
      catch (Exception e) {  
         e.printStackTrace();  
      }  
      finally {  
         if (rs != null) try { rs.close(); } catch(Exception e) {}  
         if (stmt != null) try { stmt.close(); } catch(Exception e) {}  
         if (con != null) try { con.close(); } catch(Exception e) {}  
      }  
   }  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Conectando e recuperando dados](../../../connect/jdbc/connecting-and-retrieving-data.md)  
  
  