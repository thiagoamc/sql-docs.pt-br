---
title: PDO::errorCode | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5864b1d8-6814-41cd-a88d-415124484c13
caps.latest.revision: ''
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 143a7bef0a0be2d125068a7f003b0b941ff39617
ms.sourcegitcommit: 2e130e9f3ce8a7ffe373d7fba8b09e937c216386
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/28/2018
---
# <a name="pdoerrorcode"></a>PDO::errorCode
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

PDO::errorCode recupera o SQLSTATE da operação mais recente no identificador do banco de dados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
mixed PDO::errorCode();  
```  
  
## <a name="return-value"></a>Valor de retorno  
PDO::errorCode retorna um SQLSTATE de cinco caracteres como uma cadeia de caracteres ou NULL se não houve nenhuma operação no identificador do banco de dados.  
  
## <a name="remarks"></a>Remarks  
PDO:: ErrorCode no driver PDO_SQLSRV retornará avisos sobre algumas operações bem-sucedidas. Por exemplo, em uma conexão bem-sucedida, PDO:: ErrorCode retornará "01000", indicando SQL_SUCCESS_WITH_INFO.  
  
PDO::errorCode recupera somente códigos de erro de operações executadas diretamente na conexão de banco de dados. Se você criar uma instância de PDOStatement por meio de PDO:: Prepare ou PDO:: Query e um erro é gerado no objeto de instrução, PDO:: ErrorCode não recuperará esse erro. Você deve chamar PDOStatement::errorCode para retornar o código de erro de uma operação executada em um objeto de instrução específico.  
  
O suporte para PDO foi adicionado na versão 2.0 dos [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a>Exemplo  
Neste exemplo, o nome da coluna está incorreto (`Cityx` em vez de `City`), causando um erro, que é relatado em seguida.  
  
```  
<?php  
$conn = new PDO( "sqlsrv:server=(local) ; Database = AdventureWorks ", "", "");  
$query = "SELECT * FROM Person.Address where Cityx = 'Essen'";  
  
$conn->query($query);  
print $conn->errorCode();  
?>  
```  
  
## <a name="see-also"></a>Consulte também  
[Classe PDO](../../connect/php/pdo-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
