---
title: "Criar uma nova condi&#231;&#227;o de Gerenciamento baseado em Pol&#237;ticas | Microsoft Docs"
ms.custom: ""
ms.date: "08/01/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Gerenciamento Baseado em Políticas, criando condições da política"
ms.assetid: 8a612f7e-6c70-49db-a4de-48431e097cc5
caps.latest.revision: 11
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 11
---
# Criar uma nova condi&#231;&#227;o de Gerenciamento baseado em Pol&#237;ticas
  Este tópico descreve como criar uma condição de Gerenciamento Baseado em Políticas no [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] usando o [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **Neste tópico**  
  
-   **Antes de começar:**  
  
     [Segurança](#Security)  
  
-   **Para criar uma condição, usando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Antes de começar  
  
###  <a name="Security"></a> Segurança  
  
####  <a name="Permissions"></a> Permissões  
 Requer a associação à função PolicyAdministratorRole no banco de dados msdb.  
  
##  <a name="SSMSProcedure"></a> Usando o SQL Server Management Studio  
  
#### Para criar uma condição  
  
1.  No **Pesquisador de Objetos**, clique no sinal de adição para expandir o servidor no qual você deseja criar uma condição de Gerenciamento Baseado em Políticas.  
  
2.  Clique no sinal de adição para expandir a pasta **Gerenciamento** .  
  
3.  Clique no sinal de adição para expandir a pasta **Gerenciamento de Política**.  
  
4.  Clique no sinal de adição para expandir a pasta **Facetas** .  
  
5.  Clique com o botão direito do mouse na faceta em que você deseja criar uma nova condição e selecione **Nova Condição**.  
  
6.  Na caixa de diálogo **Criar Nova Condição** , na caixa **Nome** , digite o nome da nova condição.  
  
7.  Confirme a faceta correta na lista **Faceta** ou selecione uma faceta diferente.  
  
8.  Em **Expressão**, construa expressões de condição selecionando uma propriedade de faceta na caixa **Campo** , junto com o operador e o valor associados. Quando você adicionar várias expressões, as expressões podem ser unidas usando **E** ou **Ou**. Para obter mais informações sobre as opções disponíveis nesta caixa de diálogo, veja [Caixa de diálogo Criar Nova Condição ou Abrir Condição, Página Geral](../../relational-databases/policy-based-management/create-new-condition-or-open-condition-dialog-box-general-page.md), [Caixa de diálogo Criar Nova Condição ou Abrir Condição, Página de Descrição](../../relational-databases/policy-based-management/create-new-condition-or-open-condition-dialog-box-description-page.md) e [Caixa de diálogo Edição Avançada &#40;Condição&#41;](../../relational-databases/policy-based-management/advanced-edit-condition-dialog-box.md).  
  
9. Quando terminar, clique em **OK**.  
  
  