---
title: "Exemplos: pacotes de implanta&#231;&#227;o de modelos (Master Data Services). | Microsoft Docs"
ms.custom: ""
ms.date: "02/13/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
keywords: 
  - "master data services"
  - "sample"
ms.assetid: 9b31b7b6-319b-4840-b67d-eb383e7762b1
caps.latest.revision: 21
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 20
---
# Exemplos: pacotes de implanta&#231;&#227;o de modelos (Master Data Services).
  Pacotes de modelo de exemplo com dados são incluídos durante a instalação do [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. O local padrão desses arquivos de pacote é \<drive>\Program Files\Microsoft SQL Server\130\Master Data Services\Samples\Packages.  
  
 Para obter instruções sobre como implantar os pacotes de modelo de exemplo, consulte [Implantando dados e modelos de exemplo](../sql-server/media/master-data-services.png#deploySample). Implante os pacotes de modelo de exemplo usando a [ferramenta MDSModelDeploy](../master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md).  
  
> [!IMPORTANT]  
>  **Atualizações de amostras no [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]**  
>   
>  Os pacotes de exemplo foram atualizados para dar suporte às novas funcionalidades a seguir.  
>   
>  -   Mostre relações muitos-para-muitos.  
>   
>      Para obter mais informações, consulte [Relação M2M no modelo de exemplo](../master-data-services/show-many-to-many-relationships-in-derived-hierarchies-master-data-services.md#M2MSample).  
> -   Restringir valores permitidos para atributos baseados em domínio.  
>   
>      Para obter mais informações, consulte [Criar um atributo baseado em domínio &#40;Master Data Services&#41;](../master-data-services/create-a-domain-based-attribute-master-data-services.md).  
> -   Exige aprovação para alterações de entidade.  
>   
>      Para obter mais informações, consulte [Aprovação necessária &#40;Master Data Services&#41;](../master-data-services/approval-required-master-data-services.md).  
> -   Usar operadores Not e Else em regras de negócio  
>   
>      Para obter mais informações, consulte [Exemplos de regras de negócio](../master-data-services/business-rule-examples-master-data-services.md).  
> -   Implementar um índice personalizado  
>   
>      Para obter mais informações, consulte [Índice personalizado #40;Master Data Services&#41;](../master-data-services/custom-index-master-data-services.md).  
  
 No [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], um pacote é um arquivo XML que contém uma estrutura de modelo implantável, e opcionalmente, dados do modelo. Use pacotes de modelo para mover cópias de modelos de um ambiente MDS para outro, ou crie novos modelos em seu ambiente do [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] existente.  
  
## Consulte também  
 [Implantar um pacote de implantação de modelo usando MDSModelDeploy](../master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)  
  
  