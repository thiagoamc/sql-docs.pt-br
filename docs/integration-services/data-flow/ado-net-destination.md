---
title: "Destino do ADO NET  | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.adonetdest.f1"
helpviewer_keywords: 
  - "destinos [Integration Services], ADO.NET"
  - "destino ADO.NET"
ms.assetid: cb883990-d875-4d8b-b868-45f9f15ebeae
caps.latest.revision: 28
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 28
---
# Destino do ADO NET 
  O destino ADO NET carrega dados em uma variedade de bancos de dados compatíveis com o [!INCLUDE[vstecado](../../includes/vstecado-md.md)] que utilizam uma tabela ou exibição de banco de dados. Você tem a opção de carregar esses dados em uma tabela ou exibição existente ou de criar uma nova tabela e carregar os dados nessa tabela.  
  
 Você pode usar o destino do ADO NET para conectar-se ao [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)]. Não há suporte para a conexão ao [!INCLUDE[ssSDS](../../includes/sssds-md.md)] com o uso do OLE DB. Para obter mais informações sobre o [!INCLUDE[ssSDS](../../includes/sssds-md.md)], consulte [Diretrizes gerais e limitações (Banco de dados SQL do Microsoft Azure)](http://go.microsoft.com/fwlink/?LinkId=248228).  
  
## Solucionando problemas do destino ADO NET  
 Você pode registrar as chamadas que o destino ADO NET faz para provedores de dados externos. É possível usar essa capacidade de registro para solucionar o problema de salvar os dados em fontes de dados externas que o destino ADO NET executa. Para registrar as chamadas que o destino ADO NET faz aos provedores de dados externos, habilite o registro de pacotes e selecione o evento **Diagnóstico** no nível de pacotes. Para obter mais informações, consulte [Solucionando problemas de ferramentas para execução de pacotes](../../integration-services/troubleshooting/troubleshooting-tools-for-package-execution.md).  
  
## Configurando o destino ADO NET  
 Esse destino usa um gerenciador de conexões do [!INCLUDE[vstecado](../../includes/vstecado-md.md)] para conectar-se a uma fonte de dados e o gerenciador de conexões especifica o provedor do [!INCLUDE[vstecado](../../includes/vstecado-md.md)] a ser usado. Para obter mais informações, consulte [Gerenciador de conexões ADO.NET](../../integration-services/connection-manager/ado-net-connection-manager.md).  
  
 Um destino ADO NET inclui mapeamentos entre as colunas de entrada e as colunas da fonte de dados de destino. Você não precisa mapear colunas de entrada para todas as colunas de destino. No entanto, as propriedades de algumas colunas de destino podem precisar do mapeamento de colunas de entrada. Caso contrário, podem ocorrer erros. Por exemplo, se uma coluna de destino não permitir valores nulos, você deve mapear uma coluna de entrada para aquela coluna de destino. Além disso, os tipos de dados de colunas mapeadas devem ser compatíveis. Por exemplo, você não poderá mapear uma coluna de entrada com um tipo de dados String para uma coluna de destino com um tipo de dados numéricos se o provedor do [!INCLUDE[vstecado](../../includes/vstecado-md.md)] não der suporte a este mapeamento.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] não dá suporte à inserção de texto em colunas cujo tipo de dados é definido como imagem. Para obter mais informações sobre o tipo de dados [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], veja [Tipos de dados &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md).  
  
> [!NOTE]  
>  O destino ADO NET não dá suporte ao mapeamento de uma coluna de entrada cujo tipo é definido como DT_DBTIME para uma coluna de banco de dados cujo tipo é definido como data e hora. Para obter mais informações sobre tipos de dados [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], consulte [Tipos de Dados do Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
 O destino ADO NET tem uma entrada regular e uma saída de erro.  
  
 Você pode definir propriedades pelo Designer do [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou programaticamente.  
  
 Para obter mais informações sobre as propriedades que podem ser definidas na caixa de diálogo **Editor do Destino ADO NET**, clique em um dos seguintes tópicos:  
  
-   [Editor de Destino ADO NET &#40;página Gerenciador de Conexões&#41;](../../integration-services/data-flow/ado-net-destination-editor-connection-manager-page.md)  
  
-   [Editor de Destino ADO NET &#40;página Mapeamentos&#41;](../../integration-services/data-flow/ado-net-destination-editor-mappings-page.md)  
  
-   [Editor de Destino ADO NET &#40;Página Saída de Erro&#41;](../../integration-services/data-flow/ado-net-destination-editor-error-output-page.md)  
  
 A caixa de diálogo **Editor Avançado** reflete as propriedades que podem ser definidas programaticamente. Para obter mais informações sobre as propriedades que podem ser definidas na caixa de diálogo **Editor Avançado** ou programaticamente, clique em um dos seguintes tópicos:  
  
-   [Propriedades comuns](../Topic/Common%20Properties.md)  
  
-   [Propriedades personalizadas do ADO NET](../../integration-services/data-flow/ado-net-custom-properties.md)  
  
 Para obter mais informações sobre como definir as propriedades, consulte [Definir as propriedades de um componente de fluxo de dados](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
  