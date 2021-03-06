---
title: Rastreamento (Master Data Services) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: non-specific
ms.reviewer: 
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45823fc8-723a-49f2-9a11-94d241245cfd
caps.latest.revision: 
author: leolimsft
ms.author: lle
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 72a82c699ff117d2b9b87ffec8ea2b4c97cae66f
ms.sourcegitcommit: 6ac1956307d8255dc544e1063922493b30907b80
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2018
---
# <a name="tracing-master-data-services"></a>Rastreamento (Master Data Services)
  O arquivo Web.config contém uma seção de rastreamento, conforme mostrado abaixo. Esta seção é nova no [!INCLUDE[ssSQL15](../includes/sssql15-md.md)][!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]  
  
```  
<sources>  
      <!-- Adjust the switch value to control the types of messages that should be logged.   
           http://msdn.microsoft.com/en-us/library/system.diagnostics.sourcelevels  
           Use the a switchValue of Verbose to generate a full log. Please be aware that   
           the trace file can get quite large very quickly -->  
      <source name="MDS" switchType="System.Diagnostics.SourceSwitch" switchValue="Warning, ActivityTracing">  
        <listeners>  
          <!-- Set a directory path where the service account you chose while setting up Master Data Services has read and write privileges.  
               Default path is Logs in WebApplication folder, for example C:\Program Files\Microsoft SQL Server\130\Master Data Services\WebApplication  
               New log file will be created every day or every 10 mb.  
               When directory size hits the 200mb limitation, the oldest file will be deleted.-->  
          <add name="FileTraceListener"  
               type="Microsoft.MasterDataServices.Core.Logging.FileTraceListener, Microsoft.MasterDataServices.Core"   
               initializeData="DirectoryPath = Logs; FileSizeInMb = 10; MaxDirectorySizeInMb = 200"/>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
  
```  
  
 Este é o comportamento de rastreamento padrão.  
  
-   O rastreamento está habilitado para mensagens de Aviso e de Rastreamento de Atividades.  
  
     Para saber mais, veja [Enumeração SourceLevels](https://msdn.microsoft.com/en-us/library/system.diagnostics.sourcelevels).  
  
-   Os logs são salvos na pasta Logs na pasta WebApplication. O local padrão é C:\Arquivos de Programas\Microsoft SQL Server\130\Master Data Services\WebApplication\Logs.  
  
-   O arquivo é criado para cada dia ou a cada 10 MB.  
  
-   Quando o tamanho atingir 200 MB, o log mais antigo será excluído.  
  
-   O formato de log é CSV. A tabela a seguir descreve o formato de log.  
  
    |Elemento|Description|  
    |-------------|-----------------|  
    |Hora|Quando ocorre a entrada de rastreamento.|  
    |CorrelationID|Uma ID de correlação é atribuída a cada solicitação. Todos os rastreamentos disparados por esta solicitação compartilharão a mesma ID de correlação.<br /><br /> Quando ocorre um erro na interface do usuário, a ID de correlação aparece na mensagem de erro.|  
    |Operação|Nome da operação de solicitação. Se a solicitação for uma solicitação de interface do usuário da Web, o nome da operação será a url. Se a solicitação for uma solicitação de API, o nome da operação será o nome do serviço.|  
    |Nível|Nível desta entrada de rastreamento.|  
    |Mensagem|O corpo da mensagem do rastreamento|  
  
## <a name="external-resources"></a>Recursos externos  
 Postagem de blog, [Troubleshooting Logging Improvement (Aperfeiçoamento da Solução de Problemas de Log)](http://go.microsoft.com/fwlink/p/?LinkId=615377), no msdn.com.  
  
  
