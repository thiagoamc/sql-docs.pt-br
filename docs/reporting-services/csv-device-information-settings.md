---
title: "Configura&#231;&#245;es das informa&#231;&#245;es do dispositivo CSV | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CSV [Reporting Services]"
  - "configurações de informações do dispositivo [Reporting Services], renderização de CSV"
ms.assetid: f96f83a6-50bc-48ce-9fcd-fd9e1952d40a
caps.latest.revision: 43
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 43
---
# Configura&#231;&#245;es das informa&#231;&#245;es do dispositivo CSV
  As configurações de informações de dispositivo para a extensão de renderização de CSV permitem que os delimitadores e os qualificadores sejam alterados e o tratamento de quebra de linha seja especificado. A extensão do arquivo também pode ser enviada, como também a codificação e inclusão de linhas de cabeçalho na saída. Como é provável que os delimitadores sejam caracteres especiais, você deverá codificá-los em uma seção CDATA, se as configurações forem gravadas como XML.  
  
 A tabela a seguir lista as configurações de informações de dispositivo para renderização no formato Texto.  
  
|Configuração|Value|  
|-------------|-----------|  
|**Codificação**|O nome da IANA (Internet Assigned Numbers Authority) de uma codificação de caracteres com suporte do .NET Framework. O valor padrão é **UTF-8**. Exemplos de outros valores incluem ASCII, UTF-7 e UTF-16.|  
|**ExcelMode**|Especifica se a saída de destino é para o Excel. O valor padrão é **true**.|  
|**FieldDelimiter**|A cadeia de caracteres delimitadora para colocar no resultado. O valor padrão é uma vírgula (,). Você deve codificar o valor dessas informações de dispositivo ao transmiti-lo em uma URL. Por exemplo, um caractere de tabulação como um delimitador deve ser "%09".<br /><br /> Você pode alterar o delimitador de campo padrão para qualquer caractere que desejar, inclusive o TAB, alterando as configurações de informações de dispositivo no arquivo de configuração. Por exemplo, para usar TAB, atualize a configuração do FieldDelimiter para \<FieldDelimiter xml:space="preserve">[TAB]\</FieldDelimiter><br /><br /> No exemplo [TAB] é um caractere de tabulação real, o que significa que aparece espaço em branco no arquivo de configuração. O atributo "xml:space" instrui os analisadores para preservarem o espaço em branco.|  
|**FileExtension**|A extensão do arquivo a ser colocada no resultado. O valor padrão é **.CSV**. Se tanto **FileExtension** quanto **extensão** forem especificados, **FileExtension** terá precedência.|  
|**NoHeader**|Indica se a linha do cabeçalho será excluída da saída. O valor padrão é **false**.|  
|**Qualificador**|A cadeia de caracteres do qualificador para colocar ao redor de resultados que contêm o delimitador de campo ou delimitador de registro. Se os resultados contiverem o qualificador, ele será repetido. A configuração **Qualificador** deve ser diferente das configurações **FieldDelimiter** e **RecordDelimiter**. O valor padrão é uma aspa (").|  
|**RecordDelimiter**|O delimitador de registro a ser colocado no término de cada registro. O valor padrão é \<cr>\<lf>.|  
|**SuppressLineBreaks**|Indica se as quebras de linha serão removidas dos dados incluídos na saída. O valor padrão é **false**. Se o valor for **true**, as configurações **FieldDelimiter**, **RecordDelimiter**, e **Qualifier** não poderão ser um caractere de espaço.|  
|**UseFormattedValues**|Indica se as cadeias de caracteres formatadas são colocadas na saída do CSV. O valor padrão é **true** quando **ExcelMode** é **true**; caso contrário, será **false**.|  
  
## Consulte também  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Passando configurações de informações de dispositivos para extensões de renderização](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Personalizar parâmetros de extensão de renderização em RSReportServer.config](../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Referência técnica &#40;SSRS&#41;](../reporting-services/technical-reference-ssrs.md)  
  
  