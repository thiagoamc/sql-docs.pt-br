---
title: o banco de dados mestre (SQL Server PDW)
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/13/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c71617c0-6689-4f52-81c6-58f4cf7c7377
caps.latest.revision: "8"
ms.workload: not set
ms.openlocfilehash: 1fde1a329703ed833a9fdeb6686b1a63c04aea79
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="master-database"></a>Banco de dados mestre
O banco de dados mestre do SQL Server PDW armazena informações de logon de nível de dispositivo e o catálogo de banco de dados. É um SQL Server banco de dados mestre que reside no nó de controle. Como tal, ele oferece funcionalidade semelhante para o SQL Server PDW como mestre fornece para o SQL Server.  
  
Para obter mais informações sobre bancos de dados do sistema, consulte [bancos de dados do sistema](system-databases.md).  
  
## <a name="limitations-and-restrictions"></a>Limitações e restrições  
A lista a seguir descreve as operações que você não pode executar o banco de dados mestre do SQL Server PDW.  
  
Você *não pode:*  
  
-   Execute um backup diferencial do mestre.  
  
-   Crie objetos de usuário no mestre.  
  
-   Altere o agrupamento de mestre.  
  
-   Altere o proprietário do mestre.  
  
-   Remover ou renomear mestre.  
  
-   Modificar permissões para mestre.  
  
-   Executar **SHRINKLOG DBCC**.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Tarefa|Description|  
|--------|---------------|  
|Crie um backup completo do mestre.|Exemplo:<br /><br />`BACKUP DATABASE master TO backup_directory;`<br /><br />Para obter mais informações, consulte [banco de dados de BACKUP](../t-sql/statements/backup-database-parallel-data-warehouse.md).|  
|Restaurar o banco de dados mestre|Para restaurar o banco de dados mestre, use o [restaurar o banco de dados mestre](restore-the-master-database.md) página ferramenta do Configuration Manager.|  
|Exibir informações de catálogo de banco de dados.|`SELECT * FROM master.sys.databases;`|  
|Exibir informações de logon e a permissão de todo o sistema.|`SELECT * FROM master.sys.server_permissions;`<br /><br />`SELECT * FROM master.sys.server_principals;`<br /><br />`SELECT * FROM master.sys.sql_logins;`|  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
