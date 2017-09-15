---
title: Recuperar data e hora tipo como cadeias de caracteres usando o Driver SQLSRV | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- date and time types, retrieving as strings
ms.assetid: 58a974ea-4daf-4e3b-98ed-9731b9c9250f
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9638bc7ec31f4631b2938a61f2470a057a4465db
ms.contentlocale: pt-br
ms.lasthandoff: 09/09/2017

---
# <a name="how-to-retrieve-date-and-time-type-as-strings-using-the-sqlsrv-driver"></a>Como recuperar um tipo de data e hora como cadeias de caracteres usando o driver SQLSRV
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Esse recurso foi adicionado na versão 1.1 do [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] e é válido somente ao usar o driver SQLSRV para o [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]. É um erro usar a opção de conexão ReturnDatesAsStrings com o driver PDO_SQLSRV.  
  
Você pode recuperar tipos de data e hora (**datetime**, **data**, **tempo**, **datetime2**, e **datetimeoffset**) como cadeias de caracteres especificando uma opção na cadeia de conexão.  
  
### <a name="to-retrieve-date-and-time-types-as-strings"></a>Para recuperar tipos de data e hora como cadeias de caracteres  
  
-   Use a seguinte opção de conexão:  
  
    ```  
    'ReturnDatesAsStrings'=>true  
    ```  
  
    O padrão é **false**, o que significa que os tipos **datetime**, **Date**, **Time**, **DateTime2**e **DateTimeOffset** serão retornados como tipos **Datetime** do PHP.  
  
## <a name="example"></a>Exemplo  
O exemplo a seguir mostra a sintaxe especificando a recuperação dos tipos de data e hora como cadeias de caracteres.  
  
```  
<?php  
$serverName = "MyServer";  
$connectionInfo = array( "Database"=>"AdventureWorks", 'ReturnDatesAsStrings '=> true);  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
   echo "Could not connect.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="example"></a>Exemplo  
O exemplo a seguir mostra o que você pode recuperar datas como cadeias de caracteres especificando UTF-8 quando recuperar a cadeia de caracteres, mesmo quando a conexão foi feita com `"ReturnDatesAsStrings" => false`.  
  
```  
<?php  
$serverName = "MyServer";  
$connectionInfo = array( "Database"=>"AdventureWorks", "ReturnDatesAsStrings" => false);  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false ) {  
   echo "Could not connect.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
$tsql = "SELECT VersionDate FROM AWBuildVersion";  
  
$stmt = sqlsrv_query( $conn, $tsql);  
  
if ( $stmt === false ) {  
   echo "Error in statement preparation/execution.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
sqlsrv_fetch( $stmt );  
  
// retrieve date as string  
$date = sqlsrv_get_field( $stmt, 0, SQLSRV_PHPTYPE_STRING("UTF-8"));  
  
if( $date === false ) {  
   die( print_r( sqlsrv_errors(), true ));  
}  
  
echo $date;  
  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="example"></a>Exemplo  
O exemplo a seguir mostra como recuperar datas como cadeias de caracteres especificando UTF-8 e `"ReturnDatesAsStrings" => true` na cadeia de conexão.  
  
```  
<?php  
$serverName = "MyServer";  
$connectionInfo = array( "Database"=>"AdventureWorks", 'ReturnDatesAsStrings'=> true, "CharacterSet" => 'utf-8' );  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false ) {  
   echo "Could not connect.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
$tsql = "SELECT VersionDate FROM AWBuildVersion";  
  
$stmt = sqlsrv_query( $conn, $tsql);  
  
if ( $stmt === false ) {  
   echo "Error in statement preparation/execution.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
sqlsrv_fetch( $stmt );  
  
// retrieve date as string  
$date = sqlsrv_get_field( $stmt, 0 );  
  
if ( $date === false ) {  
   die( print_r( sqlsrv_errors(), true ));  
}  
  
echo $date;  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="example"></a>Exemplo  
O exemplo a seguir mostra como recuperar a data como um tipo do PHP. `'ReturnDatesAsStrings'=> false` está ativado por padrão.  
  
```  
<?php  
$serverName = "MyServer";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false ) {  
   echo "Could not connect.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
$tsql = "SELECT VersionDate FROM AWBuildVersion";  
  
$stmt = sqlsrv_query( $conn, $tsql);  
  
if ( $stmt === false ) {  
   echo "Error in statement preparation/execution.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
sqlsrv_fetch( $stmt );  
  
// retrieve date as string  
$date = sqlsrv_get_field( $stmt, 0 );  
  
if ( $date === false ) {  
   die( print_r( sqlsrv_errors(), true ));  
}  
  
$date_string = date_format( $date, 'jS, F Y' );  
echo "Date = $date_string\n";  
  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>Consulte também  
[Recuperando dados](../../connect/php/retrieving-data.md)  
  
