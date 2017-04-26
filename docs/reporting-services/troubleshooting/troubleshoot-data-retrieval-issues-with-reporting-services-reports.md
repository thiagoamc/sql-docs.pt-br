---
title: "Solucionar problemas de recupera&#231;&#227;o de dados com relat&#243;rios do Reporting Services | Microsoft Docs"
ms.custom: ""
ms.date: "02/27/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
  - "reporting-services-sharepoint"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7680946a-1660-4b59-a03a-c4d474cd8ed3
caps.latest.revision: 4
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 4
---
# Solucionar problemas de recupera&#231;&#227;o de dados com relat&#243;rios do Reporting Services
A primeira etapa durante o processamento do relatório é recuperar seus dados para cada conjunto de dados executando a consulta de conjunto de dados. Quando você visualiza um relatório localmente, as conexões de fonte de dados e credenciais precisam usar permissões suficientes para recuperar os dados para o computador. Quando você executa um relatório no servidor de relatório, as conexões de fonte de dados e credenciais precisam usar permissões suficientes para recuperar os dados nesse servidor. Use este tópico para ajudar a solucionar problemas sobre a recuperação de dados do relatório.   
  
## Não consigo criar uma conexão com uma fonte de dados  
Quando você cria uma fonte de dados, executa uma consulta de conjunto de dados ou visualiza um relatório, pode receber a seguinte mensagem: Não é possível criar uma conexão com a fonte de dados `<data source name>`.   
    
### A fonte de dados não está disponível.  
A fonte de dados está offline ou não disponível por algum outro motivo.   
  
Verifique se você tem acesso à fonte de dados e se ela está disponível. Por exemplo, use o Sql Server Management Studio para se conectar à fonte de dados. Para bancos de dados relacionais e multidimensionais, use o botão **Teste** na caixa de diálogo **Propriedades da Conexão** para verificar a conexão e as permissões para a fonte de dados.   
  
### As credenciais da fonte de dados não são válidas.  
As credenciais que você está usando para se conectar â fonte de dados não têm permissões suficientes para recuperar os dados especificados na consulta.  
  
Verifique se essas credenciais estão corretas. Por exemplo, talvez você tenha permissão para recuperar dados de uma Tabela ou Exibição, mas não para uma coluna específica; ou talvez não tenha permissões suficientes para executar um procedimento armazenado que popula uma exibição.   
  
> [!NOTE]  
> As permissões que você usa para recuperar dados para visualização em um relatório talvez sejam diferentes das permissões necessárias para recuperar dados após a publicação de um relatório em um servidor de relatório.   
  
### A senha não é válida  
Para fontes de dados com credenciais solicitadas ou especificadas na cadeia de caracteres correspondente, os caracteres da senha são passados aos drivers de fonte de dados subjacentes. Se a senha ou a cadeia de caracteres contiver caracteres especiais, como sinais de pontuação, alguns drivers de fontes de dados não poderão validar esses caracteres especiais.   
  
Verifique se a senha não inclui caracteres especiais. Se não for possível alterar a senha, trabalhe com o administrador do banco de dados para armazenar as credenciais apropriadas localmente e no servidor como parte de um DSN (nome da fonte de dados) do sistema ODBC. Para obter mais informações, consulte "OdbcConnection.ConnectionString" na documentação do .NET Framework SDK no MSDN.   
  
> [!NOTE]  
>Não é recomendável a inclusão de informações de logon, como senhas, na cadeia de conexão. O Designer de Relatórios fornece uma página **Credenciais** na caixa de diálogo [Propriedades da Fonte de Dados](Data%20Source%20Properties%20Dialog%20Box,%20General%20(Report%20Builder).xml) ou [Propriedades da Fonte de Dados Compartilhada](Shared%20Data%20Source%20Properties%20Dialog%20Box,%20Credentials.xml) que você pode usar para inserir credenciais. Essas credenciais são armazenadas com segurança no computador de criação do relatório.  
  
## Por que não vejo dados quando executo minha consulta no designer de consulta?  
Quando você criar um conjunto de dados, a coleção de campos desse conjunto de dados aparecerá no painel de dados do relatório. Às vezes, a coleção de campos do conjunto de dados não aparece conforme o esperado.   
  
### A importação da consulta não importa os campos calculados  
  
Embora os campos calculados sejam salvos em uma definição de relatório, eles não são incluídos quando você importa uma consulta de conjunto de dados de outro relatório. Somente campos especificados pela consulta de conjunto de dados aprecem no painel Dados de Relatório depois que você cria um conjunto de dados importando uma consulta de outro relatório.   
  
Para exibir os campos calculados no painel Dados de Relatório, defina-os para cada relatório em que eles são usados.   
  
### Alguns provedores de dados não dão suporte à população automática da coleção de campos do conjunto de dados  
Quando você define uma consulta na caixa de diálogo Propriedades do Conjunto de Dados e fecha a caixa de diálogo, a coleção de campos de conjunto de dados geralmente aparece no painel Dados de Relatório. Para algumas fontes de dados, a coleção de campos de conjunto de dados não é populada automaticamente.   
  
Para popular a coleção de campos do conjunto de dados, siga este procedimento:  
* Você deve ter permissões para recuperar informações de campo do banco de dados. Para algumas fontes de dados, talvez você tenha permissões para acessar essas fontes, mas não a tabela ou coluna. Talvez você tenha permissão para acessar uma exibição, mas não para executar os procedimentos armazenados que criam a exibição. Para validar seu acesso a tabelas ou colunas específicas em um banco de dados, verifique os resultados da consulta em um aplicativo separado, como o SQL Server Management Studio usando as mesmas permissões que utiliza para o relatório. Se você não puder ver os resultados desejados para sua consulta, trabalhe com o administrador do sistema a fim de ajustar suas permissões para os dados.   
* Execute a consulta no painel de consultas da caixa de diálogo **Propriedades do Conjunto de Dados**. Para saber mais, confira [Conjuntos de Dados de Relatório (Construtor de Relatórios 3.0 e SSRS)](../../reporting-services/report-data/report-datasets-ssrs.md).  
* Adicione campos manualmente. Para saber mais, confira [Como adicionar, editar e atualizar campos no painel de dados do relatório (Construtor de Relatórios 3.0 e SSRS)](../../reporting-services/report-data/add-edit-refresh-fields-in-the-report-data-pane-report-builder-and-ssrs.md)   
  
## Consulte também  
[Erros e eventos (Reporting Services)](../../reporting-services/troubleshooting/errors-and-events-reference-reporting-services.md)  
  
  

[!INCLUDE[feedback_stackoverflow_msdn_connect](../../includes/feedback-stackoverflow-msdn-connect.md)]