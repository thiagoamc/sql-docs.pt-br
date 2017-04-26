---
title: "Atualizar pacotes do Integration Services usando o Assistente de Atualiza&#231;&#227;o de Pacote SSIS | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pacotes do Integration Services, atualizando"
  - "atualizando pacotes do Integration Services"
ms.assetid: 9359275a-48f5-4d1e-8ae7-e797759e3ccf
caps.latest.revision: 22
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 22
---
# Atualizar pacotes do Integration Services usando o Assistente de Atualiza&#231;&#227;o de Pacote SSIS
  Você pode atualizar pacotes criados nas versões anteriores do [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] para o formato do [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] usado pelo [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fornece o Assistente de Atualização de Pacote [!INCLUDE[ssIS](../../includes/ssis-md.md)] para ajudar neste processo. Como é possível configurar o assistente para fazer backup dos pacotes originais, você poderá continuar usando esses pacotes caso tenha dificuldades com a atualização.  
  
 O Assistente de Atualização de Pacote [!INCLUDE[ssIS](../../includes/ssis-md.md)] é instalado junto com o [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
> [!NOTE]  
>  O Assistente de Atualização de Pacote [!INCLUDE[ssIS](../../includes/ssis-md.md)] está disponível nas edições Standard, Enterprise e Developer do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Para obter mais informações sobre como atualizar pacotes [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], veja [Atualizar pacotes do Integration Services](../../integration-services/install-windows/upgrade-integration-services-packages.md).  
  
 O restante deste tópico descreve como executar o assistente e fazer backup dos pacotes originais.  
  
## Executando o Assistente de Atualização de Pacote SSIS  
 Você pode executar o Assistente de Atualização de Pacote [!INCLUDE[ssIS](../../includes/ssis-md.md)] do [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], do [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou do prompt de comando.  
  
#### Para executar o assistente das Ferramentas de Dados do SQL Server  
  
1.  No [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], crie ou abra um projeto do [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
2.  No Gerenciador de Soluções, clique com o botão direito do mouse no nó **Pacotes SSIS** e clique em **Atualizar Todos os Pacotes** para atualizar todos os pacotes neste nó.  
  
    > [!NOTE]  
    >  Quando você abre um projeto do [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] que contém [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] ou pacotes posteriores, o [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] abre automaticamente o Assistente de Atualização de Pacote [!INCLUDE[ssIS](../../includes/ssis-md.md)].  
  
#### Para executar o assistente do SQL Server Management Studio  
  
-   No [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], conecte-se ao [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], expanda o nó **Pacotes Armazenados** e clique com o botão direito do mouse no nó **Sistema de Arquivos** ou **MSDB** e clique em **Atualizar Pacotes**.  
  
#### Para executar o assistente no prompt de comando  
  
-   No prompt de comando, execute o arquivo SSISUpgrade.exe da pasta **C:\Arquivos de Programas\Microsoft SQL Server\130\DTS\Binn** folder.  
  
## Fazendo backup de pacotes originais  
 Para fazer backup de pacotes originais, esses pacotes originais e os pacotes atualizados devem ser armazenados na mesma pasta no sistema de arquivos. Dependendo do modo como você executa o assistente, o local de armazenamento pode ser selecionado automaticamente.  
  
-   Quando você executa o Assistente de Atualização de Pacote [!INCLUDE[ssIS](../../includes/ssis-md.md)] do [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], esse assistente armazena automaticamente os pacotes originais e atualizados na mesma pasta no sistema de arquivos.  
  
-   Quando você executa o Assistente de Atualização de Pacote [!INCLUDE[ssIS](../../includes/ssis-md.md)] do [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou no prompt de comando, pode especificar locais de armazenamento diferentes para os pacotes originais e atualizados. Para fazer backup de pacotes originais, não se esqueça de especificar que os pacotes originais e os pacotes atualizados devem ser armazenados na mesma pasta no sistema de arquivos. Se você especificar qualquer outra opção de armazenamento, o assistente não poderá fazer backup dos pacotes originais.  
  
 Quando o assistente faz backup dos pacotes originais, ele armazena uma cópia desses pacotes em uma pasta **SSISBackupFolder**. O assistente cria essa pasta **SSISBackupFolder** como uma subpasta da pasta que contém os pacotes originais e os pacotes atualizados.  
  
#### Para fazer backup dos pacotes originais no SQL Server Management Studio ou no prompt de comando  
  
1.  Salve os pacotes originais em um local no sistema de arquivos.  
  
    > [!NOTE]  
    >  A opção de backup no assistente funciona apenas com pacotes que foram armazenados no sistema de arquivos.  
  
2.  No [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou no prompt de comando, execute o Assistente de Atualização de Pacote do [!INCLUDE[ssIS](../../includes/ssis-md.md)].  
  
3.  Na página **Selecionar Local de Origem** do assistente, defina a propriedade **Origem do pacote** como **Sistema de Arquivos**.  
  
4.  Na página **Selecionar Local de Destino** do assistente, selecione **Salvar no local de origem** para salvar os pacotes atualizados no mesmo local que os pacotes originais.  
  
    > [!NOTE]  
    >  A opção de backup no assistente está disponível somente quando os pacotes atualizados são armazenados na mesma pasta que os pacotes originais.  
  
5.  Na página **Selecionar Opções de Gerenciamento de Pacote** do assistente, selecione a opção **Fazer backup dos pacotes originais**.  
  
#### Para fazer backup dos pacotes originais nas Ferramentas de Dados do SQL Server  
  
1.  Salve os pacotes originais em um local no sistema de arquivos.  
  
2.  Na página **Selecionar Opções de Gerenciamento de Pacote** do assistente, selecione a opção **Fazer backup dos pacotes originais**.  
  
    > [!WARNING]  
    >  A opção **Fazer backup dos pacotes originais** não é exibida quando você abre um [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] ou um projeto posterior do [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], que automaticamente inicia o assistente.  
  
3.  No [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], execute o Assistente de Atualização de Pacote [!INCLUDE[ssIS](../../includes/ssis-md.md)].  
  
  