---
title: Descoberta de metadados | Microsoft Docs
description: Descoberta de metadados no OLE DB Driver para SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5990632392ec4656af7f655fcbd1b19b29346066
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2018
---
# <a name="metadata-discovery"></a>Descoberta de metadados
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  A melhoria de descoberta de metadados no [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] permite que o OLE DB Driver para aplicativos do SQL Server garantir que essa coluna ou retornados da execução de uma consulta de metadados de parâmetro sejam idênticos ou compatíveis com o formato de metadados especificado antes de execução da consulta. Você receberá um erro se os metadados retornados depois da execução da consulta não forem compatíveis com o formato de metadados especificado antes da execução da consulta.  
  
 No bcp e interfaces IBCPSession e IBCPSession2, agora você pode especificar um atraso leitura (descoberta de metadados atrasada) para evitar a descoberta de metadados para operações de saída de consulta. Isso melhora o desempenho e elimina falhas de descoberta de metadados.  
  
 Se você desenvolver um aplicativo usando o Driver do OLE DB para SQL Server, mas se conectar a uma versão de servidor anterior ao [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], descoberta de metadados corresponderá a funcionalidade para a versão do servidor.  
  
## <a name="remarks"></a>Remarks   
 As funções de membros OLE DB a seguir foram aperfeiçoadas no [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] para fornecer descoberta de metadados aprimorada:  
  
-   IColumnsInfo::GetColumnInfo  
  
-   IColumnsRowset::GetColumnsRowset  
  
-   ICommandWithParameters:: Getparameterinfo (consulte [ICommandWithParameters](../../oledb/ole-db-interfaces/icommandwithparameters.md) para obter mais informações)  
  
 Você também verá uma melhoria de desempenho ao especificar o formato de metadados usando IBCPSession::BCPSetBulkMode  
  
 A descoberta de metadados aprimorada no OLE DB Driver para SQL Server é possível devido à adição de dois procedimentos armazenados em [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]:  
  
-   sp_describe_first_result_set  
  
-   sp_describe_undeclared_parameters  
  
## <a name="see-also"></a>Consulte também  
 [Driver do OLE DB para recursos do SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
