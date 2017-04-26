---
title: "Configurar a criptografia de coluna usando o PowerShell | Microsoft Docs"
ms.custom: ""
ms.date: "01/10/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "powershell"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 074c012b-cf14-4230-bf0d-55e23d24f9c8
caps.latest.revision: 8
author: "stevestein"
ms.author: "sstein"
manager: "jhubbard"
caps.handback.revision: 6
---
# Configurar a criptografia de coluna usando o PowerShell
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Este artigo fornece as etapas para definir a configuração de destino Always Encrypted para colunas de banco de dados que usam o cmdlet [Set-SqlColumnEncryption](https://msdn.microsoft.com/library/mt759790.aspx) (no módulo do *SqlServer* PowerShell). O cmdlet **Set-SqlColumnEncryption** modifica tanto o esquema de banco de dados de destino quanto os dados armazenados nas colunas selecionadas. Os dados armazenados em uma coluna podem ser criptografados, criptografados novamente ou descriptografados, de acordo com as configurações de criptografia de destino especificadas para as colunas e a configuração de criptografia atual.
Para obter informações sobre o suporte a Always Encrypted no módulo SqlServer PowerShell para Always Encrypted, veja [Configurar Always Encrypted usando o PowerShell](../../../relational-databases/security/encryption/configure-always-encrypted-using-powershell.md).

## <a name="prerequisites"></a>Pré-requisitos

Para definir a configuração de criptografia de destino, verifique se:
- uma chave de criptografia de coluna está configurada no banco de dados (se você estiver criptografando ou criptografando novamente uma coluna). Para ver mais detalhes, consulte [Configurar chaves Always Encrypted usando o PowerShell](../../../relational-databases/security/encryption/configure-always-encrypted-keys-using-powershell.md).
- Você pode acessar a chave mestra de coluna para cada coluna que deseja criptografar, criptografar novamente ou descriptografar no computador que executa os cmdlets do PowerShell. 

## <a name="performance-and-availability-considerations"></a>Considerações sobre desempenho e disponibilidade

Para aplicar as configurações de criptografia de destino especificadas para o banco de dados, o cmdlet**Set-SqlColumnEncryption** baixa transparentemente todos os dados das colunas que contêm tabelas de destino, carrega os dados de volta para um conjunto de tabelas temporárias (com as configurações de destino criptografadas) e finalmente substitui as tabelas originais pelas novas versões das tabelas. O .NET Framework Data Provider para SQL Server subjacente criptografa ou/e descriptografa os dados no download ou/e upload, dependendo da configuração de criptografia atual da coluna de destino e das definições de criptografia de destino especificadas para as colunas de destino. A operação de movimentação dos dados pode levar algum tempo, dependendo do tamanho dos dados nas tabelas afetadas e da largura de banda da rede.

O cmdlet **Set-SqlColumnEncryption** oferece suporte a duas abordagens para definir a configuração de criptografia de destino: online e offline.

Com a abordagem offline, as tabelas de destino (e as tabelas relacionadas às tabelas de destino, por exemplo, qualquer tabela com a qual uma tabela de destino tem relações de chave estrangeira) estão disponíveis para transações por toda a duração da operação de gravação.

Com a abordagem online, a operação para copiar e criptografar, descriptografar ou recriptografar os dados é realizada incrementalmente. Os aplicativos podem ler e gravar dados de e para as tabelas de destino durante a operação de movimentação de dados, exceto a última iteração, cuja duração é limitada pelo parâmetro MaxDownTimeInSeconds (você pode definir). Para detectar e processar as alterações que os aplicativos podem fazer enquanto os dados estão sendo copiados, o cmdlet habilita o Controle de Alterações no banco de dados de destino. Por causa disso, a abordagem online provavelmente consome mais recursos no lado do servidor que a abordagem online. A operação também pode levar muito mais tempo com a abordagem online, especialmente se uma carga de trabalho de gravação intensa estiver em execução no banco de dados. A abordagem online pode ser usada para criptografar uma tabela por vez e a tabela deve ter uma chave primária.

Aqui estão as diretrizes para escolher entre as abordagens online e offline:

Use a abordagem offline:
- Para minimizar a duração da operação. 
- Para criptografar/descriptografar/recriptografar colunas em várias tabelas ao mesmo tempo.
- Se a tabela não possui uma chave primária.

Use a abordagem offline:
- Para minimizar a tempo de inatividade/indisponibilidade de aplicativos usando o banco de dados.

## <a name="security-considerations"></a>Considerações sobre segurança

O cmdlet **Set-SqlColumnEncryption** , usado para configurar a criptografia para colunas de banco de dados, gerencia chaves Always Encrypted e os dados armazenados em colunas de banco de dados. Portanto, é importante que você execute o cmdlet em um computador seguro. Se seu banco de dados estive no SQL Server, execute os cmdlets de um computador diferente daquele que hospeda a instância do SQL Server. Como o objetivo principal do Always Encrypted é garantir que os dados confidenciais criptografados estejam seguros mesmo se o sistema do banco de dados for comprometido, a execução de um script do PowerShell que processa chaves e/ou dados confidenciais no computador do SQL Server pode reduzir ou anular os benefícios do recurso.

Tarefa  |Artigo  |Acessa chaves de texto não criptografado/repositório de chaves  |Acessar banco de dados   
---|---|---|---
Etapa 1. Inicie um ambiente do PowerShell e importe o módulo do SqlServer. | [Importar o módulo do SqlServer](../../../relational-databases/security/encryption/configure-always-encrypted-using-powershell.md#importsqlservermodule) | Não | Não
Etapa 2. Conecte-se ao servidor e banco de dados | [Conectando a um banco de dados](../../../relational-databases/security/encryption/configure-always-encrypted-using-powershell.md#connectingtodatabase) | Não | Sim
Etapa 3. Autentique no Azure se a chave mestra de coluna (que protege a chave de criptografia de coluna a ser girada) estiver armazenada no Cofre de Chaves do Azure | [Add-SqlAzureAuthenticationContext](https://msdn.microsoft.com/library/mt759815.aspx) | Sim | Não
Etapa 4. Construir uma matriz de objetos SqlColumnEncryptionSettings - uma para cada coluna de banco de dados que você deseja criptografar, criptografar novamente ou descriptografar. SqlColumnMasterKeySettings é um objeto que existe na memória (no PowerShell). Especifica o esquema de criptografia de destino para uma coluna. | [New-SqlColumnEncryptionSettings](https://msdn.microsoft.com/library/mt759825.aspx) | Não | Não
Etapa 5. Defina a configuração de criptografia desejada, especificada na matriz de objetos SqlColumnMasterKeySettings que você criou na etapa anterior. A coluna será criptografada, criptografada novamente ou descriptografada, dependendo das configurações de destino especificadas e a configuração de criptografia atual da coluna.| [Set-SqlColumnEncryption](https://msdn.microsoft.com/library/mt759790.aspx)<br><br>**Observação:** esta etapa pode levar muito tempo. Seus aplicativos não poderão acessar as tabelas por meio da operação inteira ou parte dela, dependendo da abordagem (online versus offline) que você seleciona. | Sim | Sim

## <a name="encrypt-columns-using-offline-approach---example"></a>Criptografar colunas usando a abordagem offline - exemplo

O exemplo abaixo demonstra a definição da configuração da criptografia de destino para duas colunas.  Se a coluna já não estiver criptografada, ela o será. Se qualquer coluna já estiver criptografada usando uma chave diferente e/ou um tipo de criptografia diferente, ela será descriptografada e criptografada novamente com o tipo da chave de destino especificado.


```
# Import the SqlServer module.
Import-Module "SqlServer"

# Connect to your database.
$serverName = "<server name>"
$databaseName = "<database name>"
$connStr = "Server = " + $serverName + "; Database = " + $databaseName + "; Integrated Security = True"
$connection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection
$connection.ConnectionString = $connStr
$connection.Connect()
$server = New-Object Microsoft.SqlServer.Management.Smo.Server($connection)
$database = $server.Databases[$databaseName]

# Encrypt the selected columns (or re-encrypt, if they are already encrypted using keys/encrypt types, different than the specified keys/types.
$ces = @()
$ces += New-SqlColumnEncryptionSettings -ColumnName "dbo.Patients.SSN" -EncryptionType "Deterministic" -EncryptionKey "CEK1"
$ces += New-SqlColumnEncryptionSettings -ColumnName "dbo.Patients.BirthDate" -EncryptionType "Randomized" -EncryptionKey "CEK1"
Set-SqlColumnEncryption -InputObject $database -ColumnEncryptionSettings $ces -LogFileDirectory .
```
 
## <a name="encrypt-columns-using-online-approach---example"></a>Criptografar colunas usando a abordagem online - exemplo

O exemplo abaixo demonstra a definição da configuração da criptografia de destino para duas colunas usando a abordagem online. Se a coluna já não estiver criptografada, ela o será. Se qualquer coluna já estiver criptografada usando uma chave diferente e/ou um tipo de criptografia diferente, ela será descriptografada e criptografada novamente com o tipo da chave de destino especificado.

```
# Import the SqlServer module.
Import-Module "SqlServer"

# Connect to your database.
$serverName = "<server name>"
$databaseName = "<database name>"
$connStr = "Server = " + $serverName + "; Database = " + $databaseName + "; Integrated Security = True"
$connection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection
$connection.ConnectionString = $connStr
$connection.Connect()
$server = New-Object Microsoft.SqlServer.Management.Smo.Server($connection)
$database = $server.Databases[$databaseName]

# Encrypt the selected columns (or re-encrypt, if they are already encrypted using keys/encrypt types, different than the specified keys/types.
$ces = @()
$ces += New-SqlColumnEncryptionSettings -ColumnName "dbo.Patients.SSN" -EncryptionType "Deterministic" -EncryptionKey "CEK1"
$ces += New-SqlColumnEncryptionSettings -ColumnName "dbo.Patients.BirthDate" -EncryptionType "Randomized" -EncryptionKey "CEK1"
Set-SqlColumnEncryption -InputObject $database -ColumnEncryptionSettings $ces -UseOnlineApproach -MaxDowntimeInSeconds 180 -LogFileDirectory .
```
## <a name="decrypt-columns---example"></a>Descriptografar colunas - exemplo

A exemplo a seguir mostra como descriptografa todas as colunas que estão criptografadas no momento em um banco de dados.


```
# Import the SqlServer module.
Import-Module "SqlServer"

# Connect to your database.
$serverName = "<server name>"
$databaseName = "<database name>"
$connStr = "Server = " + $serverName + "; Database = " + $databaseName + "; Integrated Security = True"
$connection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection
$connection.ConnectionString = $connStr
$connection.Connect()
$server = New-Object Microsoft.SqlServer.Management.Smo.Server($connection)
$database = $server.Databases[$databaseName]

# Find all encrypted columns, and create a SqlColumnEncryptionSetting object for each column.
$ces = @()
$tables = $database.Tables
for($i=0; $i -lt $tables.Count; $i++){
    $columns = $tables[$i].Columns
    for($j=0; $j -lt $columns.Count; $j++) {
        if($columns[$j].isEncrypted) {
            $threeColPartName = $tables[$i].Schema + "." + $tables[$i].Name + "." + $columns[$j].Name 
            $ces += New-SqlColumnEncryptionSettings -ColumnName $threeColPartName -EncryptionType "Plaintext" 
        }
    }
}

# Decrypt all columns.
Set-SqlColumnEncryption -ColumnEncryptionSettings $ces -InputObject $database -LogFileDirectory .
```
 

## <a name="additional-resources"></a>Recursos adicionais
- [Configurar Always Encrypted usando o PowerShell](../../../relational-databases/security/encryption/configure-always-encrypted-using-powershell.md)
- [Always Encrypted (mecanismo de banco de dados)](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)

