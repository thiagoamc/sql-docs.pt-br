---
title: PDO | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 359a87c6-c13a-4518-8f23-a922e7f3b171
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: faf387371d9d9f49fbba4cae466ef8b52f4e08c4
ms.contentlocale: pt-br
ms.lasthandoff: 09/09/2017

---
# <a name="pdoexec"></a>PDO::exec
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Prepara e executa uma instrução SQL em uma única chamada de função, retornando o número de linhas afetadas pela instrução.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
int PDO::exec ($statement)  
```  
  
#### <a name="parameters"></a>Parâmetros  
*$statement*: uma cadeia de caracteres contendo a instrução SQL a executar.  
  
## <a name="return-value"></a>Valor de retorno  
Um inteiro que informa o número de linhas afetadas.  
  
## <a name="remarks"></a>Comentários  
Se *$statement* contiver várias instruções SQL, a contagem de linhas afetadas será informada somente para a última instrução.  
  
PDO::exec não retorna resultados de uma instrução SELECT.  
  
Os atributos a seguir afetam o comportamento de PDO::exec:  
  
-   PDO::ATTR_DEFAULT_FETCH_MODE  
  
-   PDO::SQLSRV_ATTR_ENCODING  
  
-   PDO::SQLSRV_ATTR_QUERY_TIMEOUT  
  
Consulte [PDO::setAttribute](../../connect/php/pdo-setattribute.md) para obter mais informações.  
  
O suporte para PDO foi adicionado na versão 2.0 dos [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a>Exemplo  
Este exemplo exclui linhas na tabela 1 com 'xxxyy' na col1. Em seguida, o exemplo informa quantas linhas foram excluídas.  
  
```  
<?php  
   $c = new PDO( "sqlsrv:server=(local)");  
  
   $c->exec("use Test");  
   $ret = $c->exec("delete from Table1 where col1 = 'xxxyy'");  
   echo $ret;  
?>  
```  
  
## <a name="see-also"></a>Consulte também  
[Classe PDO](../../connect/php/pdo-class.md)  
[PDO](http://go.microsoft.com/fwlink/?LinkID=187441)  
  
