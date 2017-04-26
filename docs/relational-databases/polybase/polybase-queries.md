---
title: "Consultas do PolyBase | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine-polybase"
ms.tgt_pltfrm: ""
ms.topic: "article"
keywords: 
  - "PolyBase"
helpviewer_keywords: 
  - "PolyBase, importação e exportação"
  - "Hadoop, importar com PolyBase"
  - "Hadoop, exportar com PolyBase"
  - "Armazenamento de blobs do Azure, importar com PolyBase"
  - "Armazenamento de blobs do Azure, exportar com PolyBase"
ms.assetid: 2c5aa2bd-af7d-4f57-9a28-9673c2a4c07e
caps.latest.revision: 18
author: "barbkess"
ms.author: "barbkess"
manager: "jhubbard"
caps.handback.revision: 17
---
# Consultas do PolyBase
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Aqui estão as consultas de exemplo usando o recurso [Guia do PolyBase](../../relational-databases/polybase/polybase-guide.md) do SQL Server 2016. Antes de usar esses exemplos, você também deve entender as instruções T-SQL necessárias para configurar o PolyBase (consulte [PolyBase T-SQL objects](../../relational-databases/polybase/polybase-t-sql-objects.md) (Objetos T-SQL do PolyBase).)  
  
## Consultas  
 Execute instruções Transact-SQL em tabelas externas ou use as ferramentas de BI para consultar tabelas externas.  
  
## SELECT da tabela externa  
 Uma consulta simples que retorna dados de uma tabela externa definida.  
  
```tsql  
SELECT TOP 10 * FROM [dbo].[SensorData];   
```  
  
 Uma consulta simples que inclui um predicado.  
  
```  
SELECT * FROM [dbo].[SensorData]   
WHERE Speed > 65;   
```  
  
## JOIN de tabelas externas com tabelas locais  
  
```  
SELECT InsuranceCustomers.FirstName,   
                           InsuranceCustomers.LastName,   
                           SensorData.Speed  
FROM InsuranceCustomers INNER JOIN SensorData    
ON InsuranceCustomers.CustomerKey = SensorData.CustomerKey   
WHERE SensorData.Speed > 65   
ORDER BY SensorData.Speed DESC  
  
```  
  
## Computação de aplicação para Hadoop  
 Variações de aplicação são mostradas aqui.  
  
### Aplicação para selecionar um subconjunto de linhas  
 Use aplicação de predicado para melhorar o desempenho de uma consulta que seleciona um subconjunto de linhas de uma tabela externa.  
  
 Aqui o SQL Server 2016 inicia um trabalho de map-reduce para recuperar as linhas que correspondem ao predicado customer.account_balance < 200000 no Hadoop. Uma vez que a consulta pode ser concluída com êxito sem examinar todas as linhas na tabela, somente as linhas que atendem aos critérios de predicado são copiadas para o SQL Server. Isso economiza bastante tempo e exige menos espaço de armazenamento temporário quando o número de saldos do cliente \< 200000 é pequeno em comparação com o número de clientes com saldos o cliente >= 200000.  
  Copie o código de imageCopy   
SELECT * FROM customer WHERE customer.account_balance < 200000.  
  
```  
SELECT * FROM SensorData WHERE Speed > 65;  
```  
  
### Aplicação para selecionar um subconjunto de colunas  
 Use aplicação de predicado para melhorar o desempenho de uma consulta que seleciona um subconjunto de colunas de uma tabela externa.  
  
 Nesta consulta, o SQL Server inicia um trabalho map-reduce para pré-processar o arquivo de texto delimitado por Hadoop para que somente os dados de duas colunas, customer.name e customer.zip_code, serão copiados para o SQL Server PDW.  
  
```  
SELECT customer.name, customer.zip_code FROM customer WHERE customer.account_balance < 200000  
  
```  
  
### Aplicação de operadores e expressões básicas  
 O SQL Server permite os seguintes operadores e expressões básicas para a aplicação de predicado.  
  
-   Operadores de comparação binária ( \<, >, =, !=, <>, >=, <= ) para valores de hora, data e numéricos.  
  
-   Operadores aritméticos ( +, -, *, /, % ).  
  
-   Operadores lógicos (AND, OR).  
  
-   Operadores unários (NOT, IS NULL, IS NOT NULL).  
  
 Os operadores BETWEEN, NOT, IN e LIKE podem ser propagados. Isso depende de como o otimizador de consulta os reescreve como uma série de instruções que usam operadores relacionais básicos.  
  
 Esta consulta tem vários predicados que podem ser propagados para o Hadoop. O SQL Server pode enviar por push trabalhos map-reduce para o Hadoop para executar o predicado customer.account_balance <= 200000. A expressão BETWEEN 92656 e 92677 é composta por operações binárias e lógicas que podem ser enviadas por push para Hadoop. O AND lógico de customer.account_balance e customer.zipcode é uma expressão final.  
  
 Reunindo todos esses elementos, os trabalhos map-reduce podem executar tudo da cláusula WHERE. Apenas os dados que atendem aos critérios de SELECT serão copiados para o SQL Server PDW.  
  
