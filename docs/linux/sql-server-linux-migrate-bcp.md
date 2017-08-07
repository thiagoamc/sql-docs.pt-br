---
title: Copiar dados para o SQL Server no Linux em massa | Microsoft Docs
description: 
author: sanagama
ms.author: sanagama
manager: jhubbard
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 7b93d0d7-7946-4b78-b33a-57d6307cdfa9
ms.translationtype: MT
ms.sourcegitcommit: ea75391663eb4d509c10fb785fcf321558ff0b6e
ms.openlocfilehash: a4fa8a4080a8483aba8494dd1195c7fbb1aec67a
ms.contentlocale: pt-br
ms.lasthandoff: 08/02/2017

---
# <a name="bulk-copy-data-with-bcp-to-sql-server-on-linux"></a>Dados de cópia em massa com bcp para o SQL Server no Linux

Este tópico mostra como usar o [bcp](https://msdn.microsoft.com/en-us/library/ms162802.aspx) utilitário de linha de comando para dados de cópia em massa entre uma instância do SQL Server de 2017 RC2 no Linux e um arquivo de dados em um formato especificado pelo usuário.

Você pode usar `bcp` para importar grande número de linhas em tabelas do SQL Server ou para exportar dados de tabelas do SQL Server para arquivos de dados. Exceto quando usado com a opção queryout `bcp` não requer conhecimento de Transact-SQL. O `bcp` utilitário de linha de comando funciona com o Microsoft SQL Server em execução no local ou na nuvem, no Linux, Windows ou Docker e banco de dados do SQL Azure e Azure SQL Data Warehouse.

Este tópico mostra como para:
- Importar dados em uma tabela usando o `bcp in` comando
- Exportar dados de uma tabela de usar o `bcp out` comando

## <a name="install-the-sql-server-command-line-tools"></a>Instalar as ferramentas de linha de comando do SQL Server

`bcp`faz parte das ferramentas de linha de comando do SQL Server, que não são instaladas automaticamente com o SQL Server no Linux. Se já não tiver instalado as ferramentas de linha de comando do SQL Server no computador Linux, você deve instalá-los. Para obter mais informações sobre como instalar as ferramentas, selecione a distribuição de Linux da lista a seguir:

- [Red Hat Enterprise Linux (RHEL)](sql-server-linux-setup-tools.md#RHEL)
- [Ubuntu](sql-server-linux-setup-tools.md#ubuntu)
- [SUSE Linux Enterprise Server (SLES)](sql-server-linux-setup-tools.md#SLES)

## <a name="import-data-with-bcp"></a>Importar dados com bcp

Neste tutorial, você criará um banco de dados de exemplo e uma tabela na instância local do SQL Server (**localhost**) e, em seguida, usar `bcp` para carregar na tabela de exemplo de um arquivo de texto no disco.

### <a name="create-a-sample-database-and-table"></a>Criar um banco de dados de exemplo e uma tabela

Vamos começar criando um banco de dados de exemplo com uma tabela simples que será usada no restante deste tutorial.

1. Na caixa do Linux, abra um terminal de comando.

2. Copie e cole os comandos a seguir na janela de terminal. Esses comandos usam o **sqlcmd** o utilitário de linha de comando para criar um banco de dados de exemplo (**BcpSampleDB**) e uma tabela (**TestEmployees**) na instância local do SQL Server (**localhost**). Lembre-se de substituir o `username` e `<your_password>` conforme necessário antes de executar os comandos.

Criar o banco de dados **BcpSampleDB**:
```bash 
sqlcmd -S localhost -U sa -P <your_password> -Q "CREATE DATABASE BcpSampleDB;"
```
Criar a tabela **TestEmployees** no banco de dados **BcpSampleDB**:
```bash 
sqlcmd -S localhost -U sa -P <your_password> -d BcpSampleDB -Q "CREATE TABLE TestEmployees (Id INT IDENTITY(1,1) NOT NULL PRIMARY KEY, Name NVARCHAR(50), Location NVARCHAR(50));"
```
### <a name="create-the-source-data-file"></a>Criar o arquivo de dados de origem
Copie e cole o comando abaixo na janela de terminal. Usaremos o interno `cat` comando para criar um arquivo de dados de texto de exemplo com 3 registros salvá-lo em seu diretório base como **~/test_data.txt**. Os campos nos registros são delimitados por uma vírgula.

```bash
cat > ~/test_data.txt << EOF
1,Jared,Australia
2,Nikita,India
3,Tom,Germany
EOF
```

Você pode verificar se o arquivo de dados foi criado corretamente executando o comando a seguir na janela de terminal:
```bash 
cat ~/test_data.txt
```

Isso deve exibir o seguinte na janela de terminal:
```bash
1,Jared,Australia
2,Nikita,India
3,Tom,Germany
```

### <a name="import-data-from-the-source-data-file"></a>Importar dados do arquivo de dados de origem
Copie e cole os comandos a seguir na janela de terminal. Esse comando usa `bcp` para conectar-se à instância local do SQL Server (**localhost**) e importar os dados do arquivo de dados (**~/test_data.txt**) na tabela (**TestEmployees**) no banco de dados (**BcpSampleDB**). Lembre-se de substituir o nome de usuário e `<your_password>` conforme necessário antes de executar os comandos.

```bash 
bcp TestEmployees in ~/test_data.txt -S localhost -U sa -P <your_password> -d BcpSampleDB -c -t  ','
```

Aqui está uma breve visão geral dos parâmetros de linha de comando usados com `bcp` neste exemplo:
- `-S`: Especifica a instância do SQL Server ao qual se conectar
- `-U`: Especifica a ID de logon usada para se conectar ao SQL Server
- `-P`: Especifica a senha para a ID de logon
- `-d`: Especifica o banco de dados para se conectar ao
- `-c`: executa operações usando um tipo de dados de caractere
- `-t`: Especifica o terminador de campo. Estamos usando `comma` como terminador de campo para os registros em nosso arquivo de dados

> [!NOTE]
> Nós não especificar um terminador de linha personalizado neste exemplo. Linhas no arquivo de dados de texto corretamente encerradas com `newline` quando usamos o `cat` comando para criar o arquivo de dados anterior.

Você pode verificar que os dados foram importados com êxito, executando o comando abaixo na janela de terminal. Lembre-se de substituir o `username` e `<your_password>` conforme necessário antes de executar o comando.
```bash 
sqlcmd -S localhost -d BcpSampleDB -U sa -P <your_password> -I -Q "SELECT * FROM TestEmployees;"
```

Isso deve exibir os seguintes resultados:
```bash
Id          Name                Location
----------- ------------------- -------------------
          1 Jared               Australia
          2 Nikita              India
          3 Tom                 Germany

(3 rows affected)
```

## <a name="export-data-with-bcp"></a>Exportar dados com bcp

Neste tutorial, você usará `bcp` para exportar dados da tabela de exemplo criado anteriormente para um novo arquivo de dados.

Copie e cole os comandos a seguir na janela de terminal. Esses comandos usam o `bcp` utilitário de linha de comando para exportar dados da tabela **TestEmployees** no no banco de dados **BcpSampleDB** para um novo arquivo de dados chamado **~/test_export.txt**.  Lembre-se de substituir o nome de usuário e `<your_password>` conforme necessário antes de executar o comando.

```bash 
bcp TestEmployees out ~/test_export.txt -S localhost -U sa -P <your_password> -d BcpSampleDB -c -t ','
```

Você pode verificar se os dados foram exportados corretamente executando o comando a seguir na janela de terminal:
```bash 
cat ~/test_export.txt
```

Isso deve exibir o seguinte na janela de terminal:
```
1,Jared,Australia
2,Nikita,India
3,Tom,Germany
```

## <a name="see-also"></a>Consulte também
- [utilitário bcp](https://msdn.microsoft.com/en-us/library/ms162802.aspx)
- [Formatos de dados para compatibilidade usando bcp](https://msdn.microsoft.com/en-us/library/ms190759.aspx)
- [Importação em massa dados usando BULK INSERT](https://msdn.microsoft.com/en-us/library/ms175915.aspx)
- [INSERÇÃO em MASSA (Transact-SQL)](https://msdn.microsoft.com/en-us/library/ms188365.aspx)
