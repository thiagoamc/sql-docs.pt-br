---
title: Errors | Microsoft Docs
description: Erros
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-errors
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, errors
- OLE/COM errors
- errors [OLE DB]
- OLE DB error handling, about error handling
- OLE DB error handling
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0ea14d636771de6edb42d41876c5d94489ce6199
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2018
---
# <a name="errors"></a>Erros
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Os objetos OLE/COM informam erros através do código de retorno de HRESULT das funções de membro de objeto. Um HRESULT de OLE/COM é uma estrutura de bits compactados. A OLE fornece macros que eliminam a referência de membros de estrutura.  
  
 OLE/COM Especifica a **IErrorInfo** interface. A interface expõe métodos como **GetDescription**. Isso permite que clientes extraiam detalhes de erros dos servidores OLE/COM. OLE DB estende **IErrorInfo** para suportar o retorno de vários pacotes de informações de erro na execução de uma função de membro.  
  
 O [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pode retornar vários erros. Um aplicativo pode recuperar erros do servidor um cada vez chamando [imultipleresults:: GetResult](http://go.microsoft.com/fwlink/?LinkId=129630) combinado com ISQLErrorInfo e IErrorRecords.  
  
 O Driver OLE DB para SQL Server expõe o OLE DB aprimorada por registro **IErrorInfo**, personalizado **ISQLErrorInfo**e específicas do provedor [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1) erro interfaces de objeto.  
  
 Para obter informações sobre rastreamento de erros, consulte [rastreamento de acesso a dados](http://go.microsoft.com/fwlink/?LinkId=125805). Para obter informações sobre aprimoramentos para rastreamento de erro adicionados no [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], consulte [acessando informações de diagnóstico no Log de eventos estendidos](../../oledb/features/accessing-diagnostic-information-in-the-extended-events-log.md).  
  
## <a name="in-this-section"></a>Nesta seção  
  
-   [Códigos de retorno](../../oledb/ole-db-errors/return-codes.md)  
  
-   [Informações em Interfaces de erro](../../oledb/ole-db-errors/information-in-error-interfaces.md)  
  
-   [Detalhes de erro do SQL Server](../../oledb/ole-db-errors/sql-server-error-detail.md)  
  
-   [Recuperando informações de erro](../../oledb/ole-db-errors/retrieving-error-information.md)  
  
-   [Resultados de mensagem do SQL Server](../../oledb/ole-db-errors/sql-server-message-results.md)  
  
## <a name="see-also"></a>Consulte também  
 [Driver do OLE DB para SQL Server &#40;OLE DB&#41;](../../oledb/ole-db/oledb-driver-for-sql-server-ole-db.md)  
  
  
