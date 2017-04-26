---
title: "Editar uma entidade (Master Data Services) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "entidades [Master Data Services], alteração do nome"
ms.assetid: 6a5b9f14-6dfc-49d7-a771-e96461d4feae
caps.latest.revision: 8
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 8
---
# Editar uma entidade (Master Data Services)
  No [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], você pode editar uma entidade.  
  
## Pré-requisitos  
 Para executar esse procedimento:  
  
-   Você deve ter permissão para acessar a área funcional **Administração do Sistema** .  
  
-   Você deve ser um administrador de modelo. Para obter mais informações, veja [Administradores &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### Para editar uma entidade  
  
1.  No [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], clique em **Administração do Sistema**.  
  
2.  Na página **Gerenciar Modelo** , escolha um modelo na grade e clique em **Entidades**.  
  
3.  Na página **Gerenciar Entidade** , na grade, selecione a linha para a entidade que você deseja editar e clique em **Editar**.  
  
4.  Na caixa **Nome** , digite o nome atualizado da entidade.  
  
5.  No campo **Descrição** , digite a descrição atualizada da entidade.  
  
6.  Na caixa **Nome para tabelas de preparo** , digite um nome atualizado para a tabela de preparo.  
  
7.  No campo **Tipo de Log de Transações**, escolha o tipo de log de transações atualizado na lista suspensa.  
  
     Para obter mais informações, consulte [Alterar o tipo de log de transações da entidade &#40;Master Data Services&#41;](../master-data-services/change-the-entity-transaction-log-type-master-data-services.md)  
  
8.  Marque ou desmarque a caixa de seleção **Criar valores de códigos automaticamente** .  
  
     Para obter mais informações, consulte [Criação automática de código &#40;Master Data Services&#41;](../master-data-services/automatic-code-creation-master-data-services.md)  
  
9. Marque ou desmarque a caixa de seleção **Habilitar a compactação de dados** . Por padrão, a compactação de linha está ativada.  
  
     Para obter mais informações, consulte [Data Compression](../relational-databases/data-compression/data-compression.md).  
  
## Status  
 A coluna de status na grade mostra o status da operação na entidade. Quando você clica em **Salvar entidade**, a imagem a seguir é exibida, indicando que a entidade está atualizando.  
  
 ![Icon for updating status](../master-data-services/media/mds-statusicon-updating.png "Icon for updating status")  
  
 Se houver erros ao criar ou editar uma entidade, a imagem a seguir será exibida.  
  
 ![Icon for error status](../master-data-services/media/mds-statusicon-error.png "Icon for error status")  
  
 Quando o status for OK, a imagem a seguir será exibida.  
  
 ![Icon for OK status](../master-data-services/media/mds-statusicon-ok.png "Icon for OK status")  
  
## Consulte também  
 [Hierarquias explícitas &#40;Master Data Services&#41;](../master-data-services/explicit-hierarchies-master-data-services.md)   
 [Excluir uma entidade &#40;Master Data Services&#41;](../master-data-services/delete-an-entity-master-data-services.md)   
 [Entidades &#40;Master Data Services&#41;](../master-data-services/entities-master-data-services.md)  
  
  