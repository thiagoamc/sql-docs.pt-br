---
title: "Cmdlet Set-PowerPivotSystemService | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: f6ef197b-3d74-4339-ae73-8a7c1eaf0e91
caps.latest.revision: 11
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 11
---
# Cmdlet Set-PowerPivotSystemService
  Define as propriedades globais do objeto PowerPivotSystemService no nível do farm.  
  
 **Aplica-se a:** SharePoint 2010 e SharePoint 2013.  
  
## Sintaxe  
  
```  
Set-PowerPivotSystemService [-Identity <PowerPivotMidTierServicePipeBind>] [-UpdateAssemblyInformation <switch>] [-WorkbookUpgradeOnDataRefresh <boolean>] [-DirectTCPConnections <boolean>] [-Confirm <switch>] [<CommonParameters>]  
```  
  
## Description  
 O cmdlet Set-PowerPivotSystemService atualiza as propriedades do objeto-pai do Serviço de Sistema do [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] no farm.  
  
## Parâmetros  
  
### -Identity \<PowerPivotMidTierServicePipeBind>  
 Especifica o objeto pai para o qual você está atualizando propriedades. O valor deve ser um GUID válido que identifica exclusivamente o objeto no farm.  
  
|||  
|-|-|  
|Obrigatório?|false|  
|Posição?|0|  
|Valor padrão||  
|Aceitar entrada de pipeline?|true|  
|Aceitar caracteres curinga?|false|  
  
### -UpdateAssemblyInformation \<switch>  
 Usado apenas para fins de atualização. Se a versão do assembly implantada no farm for diferente da versão armazenada no banco de dados de configuração do SharePoint, você poderá executar esse cmdlet para atualizar as informações de assembly no banco de dados de configuração. As informações de versão do assembly estão disponíveis nas propriedades de arquivo de Microsoft.AnalysisServices.SharePoint.Integration.dll, armazenado no assembly global.  
  
|||  
|-|-|  
|Obrigatório?|false|  
|Posição?|1|  
|Valor padrão||  
|Aceitar entrada de pipeline?|false|  
|Aceitar caracteres curinga?|false|  
  
### -WorkbookUpgradeOnDataRefresh \<boolean>  
 Usado para atualizar automaticamente uma pasta de trabalho do [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] no início de uma atualização de dados agendada no servidor. Somente há suporte para a atualização de dados para pastas de trabalho que correspondem à versão atual do servidor. Se você habilitar essa propriedade, uma pasta de trabalho será atualizada automaticamente de forma que atualização de dados possa continuar. Essa propriedade é definida no nível da instância do servidor. Você não pode variá-la para pastas de trabalho específicas, bibliotecas, sites ou usuários.  
  
|||  
|-|-|  
|Obrigatório?|false|  
|Posição?|2|  
|Valor padrão|false|  
|Aceitar entrada de pipeline?|false|  
|Aceitar caracteres curinga?|false|  
  
### -DirectTCPConnections \<boolean>  
 Especifica se os Serviços do Excel enviam todas as consultas diretamente para a instância do SQL Server Analysis Services (POWERPIVOT) que carregou um banco de dados [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], ignorando o provedor de dados MSOLAP e o transporte de canal que, de outra forma, seriam usados a cada solicitação de consulta enviada a um banco de dados [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)].  
  
 A definição desse parâmetro melhora o desempenho e a escalabilidade das consultas [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] fazendo conexões com os bancos de dados carregados de modo mais eficiente. Observe que esse parâmetro não altera o comportamento do modo como a solicitação de carregamento inicial é alocada. Outros parâmetros, como –RoundRobinAllocation e –HealthBasedAllocation, usados para alocar as solicitações de carregamento do banco de dados entre vários [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] para a instância do SharePoint no farm não são afetados porque –DirectTCPConnections aplica-se apenas às consultas emitidas após o banco de dados ser carregado.  
  
 Para as topologias de farm que incluem os Serviços do Excel e o [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] para SharePoint em execução em servidores de aplicativo separados, você deve abrir uma porta no firewall para assegurar que as solicitações alcancem a instância do SQL Server Analysis Services (POWERPIVOT). Para obter instruções sobre como habilitar conexões de entrada para uma instância nomeada do Analysis Services, consulte [Configurar o Firewall do Windows para permitir o acesso ao Analysis Services](../../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).  
  
|||  
|-|-|  
|Obrigatório?|false|  
|Posição?|3|  
|Valor padrão|false|  
|Aceitar entrada de pipeline?|false|  
|Aceitar caracteres curinga?|false|  
  
### -Confirm \<switch>  
 Solicita sua confirmação antes de executar o comando. Este valor é habilitado por padrão. Para ignorar a resposta de confirmação em um comando, especifique Confirm:$false no comando.  
  
|||  
|-|-|  
|Obrigatório?|false|  
|Posição?|nomeado|  
|Valor padrão||  
|Aceitar entrada de pipeline?|false|  
|Aceitar caracteres curinga?|false|  
  
### \<CommonParameters>  
 Este cmdlet oferece suporte aos parâmetros comuns: Verbose, Debug, ErrorAction, ErrorVariable, WarningAction, WarningVariable, OutBuffer e OutVariable. Para obter mais informações, consulte [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## Entradas e saídas  
 O tipo de entrada é o tipo dos objetos que você pode transportar para o cmdlet. O tipo de retorno é o tipo dos objetos que o cmdlet retorna.  
  
|||  
|-|-|  
|Entradas|Nenhum.|  
|Saídas|Nenhum.|  
  
## Exemplo 1  
  
```  
C:\PS>Set-PowerPivotSystemService -WorkbookUpgradeOnDataRefresh:$true  
```  
  
 Permite a atualização automática das pastas de trabalho da versão anterior de modo que a atualização de dados agendada possa continuar.  
  
  