---
title: Ajuste uma carga de trabalho | Microsoft Docs
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: dta
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-query-tuning
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
helpviewer_keywords: workloads [SQL Server], tuning
ms.assetid: 6229bf3f-1182-4bc6-8451-cedc37f4b62e
caps.latest.revision: "25"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 6acb93ddde56546e170b01c093dff843a2ea5968
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="lesson-1-1---tuning-a-workload"></a>Lição 1-1-ajuste uma carga de trabalho
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]O orientador de otimização do mecanismo de banco de dados pode ser usado para localizar o melhor design de banco de dados físico para o desempenho de consultas em bancos de dados e tabelas que você selecionar para ajuste.  
  
Esta tarefa usa o banco de dados de exemplo [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . Para reforçar a segurança, os bancos de dados de exemplo não são instalados por padrão. Para instalar os bancos de dados de exemplo, consulte [Instalando amostras e bancos de dados de exemplo do SQL Server](http://sqlserversamples.codeplex.com).  
  
### <a name="tune-a-workload-transact-sql-script-file"></a>Ajustar uma carga de trabalho de arquivo de script do Transact-SQL  
  
1.  Copie uma instrução ou instruções de exemplo SELECT de “ A. Usando SELECT para recuperar linhas e colunas” em [Exemplos de SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-examples-transact-sql.md) e cole as instruções no Editor de Consultas do [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Salve o arquivo como **MyScript.sql** em um diretório no qual você pode encontrá-lo facilmente.  
  
2.  Inicie o Orientador de Otimização do Mecanismo de Banco de Dados. Consulte [Iniciando o Orientador de Otimização do Mecanismo de Banco de Dados](../../tools/dta/lesson-1-1-launching-database-engine-tuning-advisor.md).  
  
3.  No painel direito da GUI do Orientador de Otimização do Mecanismo de Banco de Dados, digite **MySession** em **Nome da sessão**.  
  
4.  Selecione **Arquivo** para a **Carga de trabalho**e clique no botão **Procurar um arquivo de carga de trabalho** para localizar o arquivo **MyScript.sql** salvo na Etapa 1.  
  
5.  Selecione [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] na lista **Banco de dados para análise de carga de trabalho** , selecione [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] na grade **Selecione bancos de dados e tabelas para ajuste** e deixe a opção **Salvar log de ajuste** selecionado. **Banco de dados para análise de carga de trabalho** especifica o primeiro banco de dados ao qual o Orientador de Otimização do Mecanismo de Banco de Dados se conecta ao ajustar uma carga de trabalho. Depois que a otimização começa, o Orientador de Otimização do Mecanismo de Banco de Dados se conecta aos bancos de dados especificados pelas instruções `USE DATABASE` contidas na carga de trabalho.  
  
6.  Clique na guia **Opções de Ajuste** . Você não definirá nenhuma opção de ajuste para esta prática, mas fará a revisão as opções de ajuste padrão. Pressione F1 para exibir a Ajuda da página de guias. Clique em **Opções Avançadas** para exibir outras opções de ajuste. Clique em **Ajuda** na caixa de diálogo **Opções de Ajuste Avançadas** para obter informações sobre as opções de ajuste que são exibidas nessa caixa. Clique em **Cancelar** para fechar a caixa de diálogo **Opções de Ajuste Avançadas** , deixando as opções padrão selecionadas.  
  
7.  Clique no botão **Iniciar Análise** na barra de ferramentas. Enquanto o Orientador de Otimização do Mecanismo de Banco de Dados estiver analisando a carga de trabalho, você poderá monitorar o status na guia **Progresso** . Quando o ajuste foi concluído, a guia **Recomendações** será exibida.  
  
    Se você receber um erro sobre a data e hora de interrupção do ajuste, verifique a hora em **Parar em** na guia principal de **Opções de Ajuste** . Garanta que a data e a hora em **Parar em** são posteriores à data e à hora atuais e, se necessário, altere-as.  
  
8.  Depois que a análise for concluída, salve sua recomendação como um script [!INCLUDE[tsql](../../includes/tsql-md.md)] clicando em **Salvar Recomendações** no menu **Ações** . Na caixa de diálogo **Salvar Como** , navegue até o diretório em que você quer salvar o script de recomendações e digite o nome de arquivo **MyRecommendations**.  
  
## <a name="summary"></a>Resumo  
Você completou o ajuste de uma carga de trabalho de instrução SELECT simples no banco de dados [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . O Orientador de Otimização do Mecanismo de Banco de Dados também pode usar arquivos de rastreamento e tabelas de rastreamento [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] como ajuste de cargas de trabalho. A próxima tarefa mostra como exibir e interpretar as recomendações de ajuste que foi recebido como resultado do ajuste de prática.  
  
## <a name="next-task-in-lesson"></a>Próxima tarefa da lição  
[Exibindo recomendações de ajuste](../../tools/dta/lesson-1-2-viewing-tuning-recommendations.md)  
  
  
  
