---
title: Gerenciando conjuntos de resultados com o Driver JDBC | Microsoft Docs
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
ms.assetid: 9ed5ad41-22e0-4e4a-8a79-10512db60d50
caps.latest.revision: "18"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5cf61ff8794270ca5706284118c41c224bd5518f
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2017
---
# <a name="managing-result-sets-with-the-jdbc-driver"></a>Gerenciando conjuntos de resultados com o JDBC Driver
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  O conjunto de resultados é um objeto que representa um conjunto de dados retornado de uma fonte de dados, geralmente como o resultado de uma consulta. O conjunto de resultados contém linhas e colunas para manter os elementos de dados solicitados e é navegado com um cursor. Um conjunto de resultados pode ser atualizável, ou seja, pode ser modificado e pode ter essas modificações enviadas à fonte de dados original. Um conjunto de resultados também pode ter vários níveis de sensibilidade a alterações na fonte de dados subjacentes.  
  
 O tipo de conjunto de resultados é determinado quando uma instrução é criada, o que é quando uma chamada para o [createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md) método o [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) classe é feita. A função fundamental de um conjunto de resultados é proporcionar a aplicativos Java uma representação utilizável dos dados de banco de dados. Isto é feito normalmente com os métodos de tipo getter e setter nos elementos de dados do conjunto de resultados.  
  
 No exemplo a seguir, que se baseia o [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] banco de dados de exemplo, um conjunto de resultados é criado chamando o [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) método do [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) classe. Dados do conjunto de resultados é então exibido usando o [getString](../../connect/jdbc/reference/getstring-method-sqlserverresultset.md) método o [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) classe.  
  
 [!code[JDBC#ManagingResultSets1](../../connect/jdbc/codesnippet/Java/managing-result-sets-with-t_1.java)]  
  
 Os tópicos nesta seção descrevem vários aspectos de uso de conjunto de resultados, inclusive tipos de cursor, simultaneidade e bloqueio de linha.  
  
## <a name="in-this-section"></a>Nesta seção  
  
|Tópico|Description|  
|-----------|-----------------|  
|[Noções básicas os tipos de cursor](../../connect/jdbc/understanding-cursor-types.md)|Descreve os diferentes tipos de cursor que o [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] oferece suporte.|  
|[Noções básicas sobre controle de simultaneidade](../../connect/jdbc/understanding-concurrency-control.md)|Descreve como o driver JDBC dá suporte ao controle de simultaneidade.|  
|[Noções básicas sobre bloqueio de linha](../../connect/jdbc/understanding-row-locking.md)|Descreve como o driver JDBC dá suporte ao bloqueio de linha.|  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral do JDBC Driver](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
