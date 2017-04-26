---
title: "Cmdlet Backup-ASDatabase | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 03d58a82-021c-4e13-b265-c084f42a8bb2
caps.latest.revision: 13
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 13
---
# Cmdlet Backup-ASDatabase
  Fazer backup de um banco de dados multidimensional ou tabular do Analysis Services para um arquivo de backup (.abf) do Analysis Services.  
  
## Sintaxe  
 `Backup-ASDatabase [-BackupFile] <string> [-Name] <string> [-AllowOverwrite <SwitchParameter>] [-BackupRemotePartitions <SwitchParameter>] [-ApplyCompression <SwitchParameter>] [-FilePassword <SecureString>] [-Locations <Microsoft.AnalysisServices.BackupLocation[]>] [-Server <string>] [-Credential <PSCredential>] [<CommonParameters>]`  
  
 `Backup-ASDatabase –Database <Microsoft.AnalysisServices.Database> [-AllowOverwrite <SwitchParameter>] [-BackupRemotePartitions <SwitchParameter>] [-ApplyCompression <SwitchParameter>] [-FilePassword <SecureString>] [-Locations <Microsoft.AnalysisServices.BackupLocation[]>] [-Server <string>] [-Credential <PSCredential>] [<CommonParameters>]`  
  
## Description  
 Permite que um administrador de sistemas do Analysis Services faça backup de um banco de dados multidimensional ou tabular para um arquivo de backup. Se você não especificar um local, será usado o local do backup padrão que foi especificado durante a instalação.  
  
 Os arquivos de que você faz backup podem ser criptografados. Use –FilePassword para criptografar o arquivo. Para restaurar o arquivo mais tarde, é preciso fornecer a mesma senha especificada para descriptografá-lo.  
  
 Esse cmdlet oferece suporte ao parâmetro –Credential, que pode ser usado se você configurar a instância do Analysis Services para acesso HTTP. O parâmetro –Credential usa o objeto PSCredential que fornece uma identidade de usuário do Windows. O IIS representará esse usuário ao conectar-se ao Analysis Services. A identidade deve ter permissões de administrador de sistema na instância do Analysis Services para executar o backup.  
  
## Parâmetros  
  
### -BackupFile \<string>  
 Especifica o caminho e o nome do arquivo de backup. Se você especificar apenas o nome do arquivo, sem o caminho, que o local de backup padrão será usado. Este parâmetro só será usado com o parâmetro –Name.  
  
|||  
|-|-|  
|Obrigatório?|true|  
|Posição?|0|  
|Valor padrão||  
|Aceitar entrada de pipeline?|false|  
|Aceitar caracteres curinga?|false|  
  
### -Name \<string>  
 Especifica o banco de dados do Analysis Services do qual fazer backup. Você poderá especificar um banco de dados usando o parâmetro –Database ou o parâmetro –Name se desejar passar o nome como uma cadeia de caracteres.  
  
|||  
|-|-|  
|Obrigatório?|true|  
|Posição?|1|  
|Valor padrão||  
|Aceitar entrada de pipeline?|false|  
|Aceitar caracteres curinga?|false|  
  
### -AllowOverwrite \<SwitchParameter>  
 Substitui um arquivo de backup do mesmo nome.  
  
|||  
|-|-|  
|Obrigatório?|false|  
|Posição?|nomeado|  
|Valor padrão||  
|Aceitar entrada de pipeline?|false|  
|Aceitar caracteres curinga?|false|  
  
### -BackupRemotePartitions \<SwitchParameter>  
 Especifica se as partições remotas serão incluídas no backup.  
  
|||  
|-|-|  
|Obrigatório?|false|  
|Posição?|nomeado|  
|Valor padrão||  
|Aceitar entrada de pipeline?|false|  
|Aceitar caracteres curinga?|false|  
  
### -ApplyCompression\<SwitchParameter>  
 Especifica se deseja compactar o arquivo de backup.  
  
|||  
|-|-|  
|Obrigatório?|false|  
|Posição?|nomeado|  
|Valor padrão||  
|Aceitar entrada de pipeline?|false|  
|Aceitar caracteres curinga?|false|  
  
### -FilePassword \<SecureString>  
 Especifica uma senha a ser usada com a criptografia de arquivo de backup.  
  
|||  
|-|-|  
|Obrigatório?|false|  
|Posição?|nomeado|  
|Valor padrão||  
|Aceitar entrada de pipeline?|false|  
|Aceitar caracteres curinga?|false|  
  
### -Locations \<Microsoft.AnalysisServices.BackupLocation[]>  
 Especifica o local em que o arquivo de backup será armazenado.  
  
|||  
|-|-|  
|Obrigatório?|false|  
|Posição?|nomeado|  
|Valor padrão||  
|Aceitar entrada de pipeline?|false|  
|Aceitar caracteres curinga?|false|  
  
### -Server \<string>  
 Especifica a instância do Analysis Services que o cmdlet conectará e executará. Se nenhum nome de servidor for fornecido, uma conexão será feita com o localhost. Para instâncias padrão, especifique apenas o nome do servidor. Para instâncias nomeadas, use o formato nome_do_servidor\nome_da_instância. Para conexões HTTP, use o formato http[s]://servidor[:porta]/diretório_virtual/msmdpump.dll.  
  
