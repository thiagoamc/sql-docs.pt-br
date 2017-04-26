---
title: "Tarefa Executar SQL | Microsoft Docs"
ms.custom: 
  - "ssisdev020617"
ms.date: "03/13/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.executesqltask.f1"
  - "sql13.dts.designer.executesqltask.general.f1"
  - "sql13.dts.designer.executesqltask.parametermapping.f1"
  - "sql13.dts.designer.executesqltask.resultset.f1"
helpviewer_keywords: 
  - "instruções Transact-SQL, SSIS"
  - "instruções [Integration Services]"
  - "lotes [Integration Services]"
  - "tarefa Executar SQL [Integration Services]"
ms.assetid: bebb2e8c-0410-43b2-ac2f-6fc80c8f2e9e
caps.latest.revision: 115
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 113
---
# Tarefa Executar SQL
  A tarefa Executar SQL executa instruções SQL ou procedimentos armazenados a partir de um pacote. A tarefa pode conter uma única instrução SQL ou várias instruções SQL que são executadas em sequência. Você pode usar a tarefa Executar SQL para os seguintes propósitos:  
  
-   Truncar uma tabela ou exibição em preparação para inserção de dados.  
  
-   Criar, alterar e descartar objetos de banco de dados como tabelas e exibições.  
  
-   Recriar tabelas de fatos e de dimensões antes de carregar dados nelas.  
  
-   Executar procedimentos armazenados. Se a instrução SQL invocar um procedimento armazenado que retorne resultados de uma tabela temporária, use a opção de WITH RESULT SETS para definir metadados para o conjunto de resultados.  
  
-   Salvar o conjunto de linhas retornado de uma consulta em uma variável.  
  
 A tarefa Executar SQL pode ser usada em combinação com os contêineres Loop Foreach e Loop For para executar várias instruções SQL. Esses contêineres implementam fluxos de controle repetitivos em um pacote e eles podem executar a tarefa Executar SQL várias vezes. Por exemplo, usando o contêiner Loop Foreach, um pacote pode enumerar arquivos em uma pasta e executar uma tarefa Executar SQL várias vezes para executar a instrução SQL armazenada em cada arquivo.  
  
## Conectando-se a uma fonte de dados  
 A tarefa Executar SQL pode usar tipos diferentes de gerenciadores de conexões para se conectar à fonte de dados onde a instrução SQL ou o procedimento armazenado é executado. A tarefa pode usar os tipos de conexão listados na tabela a seguir.  
  
|Tipo de conexão|Gerenciador de conexões|  
|---------------------|------------------------|  
|EXCEL|[Gerenciador de conexões do Excel](../../integration-services/connection-manager/excel-connection-manager.md)|  
|OLE DB|[Gerenciador de conexões OLE DB](../../integration-services/connection-manager/ole-db-connection-manager.md)|  
|ODBC|[Gerenciador de conexões ODBC](../../integration-services/connection-manager/odbc-connection-manager.md)|  
|ADO|[Gerenciador de conexões ADO](../../integration-services/connection-manager/ado-connection-manager.md)|  
|ADO.NET|[Gerenciador de conexões ADO.NET](../../integration-services/connection-manager/ado-net-connection-manager.md)|  
|SQLMOBILE|[Gerenciador de Conexões do SQL Server Compact Edition](../../integration-services/connection-manager/sql-server-compact-edition-connection-manager.md)|  
  
