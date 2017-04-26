---
title: "Implantando modelos (Master Data Services) | Microsoft Docs"
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
  - "pacotes de implantação [Master Data Services], sobre os pacotes de implantação"
  - "pacotes de implantação [Master Data Services]"
ms.assetid: 30085c08-034f-4efe-80fe-408f9091ff5c
caps.latest.revision: 24
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 24
---
# Implantando modelos (Master Data Services)
  No [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], um pacote é um arquivo XML que contém uma estrutura de modelo implantável, e opcionalmente, dados do modelo. Use pacotes modelo para mover cópias de modelos de um ambiente MDS para outro, ou crie novos modelos em seu ambiente MDS existente.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] A **ferramenta MDSModelDeploy** é compatível com versões anteriores com os pacotes criados no [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] ou superior.  
  
## Ferramentas para implantar modelos  
 Para trabalhar com pacotes de modelo, você pode usar uma das três ferramentas, dependendo de suas necessidades.  
  
-   **Ferramenta MDSModelDeploy**: para criar e implantar objetos de modelo e dados, use a ferramenta MDSModelDeploy.exe. Se você tiver selecionado o caminho padrão ao instalar o MDS, essa ferramenta estará localizada em *drive*:\Program Files\Microsoft SQL Server\130\Master Data Services\Configuration.  
  
-   **Assistente para Implantação de Modelo**: para criar e implantar pacotes somente da estrutura de modelo, use o assistente no aplicativo Web do [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]. Você não pode usar esse assistente para implantar dados.  
  
-   **Editor de Pacote de Modelo**: para editar um pacote de modelo, use o ModelPackageEditor.exe, que inicia o assistente do Editor de Pacote de Modelo. Use esse assistente para editar um pacote criado pela ferramenta MDSModelDeploy ou pelo assistente de Implantação de Modelo. Se você tiver selecionado o caminho padrão ao instalar o MDS, essa ferramenta estará localizada em *drive*:\Program Files\Microsoft SQL Server\130\Master Data Services\Configuration.  
  
> [!IMPORTANT]  
>  Você pode usar a ferramenta MDSModelDeploy para criar um novo modelo, criar um clone de um modelo ou atualizar um modelo existente e seus dados. Se você usar a ferramenta MDSModelDeploy para atualizar um modelo existente e seus dados, e o pacote não contiver uma entidade, um atributo ou um membro que exista no modelo de destino, MDSModelDeploy não excluirá a entidade, o atributo ou o membro do modelo.  
  
## O que os pacotes contêm  
 Um pacote de modelo é um arquivo XML salvo com a extensão .pkg. Ao criar um pacote de implantação, é possível optar por incluir dados ou não. Se decidir incluir dados, você deverá selecionar uma versão dos dados a ser incluída.  
  
 Todos os objetos de modelo são incluídos em um pacote. Esses objetos são:  
  
-   Entidades  
  
-   Atributos  
  
-   Grupos de atributos  
  
-   Hierarquias  
  
-   Coleções  
  
-   Regras de negócio  
  
-   Sinalizadores de versão  
  
-   Exibições de assinatura  
  
 Atributos de arquivo e permissões de grupo e usuário não estão incluídos. Depois de implantar um modelo, você deve atualizar esses objetos manualmente.  
  
## Pacotes de exemplo  
 Arquivos de pacotes de exemplo são incluídos quando você instala o [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. Estes arquivos de pacotes estão no diretório Master Data Services\Samples\Packages onde o [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] foi instalado. Quando você implanta esses pacotes de exemplo usando a ferramenta MDSModelDeploy, modelos de exemplo são criados e populados com dados.  
  
## Tarefas relacionadas  
  
|Descrição da tarefa|Tópico|  
|----------------------|-----------|  
|Crie um novo pacote de implantação de objetos de modelo e/ou dados usando a ferramenta MDSModelDeploy.|[Criar um pacote de implantação de modelo usando o MDSModelDeploy](../master-data-services/create-a-model-deployment-package-by-using-mdsmodeldeploy.md)|  
|Crie um novo pacote de implantação somente de objetos de modelo usando o assistente.|[Criar um pacote de implantação de modelo usando o Assistente](../master-data-services/create-a-model-deployment-package-by-using-the-wizard.md)|  
|Implante um pacote de objetos de modelo e dados usando a ferramenta MDSModelDeploy.|[Implantar um pacote de implantação de modelo usando MDSModelDeploy](../master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)|  
|Implante um pacote somente de objetos de modelo usando o assistente.|[Implantar um pacote de implantação de modelo usando o Assistente](../master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md)|  
|Edite um pacote de implantação de modelo para implantar partes selecionadas de um modelo, em vez do modelo inteiro.|[Editar um pacote de implantação de modelo](../master-data-services/edit-a-model-deployment-package.md)|  
  
## Conteúdo relacionado  
  
-   [Opções de implantação de modelo &#40;Master Data Services&#41;](../master-data-services/model-deployment-options-master-data-services.md)  
  
  