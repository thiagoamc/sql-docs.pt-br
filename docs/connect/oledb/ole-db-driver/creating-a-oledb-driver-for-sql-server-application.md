---
title: Criando um Driver do OLE DB para o aplicativo do SQL Server | Microsoft Docs
description: Criando um Driver OLE DB para o aplicativo do SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb-driver-for-sql-server
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, application creation
- applications [OLE DB Driver for SQL Server]
- OLE DB, creating applications
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e54bdee09a64cd1393a41109207d42a598cb31fa
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2018
---
# <a name="creating-an-ole-db-driver-for-sql-server-application"></a>Criando um Driver do OLE DB para o aplicativo do SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  A criação de um Driver OLE DB para o aplicativo do SQL Server envolve estas etapas:  
  
1.  Estabelecimento de uma conexão a uma fonte de dados.  
  
2.  Execução de um comando.  
  
3.  Processamento dos resultados.  
  
> [!NOTE]  
>  Quando possível, use a Autenticação do Windows. Se a Autenticação do Windows não estiver disponível, solicite aos usuários que digitem suas credenciais em tempo de execução. Evite armazenar as credenciais em um arquivo. Se você deve manter as credenciais, criptografe-as com [cryptoAPI Win32](http://go.microsoft.com/fwlink/?LinkId=9504).  
  
## <a name="in-this-section"></a>Nesta seção  
  
-   [Estabelecer uma Conexão com uma fonte de dados](../../oledb/ole-db-driver/establishing-a-connection-to-a-data-source.md)  
  
-   [Executar um comando](../../oledb/ole-db-driver/executing-a-command.md)  
  
-   [Processando resultados](../../oledb/ole-db-driver/processing-results.md)  
  
-   [Sobre propriedades OLE DB](../../oledb/ole-db-driver/about-ole-db-properties.md)  
  
-   [Usando a cláusula OUTPUT com OLE DB em Driver do OLE DB para SQL Server](../../oledb/ole-db-driver/using-the-output-clause-with-ole-db-in-oledb-driver-for-sql-server.md)  
  
## <a name="see-also"></a>Consulte também  
 [Driver do OLE DB para SQL Server &#40;OLE DB&#41;](../../oledb/ole-db/oledb-driver-for-sql-server-ole-db.md)  
  
  
