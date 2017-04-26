---
title: "Planejar a ado&#231;&#227;o de recursos de OLTP in-memory no SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "10/05/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine-imoltp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 041b428f-781d-4628-9f34-4d697894e61e
caps.latest.revision: 4
author: "MightyPen"
ms.author: "genemi"
manager: "jhubbard"
caps.handback.revision: 3
---
# Planejar a ado&#231;&#227;o de recursos de OLTP in-memory no SQL Server
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]


Este artigo descreve as formas como a adoção de recursos in-memory afeta outros aspectos do seu sistema empresarial.



## A. Adoção de recursos do OLTP in-memory


As subseções a seguir discutem fatores que você deve considerar ao planejar adotar e implementar recursos in-memory. Muitas informações explicativas estão disponíveis em:

- [Usar o OLTP in-memory para melhorar o desempenho do aplicativo no Banco de Dados SQL do Azure](https://azure.microsoft.com/documentation/articles/sql-database-in-memory-oltp-migration/)



### A.1 Pré-requisitos

Um pré-requisito para usar os recursos in-memory pode envolver a edição ou a camada de serviço do produto SQL. Para esse e outros pré-requisitos, consulte:

- [Requisitos para usar tabelas com otimização de memória](../../relational-databases/in-memory-oltp/requirements-for-using-memory-optimized-tables.md)
    - [Edições e componentes do SQL Server 2016](../../sql-server/editions-and-components-of-sql-server-2016.md)
    - [Recomendações de tipo de preço do Banco de Dados SQL](https://azure.microsoft.com/documentation/articles/sql-database-service-tier-advisor/)


### A. 2 Prever a quantidade de memória ativa

O sistema tem memória ativa suficiente para dar suporte a uma nova tabela com otimização de memória?

#### Microsoft SQL Server

Uma tabela com otimização de memória que contém 200 GB de dados requer mais de 200 GB de memória ativa dedicados a seu suporte. Antes de implementar uma tabela com otimização de memória que contém uma grande quantidade de dados, você precisa prever a quantidade de memória ativa adicional que talvez seja necessário adicionar ao computador servidor. Para obter diretrizes para fazer uma estimativa, consulte:

- [Estimar requisitos de memória para tabelas com otimização de memória](../../relational-databases/in-memory-oltp/estimate-memory-requirements-for-memory-optimized-tables.md)

#### Banco de dados SQL do Azure

Para um banco de dados hospedado no serviço de nuvem do Banco de Dados SQL do Azure, a camada de serviço escolhida afeta a quantidade de memória ativa que o banco de dados pode consumir. Você deve se planejar para monitorar o uso de memória do banco de dados usando um alerta. Para obter detalhes, confira:

- [Monitorar o armazenamento no OLTP in-memory](https://azure.microsoft.com/documentation/articles/sql-database-in-memory-oltp-monitoring/)

#### Variáveis de tabela com otimização de memória

Uma variável de tabela declarada como com otimização de memória às vezes é preferível a uma #TempTable tradicional que reside no banco de dados **tempdb**. Essas variáveis de tabela podem fornecer ganhos de desempenho significativos sem usar uma quantidade significativa de memória ativa.

### A.3 A tabela deve estar offline para ser convertida para uma tabela com otimização de memória

Algumas funcionalidades de ALTER TABLE estão disponíveis para tabelas com otimização de memória. Mas você não pode emitir uma instrução ALTER TABLE para converter uma tabela baseada em disco em uma tabela com otimização de memória. Em vez disso, você deve usar um conjunto de etapas mais manuais. A seguir, temos várias maneiras de converter a tabela baseada em disco em uma tabela com otimização de memória.

#### Script manual

Uma maneira de converter a tabela baseada em disco em uma tabela com otimização de memória é codificar você mesmo as etapas necessárias de Transact-SQL.


1. Suspenda a atividade do aplicativo.

2. Faça um backup completo.

3. Renomeie a tabela baseada em disco.

4. Emita uma instrução CREATE TABLE para criar a nova tabela com otimização de memória.

5. INSIRA na tabela com otimização de memória com uma SUBSELEÇÃO da tabela baseada em disco.

6. DESCARTE a tabela baseada em disco.

7. Faça outro backup completo.

8. Retome a atividade do aplicativo.


#### Orientador de otimização da memória

A ferramenta Orientador de Otimização de Memória pode gerar um script para ajudar a implementar a conversão de uma tabela baseada em disco para uma tabela com otimização de memória. A ferramenta é instalada como parte do SSDT (SQL Server Data Tools).

- [Orientador de otimização da memória](../../relational-databases/in-memory-oltp/memory-optimization-advisor.md)
- [Baixar o SQL Server Data Tools (SSDT)](https://msdn.microsoft.com/library/mt204009.aspx)


#### Arquivo .dacpac

Você pode atualizar seu banco de dados localmente usando um arquivo. dacpac, gerenciado pelo SSDT. No SSDT, você pode especificar alterações no esquema codificado no arquivo .dacpac.

Você trabalha com arquivos .dacpac no contexto de um projeto do Visual Studio do tipo *Banco de Dados*.

- [Aplicativos da camada de dados](../../relational-databases/data-tier-applications/data-tier-applications.md) e arquivos .dacpac



### A.4 Diretrizes sobre a adequação dos recursos de OLTP in-memory para seu aplicativo

Para obter diretrizes sobre se os recursos in-memory podem melhorar o desempenho de seu aplicativo específico, consulte:

- [OLTP na memória (otimização na memória)](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)



## B. Recursos sem suporte

Recursos que não têm suporte em determinados cenários in-memory são descritos em:

- [Recursos do SQL Server sem suporte para OLTP na Memória](../../relational-databases/in-memory-oltp/unsupported-sql-server-features-for-in-memory-oltp.md)


As subseções a seguir destacam alguns dos mais importantes recursos sem suporte.


### B.1 INSTANTÂNEO de um banco de dados

Após a primeira vez em que qualquer tabela ou módulo com otimização de memória é criado em um banco de dados, nenhum [INSTANTÂNEO](../../relational-databases/databases/database-snapshots-sql-server.md) do banco de dados pode ser feito. O motivo específico é que:

- o primeiro item com otimização de memória torna impossível remover o último arquivo do GRUPO DE ARQUIVOS com otimização de memória; e
- Nenhum banco de dados que tenha um arquivo em um GRUPO DE ARQUIVOS com otimização de memória pode dar suporte a um INSTANTÂNEO.

Normalmente, um INSTANTÂNEO pode ser útil para iterações de testes rápidas.


### B.2 Consultas entre bancos de dados

Tabelas com otimização de memória não dão suporte a transações [entre bancos de dados](../../relational-databases/in-memory-oltp/cross-database-queries.md). Você não pode acessar outro banco de dados da mesma transação ou na mesma consulta que também acesse uma tabela com otimização de memória.

Variáveis de tabela não são transacionais. Portanto, [variáveis de tabela com otimização de memória](../../relational-databases/in-memory-oltp/faster-temp-table-and-table-variable-by-using-memory-optimization.md) podem ser usadas em consultas entre bancos de dados.


### B.3 Dica de tabela READPAST

Nenhuma consulta pode aplicar a [dica de tabela](Table%20Hints%20%28Transact-SQL%29.md) READPAST a qualquer tabela com otimização de memória.

A dica READPAST é útil em cenários em que várias sessões estão acessando e modificando o mesmo conjunto pequeno de linhas, como ao processar uma fila.


### B.4 RowVersion, sequência

- Nenhuma coluna pode ser marcada para [RowVersion](../../t-sql/data-types/rowversion-transact-sql.md) em uma tabela com otimização de memória.


- Um objeto [SEQUENCE](../../t-sql/statements/create-sequence-transact-sql.md) não pode ser usado com nenhuma tabela com otimização de memória.


## C. Manutenção administrativa


Esta seção descreve diferenças na administração de bancos de dados em que tabelas com otimização de memória são usadas.


### C. 1 Redefinição de semente de identidade, incremento > 1

[DBCC CHECKIDENT](../../t-sql/database-console-commands/dbcc-checkident-transact-sql.md), para propagar uma coluna IDENTITY, não pode ser usado em uma tabela com otimização de memória.

O valor do incremento é restrito a exatamente 1 para uma coluna IDENTITY em uma tabela com otimização de memória.


### C. 2 DBCC CHECKDB não pode validar tabelas com otimização de memória

O comando [DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) não faz nada quando o destino é uma tabela com otimização de memória. As seguintes etapas são uma solução alternativa:


1. [Fazer backup do log de transações](Back%20Up%20a%20Transaction%20Log%20%28SQL Server%29.md).

2. Faça backup dos arquivos no GRUPO DE ARQUIVOS com otimização de memória para um dispositivo nulo. O processo de backup invoca uma validação de soma de verificação.

    Se forem encontrados danos, continue com as próximas etapas.

3. Copie os dados das tabelas com otimização de memória para tabelas baseadas em disco, para armazenamento temporário.

4. Restaure os arquivos do GRUPO DE ARQUIVOS com otimização de memória.

5. INSIRA nas tabelas com otimização de memória os dados armazenados temporariamente nas tabelas baseadas em disco.

6. DESCARTE as tabelas baseadas em disco que mantinham os dados temporariamente.



## D. Desempenho

Esta seção descreve situações em que o desempenho excelente de tabelas com otimização de memória pode ficar abaixo de seu potencial completo.


### D.1 Considerações sobre índices

Todos os índices em uma tabela com otimização de memória são criados e gerenciados pelas instruções CREATE TABLE e ALTER TABLE relacionadas à tabela. Você não pode ter uma tabela com otimização de memória como alvo de uma instrução CREATE INDEX.

O índice não clusterizado de árvore B tradicional normalmente é a opção mais sensata e simples quando você implementa pela primeira vez uma tabela com otimização de memória. Posteriormente, depois de ver o desempenho do seu aplicativo, você pode considerar passar para outro tipo de índice.

Dois tipos especiais de índices precisam de discussão no contexto de uma tabela com otimização de memória: índices columnstore e índices de hash.

Para ter uma visão geral dos índices em tabelas com otimização de memória, consulte:

- [Índices para tabelas com otimização de memória](../../relational-databases/in-memory-oltp/indexes-for-memory-optimized-tables.md)


#### Índices de hash

Índices de hash podem ser a forma mais rápida de acessar uma linha específica pelo valor exato de sua chave primária usando o operador "**=**".

- Operadores inexatos como "**! =**", "**>**" ou "**BETWEEN**" prejudicariam o desempenho se usados com um índice de hash.

- Um índice de hash poderá não ser a melhor opção se a taxa de duplicação do valor da chave se tornar muito alta.

- Evite subestimar a quantidade de *buckets* de que seu índice de hash pode precisar para evitar longas cadeias dentro de buckets individuais. Para obter detalhes, confira:
    - [Índices de hash para tabelas com otimização de memória](../../relational-databases/in-memory-oltp/hash-indexes-for-memory-optimized-tables.md)


#### Índices columnstore não clusterizados

Tabelas com otimização de memória oferecem alta taxa de transferência de dados de transações comerciais típicos, no paradigma que chamamos de *transação online* ou *OLTP*. Índices de columnStore oferecem alta taxa de transferência de agregações e processamentos semelhantes que chamamos de *Análise*. No passado, a melhor abordagem disponível para atender às necessidades de OLTP e Análise era ter tabelas separadas com grande movimentação de dados e com algum grau de duplicação de dados. Hoje, uma **solução híbrida** mais simples está disponível: ter um índice de columnstore em uma tabela com otimização de memória.


- Um [índice de columnstore](Columnstore%20Indexes%20Guide.md) pode ser interno a uma tabela baseada em disco, até mesmo como o índice clusterizado. Mas, em uma tabela com otimização de memória, um índice de columnstore não pode ser clusterizado.


- Colunas de LOB ou fora da linha para uma tabela com otimização de memória impedem a criação de um índice de columnstore na tabela.


- Nenhuma instrução ALTER TABLE pode ser executada em uma tabela com otimização de memória enquanto um índice de columnstore existir na tabela.
    - A partir de agosto de 2016, a Microsoft tem planos de curto prazo para melhorar o desempenho da recriação do índice de columnstore.



### D.2 Colunas de LOB e fora de linha

Objetos grandes (LOBs) são colunas como varchar (**max**). Ter duas colunas de LOB em uma tabela com otimização de memória provavelmente não causa danos suficientes no desempenho para ter importância. Mas evite ter mais colunas de LOB do que seus dados precisam. O mesmo conselho se aplica a colunas fora de linha. Não defina uma coluna como nvarchar(3072) se varchar(512) for suficiente.


Um pouco mais sobre colunas de LOB e fora de linha está disponível em:

- [Tamanho da tabela e da linha em tabelas com otimização de memória](../../relational-databases/in-memory-oltp/table-and-row-size-in-memory-optimized-tables.md)
- [Tipos de Dados com Suporte para o OLTP na Memória](../../relational-databases/in-memory-oltp/supported-data-types-for-in-memory-oltp.md)



## E. Limitações dos procedimentos nativos


Elementos particulares do Transact-SQL não têm suporte em procedimentos armazenados compilados nativamente.

Para ver considerações sobre a migração de um script do Transact-SQL para um procedimento nativo, consulte:

- [Problemas de migração para procedimentos armazenados compilados nativamente](../../relational-databases/in-memory-oltp/migration-issues-for-natively-compiled-stored-procedures.md)


### E.1 Não há CASE em um procedimento nativo

A expressão CASE no Transact-SQL não pode ser usada dentro de um processo nativo. Você pode criar uma solução alternativa:

- [Implementando uma expressão CASE em um procedimento armazenado compilado nativamente](../../relational-databases/in-memory-oltp/implementing-a-case-expression-in-a-natively-compiled-stored-procedure.md)


### E.2 Não há MERGE em um procedimento nativo


A [instrução MERGE](../../t-sql/statements/merge-transact-sql.md) do Transact-SQL tem semelhanças com o que é frequentemente chamado de funcionalidade *upsert*. Um procedimento nativo não pode usar a instrução MERGE. No entanto, você pode obter a mesma funcionalidade de MERGE usando uma combinação de instruções SELECT e UPDATE e INSERT. Um exemplo de código está em:

- [Implementando a funcionalidade MERGE em um procedimento armazenado compilado de forma nativa](../../relational-databases/in-memory-oltp/implementing-merge-functionality-in-a-natively-compiled-stored-procedure.md)



### E.3 Não há uniões em instruções UPDATE ou DELETE em um procedimento nativo

As instruções Transact-SQL em um procedimento nativo podem acessar apenas as tabelas com otimização de memória. Nas instruções UPDATE e DELETE, não é possível unir as tabelas. Tentativas de um procedimento nativo falham com uma mensagem como a Msg12319, que explica que você:

- Não pode usar a cláusula FROM em uma instrução UPDATE.
- Não pode especificar uma origem de tabela em uma instrução DELETE.

Nenhum tipo de subconsulta fornece uma solução alternativa. No entanto, você pode usar uma variável de tabela com otimização de memória para obter um resultado de junção ao longo de várias instruções. Veja os dois códigos de exemplo:

- DELETE...JOIN... queremos executar em um procedimento nativo, mas não podemos.
- Uma solução alternativa com um conjunto de instruções Transact-SQL que realiza a junção da exclusão.


*Cenário:* a tabela TabProjectEmployee tem uma chave exclusiva de duas colunas: ProjectId e EmployeeId. Cada linha indica a atribuição de um funcionário a um projeto ativo. Quando um funcionário deixa a empresa, os funcionários devem ser excluídos da tabela TabProjectEmployee.


#### T-SQL Inválido, DELETE...JOIN


Um procedimento nativo não pode realizar DELETE... JOIN, da forma a seguir.


```tsql
DELETE pe
    FROM
             TabProjectEmployee   AS pe
        JOIN TabEmployee          AS e

            ON pe.EmployeeId = e.EmployeeId
    WHERE
            e.EmployeeStatus = 'Left-the-Company'
;
```


#### Solução alternativa válida, delete...join manual

Em seguida, temos o exemplo de código da solução alternativa, em duas partes:

1. CREATE TYPE é executado uma vez, dias antes do tipo ser usado pela primeira vez por qualquer variável de tabela real.

2. O processo empresarial usa o tipo criado. Ele começa declarando uma variável de tabela do tipo de tabela criado.


```tsql

CREATE TYPE dbo.type_TableVar_EmployeeId
    AS TABLE  
    (
        EmployeeId   bigint   NOT NULL
    );
```


Em seguida, use o tipo de tabela criado.


```tsql
DECLARE @MyTableVarMo  dbo.type_TableVar_EmployeeId  

INSERT INTO @MyTableVarMo (EmployeeId)
    SELECT
            e.EmployeeId
        FROM
                 TabProjectEmployee  AS pe
            JOIN TabEmployee         AS e  ON e.EmployeeId = pe.EmployeeId
        WHERE
            e.EmployeeStatus = 'Left-the-Company'
;

DECLARE @EmployeeId   bigint;

WHILE (1=1)
BEGIN
    SET @EmployeeId = NULL;

    SELECT TOP 1 @EmployeeId = v.EmployeeId
        FROM @MyTableVarMo  AS v;

    IF (NULL = @Employeed) BREAK;
    
    DELETE TabProjectEmployee
        WHERE EmployeeId = @EmployeeId;

    DELETE @MyTableVarMo
        WHERE EmployeeId = @EmployeeId;
END;
```


### E.4 Limitações de plano de consulta para procedimentos nativos


Alguns tipos de planos de consulta não estão disponíveis para procedimentos nativos. Muitos detalhes são abordados em:

- [Um guia para processamento de consulta de tabelas com otimização de memória](../../relational-databases/in-memory-oltp/a-guide-to-query-processing-for-memory-optimized-tables.md)


#### Não há processamento paralelo em um procedimento nativo

O processamento paralelo não pode fazer parte de nenhum plano de consulta para um procedimento nativo. Procedimentos nativos são sempre do tipo single-threaded.


#### Tipos de junção


Nem uma junção de hash nem uma junção de mesclagem podem fazer parte de qualquer plano de consulta para um procedimento nativo. Junções de loops aninhados são usadas.


#### Não há agregação de hash

Quando o plano de consulta para um processo nativo requer uma fase de agregação, somente a agregação de fluxo está disponível. Não há suporte para agregação de hash em um plano de consulta para um procedimento nativo.

- A agregação de hash é melhor quando dados de um grande número de linhas precisam ser agregados.



## F. Design de aplicativos: transações e lógica de repetição

Uma transação que envolve uma tabela com otimização de memória pode se tornar dependente de outra transação que envolve a mesma tabela. Se a contagem de transações dependentes ultrapassar o máximo permitido, todas as transações dependentes falharão.

No o SQL Server 2016:

- O máximo permitido é de 8 transações dependentes. 8 também é o limite de transações de que qualquer transação pode ser dependente.
- O número do erro é 41839. (No SQL Server 2014, o número do erro é 41301.)


Você pode tornar seus scripts do Transact-SQL mais robustos contra possíveis erros de transação adicionando a *lógica de repetição* a eles. A lógica de repetição tem mais chances de ajudar quando as chamadas UPDATE e DELETE são frequentes ou se a tabela com otimização de memória for referenciada por uma chave estrangeira em outra tabela. Para obter detalhes, confira:

- [Transações com tabelas com otimização de memória](../../relational-databases/in-memory-oltp/transactions-with-memory-optimized-tables.md)
- [Limites de dependência de transações em tabelam com otimização de memória – Erro 41839](https://blogs.msdn.microsoft.com/sqlcat/2016/07/11/transaction-dependency-limits-with-memory-optimized-tables-error-41839/)



## Links relacionados

- [OLTP na memória (otimização na memória)](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)
