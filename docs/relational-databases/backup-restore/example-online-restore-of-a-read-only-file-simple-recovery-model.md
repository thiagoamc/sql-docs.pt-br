---
title: "Exemplo: Restaura&#231;&#227;o online de um arquivo somente leitura (modelo de recupera&#231;&#227;o simples) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "sequências de restauração [SQL Server], online"
  - "restaurações online [SQL Server], modelo de recuperação simples"
  - "modelo de recuperação simples [SQL Server], exemplos de RESTORE"
ms.assetid: 0c691fc6-9865-46a7-b055-8097424492d6
caps.latest.revision: 27
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 27
---
# Exemplo: Restaura&#231;&#227;o online de um arquivo somente leitura (modelo de recupera&#231;&#227;o simples)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Este tópico é pertinente para bancos de dados [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sob o modelo de recuperação simples que contenham um grupo de arquivos somente leitura. No modelo de recuperação simples, um arquivo somente leitura pode ser restaurado online se existir um backup do arquivo que tenha sido feito desde a última vez em que arquivo tornou-se somente leitura.  
  
 Neste exemplo, um banco de dados denominado `adb` contém três grupos de arquivos. O grupo de arquivos `A` é leitura/gravação, e os grupos de arquivos `B` e `C` são somente leitura. Inicialmente, todos os grupos de arquivos estão online. Um arquivo somente leitura no grupo de arquivos `B`, `b1`, tem de ser restaurado. O administrador de banco de dados pode restaurá-lo usando um backup que foi feito depois de o arquivo tornar-se somente leitura. Durante a restauração, o grupo de arquivos `B` estará offline, mas o resto do banco de dados permanecerá online.  
  
## Sequência de restauração  
  
> [!NOTE]  
>  A sintaxe para uma sequência de restauração online é igual à de uma sequência de restauração offline.  
  
 Para restaurar o arquivo, o administrador do banco de dados usa a seguinte sequência de restauração:  
  
```  
RESTORE DATABASE adb FILE='b1' FROM filegroup_B_backup   
WITH RECOVERY  
```  
  
 O arquivo agora está online.  
  
## Exemplos adicionais  
  
-   [Exemplo: restauração por etapas de banco de dados &#40;Modelo de recuperação simples&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [Exemplo: restauração por etapas de apenas alguns grupos de arquivos &#40;Modelo de recuperação simples&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [Exemplo: restauração por etapas de banco de dados &#40;Modelo de recuperação completa&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [Exemplo: restauração por etapas de apenas alguns grupos de arquivos &#40;Modelo de recuperação completa&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [Exemplo: restauração online de um arquivo de leitura/gravação #40;Modelo de recuperação completa&#41;](../../relational-databases/backup-restore/example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [Exemplo: restauração online de um arquivo somente leitura &#40;Modelo de recuperação completa&#41;](../../relational-databases/backup-restore/example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## Consulte também  
 [Restauração online &#40;SQL Server&#41;](../../relational-databases/backup-restore/online-restore-sql-server.md)   
 [Restaurações por etapas &#40;SQL Server&#41;](../../relational-databases/backup-restore/piecemeal-restores-sql-server.md)   
 [Restaurações de arquivos &#40;Modelo de recuperação simples&#41;](../../relational-databases/backup-restore/file-restores-simple-recovery-model.md)   
 [Visão geral de restauração e recuperação &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)  
  
  