---
title: "Importar dados de formato de caractere e nativo de vers&#245;es anteriores do SQL Server | Microsoft Docs"
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
  - "versões anteriores [SQL Server], importar e exportar formatos de dados"
  - "opção -V"
  - "formatos de dados [SQL Server], versões anteriores"
  - "versões anteriores [SQL Server], importar e exportar formatos de dados"
ms.assetid: e644696f-9017-428e-a5b3-d445d1c630b3
caps.latest.revision: 40
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 40
---
# Importar dados de formato de caractere e nativo de vers&#245;es anteriores do SQL Server
  No [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], você pode usar o **bcp** para importar dados de formato de caractere e nativo do [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] ou [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] usando a opção **-V**. A opção **-V** faz com que o [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] use tipos de dados da versão anterior especificada do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e o formato de arquivo de dados é igual ao formato da versão anterior.  
  
 Para especificar uma versão anterior do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para um arquivo de dados, use a opção **-V** com os seguintes qualificadores:  
  
|Versão do SQL Server|Qualificador|  
|------------------------|---------------|  
|[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]|**-V80**|  
|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|**-V90**|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|**-V100**|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|**-V 110**|  
  
## Interpretação de tipos de dados  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versões posteriores oferecem suporte para alguns novos tipos. Para importar um novo tipo de dados para uma versão anterior do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , o tipo de dados deve ser armazenado em um formato legível pelos clientes **bcp** antigos. A tabela a seguir resume como os novos tipos de dados são convertidos para compatibilidade com versões anteriores do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Novos tipos de dados no SQL Server 2005|Tipos de dados compatíveis na versão 6*x*|Tipos de dados compatíveis na versão 70|Tipos de dados compatíveis na versão 80|  
|---------------------------------------|-------------------------------------------|-----------------------------------------|-----------------------------------------|  
|**bigint**|**decimal**|**decimal**|*|  
|**sql_variant**|**text**|**nvarchar(4000)**|*|  
|**varchar(max)**|**text**|**text**|**text**|  
|**nvarchar(max)**|**ntext**|**ntext**|**ntext**|  
|**varbinary(max)**|**image**|**image**|**image**|  
|XML|**ntext**|**ntext**|**ntext**|  
|UDT**|**image**|**image**|**image**|  
  
 *Esse tipo tem suporte nativo.  
  
 **UDT indica um tipo definido pelo usuário.  
  
## Exportar usando – V 80  
 Quando você exporta dados em massa usando a opção **–V80**, **nvarchar(max)**, **varchar(max)**, **varbinary(max)**, XML e dados UDT no modo nativo são armazenados com um prefixo de 4 bytes, como dados **text**, **image** e **ntext**, em vez de um prefixo de 8 bytes que é o padrão para o [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versões posteriores.  
  
## Copiando valores de dados  
 O**bcp** usa a API de cópia em massa do ODBC. Portanto, para importar valores de data para o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], o **bcp** usa o formato de data do ODBC (*yyyy-mm-dd hh:mm:ss*[*.f...*]).  
  
 O comando **bcp** exporta arquivos de dados de formato de caractere usando o formato padrão ODBC para os valores **datetime** e **smalldatetime** . Por exemplo, uma coluna **datetime** que contém a data `12 Aug 1998` é copiada em massa em um arquivo de dados como a cadeia de caracteres `1998-08-12 00:00:00.000`.  
  
> [!IMPORTANT]  
>  Ao importar dados em um campo **smalldatetime** com o **bcp**, verifique se o valor por segundo é 00.000; caso contrário, a operação falhará. O tipo de dados **smalldatetime** só mantém valores do minuto mais próximo. BULK INSERT e INSERT ... SELECT * FROM OPENROWSET(BULK...) não falharão nesta instância, mas truncarão o valor de segundos.  
  
##  <a name="RelatedTasks"></a> Tarefas relacionadas  
 **Para usar formatos de dados para importação ou exportação em massa**  
  
-   [Usar o formato de caractere para importar ou exportar dados &#40;SQL Server&#41;](../../relational-databases/import-export/use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Usar o formato nativo para importar ou exportar dados &#40;SQL Server&#41;](../../relational-databases/import-export/use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Usar o formato de caractere Unicode para importar ou exportar dados &#40;SQL Server&#41;](../../relational-databases/import-export/use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Usar o formato nativo Unicode para importar ou exportar dados &#40;SQL Server&#41;](../../relational-databases/import-export/use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
## Consulte também  
 [Utilitário bcp](../../tools/bcp-utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/bulk-insert-transact-sql.md)   
 [OPENROWSET &#40;Transact-SQL&#41;](../../t-sql/functions/openrowset-transact-sql.md)   
 [Tipos de dados &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Compatibilidade com versões anteriores do Mecanismo de Banco de Dados do SQL Server](../../database-engine/sql-server-database-engine-backward-compatibility.md)   
 [CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
  
  