|||  
|-|-|  
|Obrigatório?|false|  
|Posição?|nomeado|  
|Valor padrão|localhost|  
|Aceitar entrada de pipeline?|false|  
|Aceitar caracteres curinga?|false|  
  
### -Credential \<PSCredential>  
 Especifica um objeto –Credential que fornece um nome de usuário e senha do Windows. Especifique esse parâmetro somente se a instância do Analysis Services estiver configurada para acesso HTTP, usando a autenticação básica. Para conexões nativas que usam a segurança integrada, esse parâmetro é ignorado.  
  
 Se esse parâmetro estiver presente, as credenciais que ele fornece serão anexadas à cadeia de conexão. O IIS representará essa identidade de usuário ao conectar-se ao Analysis Services. Se nenhuma credencial for especificada, será usada a conta do Windows padrão do usuário que está executando a ferramenta.  
  
 Para usar este parâmetro, primeiro crie um objeto PSCredential usando Get-Credential para especificar o nome de usuário e a senha (por exemplo, `$Cred=Get-Credential “adventure-works\admin”`. Você pode redirecionar este objeto para o parâmetro –Credential `(-Credential:$Cred`).  
  
 Para obter mais informações sobre o uso de autenticação e das credenciais, consulte [Scripts do PowerShell no Analysis Services](../../analysis-services/instances/powershell-scripting-in-analysis-services.md). Para obter mais informações sobre o acesso HTTP, consulte [Configurar o acesso HTTP ao Analysis Services no IIS &#40;(Serviços de Informações da Internet)&#41; 8.0](../../analysis-services/instances/configure http access to analysis services on iis 8.0.md).  
  
|||  
|-|-|  
|Obrigatório?|false|  
|Posição?|nomeado|  
|Valor padrão||  
|Aceitar entrada de pipeline?|True (ByValue)|  
|Aceitar caracteres curinga?|false|  
  
### -Database \<Microsoft.AnalysisServices.Database[]>  
 Especifica um objeto de banco de dados do Analysis Services do qual fazer backup. Você pode especificar um banco de dados usando os parâmetros -Database ou –Name. Use –Database se você desejar transportar o nome do banco de dados.  
  
|||  
|-|-|  
|Obrigatório?|true|  
|Posição?|nomeado|  
|Valor padrão||  
|Aceitar entrada de pipeline?|true|  
|Aceitar caracteres curinga?|false|  
  
### \<CommonParameters>  
 Este cmdlet oferece suporte aos parâmetros comuns: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer e -OutVariable. Para obter mais informações, consulte [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## Entradas e saídas  
 O tipo de entrada é o tipo dos objetos que você pode transportar para o cmdlet. O tipo de retorno é o tipo dos objetos que o cmdlet retorna.  
  
|||  
|-|-|  
|Entradas|Microsoft.AnalysisServices.Database<br /><br /> Você pode transportar bancos de dados para os quais você quer fazer backup, por exemplo todos os bancos de dados de uma instância específica.|  
|Saídas|Nenhum.|  
  
## Exemplo 1  
  
```  
PS SQLSERVER:\SQLAS\Localhost\default >backup-asdatabase awdb-20110930.abf “Adventure Works” -AllowOverwrite -ApplyCompression  
```  
  
 Este comando faz backup do banco de dados Adventure Works para um arquivo .abf no local padrão do backup. Se um arquivo de mesmo nome existir no local, ele será substituído.  
  
## Exemplo 2  
  
```  
PS SQLSERVER:\SQLAS\Localhost\default >$AWDB = get-item “databases\Adventure Works”   
PS SQLSERVER:\SQLAS\Localhost\default >Backup-asdatabase –database:$AWDB –AllowOverwrite  
```  
  
 Este comando usa –Database em vez de –Backupfile e –Name. Use o parâmetro –Database se você quiser transportar o nome do banco de dados para o cmdlet.  
  
## Exemplo 3  
  
```  
PS SQLSERVER:\SQLAS\Localhost\default\databases >dir * | backup-asdatabase  
```  
  
 Este comando faz backup de todos os bancos de dados no servidor local.  
  
## Exemplo 4  
  
```  
PS SQLSERVER:\SQLAS\Localhost\default > $pwd = read-host –AsSecureString –Prompt “Password”   
PS SQLSERVER:\SQLAS\Localhost\default > $pwd -is [System.IDisposable]   
PS SQLSERVER:\SQLAS\Localhost\default > backup-asdatabase –backupfile test.abf –name contoso_retail –filepassword:$pwd server myremoteserver  
PS SQLSERVER:\SQLAS\Localhost\default >$pwd.Dispose()  
PS SQLSERVER:\SQLAS\Localhost\default >Remove-Variable –Name pwd  
```  
  
 As linhas 1 e 2 são usadas para solicitar uma senha que será usada para criptografar o arquivo.  
  
 A Linha 3 faz backup do banco de dados de exemplo Contoso_Retail no servidor remoto do Analysis Services em um arquivo de backup do Analysis Services chamado test.abf, também localizado no servidor remoto. O arquivo é salvo na pasta de backup padrão da instância padrão.  
  
 As linhas 4 e 5 removem a senha.  
  
## Consulte também  
 [PowerShell scripting in Analysis Services](../../analysis-services/instances/powershell-scripting-in-analysis-services.md)   
 [Gerenciar modelos tabulares usando o PowerShell](http://go.microsoft.com/fwlink/?linkID=227685)  
  
  