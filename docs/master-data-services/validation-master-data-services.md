---
title: "Valida&#231;&#227;o (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 98eb49e7-b190-4a21-8316-08c07cde14ed
caps.latest.revision: 12
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 12
---
# Valida&#231;&#227;o (Master Data Services)
  No [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], os dados são validados para garantir sua exatidão. Alguma validação ocorre automaticamente e outra validação é baseada em regras de negócio que são criadas por administradores.  
  
## Quando ocorre a validação de dados  
 A validação ocorre em momentos diferentes e é exibida de maneira diferente no aplicativo Web do [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
|Tipo de validação|Padrões determinados por|Quando ocorre|Exibido na interface de usuário na Web do MasterData Manager como|Exibido no suplemento para Excel como|Os dados são salvos no repositório do MDS?|  
|---------------------|-----------------------------|--------------------|---------------------------------------------------|-------------------------------------------|------------------------------------------|  
|Validação da regra de negócios|Um administrador do MDS|Automaticamente quando um usuário adiciona ou edita dados.<br /><br /> Manualmente quando um usuário aplica regras de negócio.<br /><br /> Manualmente quando um administrador na área funcional de **Gerenciamento de Versões** do aplicativo Web do [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] valida uma versão em relação às regras de negócio.|Erros de validação|ValidationStatus|Sim|  
|Validação de tipo de dados e de conteúdo|Um administrador do MDS, ao criar objetos modelo (por exemplo, o comprimento ou o tipo de dados de um atributo)|Automaticamente quando um usuário adiciona ou edita dados|Erros de entrada|InputStatus|Não|  
|Validação de tipo de dados e de conteúdo|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ou [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]|Automaticamente quando um usuário adiciona ou edita dados|Erros de entrada|InputStatus|Não|  
  
## Tarefas relacionadas  
  
|Descrição da tarefa|Tópico|  
|----------------------|-----------|  
|Criar regras de negócio e publicá-las, de forma que os dados sejam validados em relação a elas.|[Criar e publicar uma regra de negócio &#40;Master Data Services&#41;](../master-data-services/create-and-publish-a-business-rule-master-data-services.md)|  
|Validar uma versão de dados em relação às regras de negócio. Apenas administradores.|[Validar uma versão em relação a regras de negócio &#40;Master Data Services&#41;](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)|  
|Validar subconjuntos específicos de dados em relação às regras de negócio. Todos os usuários com permissão para a área funcional do **Gerenciador** .|[Validar membros específicos em relação a regras de negócio &#40;Master Data Services&#41;](../master-data-services/validate-specific-members-against-business-rules-master-data-services.md)|  
|Validar subconjuntos específicos de dados em relação às regras de negócio. Todos os usuários com permissão para a área funcional do **Gerenciador** e que usam o [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)].|[Aplicar regras de negócio &#40;Suplemento MDS para Excel&#41;](../master-data-services/microsoft-excel-add-in/apply-business-rules-mds-add-in-for-excel.md)|  
  
## Consulte também  
 [Regras de negócio &#40;Master Data Services&#41;](../master-data-services/business-rules-master-data-services.md)  
  
  