---
title: PDOStatement::getAttribute | Microsoft Docs
ms.custom: ''
ms.date: 07/13/2017
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
ms.assetid: 41d0cca3-8556-4573-bb90-8e9402d9379f
caps.latest.revision: ''
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 98bf243805b739ec887ccdff3a70258b41e734b3
ms.sourcegitcommit: 2e130e9f3ce8a7ffe373d7fba8b09e937c216386
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/28/2018
---
# <a name="pdostatementgetattribute"></a>PDOStatement::getAttribute
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Recupera o valor de um atributo PDOStatement predefinido ou de um atributo de driver personalizado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
mixed PDOStatement::getAttribute( $attribute );  
```  
  
#### <a name="parameters"></a>Parâmetros  
$*atributo*: um inteiro, uma das constantes * ou PDO::SQLSRV_ATTR_\* constantes. Atributos com suporte são os atributos que você pode definir com [pdostatement:: setAttribute](../../connect/php/pdostatement-setattribute.md), PDO:: sqlsrv_attr_direct_query (para obter mais informações, consulte [execução de instrução direta e execução de instrução preparada no o Driver PDO_SQLSRV](../../connect/php/direct-statement-execution-prepared-statement-execution-pdo-sqlsrv-driver.md)), PDO:: attr_cursor e PDO:: sqlsrv_attr_cursor_scroll_type (para obter mais informações, consulte [tipos de Cursor (Driver PDO_SQLSRV)](../../connect/php/cursor-types-pdo-sqlsrv-driver.md)).  
  
## <a name="return-value"></a>Valor de retorno  
Em caso de sucesso, retorna um valor (misto) para um atributo PDO predefinido ou um atributo de driver personalizado. Retorna null em caso de falha.  
  
## <a name="remarks"></a>Remarks  
Consulte [PDOStatement::setAttribute](../../connect/php/pdostatement-setattribute.md) para obter um exemplo.  
  
O suporte para PDO foi adicionado na versão 2.0 dos [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="see-also"></a>Consulte também  
[PDOStatement Class](../../connect/php/pdostatement-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
