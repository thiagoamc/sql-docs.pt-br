---
title: "Desempenho de consultas de &#237;ndices ColumnStore | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "01/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 83acbcc4-c51e-439e-ac48-6d4048eba189
caps.latest.revision: 23
author: "barbkess"
ms.author: "barbkess"
manager: "jhubbard"
caps.handback.revision: 22
---
# Desempenho de consultas de &#237;ndices ColumnStore
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Recomendações para atingir desempenho de consultas muito rápido, que os índices columnstore são projetados para fornecer.    
    
 Índices ColumnStore podem atingir desempenho até 100 vezes melhor em análise e data warehousing de cargas de trabalho e até 10 vezes melhor compactação de dados que os índices rowstore tradicionais.   Essas recomendações ajudarão a atingir um desempenho de consultas muito rápido em suas consultas, que os índices columnstore são projetados para fornecer.  No final, há mais explicações sobre desempenho com columnstore.    
    
## Recomendações para melhorar o desempenho de consultas    
 Recomendações para atingir desempenho de consulta muito rápido, que os índices columnstore são projetados para fornecer.    
    
### 1. Organizar dados para eliminar mais rowgroups de uma verificação de tabela completa    
    
-   **Aproveite a ordem de inserção.** Geralmente, no data warehouse tradicional, os dados são realmente inseridos na ordem de tempo e análise é feita em dimensão temporal. Por exemplo, ao analisar vendas por trimestre. Para essa variante de carga de trabalho, a eliminação de rowgroup ocorre automaticamente. No SQL Server 2016, você pode descobrir que rowgroups de número foram ignorados como parte do processamento de consulta.    
    
-   **Aproveite o índice rowstore clusterizado.** Se o predicado de consulta comum estiver em uma coluna (por exemplo, C1) que não está relacionada à ordem de inserção da linha, você poderá criar um índice clusterizado rowstore em colunas C1 e criar o índice clusterizado columstore com a remoção do índice clusterizado rowstore. Se você criar o índice columnstore clusterizado explicitamente usando DOP (grau de paralelismo) = 1, o índice columnstore clusterizado resultante será ordenado perfeitamente na coluna C1. Se você especificar DOP = 8, e você verá sobreposição de valores por 8 rowgroups.  Um caso comum dessa estratégia é quando você cria inicialmente o índice columnstore com um grande conjunto de dados. Observe que, para o NCCI (índice columnstore não clusterizado), se a tabela rowstore base tiver um índice clusterizado, as linhas já estarão ordenadas. Nesse caso, o índice columnstore não clusterizado resultante será ordenado automaticamente. Um ponto importante a observar é que o índice columnstore não mantém a ordem das linhas inerentemente. Conforme novas linhas são inseridas ou linhas mais antigas são atualizadas, talvez seja necessário repetir o processo, já que o desempenho de consultas de análise pode se deteriorar    
    
-   **Aproveite o particionamento de tabela.** Você pode particionar o índice columnstore e usar a eliminação de partição para reduzir o número de rowgroups a serem verificados. Por exemplo, compras de repositórios de tabelas de fatos feitas por clientes e um padrão de consulta comum é para encontrar compras trimestrais feitas por um cliente específico, você pode combinar a ordem de inserção com o particionamento na coluna de cliente. Cada partição conterá linhas na ordem de tempo para o cliente específico.    
    
### 2. Planejar memória suficiente para criar índices columnstore em paralelo    
 Criar um índice columnstore é, por padrão, uma operação paralela, a menos que a memória seja restrita. Criar o índice em paralelo exige mais memória do que criar o índice em série. Quando há bastante memória, a criação de um índice columnstore assume a ordem de 1,5 vezes mais longa do que a criação de uma árvore B nas mesmas colunas.    
    
 A memória necessária para criar um índice columnstore depende do número de colunas, do número de colunas de cadeia de caracteres, do grau de paralelismo (DOP) e as características dos dados. Por exemplo, se sua tabela tiver menos de um milhão de linhas, o SQL Server usará apenas um thread para criar o índice columnstore.    
    
 Se a sua tabela tiver mais de um milhão de linhas, mas o SQL Server não puder obter uma quantidade de memória suficiente para criar o índice usando MAXDOP, o SQL Server diminuirá automaticamente MAXDOP conforme o necessário de acordo com a quantidade de memória disponível.  Em alguns casos, o DOP deve ser diminuído para um para criar o índice na memória restrita.    
    
 Começando com o SQL Server 2016, a consulta operará sempre em modo de lote. Em versões anteriores, a execução em lotes só é usada quando o DOP é maior do que um.    
    
