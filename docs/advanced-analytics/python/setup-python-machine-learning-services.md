---
title: "Instalação e configuração para serviços de aprendizado de máquina do Python | Microsoft Docs"
ms.custom: 
ms.date: 07/31/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 05976158e43d7dfafaf02289462d1537f5beeb36
ms.openlocfilehash: c7437cff5e2828db7c841e289e329526390e5b69
ms.contentlocale: pt-br
ms.lasthandoff: 09/08/2017

---
# <a name="set-up-python-machine-learning-services-in-database"></a>Configurar os serviços de aprendizado de máquina do Python (no banco de dados)

  Instalar os componentes necessários para Python executando o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Assistente de instalação e seguindo os prompts interativos, conforme descrito neste tópico.

## <a name="machine-learning-options-in-sql-server-setup"></a>Opções de instalação do SQL Server de aprendizado de máquina

Escolha o **serviços de aprendizado de máquina** de recursos e selecione **Python** como o idioma.

O **recursos compartilhados** seção contém uma opção de instalação separada, **Server de aprendizado de máquina (autônomo)**. Essa opção oferece suporte a operacionalização do código Python em um servidor que não tenha o SQL Server, ou que não requerem o uso de contextos de computação do SQL Server. Portanto, é recomendável que você *não* instalá-lo no mesmo computador como uma instância do SQL Server. Em vez disso, instale o servidor de aprendizado de máquina (autônomo) em um computador separado.

Depois que a instalação for concluída, reconfigure a instância para permitir a execução de scripts que usam um executável externo. Talvez seja necessário fazer alterações adicionais no servidor para dar suporte a cargas de trabalho de aprendizado de máquina. Alterações de configuração geralmente requerem uma reinicialização da instância, ou uma reinicialização do serviço Launchpad.

### <a name="prerequisites"></a>Pré-requisitos

+ 2017 do SQL Server é necessária. Não há suporte para a integração do Python em versões anteriores do SQL Server.
+ Certifique-se de instalar o mecanismo de banco de dados. Uma instância do SQL Server é necessário para executar o Python scripts no banco de dados.
+ Pré-requisitos são instalados como parte da instalação de componente do Python.
+ Você não pode instalar o aprendizado de máquina com serviços de Python em um cluster de failover. O mecanismo de segurança usado para isolar processos Python não é compatível com um ambiente de cluster de failover do Windows Server.
   
  Como alternativa, você pode usar a replicação para copiar tabelas necessárias para uma instância do SQL Server autônoma que usa os serviços de Python. Como alternativa, você pode instalar o aprendizado de máquina com os serviços de Python em um computador autônomo que usa a configuração de AlwaysOn e é parte de um grupo de disponibilidade.

+ Instalação lado a lado com outras versões do Python é possível, porque a instância do SQL Server usa sua própria cópia da distribuição Anaconda. No entanto, executando o código que usa o Python no computador do SQL Server fora do SQL Server pode causar vários problemas:
    + Usar uma biblioteca diferente e o executável diferente e obter resultados diferentes, que é feito quando você estiver executando no SQL Server.
    + Scripts de Python em execução em bibliotecas externas não podem ser gerenciados pelo SQL Server, levando a contenção de recursos.
  
> [!IMPORTANT]
> Após a conclusão da instalação, certifique-se de concluir as etapas de pós-configuração adicionais descritas neste tópico. Isso inclui habilitar o SQL Server para usar scripts externos e adicionar contas necessárias para o SQL Server executar trabalhos de Python em seu nome.

### <a name="unattended-installation"></a>Instalação autônoma

Para executar uma instalação autônoma, use as opções de linha de comando para instalação do SQL Server e os argumentos específicos para Python. Para obter mais informações, consulte [autônomo instalado do SQL Server com serviços de aprendizado de máquina do Python](./unattended-installs-of-sql-server-python-services.md).

##  <a name="bkmk_installPythonInDatabase"></a>Etapa 1: Instalar os serviços (no banco de dados) no SQL Server de aprendizado de máquina

1. Execute o Assistente de instalação para SQL Server 2017.
  
2. Sobre o **instalação** guia, selecione **instalação autônoma do novo SQL Server ou adicionar recursos a uma instalação existente**.
   
