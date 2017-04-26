---
title: "Especificar tipo de armazenamento de arquivo usando bcp (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-bulk-import-export"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "utilitário bcp [SQL Server], tipos de armazenamento de arquivos"
  - "importação de dados, tipos de armazenamento de arquivos"
  - "formato de dados nativo [SQL Server]"
  - "tipos de armazenamento de arquivo [SQL Server]"
  - "formatos de dados [SQL Server], tipos de armazenamento de arquivos"
ms.assetid: 85e12df8-1be7-4bdc-aea9-05aade085c06
caps.latest.revision: 31
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 31
---
# Especificar tipo de armazenamento de arquivo usando bcp (SQL Server)
  O *tipo de armazenamento de arquivo* descreve como são armazenados os dados no arquivo de dados. Dados podem ser exportados para um arquivo de dados como seu tipo de tabela de banco de dados (formato nativo), em sua representação de caractere (formato de caractere) ou como qualquer tipo de dados em que há suporte para conversão implícita; por exemplo, copiando um **smallint** como um **int**. Os tipos de dados definidos pelo usuário como tipos básicos são exportados.  
  
## Solicitação de bcp para o tipo de armazenamento de arquivo  
 Se um comando **bcp** interativo contiver a opção **in** ou **out** sem a opção do arquivo de formatos (**-f**) ou uma opção do formato de dados (**-n**, **-c**, **-w** ou **-N**), o comando solicitará o tipo de armazenamento de arquivos de cada campo de dados, da seguinte maneira:  
  
 `Enter the file storage type of field <field_name> [<default>]:`  
  
 Sua resposta para esta solicitação depende da tarefa que você executa, como segue:  
  