## Desempenho ColumnStore explicado    
 Índices ColumnStore obtêm alto desempenho de consultas, combinando o processamento de modo de lotes in-memory em alta velocidade com técnicas que reduzem significativamente os requisitos de E/S.  Já que consultas de análise examinam grandes números de linhas, elas são normalmente associadas a E/S e, portanto, reduzir E/S durante a execução da consulta é essencial para o design de índices columnstore.  Depois que os dados são lidos na memória, é essencial reduzir o número de operações in-memory.    
    
 Índices columnstore reduzem E/S e otimizam as operações in-memory por meio de alta compactação de dados, eliminação de columnstores, eliminação de rowgroups e processamento em lotes.    
    
### Compactação de dados    
 Índices columnstore obtêm compactação de dados até 10x maior que índices rowstore.  Isso reduz significativamente a E/S necessária para executar consultas de análise e, portanto, melhora o desempenho de consultas.    
    
-   Índices columnstore leem dados compactados do disco, o que significa que menos bytes de dados precisam ser lidos da memória.    
    
-   Índices columnstore armazenam dados em formato compactado na memória, o que reduz a E/S ao reduzir o número de vezes que tais dados são lidos da memória.  Por exemplo, com compactação de 10 vezes, os índices columnstore podem manter 10 vezes mais dados na memória do que é possível armazenando dados em formato descompactado. Com mais dados na memória, é mais provável que o índice columnstore localize os dados de que precisa na memória com a realização de leituras de disco adicionais.    
    
-   Os índices columnstore compactam dados por colunas em vez de compactá-los por linhas, o que alcança altas taxas de compactação e reduz o tamanho dos dados armazenados no disco. Cada coluna é compactada e armazenada de modo independente.  Dados em uma coluna sempre têm o mesmo tipo de dados e tendem a ter valores semelhantes. Técnicas de compactação de dados são muito boas para alcançar taxas mais altas de compactação quando os valores são semelhantes.    
    
-   Por exemplo, se uma tabela de fatos armazena endereços de clientes e tem uma coluna de país, o número total de valores possíveis é inferior a 200.  Alguns desses valores serão repetidas várias vezes.  Se a tabela de fatos tem 100 milhões de linhas, a coluna de país será compactada facilmente e exigirá muito pouco armazenamento. A compactação de linha por linha não é capaz de aproveitar a similaridade de valores de coluna dessa maneira e usará mais bytes para compactar os valores na coluna de país.    
    
### Eliminação de colunas    
 Índices columnstore ignoram a leitura em colunas que não são necessárias para o resultado da consulta. Essa capacidade, chamada de eliminação de colunas, reduz ainda mais a E/S para a execução da consulta e, portanto, melhora o desempenho de consultas.    
    
-   A eliminação de colunas é possível porque os dados são organizados e compactados coluna por coluna.   Por outro lado, quando os dados são armazenados linha por linha, os valores de coluna em cada linha são fisicamente armazenados juntos e não podem ser facilmente separados. O processador de consulta precisa ler em uma linha inteira para recuperar valores de coluna específicos, o que aumenta a E/S porque dados extras são lidos desnecessariamente na memória.    
    
-   Por exemplo, se uma tabela tiver 50 colunas e a consulta utilizar apenas 5 dessas colunas, o índice columnstore buscará apenas 5 colunas do disco. Ela ignora a leitura nas outras 45 colunas. Isso reduz a E/S em outros 90%, supondo que todas as colunas sejam de tamanho similar.  Se os mesmos dados forem armazenados em um rowstore, o processador de consulta precisará ler as 45 colunas adicionais.    
    