## Criando instruções SQL  
 A origem das instruções SQL usada por essa tarefa pode ser uma propriedade de tarefa que contém uma instrução, uma conexão com um arquivo que contém uma ou várias instruções ou o nome de uma variável que contém uma instrução. As instruções SQL devem ser gravadas na linguagem do sistema de gerenciamento de banco de dados de origem (DBMS). Para obter mais informações, consulte [Consultas do Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-queries.md).  
  
 Se as instruções SQL estiverem armazenadas em um arquivo, a tarefa usará um gerenciador de conexões de arquivo para se conectar ao arquivo. Para obter mais informações, consulte [File Connection Manager](../../integration-services/connection-manager/file-connection-manager.md).  
  
 No Designer [!INCLUDE[ssIS](../../includes/ssis-md.md)], você pode usar a caixa de diálogo **Editor da Tarefa Executar SQL** para digitar instruções SQL ou usar o **Construtor de Consultas**, uma interface do usuário gráfica para criar consultas SQL. Para obter mais informações, consulte [Editor da Tarefa Executar SQL &#40;Página Geral&#41;](../Topic/Execute%20SQL%20Task%20Editor%20\(General%20Page\).md) e [Construtor de Consultas](../Topic/Query%20Builder.md).  
  
> [!NOTE]  
>  Instruções SQL válidas gravadas fora da tarefa Executar SQL talvez não sejam analisadas com êxito pela tarefa Executar SQL.  
  
> [!NOTE]  
>  A Tarefa Executar SQL usa o valor de enumeração **RecognizeAll** ParseMode. Para obter mais informações, consulte [Namespace ManagedBatchParser](http://go.microsoft.com/fwlink/?LinkId=223617).  
  
## Enviando várias instruções em um lote  
 Se várias instruções forem incluídas em uma tarefa Executar SQL, é possível agrupá-las e executá-las como um lote. Para sinalizar o final de um lote, use o comando GO. Todas as instruções SQL entre dois comandos GO são enviadas em um lote para o provedor OLE DB a fim de serem executadas. O comando SQL pode incluir vários lotes separados por comandos GO.  
  
 Há restrições sobre os tipos de instruções SQL que podem ser agrupados em um lote. Para obter mais informações, consulte as instruções [Lotes de instruções](../../relational-databases/native-client-odbc-queries/executing-statements/batches-of-statements.md).  
  
 Se a tarefa Executar SQL executar um lote de instruções SQL, as seguintes regras se aplicam ao lote:  
  
-   Só uma instrução pode retornar um conjunto de resultados e deve ser a primeira instrução no lote.  
  
-   Se o conjunto de resultados usar associações de resultado, as consultas devem retornar o mesmo número de colunas. Se as consultas retornarem um número diferente de colunas, a tarefa falhará. Porém, mesmo que a tarefa falhe, as consultas executadas, como DELETE ou INSERT, podem ser executadas com êxito.  
  
-   Se as associações de resultado usarem nomes de coluna, a consulta deve retornar colunas que tenham os mesmos nomes do conjunto de resultados usado na tarefa. Se as colunas estiverem ausentes, a tarefa falhará.  
  
-   Se a tarefa usar associações de parâmetro, todas as consultas do lote devem ter o mesmo número e os mesmos tipos de parâmetros.  
  
## Executando comandos SQL parametrizados  
 As instruções SQL e os procedimentos armazenados frequentemente usam parâmetros de entrada, parâmetros de saída e códigos de retorno. A tarefa Execute SQL dá suporte aos tipos de parâmetro **Input**, **Output** e **ReturnValue**. Use o tipo **Input** para parâmetros de entrada, **Output** para parâmetros de saída e **ReturnValue** para códigos de retorno.  
  
> [!NOTE]  
>  Você só poderá usar parâmetros em uma tarefa Executar SQL se o provedor de dados der suporte a eles.  
  
 Para obter informações sobre como usar parâmetros e códigos de retorno na tarefa Executar SQL, consulte [Parâmetros e códigos de retorno na Tarefa Executar SQL](../Topic/Parameters%20and%20Return%20Codes%20in%20the%20Execute%20SQL%20Task.md).  
  
## Especificando um tipo de conjunto de resultados  
 Dependendo do tipo de comando SQL, um conjunto de resultados pode ou não ser retornado para a tarefa Executar SQL. Por exemplo, uma instrução SELECT normalmente retorna um conjunto de resultados, mas uma instrução INSERT não. O conjunto de resultados de uma instrução SELECT pode conter nenhuma linha, uma linha ou muitas linhas. Os procedimentos armazenados também podem retornar um valor inteiro, chamado de código de retorno, para indicar o status de execução do procedimento. Nesse caso, o conjunto de resultados consiste em uma única linha.  
  
 Para obter informações sobre como recuperar conjuntos de resultados de comandos SQL na tarefa Executar SQL, consulte [Conjuntos de resultados na tarefa Executar SQL](../Topic/Result%20Sets%20in%20the%20Execute%20SQL%20Task.md).  
  
## Solucionando problemas da tarefa Executar SQL  
 Você pode registrar as chamadas que a tarefa Executar SQL faz para provedores de dados externos. É possível usar esse recurso de registro para solucionar problemas dos comandos SQL executados pela tarefa Executar SQL. Para registrar as chamadas que a tarefa Executar SQL faz aos provedores de dados externos, habilite o registro de pacotes e selecione o evento **Diagnóstico** no nível de pacotes. Para obter mais informações, consulte [Solucionando problemas de ferramentas para execução de pacotes](../../integration-services/troubleshooting/troubleshooting-tools-for-package-execution.md).  
  
 Às vezes um comando SQL ou procedimento armazenado retorna vários conjuntos de resultados. Esses conjuntos de resultados incluem não só conjuntos de linhas que resultam de consultas **SELECT**, mas também valores únicos que resultam de erros das instruções **RAISERROR** ou **PRINT**. A tarefa poderá ignorar ou não os erros nos conjuntos de resultados que ocorrem após o primeiro conjunto de resultados dependendo do tipo de gerenciador de conexões usado:  
  
-   Quando você usa gerenciadores de conexões OLE DB e ADO, a tarefa ignora os conjuntos de resultados que ocorrem após o primeiro conjunto de resultados. Portanto, com esses gerenciadores de conexões, a tarefa ignora um erro retornado por um comando SQL ou um procedimento armazenado quando o erro não faz parte do primeiro conjunto de resultados.  
  
-   Quando você usa gerenciadores de conexões ODBC e ADO.NET, a tarefa não ignora os conjuntos de resultados que ocorrem após o primeiro conjunto de resultados. Com esses gerenciadores de conexões, a tarefa falhará quando ocorrer um erro que não seja do primeiro conjunto de resultados.  
  
### Entradas personalizadas do log  
 A tabela a seguir descreve a entrada de log personalizada da tarefa Executar SQL. Para obter mais informações, consulte [Log do SSIS &#40;Integration Services&#41;](../../integration-services/performance/integration-services-ssis-logging.md) e [Mensagens personalizadas para log](../../integration-services/performance/custom-messages-for-logging.md).  
  
|Entrada de log|Description|  
|---------------|-----------------|  
|**ExecuteSQLExecutingQuery**|Fornece informações sobre as fases de execução da instrução SQL. As entradas de log são gravadas quando a tarefa adquire conexão com o banco de dados, quando a tarefa começa a preparar a instrução SQL e depois que a execução da instrução SQL é concluída. A entrada de log da fase de preparação inclui a instrução SQL usada pela tarefa.|  
  
## Configurando a tarefa Executar SQL  
 Você pode configurar a tarefa Executar SQL das seguintes formas:  
  
-   Especifique o tipo de gerenciador de conexões a ser usado para conectar-se a um banco de dados.  
  
-   Especifique o tipo de conjunto de resultados retornado pela instrução SQL.  
  
-   Especifique um tempo limite para as instruções SQL.  
  
-   Especifique a origem da instrução SQL.  
  
-   Indique se a tarefa ignora a fase de preparação para a instrução SQL.  
  
-   Se você usar o tipo de conexão ADO, indique se a instrução SQL é um procedimento armazenado. Para outros tipos de conexão, essa propriedade é somente leitura e seu valor é sempre **falso**.  
  
 Você pode definir propriedades programaticamente ou por meio do Designer [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Para obter mais informações sobre as propriedades que podem ser definidas no [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, clique em um dos seguintes tópicos:  
  
-   [Editor da Tarefa Executar SQL &#40;Página Geral&#41;](../Topic/Execute%20SQL%20Task%20Editor%20\(General%20Page\).md)  
  
-   [Editor da Tarefa Executar SQL &#40;Página Mapeamento de Parâmetros&#41;](../Topic/Execute%20SQL%20Task%20Editor%20\(Parameter%20Mapping%20Page\).md)  
  
-   [Editor da Tarefa Executar SQL &#40;Página Conjunto de Resultados&#41;](../Topic/Execute%20SQL%20Task%20Editor%20\(Result%20Set%20Page\).md)  
  
-   [Página Expressões](../../integration-services/expressions/expressions-page.md)  
  
 Para obter mais informações sobre como definir essas propriedades no [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, clique no tópico a seguir:  
  
-   [Definir as propriedades de uma tarefa ou contêiner](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)  
  
## Configurando a tarefa Executar SQL programaticamente  
 Para obter mais informações sobre como definir essas propriedades programaticamente, clique no tópico a seguir:  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.ExecuteSQLTask.ExecuteSQLTask>  
  
## Tarefas relacionadas  
  
-   [Mapear parâmetros de consulta para variáveis em uma tarefa Executar SQL](../Topic/Map%20Query%20Parameters%20to%20Variables%20in%20an%20Execute%20SQL%20Task.md)  
  
-   [Mapear conjuntos de resultados para variáveis em uma tarefa Executar SQL](../Topic/Map%20Result%20Sets%20to%20Variables%20in%20an%20Execute%20SQL%20Task.md)  
  
## Conteúdo relacionado  
  
-   [Parâmetros e códigos de retorno na Tarefa Executar SQL](../Topic/Parameters%20and%20Return%20Codes%20in%20the%20Execute%20SQL%20Task.md)  
  
-   [Conjuntos de resultados na tarefa Executar SQL](../Topic/Result%20Sets%20in%20the%20Execute%20SQL%20Task.md)  
  
-   [Referência do Transact-SQL &#40;Mecanismo de Banco de Dados&#41;](../../t-sql/transact-sql-reference-database-engine.md)  
  
-   Entrada de blog, [Novas funções de data e hora no SQL Server 2012](http://go.microsoft.com/fwlink/?LinkId=239783) em mssqltips.com  
  
  