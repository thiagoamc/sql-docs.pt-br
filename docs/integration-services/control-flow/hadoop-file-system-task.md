---
title: "Tarefas do Sistema de Arquivos Hadoop | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.ssis.designer.hadoopfiletask.f1"
ms.assetid: 594aaf5d-7703-4788-897d-fb95aca798c5
caps.latest.revision: 7
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 7
---
# Tarefas do Sistema de Arquivos Hadoop
  A Tarefa do Sistema de Arquivos Hadoop habilita um pacote do SSIS a copiar arquivos de, para ou dentro de um cluster Hadoop.  
  
 Para adicionar uma Tarefa do Sistema de Arquivos Hadoop, arraste-a e solte-a no designer. Em seguida, clique duas vezes na tarefa ou clique com o botão direito do mouse e clique em **Editar** para abrir a caixa de diálogo **Editor de Tarefa do Sistema de Arquivos Hadoop**.  
  
 ![Hadoop File System Task Editor](../../integration-services/control-flow/media/hadoop-filesystem-task.png "Hadoop File System Task Editor")  
  
## Opções  
 Configure as opções a seguir na caixa de diálogo **Tarefa do Sistema de Arquivos Hadoop** .  
  
|Campo|Description|  
|-----------|-----------------|  
|**Conexão do Hadoop**|Especifique um Gerenciador de Conexões do Hadoop existente ou crie um novo. Esse gerenciador de conexões indica onde os arquivos de destino estão hospedados.|  
|**Caminho de arquivo do Hadoop**|Especifique o caminho de arquivo ou diretório no HDFS.|  
|**Tipo de arquivo do Hadoop**|Especifique se o objeto do sistema de arquivos HDFS é um arquivo ou diretório.|  
|**Substituir o Destino**|Especifique se deseja substituir o arquivo de destino, caso ele já exista.|  
|**Operação**|Especifique a operação. As operações disponíveis são **CopyToHDFS**, **CopyFromHDFS**e **CopyWithinHDFS**.|  
|**Conexão de arquivo local**|Especifique um Gerenciador de Conexões de Arquivo existente ou crie um novo. Esse gerenciador de conexões indica onde os arquivos de origem estão hospedados.|  
|**É Recursivo**|Especifique se deseja copiar todas as subpastas de forma recursiva.|  
  
## Consulte também  
 [Gerenciador de conexões do Hadoop](../../integration-services/connection-manager/hadoop-connection-manager.md)   
 [Gerenciador de conexões de arquivos](../../integration-services/connection-manager/file-connection-manager.md)  
  
  