### Eliminação de rowgroups    
 Para verificações de tabela completa, um grande percentual dos dados geralmente não corresponde aos critérios de predicado de consulta. Usando metadados, o índice columnstore é capaz de ignorar a leitura nos rowgroups que não contêm dados necessários para o resultado da consulta, tudo sem E/S real.  Essa capacidade, chamada de eliminação de rowgroups, reduz ainda mais a E/S para verificações de tabela completas e, portanto, melhora o desempenho de consultas.    
    
 **Quando um índice columnstore precisa executar uma verificação de tabela completa?**    
    
 Começando com o SQL Server 2016, você pode criar um ou mais índices de árvore b regulares não clusterizados em um índice columnstore clusterizado, assim como você pode fazer no heap de um rowstore.  Os índices de árvore b não clusterizados podem acelerar uma consulta contendo um predicado de igualdade ou um predicado com um intervalo de valores pequeno.  Para predicados mais complicados, o otimizador de consulta pode escolher uma verificação de tabela completa. Sem a capacidade de ignorar rowgroups, uma verificação de tabela completa seria muito demorada, especialmente para tabelas grandes.    
    
 **Quando uma consulta de análise se beneficia de eliminação de rowgroups para uma verificação de tabela completa?**    
    
 Por exemplo, uma empresa de varejo modelou seus dados de vendas usando uma tabela de fatos com índice columnstore clusterizado. Cada nova venda armazena vários atributos da transação, incluindo a data da venda. Curiosamente, mesmo que os índices columnstore não assegurem uma ordem de classificação, as linhas nessa tabela serão carregadas em uma ordem classificada por data.   Ao longo do tempo, essa tabela aumentará. Embora o negócio varejista possa manter dados de vendas pelos últimos 10 anos, uma consulta de análise talvez precise apenas computar uma agregação do último trimestre. Índices columnstore podem eliminar o acesso aos dados dos 39 trimestres anteriores, apenas observando os metadados da coluna de data.  Isso é uma redução de 97% adicionais na quantidade de dados lidos na memória e processados.    
    
 **Quais rowgroups são ignorados em uma verificação de tabela completa?**    
    
 Para determinar quais grupos de linhas eliminar, o índice columnstore usa metadados para armazenar os valores mínimo e máximo de cada segmento de coluna para cada rowgroup. Quando nenhum dos intervalos de segmento de coluna atendem aos critérios de predicado de consulta, o rowgroup inteiro será ignorado sem fazer nenhuma E/S real. Isso funciona porque os dados geralmente são carregados em uma ordem classificada e, embora não exista garantia de que as linhas são classificadas, valores de dados semelhantes geralmente estão localizados no mesmo rowgroup ou em outro adjacente.    
    
 Para obter mais detalhes sobre rowgroups, veja [Guia de índices Columnstore](../Topic/Columnstore%20Indexes%20Guide.md)    
    
### Execução em modo de lote    
 A execução em modo de lote refere-se ao processamento de um conjunto de linhas, normalmente até 900, agrupadas para eficiência de execução. Por exemplo, a consulta  `Select SUM (Sales)from SalesData` agrega as vendas totais da tabela SalesData.    Na execução em modo de lote, o mecanismo de execução de consulta calcula a agregação de 900 valores em grupo.  Isso estende aos metadados os custos de acesso e outros tipos de sobrecarga em todas as linhas em um lote, em vez de pagar o custo para cada linha; assim, o caminho do código é reduzido significativamente.  Processamento de modo de lote opera nos dados compactados quando possível e elimina alguns dos operadores de troca usados pelo processamento de modo de linha.  Isso acelera a execução de consultas de análise em ordens de magnitude.    
    
 Nem todos os operadores de execução de consulta podem ser executados em modo de lote. Por exemplo, operações DML como Insert, Delete ou Update são executadas em uma linha por vez. O modo de lote destina-se a operadores voltados à aceleração do desempenho de consultas, como Scan, Join, Aggregate, sort e outros mais.  Como o índice columnstore foi introduzido no SQL Server 2012, há um esforço contínuo para expandir os operadores que podem ser executados em modo em lote. A tabela abaixo mostra os operadores que são executados em modo de lote, de acordo com a versão do produto.    
    
