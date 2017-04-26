---
title: "Propriedades do banco de dados de distribuição | Microsoft Docs"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.configdistwizard.distdbproperties.f1
helpviewer_keywords:
- Distribution Database Properties dialog box
ms.assetid: 0f404ab9-1237-4936-8df5-888baab6a245
caps.latest.revision: 23
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 7e086caef0d106066a3f8a9f42d1bbd51d473826
ms.lasthandoff: 04/11/2017

---
# <a name="distribution-database-properties"></a>Propriedades do Banco de Dados de Distribuição
  A caixa de diálogo **Propriedades do Banco de Dados de Distribuição** permite a exibição de várias propriedades e a definição do período de retenção da transação e do período de retenção do histórico para o banco de dados.  
  
## <a name="options"></a>Opções  
 **Nome**  
 O nome do banco de dados de distribuição, que assume o padrão “distribuição” (somente leitura).  
  
 **Locais de arquivo**  
 O local do arquivo de banco de dados e do arquivo de log (somente leitura).  
  
 **Período de retenção de transação**  
 Também conhecido como o período de retenção de distribuição. O tempo de armazenamento das transações para replicação transacional. Para obter mais informações, consulte [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md).  
  
 **Período de retenção de histórico**  
 O período de armazenamento dos metadados de histórico para todos os tipos de replicação.  
  
 **Segurança do Queue Reader Agent**  
 O Queue Reader Agent é usado pela replicação transacional com assinaturas de atualização enfileiradas. Um Agente de Leitor de Fila será criado automaticamente se você selecionar **Publicação transacional com assinaturas de atualização** na página **Tipo de Publicação** do Assistente para Nova Publicação. Clique em **Configurações de Segurança…** para alterar a conta na qual o agente é executado e efetua conexões com o Distribuidor.  
  
 Um Queue Reader Agent também pode ser criado selecionando **Criar Queue Reader Agent** nessa página (essa opção estará desabilitada se o agente já tiver sido criado).  
  
 Informações de conexão adicionais para o Queue Reader Agent são especificadas em dois lugares:  
  
-   O agente se conecta ao Publicador usando as credenciais especificadas na caixa de diálogo **Propriedades do Publicador** , disponível na página **Publicadores** da caixa de diálogo **Propriedades do Distribuidor** .  
  
-   O agente se conecta ao Assinante usando as credenciais especificadas para o Agente de Distribuição no Assistente para Nova Assinatura.  
  
 Para obter mais informações, consulte  [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
## <a name="see-also"></a>Consulte também  
 [Configurar Distribuição](../../relational-databases/replication/configure-distribution.md)   
 [Criar uma assinatura pull](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Exibir e modificar propriedades de Publicador e Distribuidor](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)  
  
  