-   Para exportar dados em massa de uma instância do [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para um arquivo de dados no armazenamento mais compacto possível (formato de dados nativo), aceite os tipos de armazenamento de arquivos padrão fornecidos pelo **bcp**. Para obter uma lista de tipos de armazenamento de arquivos nativos, digite "Tipos de Armazenamento de Arquivos Nativos", mais adiante neste tópico.  
  
-   Para agrupar dados exportados de uma instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para um arquivo de dados no formato de caractere, especifique **char** como o tipo de armazenamento de arquivo para todas as colunas na tabela.  
  
-   Para agrupar dados importados para uma instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de um arquivo de dados, especifique o tipo de armazenamento de arquivo como **char** para tipos armazenados no formato de caractere; e para dados armazenados no formato de tipo de dados nativo, especifique um dos tipos de armazenamento de arquivo como apropriado:  
  
    |Tipo de armazenamento de arquivo|Digite no prompt de comando|  
    |-----------------------|-----------------------------|  
    |**char***|**c**[**har**]|  
    |**varchar**|**c[har]**|  
    |**nchar**|**w**|  
    |**nvarchar**|**w**|  
    |**text***\*|**T**[**ext**]|  
    |**ntext2**|**L**|  
    |**binary**|**x**|  
    |**varbinary**|**x**|  
    |**image***\*|**I**[**mage**]|  
    |**datetime**|**d[ate]**|  
    |**smalldatetime**|**D**|  
    |**time**|**te**|  
    |**date**|**de**|  
    |**datetime2**|**d2**|  
    |**datetimeoffset**|**do**|  
    |**decimal**|**n**|  
    |**numeric**|**n**|  
    |**float**|**f[loat]**|  
    |**real**|**r**|  
    |**Int**|**i[nt]**|  
    |**bigint**|**B[igint]**|  
    |**smallint**|**s[mallint]**|  
    |**tinyint**|**t[inyint]**|  
    |**money**|**m[oney]**|  
    |**smallmoney**|**M**|  
    |**bit**|**b[it]**|  
    |**uniqueidentifier**|**u**|  
    |**sql_variant**|**V[ariant]**|  
    |**timestamp**|**x**|  
    |UDT **um tipo de dados definido pelo usuário**|**U**|  
    |**XML**|**X**|  
  
     \*A interação do tamanho do campo, do tamanho do prefixo e dos terminadores determina a quantidade de espaço de armazenamento alocado em um arquivo de dados para dados que não são de caractere que é exportada como o tipo de armazenamento de arquivos **char**.  
  
     \*\* Os tipos de dados **ntext**, **text** e **image** serão removidos em uma versão futura do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. No novo projeto de desenvolvimento, evite usar esses tipos de dados e planeje modificar os aplicativos que atualmente os utilizam. Em vez disso, use **nvarchar(max)**, **varchar(max)** e **varbinary(max)**.  
  
## Tipos de armazenamento de arquivos nativos  
 Cada tipo de armazenamento de arquivo nativo é registrado no arquivo de formato como um tipo de dados do arquivo host correspondente.  
  
|Tipo de armazenamento de arquivo|Tipo de dados do arquivo host|  
|-----------------------|-------------------------|  
|**char***|SQLCHAR|  
|**varchar**|SQLCHAR|  
|**nchar**|SQLNCHAR|  
|**nvarchar**|SQLNCHAR|  
|**text***\*|SQLCHAR|  
|**ntext***\*|SQLNCHAR|  
|**binary**|SQLBINARY|  
|**varbinary**|SQLBINARY|  
|**image***\*|SQLBINARY|  
|**datetime**|SQLDATETIME|  
|**smalldatetime**|SQLDATETIM4|  
|**decimal**|SQLDECIMAL|  
|**numeric**|SQLNUMERIC|  
|**float**|SQLFLT8|  
|**real**|SQLFLT4|  
|**int**|SQLINT|  
|**bigint**|SQLBIGINT|  
|**smallint**|SQLSMALLINT|  
|**tinyint**|SQLTINYINT|  
|**money**|SQLMONEY|  
|**smallmoney**|SQLMONEY4|  
|**bit**|SQLBIT|  
|**uniqueidentifier**|SQLUNIQUEID|  
|**sql_variant**|SQLVARIANT|  
|**timestamp**|SQLBINARY|  
|UDT (um tipo de dados definido pelo usuário)|SQLUDT|  
  
 \*Arquivos de dados armazenados no formato de caractere usam **char** como o tipo de armazenamento de arquivos. Então, para arquivos de dados de caractere, SQLCHAR é o único tipo de dados que aparece em um arquivo de formato.  
  
 \*\*Não é possível importar dados em massa para as colunas **text**, **ntext**, e **image** que têm valores PADRÃO.  
  
## Considerações adicionais para tipos de armazenamento de arquivo  
 Quando você agrupa dados exportados de uma instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para um arquivo de dados:  
  
-   Você sempre pode especificar **char** como o tipo de armazenamento de arquivo.  
  
-   Se você inserir um tipo de armazenamento de arquivo que represente uma conversão implícita inválida, **bcp** falhará; por exemplo, embora você possa especificar **int** para dados **smallint** , se você especificar **smallint** para dados **int** , isso resultará em erros de estouro.  
  
-   Quando tipos de dados que não são de caractere, como **float**, **money**, **datetime** ou **int**, são armazenados como seus tipos de bancos de dados, os dados são gravados para o arquivo de dados no formato nativo do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    > [!NOTE]  
    >  Depois que você especificar interativamente todos os campos em um comando **bcp**, o comando solicitará que salve suas respostas para cada campo em um arquivo de formato não XML. Para obter mais informações sobre arquivos de formato não XML, veja [Arquivos de formato não XML &#40;SQL Server&#41;](../../relational-databases/import-export/non-xml-format-files-sql-server.md).  
  
## Consulte também  
 [Utilitário bcp](../../tools/bcp-utility.md)   
 [Tipos de dados &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Especificar tamanho do campo usando bcp &#40;SQL Server&#41;](../../relational-databases/import-export/specify-field-length-by-using-bcp-sql-server.md)   
 [Especificar terminadores de campo e linha &#40;SQL Server&#41;](../../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md)   
 [Especificar o tamanho de prefixo em arquivos de dados usando bcp &#40;SQL Server&#41;](../../relational-databases/import-export/specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)  
  
  