|Operadores em Modo de Lote|Quando isso é usado?|SQL Server 2012|SQL Server 2014|SQL Server 2016 e Banco de Dados SQL|Comentários|    
|---------------------------|------------------------|---------------------|---------------------|---------------------------------------|--------------|    
|Operações DML (insert, delete, update, merge)||não|não|não|DML não é uma operação de modo de lote porque ele não é paralelo. Mesmo quando podemos habilitar o processamento em lotes de modo serial, não vemos ganhos significativos ao permitir que o DML seja processado em modo em lote.|    
|verificação de índice columnstore|SCAN|NA|sim|sim|Para índices columnstore, podemos enviar por push o predicado por push para o nó SCAN.|    
|Verificação de índice columnstore (não clusterizado)|SCAN|sim|sim|sim|sim|    
|busca de índice||NA|NA|não|Podemos executar uma operação de busca por meio de um índice de árvore b não clusterizado em modo linha.|    
|computar escalar|Uma expressão que é avaliada como um valor escalar.|sim|sim|sim|Há algumas restrições para o tipo de dados. Isso é verdadeiro para todos os operadores de modo de lote.|    
|concatenação|UNION e UNION ALL|não|sim|sim||    
|filtro|Aplicação de predicados|sim|sim|sim||    
|correspondência de hash|Funções de agregação baseadas em hash, junção de hash externa, junção de hash à direita, junção de hash à esquerda, junção interna direita, junção interna esquerda|sim|sim|sim|Restrições de agregação: nenhum mín/máx para cadeias de caracteres. As funções de agregação disponíveis são sum/count/avg/min/max.<br />Restrições de associação: nenhum tipo incompatível ingressa em tipos não inteiros.|    
|junção de mesclagem||não|não|não||    
|consultas multithread||sim|sim|sim||    
|loops aninhados||não|não|não||    
|consultas de thread único executando no MAXDOP 1||não|não|sim||    
|consultas de thread único com um plano de consulta serial||não|não|sim||    
|classificar|Classificar por cláusula em SCAN com índice columnstore.|não|não|sim||    
|classificação superior||não|não|sim||    
|agregações de janela||NA|NA|sim|Novo operador no SQL Server 2016.|    
    
 ¹Aplica-se ao SQL Server 2016, Banco de Dados SQL V12 Premium Edition e SQL Data Warehouse    
    
### Aplicação de agregação    
 Um caminho de execução normal para a computação de agregação buscar as linhas de qualificação do nó SCAN e agregar os valores em modo de lote.  Embora isso ofereça bom desempenho, no SQL Server 2016 a operação de agregação pode ser enviada por push para o nó SCAN para melhorar o desempenho da computação de agregação em ordens de magnitude além da execução do modo de lote, desde que as condições a seguir sejam atendidas    
    
-   Os operadores de agregação com suporte são MIN, MAX, SUM, COUNT, AVG    
    
-   Qualquer tipo de dados <= 64 bits tem suporte.  Por exemplo, bigint tem suporte já que seu tamanho é de 8 bytes, mas decimal (38,6) não tem, pois seu tamanho é de 17 bytes. Além disso, não há suporte para nenhum tipo de cadeia de caracteres    
    
-   O operador de agregação deve ficar sobre o nó SCAN ou nó SCAN com agrupar por    
    
 A propagação de agregação é ainda mais acelerada pela agregação eficiente nos dados compactados/codificados em execução amigável a cache e aproveitando SIMD    
    
 ![aggregate pushdown](../../relational-databases/indexes/media/aggregate-pushdown.jpg "aggregate pushdown")    
    
 Por exemplo, a aplicação de agregação é feita em ambas as consultas abaixo    
    
```    
    
SELECT  productkey, SUM(TotalProductCost)    
FROM FactResellerSalesXL_CCI    
GROUP BY productkey    
    
SELECT  SUM(TotalProductCost)    
FROM FactResellerSalesXL_CCI    
```    
    
