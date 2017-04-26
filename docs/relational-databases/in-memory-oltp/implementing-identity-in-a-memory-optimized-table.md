---
title: "Implementando IDENTITY em uma tabela otimizada em mem&#243;ria | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine-imoltp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c0a704a3-3a31-4c2c-b967-addacda62ef8
caps.latest.revision: 11
author: "MightyPen"
ms.author: "genemi"
manager: "jhubbard"
caps.handback.revision: 11
---
# Implementando IDENTITY em uma tabela otimizada em mem&#243;ria
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

Há suporte para IDENTITY em uma tabela com otimização de memória, desde que a semente e o incremento sejam 1 (padrão). Não há suporte em tabelas com otimização de memória para colunas de identidade com definição de IDENTITY(x, y), em que x != 1 ou y != 1.   
    
Para aumentar a semente de IDENTITY, insira uma nova linha com um valor explícito para a coluna de identidade, usando a opção de sessão `SET IDENTITY_INSERT table_name ON`. Com a inserção da linha, a semente de IDENTITY é alterada para o valor inserido explicitamente, mais 1. Por exemplo, para aumentar a semente para 1.000, insira uma linha com valor 999 na coluna de identidade. Os valores de identidade gerados serão iniciados em 1.000.     
  
## Consulte também  
 [Migrando para OLTP na memória](../../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)  
  
  