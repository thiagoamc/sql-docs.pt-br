---
title: "Colocar arquivos de dados e de log em unidades separadas | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Práticas recomendadas [Mecanismo de Banco de Dados]"
ms.assetid: 6cbedc27-4d77-44ad-bed2-c23b628475a7
caps.latest.revision: 9
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 9
---
# Colocar arquivos de dados e de log em unidades separadas
  Esta regra verifica se os arquivos de dados e de log são colocados em unidades lógicas separadas. Colocar arquivos de dados E de log no mesmo dispositivo pode causar contenção para esse dispositivo e resultar em um baixo desempenho. Colocar os arquivos em unidades separadas permite que a atividade de E/S ocorra ao mesmo tempo para os arquivos de dados e de log.  
  
## Recomendações  
 Ao criar um novo banco de dados novo, especifique unidades separadas para os dados e o log. Para mover os arquivos depois que o banco de dados é criado, o banco de dados deve ser usado offline. Mova os arquivos usando um dos seguintes métodos:  
  
> [!NOTE]  
>  Essa política não pode detectar dispositivos físicos separados por pontos de montagem  
  
-   Restaure o banco de dados do backup usando a instrução RESTORE DATABASE com a opção WITH MOVE.  
  
-   Desanexe e, em seguida, anexe o banco de dados especificando locais separados para os dispositivos de dados e de log.  
  
-   Especifique um novo local executando a instrução ALTER DATABASE com a opção MODIFY FILE e, em seguida, reinicie a instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## Para obter mais informações  
 [Mover arquivos de banco de dados](../../relational-databases/databases/move-database-files.md)  
  
 [Mover bancos de dados de usuário](../../relational-databases/databases/move-user-databases.md)  
  
 [Anexar e desanexar bancos de dados &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)  
  
## Consulte também  
 [Monitorar e impor práticas recomendadas usando o Gerenciamento Baseado em Políticas](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  