### Aplicação de predicado de cadeia de caracteres    
 Motivação: ao criar um esquema de data warehouse, o modelo de esquema recomendado é usar um esquema em estrela ou floco de neve, consistindo de uma ou mais tabelas de fatos e várias tabelas de dimensão. A [tabela de fatos](https://en.wikipedia.org/wiki/Fact_table) armazena as transações ou medidas de negócios e a [tabela de dimensões](https://en.wikipedia.org/wiki/Dimension_table) armazena as dimensões pelas quais os fatos precisam ser analisados.    
    
 Por exemplo, um fato pode ser um registro que representa uma venda de um produto específico em uma região específica, enquanto a dimensão representa um conjunto de regiões, produtos e assim por diante. As tabelas de fatos e dimensões são conectadas por meio de uma relação de chaves primária/estrangeira. As consultas de análise mais comumente usadas unem uma ou mais tabelas de dimensão à tabela de fatos.    
    
 Vamos considerar uma tabela de dimensões de produtos. Uma chave primária típica será productcode, que normalmente é representada como um tipo de dados String.  Para desempenho de consultas, uma melhor prática é criar uma chave substituta, normalmente uma coluna de inteiros, para referir-se à linha na tabela de dimensões da tabela de fatos.    
    
 O índice columnstore executa consultas de análise com junções/predicados que envolvem chaves baseadas em valores numéricos ou inteiros de maneira muito eficiente.   No entanto, em muitas cargas de trabalho do cliente, vemos o uso de colunas com base em cadeias de caracteres vinculando tabelas de fatos/dimensões e, como resultado disso, o desempenho de consultas com índice columnstore não era tão bom.    O SQL Server 2016 melhora significativamente o desempenho de consultas de análise com colunas baseadas em cadeia de caracteres, ao realizar a aplicação dos predicados com colunas de cadeia de caracteres no nó SCAN    
    
 A aplicação de predicado de cadeia de caracteres aproveita o dicionário primário/secundário criado para coluna(s) para melhorar o desempenho de consultas.  Por exemplo, consideremos o segmento de coluna de cadeia de caracteres dentro de um rowgroup que consiste de 100 valores de cadeia de caracteres distintos. Isso significa que cada valor de cadeia de caracteres distinto é referenciado 10.000 vezes em média, pressupondo 1 milhão de linhas.    
    
 Com a aplicação de predicado de cadeia de caracteres, a execução da consulta calcula o predicado em relação aos valores no dicionário e se ela se qualificar, todas as linhas se referindo ao valor do dicionário são qualificadas automaticamente.   Isso melhora o desempenho de duas maneiras. Primeiro, apenas as linhas qualificadas são retornadas reduzindo o número de linhas que precisam fluir para fora do nó SCAN. Em segundo lugar, o número de comparações de cadeias de caracteres é significativamente reduzido. Neste exemplo, apenas 100 comparações de cadeias de caracteres são necessárias, em vez de 1 milhão de comparações.     Existem algumas limitações, conforme descrito abaixo    
    
-   Nenhuma aplicação de predicado da cadeia de caracteres para rowgroups delta. Não há dicionário para colunas em rowgroups delta    
    
-   Nenhuma aplicação de predicado de cadeia de caracteres se o dicionário exceder 64 mil entradas    
    
-   Expressões que são avaliadas como NULOs não têm suporte    
    
## Consulte também    
 [Guia de Índices Columnstore](../Topic/Columnstore%20Indexes%20Guide.md)     
 [Carregamento de dados dos índices columnstore](../Topic/Columnstore%20Indexes%20Data%20Loading.md)     
 [Resumo de recursos com versão dos índices columnstore](../Topic/Columnstore%20Indexes%20Versioned%20Feature%20Summary.md)     
 [Desempenho de consultas de índices ColumnStore](../../relational-databases/indexes/columnstore-indexes-query-performance.md)     
 [Introdução ao Columnstore para análise operacional em tempo real](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)     
 [Índices columnstore para Data Warehouse](../Topic/Columnstore%20Indexes%20for%20Data%20Warehousing.md)     
 [Desfragmentação de índices columnstore](../../relational-databases/indexes/columnstore-indexes-defragmentation.md)    
    
  