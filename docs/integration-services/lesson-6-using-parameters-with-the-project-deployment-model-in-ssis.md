---
title: "Li&#231;&#227;o 6: Usando par&#226;metros com o modelo de implanta&#231;&#227;o de projetos no SSIS | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 9216f18c-1762-4f2d-8c22-bd0ab7107555
caps.latest.revision: 5
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 5
---
# Li&#231;&#227;o 6: Usando par&#226;metros com o modelo de implanta&#231;&#227;o de projetos no SSIS
O SQL Server 2012 apresenta um novo modelo de implantação em que você pode implantar seus projetos no servidor do Integration Services. O servidor do Integration Services permite gerenciar e executar pacotes e configurar valores de tempo de execução para pacotes.  
  
Nesta lição, você aprenderá a modificar o pacote criado na [Lição 5: Adicionar configurações do pacote SSIS ao modelo de implantação de pacotes](../integration-services/lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md) para usar o Modelo de Implantação do Projeto. Você substitui o valor de configuração com um parâmetro para especificar o local de dados de exemplo. Você também pode copiar o pacote concluído da Lição 5 que está incluso no tutorial.  
  
Usando o Assistente de Configuração de Projeto do Integration Services, você converterá o projeto no Modelo de Implantação do Projeto e usará um parâmetro, em vez de um valor de configuração, para definir a propriedade do Diretório. Esta lição abrange parcialmente as etapas que você seguirá para converter os pacotes SSIS existentes no novo Modelo de Implantação do Projeto.  
  
Quando você executar o pacote novamente, o serviço Integration Services usará o parâmetro para popular o valor da variável e, por sua vez, a variável atualizará a propriedade Diretório. Assim, o pacote itera pelos arquivos na nova pasta de dados especificada pelo valor de parâmetro, em vez da pasta que foi definida no arquivo de configuração do pacote.  
  
> [!IMPORTANT]  
> Este tutorial requer o banco de dados de exemplo **AdventureWorksDW2012** . Para obter mais informações sobre como instalar e implantar o **AdventureWorksDW2012**, consulte [Considerações sobre a instalação de amostras e bancos de dados de exemplo do SQL Server](http://technet.microsoft.com/en-us/library/ms161556%28v=sql.105%29).  
  
## Tarefas da lição  
Esta lição contém as seguintes tarefas:  
  
1.  [Etapa 1: Copiando o pacote da Lição 5](../integration-services/step-1-copying-the-lesson-5-package.md)  
  
2.  [Etapa 2: Convertendo o projeto para o modelo de implantação de projetos](../integration-services/step-2-converting-the-project-to-the-project-deployment-model.md)  
  
3.  [Etapa 3: Testando o pacote da Lição 6](../integration-services/step-3-testing-the-lesson-6-package.md)  
  
4.  [Etapa 4: Implantando o pacote da Lição 6](../integration-services/step-4-deploying-the-lesson-6-package.md)  
  
## Iniciar a lição  
[Etapa 1: Copiando o pacote da Lição 5](../integration-services/step-1-copying-the-lesson-5-package.md)  
  