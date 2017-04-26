---
title: "Li&#231;&#227;o 1: Preparando-se para criar o pacote de implanta&#231;&#227;o | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: b6fe283c-9856-4ba1-a497-e3912424fd18
caps.latest.revision: 21
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 21
---
# Li&#231;&#227;o 1: Preparando-se para criar o pacote de implanta&#231;&#227;o
Nesta lição, você criará as pastas de trabalho e as variáveis de ambiente que oferecem suporte ao tutorial, criará um projeto [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], adicionará vários pacotes e seus arquivos de suporte ao projeto e implementará configurações em pacotes.  
  
[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] implanta pacotes em uma base de projeto; portanto, como a primeira etapa na criação do pacote de implantação, você deve coletar todos os pacotes e dependências de pacotes em um único projeto do [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Normalmente é útil incluir outras informações com os pacotes implantados: por exemplo, você também adicionará ao projeto um arquivo Leiame, que fornece a documentação básica para esse grupo de pacotes.  
  
Depois que você adicionar os pacotes e os arquivos, adicionará configurações aos pacotes que ainda não usam as configurações. As configurações atualizam as propriedades dos pacotes e os objetos do pacote em tempo de execução. Em uma lição posterior, você modificará os valores dessas configurações durante a implantação de pacotes para oferecer suporte aos pacotes no ambiente implantado.  
  
Depois que você adicionar as configurações, deverá abrir os pacotes no Designer [!INCLUDE[ssIS](../includes/ssis-md.md)], a ferramenta gráfica do [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] para compilação de pacotes ETL, e examinar as propriedades e os elementos do pacote, assim como as configurações de pacote, para entender melhor os problemas que a implantação precisa resolver. Por exemplo, um dos pacotes extrai dados de arquivos de texto, portanto, o local dos arquivos de dados deve ser atualizado antes dos pacotes serem implantados com êxito.  
  
**Tempo estimado para concluir esta lição:** 1 hora  
  
## Tarefas da lição  
Esta lição contém as seguintes tarefas:  
  
-   [Etapa 1: Criando pastas de trabalho e variáveis de ambiente](../integration-services/step-1-creating-working-folders-and-environment-variables.md)  
  
-   [Etapa 2: Criando o projeto de implantação](../integration-services/step-2-creating-the-deployment-project.md)  
  
-   [Etapa 3: Adicionando pacotes e outros arquivos](../integration-services/step-3-adding-packages-and-other-files.md)  
  
-   [Etapa 4: Adicionando configurações de pacote](../integration-services/step-4-adding-package-configurations.md)  
  
-   [Etapa 5: Testando os pacotes atualizados](../integration-services/step-5-testing-the-updated-packages.md)  
  
## Iniciar a lição  
[Etapa 1: Criando pastas de trabalho e variáveis de ambiente](../integration-services/step-1-creating-working-folders-and-environment-variables.md)  
  
  
  