---
title: "P&#225;gina Inserir Senhas (Assistente para Adicionar R&#233;plica) | Microsoft Docs"
ms.custom: ""
ms.date: "05/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.addreplicawizard.enterpasswords.f1"
ms.assetid: e69207a0-c5c4-44e4-ae9a-4afbb67251d1
caps.latest.revision: 7
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 7
---
# P&#225;gina Inserir Senhas (Assistente para Adicionar R&#233;plica)
  Este tópico da ajuda descreve as opções da página **Inserir Senhas** . Este tópico aplica-se ao [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)] do [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
 Se as réplicas escolhidas na página **Especificar Réplicas** tiver bancos de dados com uma chave mestra do banco de dados, a página Inserir Senhas aparecerá.  
  
## Opções para Inserir Senhas  
 A grade **Bancos de dados de usuário nesta instância do SQL Server** lista todos os bancos de dados de usuário locais. As colunas são apresentadas assim:  
  
 **Nome**  
 Exibe o nome do banco de dados de usuário local.  
  
 **Tamanho**  
 Exibe o tamanho do banco de dados, se o tamanho estiver disponível para o assistente.  
  
 **Status**  
 Indica a **Senha necessária** para os bancos de dados que têm uma chave mestra do banco de dados. Depois de inserir as senhas para as chaves mestras do banco de dados na coluna **Senhas** , clique em **Atualizar**. Se você tiver digitado as senhas corretamente, a coluna **Status** indicará **Senha digitada**.  
  
 Se o banco de dados não tiver uma chave mestra do banco de dados, a coluna **Status** indicará **Senha não necessária**.  
  
 **Senha**  
 Se a coluna **Status** indicar **Senha necessária**, insira a senha para a chave mestra do banco de dados.  
  
 **Atualizar**  
 Clique para atualizar a grade. Isso será útil após você inserir as senhas necessárias.  
  
## Tarefas relacionadas  
  
-   [Usar o Assistente para Adicionar Réplica ao Grupo de Disponibilidade &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
## Consulte também  
 [Pré-requisitos, restrições e recomendações para grupos de disponibilidade AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/prereqs, restrictions, recommendations - always on availability.md)  
  
  