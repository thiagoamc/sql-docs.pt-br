---
title: Componentes do Driver do OLE DB para SQL Server | Microsoft Docs
description: Componentes do Driver do OLE DB para SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|applications
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], components
- components [OLE DB Driver for SQL Server]
- MSOLEDBSQL, about OLE DB Driver for SQL Server
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 18b0f0e13fefefe5e3be09d7538150cfccbfcb21
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2018
---
# <a name="components-of-ole-db-driver-for-sql-server"></a>Componentes do Driver do OLE DB para SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  OLE DB Driver para SQL Server contém os seguintes componentes:  

|Componente|Description|  
|---------------|-----------------|  
|msoledbsql.dll|O arquivo de biblioteca de vínculo dinâmico (DLL) que contém todos os Driver OLE DB para a funcionalidade do SQL Server.|  
|msoledbsqlr.rll|O arquivo de recurso fornecido para o Driver OLE DB para a biblioteca do SQL Server.|   
|msoledbsql.h|O Driver OLE DB para o arquivo de cabeçalho do SQL Server que contém todas as novas definições necessárias para usar o Driver do OLE DB para SQL Server. Esse arquivo de cabeçalho substitui o arquivo de cabeçalho SQLOLEDB.<br /><br /> Observação: Você pode referenciar msoledbsql.h e SQLOLEDB no mesmo programa desde que SQLOLEDB é definido pela primeira vez.|  
|msoledbsql.lib|O arquivo de biblioteca necessário para chamar diretamente o **bcp** funções de utilitário que fazem parte do Driver OLE DB para SQL Server.<br /><br /> Observação: Se você referenciar o arquivo de msoledbsql.lib no código de programação, você precisa certificar-se de que o arquivo de msoledbsql.dll está no caminho do sistema e no caminho do sistema dos usuários que usam o seu aplicativo.|  

## <a name="see-also"></a>Consulte também  
 [Criando aplicativos com o Driver do OLE DB para SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
