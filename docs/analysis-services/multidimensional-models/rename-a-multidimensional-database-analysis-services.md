---
title: "Renomear um bancos de dados multidimensional (Analysis Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "renomeando bancos de dados"
ms.assetid: 15fdaec7-f3e4-44d9-9b78-1a1d78c484e0
caps.latest.revision: 20
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 20
---
# Renomear um bancos de dados multidimensional (Analysis Services)
  A maneira como você altera o nome de um banco de dados do [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] depende de como você se conecta ao banco de dados do [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Para alterar o nome de um banco de dados existente, conecte-se em modo online. Para alterar o nome do banco de dados no qual os objetos de um projeto do [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] serão instanciados, conecte-se em modo de projeto.  
  
### Alterar o nome do banco de dados em modo online  
  
1.  Usando o [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], conecte-se diretamente ao banco de dados do [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
2.  No Gerenciador de Soluções, clique com o botão direito do mouse no banco de dados e clique em **Editar Banco de Dados**.  
  
3.  Na caixa de texto **Nome do Banco de Dados** , altere o nome do banco de dados.  
  
4.  Clique em **Salvar** ou em **Salvar Tudo** na barra de ferramentas, clique em **Salvar Itens Selecionados** ou em **Salvar Tudo** no menu **Arquivo** ou feche o **Designer de Banco de Dados** e, em seguida, clique em **Salvar** quando solicitado.  
  
     O nome de banco de dados é atualizado na instância do [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , bem como o objeto de banco de dados no Gerenciador de Soluções.  
  
### Alterar o nome do banco de dados em modo de projeto  
  
1.  Abra o projeto do [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
2.  No Gerenciador de Soluções, clique com o botão direito do mouse no projeto do [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] e clique em **Propriedades**.  
  
3.  Na caixa de diálogo **Páginas de Propriedades** , clique em **Implantação** na seção **Propriedades de Configuração** .  
  
4.  Altere a propriedade **Banco de Dados** com o novo nome do banco de dados.  
  
     Na próxima vez que o projeto do [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] for implantado, ele será implantado com esse novo nome de banco de dados. Se existir um banco de dados com o mesmo nome, ele será substituído.  
  
### Para alterar o nome do banco de dados usando o SQL Server Management Studio  
  
-   Clique com o botão direito do mouse no banco de dados [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] e edite a propriedade Name.  
  
## Consulte também  
 [Propriedades do servidor do Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
 [Definir as propriedades de banco de dados multidimensional &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/set-multidimensional-database-properties-analysis-services.md)   
 [Configurar propriedades do projeto do Analysis Services &#40;SSDT&#41;](../../analysis-services/multidimensional-models/configure-analysis-services-project-properties-ssdt.md)   
 [Implantar projetos do Analysis Services &#40;SSDT&#41;](../../analysis-services/multidimensional-models/deploy-analysis-services-projects-ssdt.md)  
  
  