3. Na página **Seleção de Recursos** , selecione estas opções:
  
    -   **Serviços do Mecanismo de Banco de Dados**
  
         Para usar o Python com o SQL Server, você deve instalar uma instância do mecanismo de banco de dados. Você pode usar um padrão ou uma instância nomeada.
  
    -   **Serviços (no banco de dados) de aprendizado de máquina**
  
         Esta opção instala os serviços de banco de dados que oferece suporte à execução de script de Python.

    -   **Python** Marque esta opção para obter o executável do Python 3.5 e selecione bibliotecas da distribuição Anaconda. Instale apenas um idioma por instância.

        > [!NOTE]
        > Não selecione a opção em **recursos compartilhados** para **Microsoft R Server (autônomo)**. Use essa opção em uma instalação separada, se você precisa adicionar a componentes em um computador diferente que é usado para desenvolvimento de R de aprendizado de máquina. Por exemplo, isso pode ser útil para o laptop do seu cientista de dados.
        
        ![Opções de configuração para Python](media/ml-svcs-features-python-highlight.png "opções de configuração para Python")

4. Sobre o **consentimento para instalar o Python** página, selecione **aceitar**.
  
     Este contrato de licença é necessário para baixar o Python executável, pacotes do Python de Anaconda.
     
     ![Contrato de licença de Python](media/ml-svcs-license-python.png "contrato para Python de licença")
  
    > [!NOTE]
    >  Se o computador que está usando não tiver acesso à internet, você pode pausar o programa de instalação neste momento para baixar os instaladores separadamente. Para obter mais informações, consulte [Instalando componentes sem acesso à internet](../r/installing-ml-components-without-internet-access.md).
  
     Selecione **aceitar**, aguarde até que o **próximo** botão se torna ativo e, em seguida, selecione **próximo**.
  
5. Sobre o **pronto para instalar** página, verifique se essas seleções são incluídas e selecione **instalar**.
  
     + Serviços do Mecanismo de Banco de Dados
     + Serviços de Machine Learning (No Banco de Dados)
     + Python
  
    Essas seleções representam a configuração mínima necessária para usar o Python com o SQL Server.
    
    ![Pronto para instalar o Python](media/ready-to-install-python.png "componentes necessários para a instalação da Python")

    Opcionalmente, anote o local da pasta no caminho `..\Setup Bootstrap\Log` onde os arquivos de configuração são armazenados. Quando a instalação for concluída, você pode examinar os componentes instalados no arquivo de resumo.

6. Quando a instalação for concluída, reinicie o computador.

##  <a name="bkmk_enableFeature"></a>Etapa 2: Habilitar a execução do script Python

