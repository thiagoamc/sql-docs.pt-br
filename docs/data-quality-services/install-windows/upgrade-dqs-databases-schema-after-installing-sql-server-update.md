---
title: "Atualize o esquema de bancos de dados DQS depois de instalar a atualiza&#231;&#227;o do SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c8f3fbae-02c4-464d-a35c-7108f48c58cb
caps.latest.revision: 11
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 11
---
# Atualize o esquema de bancos de dados DQS depois de instalar a atualiza&#231;&#227;o do SQL Server
  Depois que instalar uma atualização do SQL Server (patch, hotfix ou atualização cumulativa) em uma instância do DQS previamente configurada, você poderá ter de atualizar o esquema de bancos de dados do DQS executando o arquivo DQSInstaller.exe com o parâmetro de linha de comando **upgrade**. Caso contrário, você poderá receber o erro a seguir ao tentar se conectar ao Servidor do Data Quality usando seu Cliente do Data Quality:  
  
```  
An error occurred in the Microsoft .NET Framework while trying to load assembly id 65581.  
```  
  
 Atualizar esquema de bancos de dados do DQS não afeta seus dados existentes nos bancos de dados do DQS (bases de dados de conhecimento, projetos de qualidade de dados e resultados exportados no banco de dados DQS_STAGING_DATA). No entanto, você deve fazer backup de seus bancos de dados do DQS antes de atualizar o esquema de bancos de dados do DQS para impedir qualquer perda de dados acidental durante a atualização do esquema. Para obter informações sobre como fazer backup de bancos de dados DQS, veja [Fazendo backup e restaurando banco de dados do DQS](../../data-quality-services/backing-up-and-restoring-dqs-databases.md).  
  
> [!NOTE]  
>  A maioria das atualizações do SQL Server exigirá uma atualização para o esquema de bancos de dados do DQS. Para obter informações sobre as atualizações do SQL Server que exigirão uma atualização para o esquema de bancos de dados do DQS, veja o gráfico na etapa 1.A em [Atualizar DQS: instalando atualizações cumulativas ou patches de hotfix no Data Quality Services](http://go.microsoft.com/fwlink/?LinkID=251565).  
  
## Pré-requisitos  
  
-   Você deve estar conectado como um membro do grupo Administradores no computador do [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)].  
  
-   Sua conta de usuário do Windows deve ser um membro da função de servidor fixa sysadmin na instância do SQL Server em que o [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] está instalado.  
  
### Para atualizar o esquema de bancos de dados do DQS  
  
1.  (Recomendado) Faça backup de seus bancos de dados do DQS antes de continuar com a atualização de esquema. Para obter informações sobre como fazer backup de bancos de dados DQS, veja [Fazendo backup e restaurando banco de dados do DQS](../../data-quality-services/backing-up-and-restoring-dqs-databases.md).  
  
2.  Iniciar o prompt de comando.  
  
3.  Ao prompt de comando, altere seu diretório ao local onde DQSInstaller.exe está disponível. Se você tiver instalado a instância padrão do SQL Server, o arquivo DQSInstaller.exe estará disponível em C:\Arquivos de Programas\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn:  
  
    ```  
    cd C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn  
    ```  
  
4.  No prompt de comando, digite o seguinte comando e pressione ENTER:  
  
    ```  
    dqsinstaller.exe -upgrade  
    ```  
  
5.  O instalador solicita que você faça backup dos bancos de dados do DQS antes de continuar. Se você já tiver feito backup de seus bancos de dados do DQS, digite **Y** ou **Sim** e pressione ENTER para continuar com a atualização.  
  
6.  Uma mensagem de conclusão é exibida depois da atualização bem-sucedida do esquema de bancos de dados do DQS.  
  
## Próximas etapas  
 Faça logon no Servidor do Data Quality de um aplicativo Cliente do Data Quality.  
  
 Para obter mais informações sobre como atualizar esquema de bancos de dados do DQS depois de instalar atualizações do SQL Server e etapas de solução de problemas associadas, veja [Atualizar DQS: instalando atualizações cumulativas ou patches de hotfix no Data Quality Services](http://go.microsoft.com/fwlink/?LinkID=251565).  
  
## Consulte também  
 [Instalar o Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md)   
 [Atualizar assemblies SQLCLR após atualizar o .NET Framework](../../data-quality-services/install-windows/upgrade-sqlclr-assemblies-after-net-framework-update.md)  
  
  