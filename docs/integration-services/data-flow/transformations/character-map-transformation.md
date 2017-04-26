---
title: "Transforma&#231;&#227;o Mapas de Caracteres | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.charactertrans.f1"
helpviewer_keywords: 
  - "mapeamento mutuamente exclusivo [Integration Services]"
  - "mapeando dados [Integration Services]"
  - "funções de cadeia de caracteres"
  - "Transformação Mapa de Caracteres [Integration Services]"
ms.assetid: e0f50eb6-b893-400f-bb8c-fb3072cc2620
caps.latest.revision: 42
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 42
---
# Transforma&#231;&#227;o Mapas de Caracteres
  A transformação Mapa de Caracteres aplica funções de cadeia de caracteres, como a conversão de letra minúscula em maiúscula, em dados de caracteres. Essa transformação funciona apenas em dados de coluna com um tipo de dados de cadeia de caracteres.  
  
 A transformação Mapa de Caracteres pode converter dados de coluna existentes ou adicionar uma coluna à saída de transformação e colocar os dados convertidos na coluna nova. Você pode aplicar conjuntos diferentes de operações de mapeamento na mesma coluna de entrada e colocar os resultados em colunas diferentes. Por exemplo, é possível converter a mesma coluna em maiúsculas e minúsculas e colocar os resultados em duas colunas diferentes.  
  
 O mapeamento pode, em algumas circunstâncias, fazer com que os dados fiquem truncados. Por exemplo, o truncamento pode acontecer quando caracteres de byte único são mapeados para caracteres com representação de vários bytes. A transformação Mapa de Caracteres inclui uma saída de erro, que pode ser usada para direcionar dados truncados para uma saída separada. Para obter mais informações, consulte [Tratamento de erros em dados](../../../integration-services/data-flow/error-handling-in-data.md).  
  
 Essa transformação tem uma entrada, uma saída e uma saída de erro.  
  
## Mapeando operações  
 A tabela a seguir descreve as operações de mapeamento suportadas pela transformação Mapa de Caracteres.  
  
|Operação|Description|  
|---------------|-----------------|  
|Inversão de bytes|Inverte a ordem de bytes.|  
|Largura inteira|Mapeia caracteres de meia largura para caracteres de largura inteira.|  
|Meia largura|Mapeia caracteres de largura inteira para caracteres de meia largura.|  
|Hiragana|Mapeia caracteres katakana para caracteres hiragana.|  
|Katakana|Mapeia caracteres hiragana para caracteres katakana.|  
|Caixas linguísticas|Aplica caixas linguísticas em vez de regras do sistema. As caixas linguísticas se referem à funcionalidade fornecida pela API do Win32 para mapeamento de maiúsculas/minúsculas simples de Unicode de idiomas turcomanos e de outras localidades.|  
|Minúscula|Converte caracteres em minúsculas.|  
|Chinês simplificado|Mapeia caracteres de chinês tradicional para caracteres de chinês simplificado.|  
|Chinês tradicional|Mapeia caracteres de chinês simplificado para caracteres de chinês tradicional.|  
|Letras Maiúsculas|Converte caracteres em maiúsculas.|  
  
## Operações de mapeamento mutuamente exclusivas  
 Mais de uma operação pode ser executada em uma transformação. Entretanto, algumas operações de mapeamento são mutuamente exclusivas. A tabela a seguir relaciona restrições que se aplicam quando você usa várias operações na mesma coluna. As operações nas colunas Operação A e Operação B são mutuamente exclusivas.  
  
|Operação A|Operação B|  
|-----------------|-----------------|  
|Minúscula|Letras Maiúsculas|  
|Hiragana|Katakana|  
|Meia largura|Largura inteira|  
|Chinês tradicional|Chinês simplificado|  
|Minúscula|Hiragana, katakana, meia largura, largura inteira|  
|Letras Maiúsculas|Hiragana, katakana, meia largura, largura inteira|  
  
## Configuração da transformação Mapa de Caracteres  
 Você pode configurar a transformação Mapa de Caracteres das seguintes formas:  
  
-   Especificando as colunas a serem convertidas.  
  
-   Especificando as operações a serem aplicadas em cada coluna.  
  
 Você pode definir propriedades pelo Designer do [!INCLUDE[ssIS](../../../includes/ssis-md.md)] ou programaticamente.  
  
 Para obter mais informações sobre as propriedades que podem ser definidas na caixa de diálogo **Editor de Transformação de Mapas de Caracteres** , consulte [Character Map Transformation Editor](../../../integration-services/data-flow/transformations/character-map-transformation-editor.md).  
  
 A caixa de diálogo **Editor Avançado** reflete as propriedades que podem ser definidas programaticamente. Para obter mais informações sobre as propriedades que podem ser definidas na caixa de diálogo **Editor Avançado** ou programaticamente, clique em um dos seguintes tópicos:  
  
-   [Propriedades comuns](../Topic/Common%20Properties.md)  
  
-   [Propriedades personalizadas de Transformação](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)  
  
 Para obter mais informações sobre como definir propriedades, clique em um dos seguintes tópicos:  
  
-   [Definir as propriedades de um componente de fluxo de dados](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)  
  
-   [Classificar dados para as transformações Mesclagem e Junção de Mesclagem](../../../integration-services/data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md)  
  
  