---
title: "Comandos com os comandos de computação parametrizados | Microsoft Docs"
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
helpviewer_keywords:
- data shaping [ADO], parameterized commands
- parameterized commands [ADO]
- APPEND clause [ADO]
- COMPUTE command [ADO]
ms.assetid: 732f624f-8900-4608-9815-194302d22e8b
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 18bfbc4a2e18e0232380edf157410fbd4eb3b12c
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="parameterized-commands-with-intervening-compute-commands"></a>Comandos de computação de comandos com parâmetros com intervenção
Uma forma com parâmetros típica comando APPEND possui uma cláusula que cria um pai **registros** com um comando de consulta e outra cláusula que cria um filho **registros** com um comando de consulta parametrizada — ou seja, um comando que contém um espaço reservado de parâmetro (um ponto de interrogação, "?"). Resultante em forma de **registros** possui dois níveis, em que o pai ocupa o nível superior e o filho ocupa um nível inferior.  
  
 A cláusula que cria o filho **registros** pode agora ser um número arbitrário de forma aninhada comandos de computação, em que o comando mais aninhado contém a consulta parametrizada. Resultante em forma de **registros** possui vários níveis, em que o pai ocupa o nível superior, o filho ocupa o nível mais baixo e um número arbitrário de **registros**s geradas pelo comandos de computação de forma ocupam os níveis intermediários.  
  
 O uso típico para esse recurso é chamar a função de agregação e as habilidades de agrupamento de shapeCOMPUTE comandos para criar intervenção **registros** objetos analíticos informações sobre o filho **conjunto de registros** . Além disso, porque este é um comando de forma com parâmetros, cada vez que uma coluna de capítulo do pai é acessada, um novo filho **registros** podem ser recuperadas. Como os níveis intermediários são derivados de filho, eles também serão computada novamente.  
  
## <a name="see-also"></a>Consulte também  
 [Exemplo de data shaping](../../../ado/guide/data/data-shaping-example.md)
