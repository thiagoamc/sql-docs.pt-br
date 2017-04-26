---
title: "Passo a passo: publicar um Pacote SSIS como um modo SQL | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.ssis.packagepublishwizard.f1"
ms.assetid: d32d9761-93fb-4020-bf82-231439c6f3ac
caps.latest.revision: 12
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 12
---
# Passo a passo: publicar um Pacote SSIS como um modo SQL
  Este passo a passo fornece as etapas detalhadas para publicar um pacote SSIS como um modo SQL em um banco de dados [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## Pré-requisitos  
 Você deve ter o software a seguir instalado no seu computador para executar este passo a passo.  
  
1.  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ou posterior com [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
2.  [SQL Server Data Tools](https://msdn.microsoft.com/library/mt204009.aspx).  
  
## Etapa 1: Compilar e implantar o projeto do SSIS no catálogo do SSIS  
 Nesta etapa, você cria um pacote do SSIS que extrai dados de uma fonte de dados para a qual o SSIS dá suporte (neste exemplo, usamos um banco de dados [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) e promove a saída dos dados usando um componente de Destino do Streaming de Dados. Em seguida, você compila e implanta o projeto do SSIS no catálogo do SSIS.  
  
1.  Inicie o **SQL Server Data Tools**. Clique no menu **Iniciar** , aponte para **Todos os Programas**, aponte para **Microsoft SQL Server**e clique em **SQL Server Data Tools**.  
  
2.  Criar um novo projeto do [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
    1.  Clique em **Arquivo** na barra de menus, aponte para **Novo**e clique em **Projeto**.  
  
    2.  Expanda **Business Intelligence** no painel esquerdo e clique em **Integration Services** no modo de exibição de árvore.  
  
    3.  Selecione **Projeto do Integration Services** se ainda não estiver selecionado.  
  
    4.  Especifique **SSISPackagePublishing** para o **nome do projeto**.  
  
    5.  Especifique um local para o projeto.  
  
    6.  Clique em **OK** para fechar a caixa de diálogo **Novo Projeto** .  
  
3.  Arraste o componente de **Fluxo de Dados** da **Caixa de Ferramentas do SSIS** para a superfície de design da guia **Fluxo de Controle** .  
  
4.  Clique duas vezes no componente **Fluxo de Dados** no **Fluxo de Controle** para abrir o **Designer do Fluxo de Dados**.  
  
5.  Arraste um **componente de origem** da caixa de ferramentas para o **Designer do Fluxo de Dados** e configure-o para extrair dados de uma fonte de dados.  
  
    1.  Para os fins deste passo a passo: crie um banco de dados de teste: **TestDB** com uma tabela: **Funcionário**. Criar a tabela com três colunas, **ID**, **FirstName** e **LastName**.  
  
    2.  Defina **ID** como uma chave primária.  
  
    3.  Insira dois registros com os dados a seguir.  
  
        |ID|FirstName|LastName|  
        |--------|---------------|--------------|  
        |1|John|Doe|  
        |2|Jane|Doe|  
  
    4.  Arraste o componente **Origem OLE DB** da **Caixa de Ferramentas do SSIS** para o **Designer do Fluxo de Dados**.  
  
    5.  Configurar o componente para extrair dados da tabela **Funcionário** no banco de dados **TestDB** . Selecione **(local).TestDB** para **Gerenciador de conexões OLE DB**, **Tabela ou exibição** para **Modo de acesso a dados** e **[dbo].[Funcionário]** para **Nome da tabela ou exibição**.  
  
         ![Data Streaming Destination - OLE DB Connection](../../integration-services/data-flow/media/dsd-oledbconnectionmanager.jpg "Data Streaming Destination - OLE DB Connection")  
  
6.  Agora, arraste o **Destino do Streaming de Dados** da caixa de ferramentas para o fluxo de dados. Você deve encontrar este componente na seção Comum da caixa de ferramentas.  
  
7.  Conecte o componente **Origem OLE DB** no fluxo de dados ao componente **Destino do Streaming de Dados** .  
  
8.  Compile e implante o projeto do SSIS no catálogo do SSIS.  
  
    1.  Clique em **Projeto** na barra de menus e clique em **Implantar**.  
  
    2.  Siga as instruções no assistente para implantar o projeto no catálogo do SSIS no servidor de banco de dados local. O exemplo a seguir usa **Power BI** como o nome da pasta e **SSISPackagePublishing** como o nome do projeto no catálogo do SSIS.  
  
## Etapa 2: Usar o Assistente de publicação do feed de dados do SSIS para publicar o pacote do SSIS como um modo SQL  
 Nesta etapa, você usará o Assistente de publicação do feed de dados do SSIS (SQL Server Integration Services) para publicar o pacote do SSIS como um modo de exibição em um banco de dados do SQL Server. Os dados de saída do pacote podem ser consumidos ao consultar esse modo de exibição.  
  
 O Assistente de publicação do feed de dados do SSIS cria um servidor vinculado usando o SSISOLEDB (provedor OLE DB para SSIS) e, em seguida, cria um modo SQL que consiste em uma consulta no servidor vinculado. Essa consulta inclui o nome da pasta, o nome do projeto e o nome do pacote no catálogo do SSIS.  
  
 Em tempo de execução, o modo de exibição envia a consulta para o Provedor OLE DB para SSIS por meio do servidor vinculado criado por você. O provedor OLE DB para SSIS executa o pacote especificado na consulta e retorna o conjunto de resultados de tabela à consulta.  
  
1.  Inicie o **Assistente de publicação do feed de dados do SSIS** executando ISDataFeedPublishingWizard.exe de C:\Arquivos de Programas\Microsoft SQL Server\130\DTS\Binn ou clicando em Microsoft SQL Server 2016\Assistente de Publicação do Feed de Dados do SQL Server 2016 em Iniciar\Todos os Programas.  
  
2.  Clique em **Avançar** na página **Introdução** .  
  
     ![Data Feed Publishing Wizard - Introduction Page](../../integration-services/data-flow/media/dsd-feedpublishingwizard-introductionpage.jpg "Data Feed Publishing Wizard - Introduction Page")  
  
3.  Na página **Configurações de Pacote** , execute as seguintes tarefas:  
  
    1.  Digite o **nome** da instância do SQL Server que contém o catálogo do SSIS ou clique em **Procurar** para selecionar o servidor.  
  
         ![Data Feed Publishing Wizard - Package Settings Pag](../../integration-services/data-flow/media/dsd-feedpublishingwizard-packagesettingspage.jpg "Data Feed Publishing Wizard - Package Settings Pag")  
  
    2.  Clique em **Procurar** ao lado do campo Caminho, procure o catálogo do SSIS, selecione o pacote do SSIS que deseja publicar (por exemplo: **SSISDB**->**SSISPackagePublishing**->**Package.dtsx**), e clique em **OK**.  
  
         ![Data Feed Publishing Wizard - Browse for Package](../../integration-services/data-flow/media/dsd-feedpublishingwizard-browseforpackage.jpg "Data Feed Publishing Wizard - Browse for Package")  
  
    3.  Usando as guias Parâmetros de Pacote, Parâmetros de Projeto e Gerenciadores de Conexões na parte inferior da página, insira valores para quaisquer parâmetros de pacote, parâmetros de projeto ou configurações do gerenciador de conexões para o pacote. Você também pode indicar uma referência de ambiente a ser usado para a execução do pacote e associar parâmetros de pacote/projeto a variáveis de ambiente.  
  
         É recomendável que você associe parâmetros com distinção a variáveis de ambiente. Isso é para garantir que o valor de um parâmetro com distinção não seja armazenado no formato de texto sem formatação no modo SQL criado pelo assistente.  
  
    4.  Clique em **Avançar** para alternar a página **Configurações de Publicação** .  
  
4.  Na página **Configurações de Publicação** , execute as seguintes tarefas:  
  
    1.  Selecione o **banco de dados** para o modo de exibição a ser criado.  
  
         ![Data Feed Publishing Wizard - Publish Settings Pag](../../integration-services/data-flow/media/dsd-feedpublishingwizard-publishsettingspage.jpg "Data Feed Publishing Wizard - Publish Settings Pag")  
  
    2.  Digite um **nome** para o **modo de exibição**. Você também pode selecionar um modo de exibição existente na lista suspensa.  
  
    3.  Na lista **Configurações** , especifique um **nome** do **servidor vinculado** a ser associado ao modo de exibição. Se o servidor vinculado ainda não existir, o assistente criará o servidor vinculado antes de criar o modo de exibição. Você também pode definir valores para **User32BitRuntime** e **Timeout** aqui.  
  
    4.  Clique no botão **Avançado** . Você deverá ver a caixa de diálogo **Configurações Avançadas** .  
  
    5.  Na caixa de diálogo **Configurações Avançadas** , faça o seguinte:  
  
        1.  Especifique o esquema de banco de dados no qual você deseja que o modo de exibição seja criado (campo Esquema).  
  
        2.  Especifique se os dados devem ser criptografados antes de enviá-los pela rede (campo Criptografar). Consulte o tópico [Usando criptografia sem validação](http://msdn.microsoft.com/library/ms131691.aspx) para obter mais detalhes sobre essa configuração e a configuração TrustServerCertificate.  
  
        3.  Especifique se um certificado do servidor autoassinado pode ser usado quando a configuração de criptografia está habilitada (campo **TrustServerCertificate**).  
  
        4.  Clique em **OK** para fechar a caixa de diálogo **Configurações Avançadas** .  
  
    6.  Clique em **Avançar** para alternar para a página **Validação** .  
  
5.  Na página **Validação** , examine os resultados da validação de valores para todas as configurações. No exemplo a seguir, você vê um **aviso** sobre a existência de servidor vinculado porque o servidor vinculado não existe na instância do SQL Server selecionada. Se você vir **Erro** para **Resultado**, passe o mouse sobre **Erro** e você verá os detalhes sobre o erro. Por exemplo, caso você não tenha habilitado a opção Permitir inprocess para o provedor SSISOLEDB, você obterá um erro na ação de Configuração do Servidor Vinculado.  
  
     ![Data Feed Publishing Wizard - Validation Page](../../integration-services/data-flow/media/dsd-feedpublishingwizard-validationpage.jpg "Data Feed Publishing Wizard - Validation Page")  
  
6.  Para salvar esse relatório como um arquivo XML, clique em Salvar Relatório.  
  
7.  Clique em **Avançar** na página **Validação** para alternar para a página **Resumo** .  
  
8.  Examine sua seleção na página **Resumo** e clique em **Publicar** para iniciar o processo de publicação, que criará o servidor vinculado se não existir no servidor e, em seguida, criará o modo de exibição usando o servidor vinculado.  
  
     ![Data Feed Publishing Wizard - Summary Page](../../integration-services/data-flow/media/dsd-feedpublishingwizard-summarypage.jpg "Data Feed Publishing Wizard - Summary Page")  
  
     Os dados de saída do pacote agora podem ser consultados, executando a instrução SQL a seguir no banco de dados TestDB: SELECT * FROM [SSISPackageView].  
  
9. Para salvar esse relatório como um arquivo XML, clique em **Salvar Relatório**.  
  
10. Examine os resultados do processo de publicação e clique em **Concluir** para fechar o assistente.  
  
    > [!NOTE]  
    >  Não há suporte para os seguintes tipos de dados: text, ntext, image, nvarchar(max), varchar(max) e varbinary(max).  
  
## Etapa 3: Testar o modo SQL  
 Aqui, você executará o modo SQL criado pelo Assistente de publicação do feed de dados do SSIS.  
  
1.  Inicie o SQL Server Management Studio.  
  
2.  Expanda \<**nome do computador**>, **Bancos de dados**, \<**banco de dados selecionado por você no assistente**>e **Modos de exibição**.  
  
3.  Clique com o botão direito do mouse no \<**modo de exibição criado pelo assistente**> criado pelo assistente e clique em **Selecionar as 1000 primeiras linhas**.  
  
4.  Confirme que você vê os resultados do pacote do SSIS.  
  
## Etapa 4: Verificar a execução de pacote do SSIS  
 Nesta etapa, você verificará que o pacote do SSIS foi executado.  
  
1.  No SQL Server Management Studio, expanda **Catálogos do Integration Services**, expanda **SSISDB**, expanda a **pasta** na qual seu projeto SSIS existe, expanda **projetos**, expanda o nó do projeto e expanda **Pacotes**.  
  
2.  Clique com o botão direito do mouse no pacote do SSIS, clique e aponte para **Relatórios**, aponte para **Relatórios Padrão** e clique em **Todas as Execuções**.  
  
3.  Você deve ver a execução do pacote do SSIS no relatório.  
  
    > [!NOTE]  
    >  Em um computador com Windows Vista Service Pack 2, você poderá ver duas execuções de pacote do SSIS no relatório, uma bem-sucedida e uma com falha. Ignore a execução com falha, que é causada por um problema conhecido nesta versão.  
  
## Obter mais informações  
 O Assistente de publicação do feed de dados executa as seguintes etapas importantes:  
  
1.  Cria um servidor vinculado e configura-o para usar o provedor OLE DB para SSIS.  
  
2.  Cria um modo SQL no banco de dados especificado, que consulta o servidor vinculado com informações de catálogo para o pacote selecionado.  
  
 Esta seção apresenta os procedimentos para criar um servidor vinculado e um modo SQL sem usar o Assistente de publicação do feed de dados. Ela também tem informações adicionais sobre como usar a função OPENQUERY com o provedor OLE DB para SSIS.  
  
### Criar um servidor vinculado usando o provedor OLE DB para SSIS  
 Crie um servidor vinculado usando o SSISOLEDB (provedor OLE DB para SSIS), executando a consulta a seguir no SQL Server Management Studio.  
  
```  
  
USE [master]  
GO  
  
EXEC sp_addlinkedserver  
@server = N'SSISFeedServer',  
@srvproduct = N'Microsoft',  
@provider = N'SSISOLEDB',  
@datasrc = N'.'  
GO  
  
```  
  
### Criar uma exibição usando o servidor vinculado e informações de catálogo do SSIS  
 Nesta etapa, você criará um modo SQL que executa uma consulta no servidor vinculado que você criou na seção anterior. Essa consulta incluirá o nome da pasta, o nome do projeto e o nome do pacote no catálogo do SSIS.  
  
 No tempo de execução, quando a exibição é executada, a consulta de servidor vinculado definida no modo de exibição inicia o pacote do SSIS especificado na consulta e recebe a saída do pacote como um conjunto de resultados de tabela.  
  
1.  Antes de criar o modo de exibição, digite e execute a consulta a seguir na nova janela de consulta. OPENQUERY é uma função de conjunto de linhas com suporte pelo SQL Server. Ela executa a consulta passagem especificada no servidor vinculado especificado usando o provedor OLE DB associado ao servidor vinculado. OPENQUERY pode ser referenciada na cláusula FROM de uma consulta como se fosse um nome de tabela. Consulte [Documentação OPENQUERY na biblioteca MSDN](http://msdn.microsoft.com/library/ms188427.aspx) para obter mais informações.  
  
    ```  
    SELECT * FROM OPENQUERY(SSISFeedServer,N'Folder=Eldorado;Project=SSISPackagePublishing;Package=Package.dtsx')   
    GO  
    ```  
  
    > [!IMPORTANT]  
    >  Atualize o nome da pasta, nome do projeto e nome do pacote se necessário. Se a função OPENQUERY falhar, no **SQL Server Management Studio**, expanda **Objetos de Servidor**, expanda **Servidores Vinculados**, expanda **Provedores**e clique duas vezes em provedor **SSISOLEDB** , então verifique se a opção **Permitir inprocess** está habilitada.  
  
2.  Crie um modo de exibição no banco de dados **TestDB** para fins deste passo a passo executando a consulta a seguir.  
  
    ```  
  
    USE [TestDB]   
    GO   
  
    CREATE VIEW SSISPackageView AS   
    SELECT * FROM OPENQUERY(SSISFeedServer, 'Folder=Eldorado;Project=SSISPackagePublishing;Package=Package.dtsx')   
    GO  
  
    ```  
  
3.  Teste o modo de exibição executando a consulta a seguir.  
  
    ```  
    SELECT * FROM SSISPackageView  
    ```  
  
### Função OPENQUERY  
 A sintaxe para a função OPENQUERY é:  
  
```  
SELECT * FROM OPENQUERY(<LinkedServer Name>, N’Folder=<Folder Name from SSIS Catalog>; Project=<SSIS Project Name>; Package=<SSIS Package Name>; Use32BitRuntime=[True | False];Parameters=”<parameter_name_1>=<value1>; parameter_name_2=<value2>”;Timeout=<Number of Seconds>;’)  
```  
  
 Os parâmetros Folder, Project e Package são obrigatórios. Use32BitRuntime, Timeout e Parameters são opcionais.  
  
 O valor de Use32BitRuntime pode ser apenas 0, 1, true ou false. Ele indica se o pacote deverá ser executado com o tempo de execução de 32 bits (1 ou true) quando a plataforma do SQL Server for de 64 bits.  
  
 Timeout indica o número de segundos que o provedor OLE DB para SSIS pode aguardar antes que novos dados cheguem do pacote do SSIS. Por padrão, o tempo limite é de 60 segundos. Você pode especificar um valor inteiro para o tempo limite entre 20 e 32000.  
  
 Parameters contém o valor tanto dos parâmetros do pacote quanto dos parâmetros do projeto. As regras para os parâmetros são as mesmas usadas para os parâmetros em [DTExec](http://msdn.microsoft.com/library/hh231187.aspx).  
  
 A lista a seguir especifica os caracteres especiais permitidos na cláusula de consulta:  
  
-   Aspas Simples (') – têm suporte pelo OPENQUERY padrão. Se você quiser usar as aspas simples na cláusula de consulta, use duas aspas simples (‘’).  
  
-   Aspas duplas (“) – a parte da consulta correspondente aos parâmetros é colocada entre aspas duplas. Se um valor de parâmetro contiver aspas duplas, use o caractere de escape. Por exemplo: \”.  
  
-   Colchetes esquerdo e direito ([ e ]) – esses caracteres são usados para indicar os espaços à esquerda/direita. Por exemplo, “[ alguns espaços ]” representa a cadeia de caracteres “alguns espaços” com um espaço à esquerda e um espaço à direita. Se esses caracteres forem usados na cláusula de consulta, eles deverão ser usados com escape. Por exemplo: \\ [e \\].  
  
-   Barra (\\) – cada \ usada na cláusula de consulta deve usar o caractere de escape. Por exemplo, \\\ é avaliada como \ na cláusula de consulta.  
  
 Barra (\\) – cada \ usada na cláusula de consulta deve usar o caractere de escape. Por exemplo, \\\ é avaliada como \ na cláusula de consulta.  
  
## Consulte também  
 [Destino do Fluxo de Dados](../../integration-services/data-flow/data-streaming-destination.md)   
 [Configurar destino do fluxo de dados](../../integration-services/data-flow/configure-data-streaming-destination.md)  
  
  