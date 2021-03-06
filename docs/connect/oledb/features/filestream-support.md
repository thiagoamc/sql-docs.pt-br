---
title: Suporte a FILESTREAM | Microsoft Docs
description: Suporte FILESTREAM no Driver do OLE DB para SQL Server
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
helpviewer_keywords:
- FILESTREAM [SQL Server], OLE DB Driver for SQL Server
- OLE DB Driver for SQL Server [FILESTREAM support]
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d528a05cd30024d2ff865a99acae1a11f187dbfc
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2018
---
# <a name="filestream-support"></a>Suporte a FILESTREAM
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  FILESTREAM é uma forma de armazenar e acessar valores altos de binário, por meio do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ou por acesso direto ao sistema de arquivos do Windows. Um valor binário grande é um valor superior a 2 gigabytes (GB). Para obter mais informações sobre suporte a FILESTREAM aprimorado, consulte [FILESTREAM &#40;SQL Server&#41;](../../../relational-databases/blob/filestream-sql-server.md).  
  
 Quando uma conexão de banco de dados é aberto, **@@TEXTSIZE**  será definido como -1 ("ilimitado"), por padrão.  
  
 Também é possível acessar e atualizar colunas FILESTREAM usando as APIs do sistema de arquivos do Windows.  
  
 Para obter mais informações, consulte os tópicos a seguir:  
  
-   [Suporte a FILESTREAM &#40;OLE DB&#41;](../../oledb/ole-db/filestream-support-ole-db.md)    
  
-   [Acessar dados do FILESTREAM com OpenSqlFilestream](../../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md)  
  
## <a name="querying-for-filestream-columns"></a>Consultando colunas FILESTREAM  
 Conjuntos de linhas de esquema no OLE DB não relatarão se uma coluna é uma coluna FILESTREAM. ITableDefinition no OLE DB não pode ser usado para criar uma coluna FILESTREAM.    
  
 Para criar colunas FILESTREAM ou detectar quais colunas existentes são colunas FILESTREAM, você pode usar o **is_filestream** coluna o [Columns](../../../relational-databases/system-catalog-views/sys-columns-transact-sql.md) exibição do catálogo.  
  
 A seguir, é mostrado um exemplo:  
  
```  
-- Create a table with a FILESTREAM column.  
CREATE TABLE Bob_01 (GuidCol1 uniqueidentifier ROWGUIDCOL NOT NULL UNIQUE DEFAULT NEWID(), IntCol2 int, varbinaryCol3 varbinary(max) FILESTREAM);  
  
-- Find FILESTREAM columns.  
SELECT name FROM sys.columns WHERE is_filestream=1;  
  
-- Determine whether a column is a FILESTREAM column.  
SELECT is_filestream FROM sys.columns WHERE name = 'varbinaryCol3' AND object_id IN (SELECT object_id FROM sys.tables WHERE name='Bob_01');  
```  
  
## <a name="down-level-compatibility"></a>Compatibilidade com níveis inferiores  
 Se o cliente tiver sido compilado usando o Driver do OLE DB para SQL Server e o aplicativo se conecta ao [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], **varbinary (max)** comportamento será compatível com [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Ou seja, o tamanho máximo de dados retornados será limitado a 2 GB. Para valores de resultados maiores que 2 GB, ocorrerá truncamento e um aviso de "truncamento à direita dados de cadeia de caracteres" será retornado.  
  
 Quando a compatibilidade de tipo de dados estiver definida como 80, o comportamento do cliente será consistente com o comportamento de clientes de nível inferior.  
  
 Para clientes que usam SQLOLEDB ou outros provedores lançados antes do [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], **varbinary (max)** será mapeado para imagem.  
  
## <a name="see-also"></a>Consulte também  
 [Driver do OLE DB para recursos do SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
