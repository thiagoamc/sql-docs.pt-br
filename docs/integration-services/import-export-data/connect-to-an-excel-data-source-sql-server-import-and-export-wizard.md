---
title: "Conectar-se a uma fonte de dados do Excel (Assistente de Importação e Exportação do SQL Server) | Microsoft Docs"
ms.custom: 
ms.date: 06/20/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: import-export-data
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 43fbaca0-36d8-4583-9056-af7010209b87
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 16ace15a73d9ef727612c59f8c9329a4d4437312
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2018
---
# <a name="connect-to-an-excel-data-source-sql-server-import-and-export-wizard"></a>Conectar-se a uma fonte de dados do Excel (Assistente de Importação e Exportação do SQL Server)
Este tópico mostra como se conectar a uma fonte de dados do **Microsoft Excel** (arquivo de texto) por meio da página **Escolher uma Fonte de Dados** ou **Escolher um Destino** do Assistente de Importação e Exportação do SQL Server.

A captura de tela a seguir mostra uma conexão de exemplo a uma pasta de trabalho do Microsoft Excel.

![Conexão do Excel](../../integration-services/import-export-data/media/excel-connection.png) 

## <a name="options-to-specify"></a>Opções a serem especificadas

> [!NOTE]
> As opções de conexão para este provedor de dados serão as mesmas se o Excel for sua origem ou seu destino. Ou seja, as opções exibidas nas páginas **Escolher uma Fonte de Dados** e **Escolher um Destino** do assistente são as mesmas.

**Caminho de arquivo do Excel**  
 Especifique o nome do arquivo e o caminho completo para o arquivo do Excel. Por exemplo:
-   Para um arquivo no computador local, **C:\\MyData.xlsx**.
-   Para um arquivo em um compartilhamento de rede, **\\\\Sales\\Database\\Northwind.xlsx**.

Se preferir, clique em **Procurar**.  
  
 **Procurar**  
 Localize a planilha usando a caixa de diálogo **Abrir**.  

> [!NOTE]
> O assistente não pode abrir um arquivo do Excel protegido por senha.

 **Versão do Excel**  
Selecione a versão do Excel usada pela pasta de trabalho de origem.

> [!IMPORTANT]
> Talvez seja necessário baixar e instalar arquivos adicionais para se conectar a arquivos do Excel. Consulte [Obter os arquivos necessários para se conectar ao Excel](#officeDownloads) nesta página para obter mais informações.

**Primeira linha com nomes de coluna**  
Indique se a primeira linha dos dados contém nomes de coluna.
-   Se os dados de origem não contiverem nomes de coluna, mas você habilitar essa opção, o assistente tratará a primeira linha dos dados de origem como os nomes de coluna.
-   Se os dados de origem contiverem nomes de coluna mas você desabilitar essa opção, o assistente tratará a linha de nomes de coluna como a primeira linha de dados.

Se você especificar que os dados não têm nomes de coluna, o assistente usará F1, F2 e assim por diante como títulos de coluna.

## <a name="i-dont-see-excel-in-the-list-of-data-sources"></a>Não vejo o Excel na lista de fontes de dados
Se você não vê o Excel na lista de fontes de dados, você está executando o assistente de 64 bits? Os provedores para o Excel e Access são geralmente de 32 bits e não são visíveis no assistente de 64 bits. Em vez disso, execute o Assistente de 32 bits.

> [!NOTE]
> Para usar a versão de 64 bits do Assistente de Importação e Exportação do SQL Server, você precisa instalar o SQL Server. O SSDT (SQL Server Data Tools) e o SSMS (SQL Server Management Studio) são aplicativos de 32 bits e somente instalam arquivos de 32 bits, incluindo a versão de 32 bits do assistente.

## <a name="officeDownloads"></a>Obter os arquivos necessários para se conectar ao Excel  
Talvez seja preciso baixar os componentes de conectividade para as fontes de dados do Microsoft Office, incluindo Excel e Access, se eles ainda não estiverem instalados. Baixe a versão mais recente dos componentes de conectividade para arquivos do Excel e do Access aqui: [Mecanismo de Banco de Dados do Microsoft Access 2016](https://www.microsoft.com/download/details.aspx?id=54920).
  
A versão mais recente dos componentes podem abrir arquivos criados em versões anteriores do Excel.

Se o computador tiver uma versão de 32 bits do Office, você precisará instalar a versão de 32 bits dos componentes e precisará também certificar-se de executar o pacote no modo de 32 bits.

Se você tem uma assinatura do Office 365, verifique se você baixou o Mecanismo de Banco de Dados do Access 2016 Redistribuível e não o Tempo de Execução do Microsoft Access 2016. Quando você executar o instalador, você verá uma mensagem de erro dizendo que você não pode instalar o download lado a lado com componentes do tipo clique para executar do Office. Para ignorar essa mensagem de erro, execute a instalação no modo silencioso abrindo uma janela de Prompt de Comando e executando o arquivo .EXE baixado com a opção `/quiet`. Por exemplo:

`C:\Users\<user name>\Downloads\AccessDatabaseEngine.exe /quiet`

## <a name="see-also"></a>Consulte também
[Escolher uma Fonte de Dados](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[Escolher um Destino](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)

