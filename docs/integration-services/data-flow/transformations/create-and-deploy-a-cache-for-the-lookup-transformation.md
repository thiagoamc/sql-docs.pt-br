---
title: "Criar e implantar um cache para a Transforma&#231;&#227;o Pesquisa | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "criando arquivos de cache para a transformação Pesquisa"
  - "implantando arquivos de cache para a transformação Pesquisa"
  - "Arquivos de cache da transformação Pesquisa"
ms.assetid: cedf5cad-2fac-42d0-ad91-9461e117d330
caps.latest.revision: 23
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 23
---
# Criar e implantar um cache para a Transforma&#231;&#227;o Pesquisa
  Você pode criar e implementar um arquivo de cache (.caw) para uma transformação Pesquisa. O conjunto de dados de referência é armazenado no arquivo de cache.  
  
 A transformação Pesquisa executa pesquisas ao unir dados em colunas de dados de uma fonte de dados conectados com colunas no conjunto de dados de referência.  
  
 Você cria um arquivo de cache usando um gerenciador de conexões de cache e uma transformação Cache. Para obter mais informações, consulte [Editor do Gerenciador de Conexões de Cache](../../../integration-services/data-flow/transformations/cache-connection-manager.md) e [Transformação de Cache](../../../integration-services/data-flow/transformations/cache-transform.md).  
  
 Para saber mais sobre a transformação Pesquisa e os arquivos de cache, consulte [Transformação Pesquisa](../../../integration-services/data-flow/transformations/lookup-transformation.md).  
  
### Para criar um arquivo de cache  
  
1.  No [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], abra o projeto do [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] que contém o pacote que você deseja, e, então, abra o pacote.  
  
2.  Na guia **Fluxo de Controle**, adicione uma tarefa de Fluxo de Dados.  
  
3.  Na guia **Fluxo de Dados**, adicione uma transformação Cache Transform ao fluxo de dados, e, então, conecte a transformação à fonte de dados.  
  
     Configure a fonte de dados como necessário.  
  
4.  Clique duas vezes na transformação Cache e, depois, em **Editor de Transformação Cache**, na página **Gerenciador de Conexões**, clique em **Novo** para criar um novo gerenciador de conexões de Cache.  
  
5.  No **Editor do Gerenciador de Conexões de Cache**, na guia **Geral**, configure o gerenciador de conexões de cache para salvar o cache selecionando as seguintes opções:  
  
    1.  Selecione **Usar Cache de Arquivo**.  
  
    2.  Para **Nome do arquivo**, digite o caminho de arquivo.  
  
     O sistema cria o arquivo quando você executa o pacote.  
  
    > [!NOTE]  
    >  O nível de proteção do pacote não se aplica ao arquivo de cache. Se o arquivo de cache tiver informações confidenciais, use uma lista de controle de acesso (ACL) para restringir o acesso ao local ou à pasta na qual você deseja armazenar o arquivo. Você deve habilitar o acesso apenas para determinadas contas. Para obter mais informações, consulte [Acesso aos arquivos usados por pacotes](../../../integration-services/security/access-to-files-used-by-packages.md).  
  
6.  Clique na guia **Colunas** e, então, especifique quais são as colunas de índice usando a opção **Posição do Índice** .  
  
     Para colunas sem-índice, a posição de índice é 0. Para colunas de índice, a posição de índice é um número sequencial positivo.  
  
    > [!NOTE]  
    >  Quando a transformação Pesquisa é configurada para usar um gerenciador de conexões de Cache, somente as colunas de índice no conjunto de dados de referência podem ser mapeadas para as colunas de entrada. Além disso, todas as colunas de índice devem ser mapeadas.  
  
     Para obter mais informações, consulte [Cache Connection Manager Editor](../../../integration-services/data-flow/transformations/cache-connection-manager-editor.md).  
  
7.  Configure o Cache Transform como necessário.  
  
     Para obter mais informações, consulte [Editor de Transformação Cache &#40;Página Gerenciador de Conexões&#41;](../../../integration-services/data-flow/transformations/cache-transformation-editor-connection-manager-page.md) e [Editor de Transformação Cache &#40;Página Mapeamentos&#41;](../../../integration-services/data-flow/transformations/cache-transformation-editor-mappings-page.md).  
  
8.  Execute o pacote.  
  
### Para implementar um arquivo de cache  
  
1.  No [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], abra o projeto do [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] que contém o pacote que você deseja, e, então, abra o pacote.  
  
2.  Opcionalmente, crie uma configuração de pacote Para obter mais informações, consulte [Criar configurações de pacote](../../../integration-services/packages/create-package-configurations.md).  
  
3.  Adicione o arquivo de cache ao projeto fazendo o seguinte:  
  
    1.  No Gerenciador de Soluções, selecione o projeto que você abriu na etapa 1.  
  
    2.  No menu **Projeto**, clique em **Item AddExisting**.  
  
    3.  Selecione o arquivo de cache e clique em **Adicionar**.  
  
     O arquivo aparece na pasta **Diversos** no Gerenciador de Soluções.  
  
4.  Configure o projeto para criar um utilitário de implantação e, em seguida, crie o projeto. Para obter mais informações, consulte [Criar um utilitário de implantação](../../../integration-services/packages/create-a-deployment-utility.md).  
  
     Um arquivo de manifesto, \<*nome do projeto*>.SSISDeploymentManifest.xml é criado e lista os arquivos diversos no projeto, os pacotes e as configurações de pacote.  
  
5.  Implemente os pacotes no sistema de arquivos Para obter mais informações, consulte [Implantar pacotes por meio do utilitário de implantação](../../../integration-services/packages/deploy-packages-by-using-the-deployment-utility.md).  
  
## Consulte também  
 [Criar um utilitário de implantação](../../../integration-services/packages/create-a-deployment-utility.md)  
  
  