```  
SELECT * FROM customer WHERE customer.account_balance <= 200000 AND customer.zipcode BETWEEN 92656 AND 92677  
  
```  
  
### Forçar aplicação  
  
```  
SELECT * FROM [dbo].[SensorData]   
WHERE Speed > 65  
OPTION (FORCE EXTERNALPUSHDOWN);   
```  
  
### Desabilitar aplicação  
  
```  
SELECT * FROM [dbo].[SensorData]   
WHERE Speed > 65  
OPTION (DISABLE EXTERNALPUSHDOWN);  
```  
  
## Importar dados  
 Importe dados do Hadoop ou armazenamento do Azure para SQL Server, para armazenamento persistente. Use SELECT INTO para importar dados referenciados por uma tabela externa para armazenamento persistente no SQL Server. Crie uma tabela relacional rapidamente e, em seguida, crie um índice de repositório de coluna sobre a tabela em uma segunda etapa.  
  
```sql  
-- PolyBase Scenario 2: Import external data into SQL Server.  
-- Import data for fast drivers into SQL Server to do more in-depth analysis and  
-- leverage Columnstore technology.  
  
SELECT DISTINCT   
        Insured_Customers.FirstName, Insured_Customers.LastName,   
        Insured_Customers.YearlyIncome, Insured_Customers.MaritalStatus  
INTO Fast_Customers from Insured_Customers INNER JOIN   
(  
        SELECT * FROM CarSensor_Data where Speed > 35   
) AS SensorD  
ON Insured_Customers.CustomerKey = SensorD.CustomerKey  
ORDER BY YearlyIncome  
  
CREATE CLUSTERED COLUMNSTORE INDEX CCI_FastCustomers ON Fast_Customers;  
```  
  
## Exportar dados  
Exporte dados do SQL Server para o Hadoop ou armazenamento do Azure. Primeiro, habilite a funcionalidade de exportação definindo o valor sp_configure 'permitir exportação de polybase' para 1. Em seguida, crie uma tabela externa que aponta para o diretório de destino. Em seguida, use INSERT INTO para exportar dados de uma tabela do SQL Server local para uma fonte de dados externa. A instrução INSERT INTO criará o diretório de destino se ele não existir e os resultados da instrução SELECT serão exportados para o local especificado no formato de arquivo especificado. Os arquivos externos são nomeados *QueryID_date_time_ID.format*, em que *ID* é um identificador incremental e *formato* é o formato de dados exportados. Por exemplo, QID776_20160130_182739_0.orc.  
  
```sql  
-- PolyBase Scenario 3: Export data from SQL Server to Hadoop.  
-- Create an external table.   
CREATE EXTERNAL TABLE [dbo].[FastCustomers2009] (  
        [FirstName] char(25) NOT NULL,   
        [LastName] char(25) NOT NULL,   
        [YearlyIncome] float NULL,   
        [MaritalStatus] char(1) NOT NULL  
)  
WITH (  
        LOCATION='/old_data/2009/customerdata',  
        DATA_SOURCE = HadoopHDP2,  
        FILE_FORMAT = TextFileFormat,  
        REJECT_TYPE = VALUE,  
        REJECT_VALUE = 0  
);  
  
-- Export data: Move old data to Hadoop while keeping it query-able via an external table.  
INSERT INTO dbo.FastCustomer2009  
SELECT T.* FROM Insured_Customers T1 JOIN CarSensor_Data T2  
ON (T1.CustomerKey = T2.CustomerKey)  
WHERE T2.YearMeasured = 2009 and T2.Speed > 40;  
```  
  
## Novas exibições do catálogo  
 As novas exibições do catálogo a seguir mostram os recursos externos.  
  
```sql  
SELECT * FROM sys.external_data_sources;   
SELECT * FROM sys.external_file_formats;  
SELECT * FROM sys.external_tables;  
```  
  
 Determine se uma tabela é uma tabela externa usando `is_external`  
  
```sql  
SELECT name, type, is_external FROM sys.tables WHERE name='myTableName'   
```  
  
## Próximas etapas  
 Para saber mais sobre como solucionar problemas, consulte [PolyBase troubleshooting](../../relational-databases/polybase/polybase-troubleshooting.md) (Solução de problemas do PolyBase).  
  
  