---
title: Definir ou alterar o agrupamento de servidor | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: collations
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- server collations [SQL Server]
- collations [SQL Server], server
ms.assetid: 3242deef-6f5f-4051-a121-36b3b4da851d
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Active
ms.openlocfilehash: 7c7619944421bd1d7f7ddf30ab513543a71465bc
ms.sourcegitcommit: 9d0467265e052b925547aafaca51e5a5e93b7e38
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/02/2018
---
# <a name="set-or-change-the-server-collation"></a>Definir ou alterar o agrupamento do servidor
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
O agrupamento do servidor atua como o agrupamento padrão de todos os bancos de dados do sistema instalados com a instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], e também com quaisquer bancos de dados de usuário recém-criados. O agrupamento do servidor é especificado durante a instalação do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Para obter mais informações, consulte [Suporte a agrupamentos e Unicode](../../relational-databases/collations/collation-and-unicode-support.md).  
  
## <a name="changing-the-server-collation"></a>Alterando o agrupamento do servidor  
 A alteração do agrupamento padrão para uma instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pode ser uma operação complexa e engloba as seguintes etapas:  
  
-   Verifique se você tem todas as informações ou scripts necessários para recriar seus bancos de dados de usuário e todos os objetos neles.  
  
-   Exporte todos os seus dados usando uma ferramenta como [bcp Utility](../../tools/bcp-utility.md). Para obter mais informações, consulte [Importação e exportação em massa de dados &#40;SQL Server&#41;](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md).  
  
-   Descarte todos os bancos de dados de usuário.  
  
-   Reconstrua o banco de dados mestre especificando o novo agrupamento na propriedade SQLCOLLATION do comando **setup** . Por exemplo:  
  
    ```  
    Setup /QUIET /ACTION=REBUILDDATABASE /INSTANCENAME=InstanceName   
    /SQLSYSADMINACCOUNTS=accounts /[ SAPWD= StrongPassword ]   
    /SQLCOLLATION=CollationName  
    ```  
  
     Para obter mais informações, consulte [Recriar bancos de dados do sistema](../../relational-databases/databases/rebuild-system-databases.md).  
  
-   Crie todos os bancos de dados e todos os objetos neles.  
  
-   Importe todos os dados.  
  
> [!NOTE]  
>  Em vez de alterar o agrupamento padrão de uma instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], você pode especificar um agrupamento para cada novo banco de dados que criar.  
  
## <a name="see-also"></a>Consulte Também  
 [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md)   
 [Definir ou alterar o agrupamento de banco de dados](../../relational-databases/collations/set-or-change-the-database-collation.md)   
 [Definir ou alterar o agrupamento de coluna](../../relational-databases/collations/set-or-change-the-column-collation.md)   
 [Recompilar bancos de dados do sistema](../../relational-databases/databases/rebuild-system-databases.md)  
  
  
