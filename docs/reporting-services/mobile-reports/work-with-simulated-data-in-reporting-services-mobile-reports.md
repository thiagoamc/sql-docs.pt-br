---
title: "Trabalhar com dados simulados em relat&#243;rios do Reporting Services m&#243;veis | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "02/08/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6baabc36-58fb-4a98-bb9c-c42bafb16d0f
caps.latest.revision: 9
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 9
---
# Trabalhar com dados simulados em relat&#243;rios do Reporting Services m&#243;veis
Quando você coloca um elemento de galeria na superfície do design, [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)] gera imediatamente dados simulados para esse elemento. Esses dados servem para várias finalidades úteis ao criar relatórios móveis.   
  
![SS_MRP_SimDataTreeMapProps](../../reporting-services/mobile-reports/media/ss-mrp-simdatatreemapprops.png)  
  
Dados simulados ajudam ao usar uma abordagem baseada em projeto para a criação de relatório móvel. Inicialmente, o preenchimento de elementos com dados simulados permite que você crie protótipos de relatório móveis rapidamente sem ter que lidar com requisitos específicos de dados. Esses relatórios móveis podem, então, ser avaliados quanto a estética e eficiência geral.  
  
## Criar um arquivo do Excel com dados simulados como modelo  
  
Dados simulados também fornecem um modelo que representa com precisão os requisitos de dados de um design de relatório móvel específico.   
  
-  Clique em **Exportar todos os dados** no canto superior direito da Exibição de Dados.   
  
[!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)] gera um documento do Excel que contém os dados simulados, permitindo a rápida substituição de dados reais, prontos para importação.   
  
## Como os dados simulados se comportam  
  
Os dados simulados gerados são projetados especificamente para o relatório móvel que você está criando. À medida que você coloca mais elementos na superfície do design, os dados simulados associados aumentam e mudam para fornecer a melhor experiência possível sem dados reais. Essa evolução garante que campos extras e possibilidades de filtro estejam disponíveis, caso você adicione séries extras às visualizações do gráficos ou expanda o escopo de um ou mais elementos do relatório móvel de outra maneira.  
  
Conforme mencionado anteriormente, você pode exportar dados simulados para um arquivo do Excel, criando um modelo de dados perfeito para o relatório móvel associado. Você pode trocar seus próprios dados reais no arquivo do Excel e importá-lo novamente para o [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)].   
  
Depois que todos os controles são associados a dados reais, as tabelas simuladas que não estão mais em uso são automaticamente removidas do relatório móvel. Não é possível remover tabelas simuladas ainda referenciadas por elementos na superfície do design.  
  
>**Observação**: dados simulados não acrescentam à superfície geral móvel do relatório porque não são serializados com o relatório móvel, mas geradas dinamicamente em tempo de execução.  
  
### Consulte também  
- [Criar e publicar relatórios móveis com o Publicador de Relatórios Móveis do SQL Server](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)  
-  Exibir [relatórios móveis do SQL Server e KPIs no aplicativo de iPad](https://pbiwebprod-docs.azurewebsites.net/en-us/documentation/powerbi-mobile-ipad-kpis-mobile-reports) (Power BI para iOS)  
-  Exibir [relatórios móveis do SQL Server e KPIs no aplicativo do iPhone](https://pbiwebprod-docs.azurewebsites.net/en-us/documentation/powerbi-mobile-iphone-kpis-mobile-reports) (Power BI para iOS)  
  
  
  
  
  