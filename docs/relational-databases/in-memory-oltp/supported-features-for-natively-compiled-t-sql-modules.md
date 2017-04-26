---
title: "Recursos com suporte para m&#243;dulos T-SQL compilados nativamente | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine-imoltp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 05515013-28b5-4ccf-9a54-ae861448945b
caps.latest.revision: 44
author: "MightyPen"
ms.author: "genemi"
manager: "jhubbard"
caps.handback.revision: 44
---
# Recursos com suporte para m&#243;dulos T-SQL compilados nativamente
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]


  Este tópico contém uma lista da área da superfície do T-SQL e os recursos com suporte no corpo de módulos T-SQL compilados nativamente, como procedimentos armazenados ([CREATE PROCEDURE (Transact-SQL)](../../t-sql/statements/create-procedure-transact-sql.md)), gatilhos, funções escalares definidas pelo usuário e funções embutidas com valor de tabela.  

 Para ver os recursos com suporte na definição de módulos nativos, consulte [DDL com suporte para módulos nativamente compilados do T-SQL](../../relational-databases/in-memory-oltp/supported-ddl-for-natively-compiled-t-sql-modules.md).  

-   [Área da superfície da consulta em módulos nativos](#qsancsp)  

-   [Modificação de dados](#dml)  

-   [Linguagem de controle de fluxo](#cof)  

-   [Operadores com suporte](#so)  

-   [Funções internas em módulos compilados nativamente](#bfncsp)  

-   [Auditoria](../../relational-databases/in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md#auditing)  

-   [Dicas de tabela e de consulta](../../relational-databases/in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md#tqh)  

-   [Limitações na classificação](../../relational-databases/in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md#los)  

 Para obter informações completas sobre construções sem suporte e sobre como resolver problemas de alguns recursos sem suporte em módulos compilados nativamente, consulte [Migration Issues for Natively Compiled Stored Procedures](../../relational-databases/in-memory-oltp/migration-issues-for-natively-compiled-stored-procedures.md). Para mais informações sobre os recursos sem suporte, veja [Constructos do Transact-SQL sem suporte no OLTP in-memory](../../relational-databases/in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md).  

##  <a name="a-nameqsancspa-query-surface-area-in-native-modules"></a><a name="qsancsp"></a> Área da superfície da consulta em módulos nativos  

Há suporte para as seguintes construções de consulta:  

Cláusula SELECT:  

-   Aliases de nome e colunas (usando a sintaxe = ou então AS).  

-   Subconsultas escalares  

-   INÍCIO*  

-   SELECT DISTINCT  

              DISTINCT aggregates are not supported.  

-   UNION e UNION ALL

-   Atribuições de variável  

Cláusula FROM:  

-   FROM \<tabela com otimização de memória ou variável de tabela>  

-   FROM \<TVF embutida compilada nativamente>  

-   LEFT OUTER JOIN, RIGHT OUTER JOIN, CROSS JOIN e INNER JOIN.  

-   Subconsultas `[AS] table_alias`. Para obter mais informações, consulte [FROM &#40;Transact-SQL&#41;](../../t-sql/queries/from-transact-sql.md).  

Cláusula WHERE:  

-   Predicado de filtro IS [NOT] NULL  

-   AND, OR, NOT, IN, EXISTS, BETWEEN  


Cláusula[GROUP BY](../Topic/GROUP%20BY%20%28Transact-SQL%29.md) :

- Funções de agregação AVG, COUNT, COUNT_BIG, MIN, MAX e SUM.  

- MIN e MAX não têm suporte para os tipos nvarchar, char, varchar, varchar, varbinary e binary.  

Cláusula[ORDER BY](../Topic/ORDER%20BY%20Clause%20%28Transact-SQL%29.md) :


- Não há suporte para **DISTINCT** na cláusula **ORDER BY** .


- tem suporte com [GROUP BY &#40;Transact-SQL&#41;](../Topic/GROUP%20BY%20\(Transact-SQL\).md) se uma expressão na lista ORDER BY for exibida literalmente na lista GROUP BY.
  - Por exemplo, GROUP BY + b ORDER BY a + b tem suporte, mas GROUP BY a, b ORDER BY a + b, não.  


Cláusula HAVING:

- sujeito às mesmas limitações de expressão que a cláusula WHERE.


#### <a name="order-by-and-top-are-supported-in-natively-compiled-modules-with-some-restrictions"></a>ORDER BY e TOP têm suporte em módulos compilados nativamente, com algumas restrições


- Não há suporte para **WITH TIES** ou **PERCENT** na cláusula **TOP** .


- Não há suporte para **DISTINCT** na cláusula **ORDER BY** .  


- **TOP** combinado com **ORDER BY** não dá suporte a mais de 8.192 ao usar uma constante na cláusula **TOP** .
  - Esse limite poderá ser diminuído caso a consulta contenha junções ou funções de agregação. (Por exemplo, com uma junção (duas tabelas), o limite é 4.096 linhas. Com duas junções (três tabelas), o limite é 2.730 linhas.)  
  - Você pode obter resultados maiores que 8.192 armazenando o número de linhas em uma variável:  

```tsql
DECLARE @v INT = 9000;
SELECT TOP (@v) … FROM … ORDER BY …
```

No entanto, uma constante na cláusula **TOP** resulta em um desempenho melhor comparado a usar uma variável.  

Essas restrições em [!INCLUDE[tsql](../../includes/tsql-md.md)] compilado nativamente não se aplica ao acesso [!INCLUDE[tsql](../../includes/tsql-md.md)] interpretado em tabelas com otimização de memória.  


##  <a name="a-namedmla-data-modification"></a><a name="dml"></a> Modificação de dados  

Há suporte para as instruções DML a seguir.  

-   INSERT VALUES (uma linha por instrução) e INSERT ... SELECT  

-   UPDATE  

-   DELETE  

-   WHERE tem suporte com instruções UPDATE e DELETE.  

##  <a name="a-namecofa-control-of-flow-language"></a><a name="cof"></a> Linguagem de controle de fluxo  
 Há suporte para as construções de linguagem de controle de fluxo a seguir.  

-   [IF...ELSE &#40;Transact-SQL&#41;](../../t-sql/language-elements/if-else-transact-sql.md)  

-   [WHILE &#40;Transact-SQL&#41;](../../t-sql/language-elements/while-transact-sql.md)  

-   [RETURN &#40;Transact-SQL&#41;](../../t-sql/language-elements/return-transact-sql.md)  

-   [DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md) pode usar todos os [Tipos de dados com suporte no OLTP in-memory](../../relational-databases/in-memory-oltp/supported-data-types-for-in-memory-oltp.md), bem como os tipos de tabela com otimização de memória. É possível declarar variáveis como NULL ou NOT NULL.  

-   [SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)  

-   [TRY...CATCH &#40;Transact-SQL&#41;](../../t-sql/language-elements/try-catch-transact-sql.md)  

               To achieve optimal performance, use a single TRY/CATCH block for an entire natively compiled T-SQL module.  

-   [THROW &#40;Transact-SQL&#41;](../../t-sql/language-elements/throw-transact-sql.md)  

-   BEGIN ATOMIC (no nível externo do procedimento armazenado). Para obter mais detalhes, consulte [Atomic Blocks](../../relational-databases/in-memory-oltp/blocos-atômicos-nos-procedimentos-nativos.md).  

##  <a name="a-namesoa-supported-operators"></a><a name="so"></a> Operadores com suporte  
 Há suporte para os operadores que se seguem.  

-   [Operadores de comparação &#40;Transact-SQL&#41;](../../t-sql/language-elements/comparison-operators-transact-sql.md) (por exemplo >, \<, >= e <=)  

-   Operadores unários (+, -).  

-   Operadores binários (*, /, +, -, % (módulo)).  

               The plus operator (+) is supported on both numbers and strings.  

-   Operadores lógicos (AND, OR, NOT).  

-   Operadores bit a bit ~, &, |, e ^  

-   operador APPLY
    - **Aplica-se ao:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.  
      Do [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1 em diante, há suporte para o operador APPLY em módulos compilados nativamente.

##  <a name="a-namebfncspa-built-in-functions-in-natively-compiled-modules"></a><a name="bfncsp"></a> Funções internas em módulos compilados nativamente  
 As funções a seguir têm suporte em restrições nas tabelas com otimização de memória e em módulos T-SQL compilados nativamente.  

-   Todas as [Funções matemáticas &#40;Transact-SQL&#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)  

-   Funções de data: CURRENT_TIMESTAMP, DATEADD, DATEDIFF, DATEFROMPARTS, DATEPART, DATETIME2FROMPARTS, DATETIMEFROMPARTS, DAY, EOMONTH, GETDATE, GETUTCDATE, MONTH, SMALLDATETIMEFROMPARTS, SYSDATETIME, SYSUTCDATETIME e YEAR.  

-   Funções de cadeia de caracteres: LEN, LTRIM, RTRIM e SUBSTRING.  
    - **Aplica-se ao:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.  
      Do [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1 em diante, também há suporte para as seguintes funções internas: TRIM, TRANSLATE e CONCAT_WS.  

-   Funções de identidade: SCOPE_IDENTITY  

-   Funções NULL: ISNULL  

-   Funções Uniqueidentifier: NEWID e NEWSEQUENTIALID  

-   Funções JSON  
    - **Aplica-se ao:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.  
      Do [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1 em diante, há suporte para as funções JSON em módulos compilados nativamente.

-   Funções de erro: ERROR_LINE, ERROR_MESSAGE, ERROR_NUMBER, ERROR_PROCEDURE, ERROR_SEVERITY e ERROR_STATE  

-   Funções do sistema: @@rowcount. As instruções dentro de procedimentos armazenados compilados nativamente atualizam @@rowcount e você pode usar @@rowcount em um procedimento armazenado compilado nativamente para determinar o número de linhas afetadas pela última instrução executada nesse procedimento armazenado compilado nativamente. No entanto, @@rowcount é redefinido como 0 no início e no final da execução de um procedimento armazenado compilado nativamente.  

-   Funções de segurança: IS_MEMBER({'grupo' | 'função'}), IS_ROLEMEMBER ('função' [, 'entidade_do_banco_de_dados']), IS_SRVROLEMEMBER ('função' [, 'logon']), ORIGINAL_LOGIN(), SESSION_USER, CURRENT_USER, SUSER_ID(['logon']), SUSER_SID(['logon'] [, Param2]), SUSER_SNAME([sid_de_usuário_do_servidor]), SYSTEM_USER, SUSER_NAME, USER, USER_ID(['usuário']), USER_NAME([id]), CONTEXT_INFO().

-   Execuções de módulos nativos podem ser aninhadas.

##  <a name="a-nameauditinga-auditing"></a><a name="auditing"></a> Auditoria  
 A auditoria no nível de procedimento tem suporte em procedimentos armazenados compilados nativamente.  

 Para obter mais informações sobre a auditoria, consulte [Create a Server Audit and Database Audit Specification](../../relational-databases/security/auditing/create-a-server-audit-and-database-audit-specification.md).  

##  <a name="a-nametqha-table-and-query-hints"></a><a name="tqh"></a> Dicas de tabela e de consulta  
 Há suporte para o seguinte:  

-   As dicas INDEX, FORCESCAN e FORCESEEK, seja na sintaxe das dicas de tabela ou na [Cláusula OPTION &#40;Transact-SQL&#41;](../../t-sql/queries/option-clause-transact-sql.md) da consulta. Para obter mais informações, consulte [Dicas de tabela &#40;Transact-SQL&#41;](../Topic/Table%20Hints%20\(Transact-SQL\).md).  

-   FORCE ORDER  

-   Dica de LOOP JOIN  

-   OPTIMIZE FOR  

 Para obter mais informações, veja [Dicas de consulta &#40;Transact-SQL&#41;](../Topic/Query%20Hints%20\(Transact-SQL\).md).  

##  <a name="a-namelosa-limitations-on-sorting"></a><a name="los"></a> Limitações na classificação  
 Você pode classificar maior que 8.000 linhas em uma consulta que usa [TOP &#40;Transact-SQL&#41;](../../t-sql/queries/top-transact-sql.md) e uma [Cláusula ORDER BY &#40;Transact-SQL&#41;](../Topic/ORDER%20BY%20Clause%20\(Transact-SQL\).md). No entanto, sem a [Cláusula ORDER BY &#40;Transact-SQL&#41;](../Topic/ORDER%20BY%20Clause%20\(Transact-SQL\).md), [TOP &#40;Transact-SQL&#41;](../../t-sql/queries/top-transact-sql.md) pode classificar até 8.000 linhas (menos linhas se houver junções).  

 Se sua consulta usar o operador [TOP &#40;Transact-SQL&#41;](../../t-sql/queries/top-transact-sql.md) e uma [Cláusula ORDER BY &#40;Transact-SQL&#41;](../Topic/ORDER%20BY%20Clause%20\(Transact-SQL\).md), você pode especificar até 8192 linhas para o operador TOP. Se você especificar mais de 8192 linhas, receberá a mensagem de erro: **Msg 41398, Nível 16, Estado 1, Procedimento *\<procedureName>*, Linha *\<lineNumber>* O operador TOP pode retornar no máximo 8192 linhas; *\<number>* foi solicitado.**  

 Se você não tiver uma cláusula TOP, poderá classificar qualquer número de linhas com ORDER BY.  

 Se você não usar uma cláusula ORDER BY, poderá usar qualquer valor inteiro com o operador TOP.  

 Exemplo com TOP N = 8192: compila  

```tsql  
CREATE PROCEDURE testTop  
WITH EXECUTE AS OWNER, SCHEMABINDING, NATIVE_COMPILATION  
  AS  
  BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
    SELECT TOP 8192 ShoppingCartId, CreatedDate, TotalPrice FROM dbo.ShoppingCart  
    ORDER BY ShoppingCartId DESC  
  END;  
GO  
```

 Exemplo com TOP N > 8192: não compila.  

```tsql  
CREATE PROCEDURE testTop  
WITH EXECUTE AS OWNER, SCHEMABINDING, NATIVE_COMPILATION  
  AS  
  BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
    SELECT TOP 8193 ShoppingCartId, CreatedDate, TotalPrice FROM dbo.ShoppingCart  
    ORDER BY ShoppingCartId DESC  
  END;  
GO  
```

 A limitação de 8192 linhas só se aplica a `TOP N` onde `N` é uma constante, como nos exemplos anteriores.  Se você precisar de `N` maior que 8192, poderá atribuir o valor a uma variável e usar essa variável com `TOP`.  

 Exemplo que usa uma variável: compila  

```tsql  
CREATE PROCEDURE testTop  
WITH EXECUTE AS OWNER, SCHEMABINDING, NATIVE_COMPILATION  
  AS  
  BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
    DECLARE @v int = 8193   
    SELECT TOP (@v) ShoppingCartId, CreatedDate, TotalPrice FROM dbo.ShoppingCart  
    ORDER BY ShoppingCartId DESC  
  END;  
GO  
```

 **Limitações nas linhas retornadas:** Há dois casos em que isso pode, potencialmente, reduzir o número de linhas a serem retornadas pelo operador TOP:  

-   Uso de JOINs na consulta.  A influência de JOINs na limitação depende do plano de consulta.  

-   Uso de funções de agregação ou de referências a funções de agregação na cláusula ORDER BY.  

 A fórmula para calcular o pior caso de N com suporte em TOP N é: `N = floor ( 65536 / number_of_tables * 8 + total_size+of+aggs )`.  

## <a name="see-also"></a>Consulte também  
 [Procedimentos armazenados compilados nativamente](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)   
 [Problemas de migração para procedimentos armazenados compilados nativamente](../../relational-databases/in-memory-oltp/migration-issues-for-natively-compiled-stored-procedures.md)  
