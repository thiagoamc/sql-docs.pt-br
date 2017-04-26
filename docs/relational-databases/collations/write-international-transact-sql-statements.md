---
title: "Gravar instru&#231;&#245;es Transact-SQL internacionais | Microsoft Docs"
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
  - "gravando instruções internacionais"
  - "considerações internacionais da Transact-SQL"
  - "considerações internacionais [SQL Server], Transact-SQL"
  - "considerações internacionais sobre o Mecanismo de Banco de Dados [SQL Server], Transact-SQL"
  - "instruções [SQL Server], internacionais"
  - "considerações internacionais sobre o banco de dados [SQL Server], Transact-SQL"
  - "datas [SQL Server], considerações internacionais"
ms.assetid: f0b10fee-27f7-45fe-aece-ccc3f63bdcdb
caps.latest.revision: 35
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 35
---
# Gravar instru&#231;&#245;es Transact-SQL internacionais
  Os bancos de dados e aplicativos de bancos de dados que usam instruções [!INCLUDE[tsql](../../includes/tsql-md.md)] serão mais portáteis de um idioma para outro, ou darão suporte a vários idiomas, se as diretrizes a seguir forem cumpridas.  
  
-   Substitua todos os usos dos tipos de dados **char**, **varchar** e **text** por **nchar**, **nvarchar** e **nvarchar(max)**. Fazendo isto, você não deve considerar assuntos relacionados à conversão de página de código. Para obter mais informações, consulte [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).  
  
-   Ao executar comparações e operações de mês e dia da semana, use as partes de data numérica em vez de cadeias de caracteres de nomes. Configurações de linguagem diferentes retornam nomes diferentes para os meses e dias de semana. Por exemplo, DATENAME(MONTH,GETDATE()) retorna May quando o idioma está definido como inglês dos EUA, retorna Mai quando o idioma é definido como alemão e retorna mai quando o idioma é definido como francês. No lugar, use uma função como DATEPART que usa o número do mês ao invés do nome. Use os nomes DATEPART quando for construir conjuntos de resultados a serem exibidos a um usuário, pois os nomes de datas geralmente são mais significativos que uma representação numérica. Porém, não codifique qualquer lógica que dependa dos nomes exibidos sendo modificados em um idioma específico.  
  
-   Quando especificar datas em comparações ou para entradas nas instruções INSERT ou UPDATE, use as constantes que são interpretadas da mesma maneira de todas as definições de linguagem:  
  
    -   Os aplicativos ODBC, ADO e OLE DB devem usar as cláusulas de fuga ODBC timestamp, data e hora para:  
  
         **{ ts'**yyyy**-***mm***-***dd**hh***:***mm***:***ss*[**.***fff*] **'}** como: **{ ts'**1998**-**09**-**24 10**:**02**:**20**' }**  
  
         **{ d'** *yyyy* **-** *mm* **-** *dd* **'}** como: **{ d'**1998**-**09**-**24**'}**  
  
         **{ t'** *hh* **:** *mm* **:** *ss* **'}** como: **{ t'**10:02:20**'}**  
  
    -   Os aplicativos que usam outras APIs ou scripts [!INCLUDE[tsql](../../includes/tsql-md.md)], procedimentos armazenados e gatilhos, devem usar as sequências numéricas de não separadas. Por exemplo, *yyyymmdd* como 19980924.  
  
    -   Os aplicativos que usam outras APIs, ou scripts [!INCLUDE[tsql](../../includes/tsql-md.md)], procedimentos armazenados e gatilhos, devem usar a instrução CONVERT com um parâmetro de estilo explícito para todas as conversões entre os tipos de dados **time**, **date**, **smalldate**, **datetime**, **datetime2** e **datetimeoffset** e os tipos de dados da cadeia de caracteres. Por exemplo, a instrução a seguir é interpretada da mesma maneira para todas configurações de conexão de formato de data ou de linguagem:  
  
        ```  
        SELECT *  
        FROM AdventureWorks2012.Sales.SalesOrderHeader  
        WHERE OrderDate = CONVERT(DATETIME, '20060719', 101)  
        ```  
  
         Para obter mais informações, veja [CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md).  
  
  