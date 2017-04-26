---
title: "Lição 5: Fazer backup do banco de dados usando o backup de instantâneo de arquivo | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: d9134ade-7b03-4c5c-8ed3-3bc369a61691
caps.latest.revision: 19
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: dd3226cf6bf52151c94853d87b4de28e54b5d2df
ms.lasthandoff: 04/11/2017

---
# <a name="lesson-5-backup-database-using-file-snapshot-backup"></a>Lição 5: Fazer backup do banco de dados usando o backup de instantâneo de arquivo
Nesta lição, você aprenderá a fazer backup do banco de dados AdventureWorks2014 na máquina virtual do Azure usando o backup de instantâneo de arquivo para executar um backup quase instantâneo usando instantâneos do Azure. Para obter mais informações sobre backups de instantâneo, veja [Backups de instantâneo de arquivo para arquivos de banco de dados no Azure](../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md)  
  
Para fazer backup do banco de dados AdventureWorks2014 usando o backup de instantâneo de arquivo, siga estas etapas:  
  
1.  Conecte-se ao SQL Server Management Studio.  
  
2.  Abra uma nova janela de consulta e conecte-se à instância do SQL Server 2016 do mecanismo de banco de dados na máquina virtual do Azure.  
  
3.  Copie, cole e execute o script Transact-SQL a seguir na janela de consulta (não feche esta janela de consulta – você vai executar esse script novamente na etapa 5). Esse procedimento armazenado do sistema permite exibir os backups de instantâneo de arquivo existentes de cada arquivo que consiste em um banco de dados especificado. Você observará que não há nenhum backup de instantâneo de arquivo desse banco de dados.  
  
    ```  
  
    -- Verify that no file snapshot backups exist  
    SELECT * FROM sys.fn_db_backup_file_snapshots ('AdventureWorks2014');  
  
    ```  
  
4.  Copie e cole o script Transact-SQL a seguir na janela de consulta. Modifique a URL de forma adequada para o nome de sua conta de armazenamento e o contêiner especificado na Lição 1 e execute este script. Observe como o backup ocorre rapidamente.  
  
    ```  
  
    -- Backup the AdventureWorks2014 database with FILE_SNAPSHOT  
    BACKUP DATABASE AdventureWorks2014   
       TO URL = 'https://<mystorageaccountname>.blob.core.windows.net/<mystorageaccountcontainername>/AdventureWorks2014_Azure.bak'   
       WITH FILE_SNAPSHOT;  
  
    ```  
  
    ![painel Resultados mostrando instantâneos de arquivo de cada arquivo de banco de dados](../relational-databases/media/2a9320e0-067a-485a-8e0e-636660005e5c.JPG "painel Resultados mostrando instantâneos de arquivo de cada arquivo de banco de dados")  
  
5.  Depois de verificar se o script da etapa 4 foi executado com êxito, execute novamente o script a seguir. Observe que a operação de backup de instantâneo de arquivo da etapa 4 gerou instantâneos de arquivo dos dados e do arquivo de log.  
  
    ```  
  
    -- Verify that two file-snapshot backups exist  
    SELECT * FROM sys.fn_db_backup_file_snapshots ('AdventureWorks2014');  
  
    ```  
  
    ![resultados da função sys.fn_db_backup_file_snapshots mostrando 2 instantâneos](../relational-databases/media/fca1436e-9607-4432-97ee-f66ac2f2108d.JPG "resultados da função sys.fn_db_backup_file_snapshots mostrando 2 instantâneos")  
  
6.  No Pesquisador de Objetos, na instância do SQL Server 2016 na máquina virtual do Azure, expanda o nó Bancos de Dados e verifique se o banco de dados AdventureWorks2014 foi restaurado para essa instância (atualize o nó, conforme necessário).  
  
7.  No Pesquisador de Objetos, conecte-se ao armazenamento do Azure.  
  
8.  Expanda Contêineres, expanda o contêiner criado na Lição 1 e verifique se AdventureWorks2014_Azure.bak na etapa 4 acima é exibido nesse contêiner, juntamente com o arquivo de backup da Lição 3 e os arquivos de banco de dados da Lição 4 (atualize o nó, conforme necessário).  
  
    ![O backup de instantâneo de arquivo aparece no contêiner do Azure](../relational-databases/media/181bc970-4af7-4272-a9ae-4bef674f2e02.JPG "O backup de instantâneo de arquivo aparece no contêiner do Azure")  
  
**Próxima lição:**  
  
[Lição 6: Gerar log de atividade e de backup usando o backup de instantâneo de arquivo](../relational-databases/lesson-6-generate-activity-and-backup-log-using-file-snapshot-backup.md)  
  
## <a name="see-also"></a>Consulte também  
[Backups de instantâneo de arquivo para arquivos de banco de dados no Azure](../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md)  
[sys.fn_db_backup_file_snapshots &#40;Transact-SQL&#41;](../relational-databases/system-functions/sys-fn-db-backup-file-snapshots-transact-sql.md)  
  
  
  