1. Abra o [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Se ele não estiver instalado, você pode executar o Assistente de instalação do SQL Server novamente para abrir um link de download e instalá-lo.
  
2. Conecte-se à instância onde você instalou os serviços de aprendizado de máquina e execute o seguinte comando:

   ```SQL
   sp_configure
   ```

    O valor da propriedade `external scripts enabled`, deve ser **0** neste momento. Isso ocorre porque o recurso está desativado por padrão. O recurso deve ser habilitado explicitamente por um administrador antes de executar scripts R ou Python.
    
3.  Para habilitar o recurso de script externo que dá suporte a Python, execute a seguinte instrução:
    
    ```SQL
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
    Isso é exatamente o mesmo processo que é usado para habilitar R, porque o recurso de extensibilidade subjacente oferece suporte a ambas as linguagens.

4. Reinicie o serviço SQL Server da instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Reiniciar o serviço do SQL Server também automaticamente reinicia relacionado [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] serviço.

    Você pode reiniciar o serviço usando o **serviços** painel no painel de controle ou usando [SQL Server Configuration Manager](../../relational-databases/sql-server-configuration-manager.md).

## <a name="step-3-verify-that-the-external-script-execution-feature-is-running"></a>Etapa 3: Verificar se o recurso de execução do script externo está em execução

Dedique alguns momentos para verificar se todos os componentes usados para iniciar o script de Python estão em execução.

1. No SQL Server Management Studio, abra uma nova janela de consulta e execute o seguinte comando:
    
    ```SQL
    EXEC sp_configure  'external scripts enabled'
    ```

    O **run_value** agora deve ser definido como 1.
    
2. Abra o **serviços** painel ou o SQL Server Configuration Manager e verifique se o serviço barra inicial para a instância está em execução. Se a barra inicial não está em execução, reinicie o serviço.
  
    Se você tiver instalado várias instâncias do SQL Server, qualquer instância que tem o R ou Python habilitado tem seu próprio serviço barra inicial.

    No entanto, se você instalar o R e Python em uma única instância, Launchpad somente um está instalado. Um iniciador separado, específico do idioma DLL é adicionado para cada idioma. Para obter mais informações, consulte [componentes para dar suporte à integração do Python](new-components-in-sql-server-to-support-python-integration.md). 
   
3. Se estiver executando a barra inicial, você deve ser capaz de executar scripts Python simples semelhante à seguinte no [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]:
    
    ```SQL
    EXEC sp_execute_external_script  @language =N'Python',
    @script=N'OutputDataSet=InputDataSet',
    @input_data_1 = N'SELECT 1 AS col'
    ```
    
    **Resultados**
    
    *<code>&nbsp;&nbsp;</code>* *1*

> [!NOTE]
> Títulos usados no script Python ou colunas não são retornados, por design. Para adicionar nomes de coluna de saída, você deve especificar o esquema para o conjunto de dados retornado. Faça isso usando o parâmetro com resultados do procedimento armazenado, nomear as colunas e especificando o tipo de dados SQL.
> Por exemplo, você pode adicionar a linha a seguir para gerar um nome arbitrário de coluna:`WITH RESULT SETS ((Col1 AS int))`

## <a name="step-4-additional-configuration"></a>Etapa 4: Configuração adicional

Se o comando anterior foi bem-sucedida, você pode executar comandos de Python do SQL Server Management Studio, o código do Visual Studio ou qualquer outro cliente que pode enviar instruções T-SQL para o servidor.

Se você receber um erro ao executar o comando, examine a lista a seguir. Talvez seja necessário fazer configurações adicionais de apropriado para o serviço ou o banco de dados.

> [!NOTE]
> 
> Nem todas as alterações listadas são necessárias, e nenhum pode ser necessária. Requisitos dependem de seu esquema de segurança, onde você instalou o SQL Server e como você espera que os usuários a se conectar ao banco de dados e executar scripts externos.

###  <a name="bkmk_configureAccounts"></a>Habilitar autenticação implícita para o grupo de contas da barra inicial

Durante a instalação, um número de novas contas de usuário do Windows são criadas com a finalidade de executar tarefas no token de segurança do serviço [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]. Quando um usuário envia um script Python ou R de um cliente externo, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ativa uma conta de trabalho disponíveis. Em seguida, ele mapeia para a identidade do usuário da chamada e executa o script em nome do usuário.

Isso é chamado de *autenticação implícita*, e é um serviço de mecanismo de banco de dados. Este serviço oferece suporte a execução segura de scripts externos no SQL Server 2016 e 2017 do SQL Server.

Exiba essas contas no grupo de usuários do Windows, **SQLRUserGroup**. Por padrão, 20 contas de trabalho são criadas, que geralmente é mais do que suficiente para executar o script externo trabalhos.

> [!IMPORTANT]
> O grupo de trabalho é chamado SQLRUserGroup, independentemente do tipo de script que você está executando. Há um único grupo para cada instância.

Se você precisa executar scripts R de um cliente de ciência de dados remotos, e você estiver usando autenticação do Windows, há considerações adicionais. Essas contas de trabalho devem receber permissão para entrar para a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instância em seu nome.

1. Em [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], no Pesquisador de objetos, expanda **segurança**. Em seguida, clique com botão direito **logons**e selecione **novo logon**.
2. No **logon - novo** caixa de diálogo, selecione **pesquisa**.
3. Selecione **tipos de objeto**e selecione **grupos**. Limpe tudo.
4. Em **insira o nome do objeto para selecionar**, tipo *SQLRUserGroup*e selecione **verificar nomes**.
5. O nome do grupo local associado ao serviço Launchpad da instância deverá ser resolvido para algo como *instancename\SQLRUserGroup*. Escolha **OK**.
6. Por padrão, a entrada é atribuído para o **pública** função, e tem permissão para conectar-se ao mecanismo de banco de dados.
7. Escolha **OK**.

> [!NOTE]
> Se você usar um SQL entrar para executar scripts em um contexto de computação do SQL Server, esta etapa adicional não é necessária.

### <a name="give-users-permission-to-run-external-scripts"></a>Conceder aos usuários permissão para executar scripts externos

Se você instalou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] por conta própria e você está executando scripts de Python em sua própria instância, você normalmente executa scripts como administrador. Portanto, você tem permissão implícita em várias operações e todos os dados no banco de dados.

A maioria dos usuários, no entanto, não tem tais permissões elevadas. Por exemplo, os usuários em uma organização que usam logons do SQL para acessar o banco de dados geralmente não têm permissões elevadas. Portanto, para cada usuário que está usando o Python, você deve conceder aos usuários dos serviços de aprendizado de máquina a permissão para executar scripts externos em cada banco de dados onde o Python é usado. Aqui está como:

```SQL
USE <database_name>
GO
GRANT EXECUTE ANY EXTERNAL SCRIPT  TO [UserName]
```

> [!NOTE]
> As permissões não são específicas para a linguagem de script com suporte. Em outras palavras, não há níveis de permissão separados para o script R versus script Python. Se você precisar manter permissões separadas para esses idiomas, instale o R e Python em instâncias separadas.

### <a name="give-your-users-read-write-or-data-definition-language-ddl-permissions-to-databases"></a>Conceder permissões de language (DDL) para bancos de dados de sua definição de leitura, gravação ou dados de usuários

Enquanto um usuário está em execução de scripts, a conta de usuário ou entrada do SQL, talvez seja necessário ler dados de outros bancos de dados. A conta de usuário ou logon no SQL também seja necessário criar novas tabelas para armazenar os resultados e gravar dados em tabelas.

Para cada conta de usuário de logon ou de SQL que está executando os scripts de R ou Python, certifique-se de que ele tem `db_datareader`, `db_datawriter`, ou `db_ddladmin` permissões no banco de dados específico.

Por exemplo, a seguinte [!INCLUDE[tsql](../../includes/tsql-md.md)] fornece instrução SQL na entrada *MySQLLogin* os direitos para executar consultas T-SQL *ML_Samples* banco de dados. Para executar essa instrução, o SQL entrar já deve existir no contexto de segurança do servidor.
  
```SQL
USE ML_Samples
GO
EXEC sp_addrolemember 'db_datareader', 'MySQLLogin'
```

Para obter mais informações sobre as permissões incluídas em cada função, consulte [funções de nível de banco de dados](../../relational-databases/security/authentication-access/database-level-roles.md).

### <a name="ensure-that-the-sql-server-installation-supports-remote-connections"></a>Certifique-se de que a instalação do SQL Server oferece suporte a conexões remotas

Se você não pode conectar-se de um computador remoto, verifique se o firewall permite o acesso ao SQL Server. Em uma instalação padrão, conexões remotas podem ser desabilitadas ou a porta específica usada pelo SQL Server pode ser bloqueada pelo firewall. Para obter mais informações, consulte [configurar o Firewall do Windows para acesso ao mecanismo de banco de dados](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md).

### <a name="create-an-odbc-data-source-for-the-instance-on-your-data-science-client"></a>Criar uma fonte de dados ODBC para a instância no cliente de ciência de dados

Você pode criar uma solução em um computador de cliente de ciência de dados de aprendizado de máquina. Se você precisar executar código usando o computador do SQL Server como o contexto de computação, você tem duas opções. Você pode usar um SQL logon ou autenticação integrada do Windows.

+ Para logons do SQL: Verifique se a entrada tem as permissões apropriadas no banco de dados em que você está lendo dados. Você pode fazer isso adicionando *conectem* e *selecione* permissões, ou adicionando a entrada para o `db_datareader` função. Precisam de entradas que criam objetos `DDL_admin` direitos. Entradas que devem salvar dados em tabelas devem ser adicionadas para o `db_datawriter` função.

+ Para autenticação do Windows: talvez seja necessário criar uma fonte de dados ODBC no cliente de ciência de dados que especifica o nome da instância e outras informações de conexão. Para obter mais informações, consulte [administrador de fonte de dados ODBC](https://docs.microsoft.com/sql/odbc/admin/odbc-data-source-administrator).


## <a name="additional-optimizations"></a>Otimizações adicionais

Agora que você tem que tudo funcione, você também poderá otimizar o servidor para suportar o aprendizado de máquina ou modelos de classificação de instalação.

### <a name="add-more-worker-accounts"></a>Adicionar mais contas de trabalho

Se você espera que muitos usuários em execução simultaneamente scripts, você pode aumentar o número de contas de trabalho que são atribuídos ao serviço barra inicial. Para obter mais informações, consulte [modificar o pool de conta de usuário do SQL Server R Services](../r/modify-the-user-account-pool-for-sql-server-r-services.md).

### <a name="optimize-the-server-for-script-execution"></a>Otimizar o servidor para execução de script

As configurações padrão para [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instalação otimizar o equilíbrio do servidor para uma variedade de serviços. Esses serviços incluem processos ETL, relatórios, auditoria e aplicativos que usam [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dados.

Se você usar as configurações padrão, você perceberá que recursos para execução de scripts externos são restritos ou limitados, especialmente em operações com uso intensivo de memória. Se o aprendizado de máquina é uma prioridade, altere as configurações de banco de dados padrão para garantir que os trabalhos de script externo são priorizados e recursos adequadamente. Essas alterações podem incluir:

+ Reduzindo a quantidade de memória alocada para o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mecanismo de banco de dados.
+ Aumentar o número de contas em execução sob o [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] service. Isso não aumenta o número de recursos, mas aumenta o número de scripts que podem ser executados simultaneamente.

Se você tiver o SQL Server Enterprise Edition, use o administrador de recursos para configurar um pool de recursos externos para Python. Para obter mais informações, consulte os artigos a seguir.

-   Configurar um pool de recursos para o gerenciamento de recursos externos
  
     [CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md)
  
-   Alterar a quantidade de memória reservada para o mecanismo de banco de dados
  
     [Opções Server memory de configuração de servidor](../../database-engine/configure-windows/server-memory-server-configuration-options.md)
  
-   Alterar o número de contas de trabalho que podem ser iniciados por[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]
  
     [Modificar o pool de conta de usuário do SQL Server R Services](../r/modify-the-user-account-pool-for-sql-server-r-services.md)

Se você estiver usando o SQL Server Standard Edition e não tiver o administrador de recursos, você pode usar modos de exibição de gerenciamento dinâmico e eventos estendidos para ajudá-lo a gerenciar recursos do servidor. Você também pode usar o monitoramento de eventos do Windows para essa finalidade. Para obter mais informações, consulte [monitoramento e gerenciamento de serviços de R](../r/managing-and-monitoring-r-solutions.md).

### <a name="upgrade-the-machine-learning-components"></a>Atualizar a componentes de aprendizado de máquina

Quando você instala os serviços de aprendizado de máquina usando o SQL Server 2017, que obter a versão dos componentes no momento em que a versão publicada. Cada vez que você corrigir ou atualiza a instância do SQL Server, os componentes de aprendizado de máquina são atualizados também.

Você pode atualizar a componentes em um agendamento mais rápido do que há suporte para de aprendizado de máquina por versões do SQL Server, instalando o servidor de aprendizado de máquina do Microsoft. Quando você fizer isso, você também obter os novos recursos de suporte na versão mais recente do servidor de aprendizado de máquina, como:

+ Atualizações para pacotes do Python para [revoscalepy](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package) e [microsoftml para Python](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package).
+ [Modelos de classificação](https://docs.microsoft.com/r-server/install/microsoftml-install-pretrained-models) para análise de texto e de classificação de imagem.

Para obter informações sobre como atualizar uma instância, consulte [componentes de R de atualização por meio da associação](..\r\use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

> [!NOTE]
> 
> A versão atual contém a versão mais recente de todos os componentes de aprendizado de máquina. Portanto, embora há suporte para atualizações através do servidor de aprendizado de máquina do Microsoft para SQL Server 2017, a atualização que está disponível no momento se aplica apenas às instâncias do SQL Server 2016.

### <a name="tutorials"></a>Tutoriais

Consulte os tutoriais a seguir para obter alguns exemplos de como você pode usar o Python com o SQL Server para criar e implantar soluções de aprendizado de máquina:

[Usando Python no T-SQL](../tutorials/run-python-using-t-sql.md)

[Criar um modelo de Python usando revoscalepy](../tutorials/use-python-revoscalepy-to-create-model.md)