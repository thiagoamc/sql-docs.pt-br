---
title: "Configurações de migração de dados (MySQLToSQL) | Microsoft Docs"
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-mysql
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 9c396df4-5676-4f32-9c57-70d4f15f9b7a
caps.latest.revision: "9"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5776d0e27ab6d68b83ce0e8ce7c9ddb667b13f1a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="data-migration-settings-mysqltosql"></a>Configurações de migração de dados (MySQLToSQL)
  
## <a name="data-migration-settings"></a>Configurações de migração de dados  
**As configurações de migração de dados** permite que o usuário escreva consultas personalizadas para a migração de dados.  
  
-   Essa guia está disponível quando **estendidos opções de migração de dados** é definido como **Mostrar** e ficará oculto quando a configuração é definida como **ocultar** nas configurações do projeto. Para obter mais informações sobre configurações de projeto de migração, consulte [configurações do projeto (migração)](http://msdn.microsoft.com/en-us/2a3cba9e-cd54-4a8b-b858-8fc4cf2580d9) .  
  
-   Análise de instruções SQL personalizada será implementado em **as configurações de migração de dados** guia do nó de tabela.  
  
-   A seguir está as duas caixas de seleção disponíveis no **as configurações de migração de dados** viz.:  
  
    1.  Truncar a tabela do SQL Server  
  
    2.  Selecione Usar personalizado  
  
1.  **Truncar a tabela do SQL Server:**  
     Essa opção permite que o usuário tenha uma visão clara dos dados migrados no banco de dados de destino.  
  
    -   Por padrão, esta caixa de texto é verificada.  
  
    -   Se esta caixa de texto não estiver marcada, os dados migrados serão adicionados para os dados existentes no banco de dados de destino.  
  
2.  **Selecione Usar personalizado:**  
     Essa opção permite que o usuário modifique o **selecione** instrução presente (**selecione** instrução permite que os usuários selecionar os dados a serem exibidos no banco de dados de destino).  
  
    1.  Por padrão, esta caixa de texto está desmarcada.  
  
    2.  Se esta caixa de texto é verificada, ele permite que os usuários modifiquem o **selecione** instrução presente.  
  
Há dois botões presentes viz.:  
  
-   **Aplicar:** clique **aplicar** para aplicar as configurações que foram alteradas.  
  
-   **Cancelar:** clique **Cancelar** para restaurar as configurações presentes antes que as alterações sejam feitas.  
  
## <a name="see-also"></a>Consulte Também  
[Migração de dados MySQL para o SQL Server/SQL Azure](http://msdn.microsoft.com/en-us/a6a7f4d6-68aa-4a38-93bf-53eba0d7dc82)  
  
