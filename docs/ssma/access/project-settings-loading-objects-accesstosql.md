---
title: "Configurações (Carregando objetos) do projeto (AccessToSQL) | Microsoft Docs"
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-access
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
ms.assetid: 9ec1c1e8-a3e1-4e81-bf49-631f87daa209
caps.latest.revision: "4"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: da86fe46153ede299a41a2b4e308f1b5b51f6947
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="project-settings-loading-objects-accesstosql"></a>Configurações (Carregando objetos) do projeto (AccessToSQL)
As configurações do projeto ao carregar objetos permitem que você configure como os objetos de banco de dados do Access são sincronizados com os objetos de banco de dados do SQL Server.  
  
As ações padrão especifica as configurações padrão para atualizar objetos do banco de dados do Access e para sincronizar objetos do banco de dados do SQL Server. Para obter mais informações, consulte [de atualização de banco de dados &#40; AccessToSQL &#41;](../../ssma/access/refresh-from-database-accesstosql.md)  
  
Você pode acessar duas páginas diferentes de sincronização que contêm as mesmas configurações:  
  
-   Para especificar configurações para todos os projetos futuros do SSMA, no **ferramentas** menu, clique em **DefaultProject configurações**e, em seguida, clique em **carregar objetos** na parte inferior do painel esquerdo.  
  
-   Para especificar as configurações para o projeto atual, no **ferramentas** menu, clique em **configurações de projeto**e, em seguida, clique em **carregar objetos** na parte inferior do painel esquerdo.  
  
## <a name="options"></a>Opções  
  
##### <a name="misc"></a>Diversos  
  
##### <a name="attempts"></a>Tentativas  
Fornece as informações sobre o número de etapas necessárias de objetos para carregar no SQL Server. Carregando objetos no SQL Server normalmente é executada em várias etapas. Objetos que não carregarão na primeira passagem, tais como chaves estrangeiras, poderão carregar com êxito no próximo passo.  
  
Por padrão, o valor é 2.  
  
## <a name="synchronization-for-sql-server"></a>Sincronização para o SQL Server  
  
##### <a name="default-action-on-local-and-remote-object-change"></a>Ação padrão na alteração de objeto Local e remoto  
Especifica a configuração padrão na caixa de diálogo de sincronização quando a definição do objeto alterado no SSMA e no servidor de banco de dados.  
  
-   Se você selecionar **de atualização do banco de dados**, SSMA carregar definições de banco de dados nos metadados quando a condição for atendida.  
  
-   Se você selecionar **gravar no banco de dados**, SSMA atualizará os objetos no banco de dados de acordo com o conteúdo de metadados do SSMA quando a condição for atendida.  
  
-   Se você selecionar **ignorar**, SSMA não executará qualquer ação de atualização.  
  
##### <a name="default-action-on-local-object-change"></a>Ação padrão de alterações do objeto local  
Especifica a configuração padrão na caixa de diálogo de sincronização quando o objeto for alterado no SSMA.  
  
-   Se você selecionar **de atualização do banco de dados**, SSMA carregar definições de banco de dados nos metadados quando a condição for atendida.  
  
-   Se você selecionar **gravar no banco de dados**, SSMA atualizará o objeto no banco de dados de acordo com o conteúdo de metadados do SSMA quando a condição for atendida.  
  
-   Se você selecionar **ignorar**, SSMA não executará qualquer ação de atualização.  
  
##### <a name="default-action-on-remote-object-change"></a>Ação padrão de alterações do objeto remoto  
Especifica a configuração padrão na caixa de diálogo de sincronização quando os objetos alterados no servidor de banco de dados.  
  
-   Se você selecionar **de atualização do banco de dados**, SSMA carregar definições de banco de dados nos metadados quando a condição for atendida.  
  
-   Se você selecionar **gravar no banco de dados**, SSMA atualizará o objeto no banco de dados de acordo com o conteúdo de metadados do SSMA quando a condição for atendida.  
  
-   Se você selecionar **ignorar**, SSMA não executará qualquer ação de atualização.  
  
##### <a name="default-action-when-local-object-metadata-is-missing"></a>Ação padrão quando os metadados de objeto local estão ausente  
Especifica a configuração padrão na caixa de diálogo de sincronização quando metadados local estão ausente.  
  
-   Se você selecionar **de atualização do banco de dados**, SSMA seleciona a atualização da opção de banco de dados quando a condição for atendida.  
  
-   Se você selecionar **gravar no banco de dados**, SSMA excluirá o objeto do banco de dados quando a condição for atendida.  
  
-   Se você selecionar **ignorar**, SSMA não executará qualquer ação de atualização.  
  
