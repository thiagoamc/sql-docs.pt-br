---
title: "Refer&#234;ncia das regras de integridade (Power Pivot para SharePoint) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 47ae04ce-7b9d-49c2-8dbc-bafcb73d4603
caps.latest.revision: 19
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 18
---
# Refer&#234;ncia das regras de integridade (Power Pivot para SharePoint)
  Este tópico de referência descreve as regras de integridade do SharePoint que são adicionadas por uma instalação do [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] para SharePoint. Estas regras são usadas para relatar problemas com integridade de servidor, disponibilidade ou configuração de um aplicativo de serviço [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] ou sua instância associada do [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 A tabela a seguir lista as regras na ordem em que elas aparecem na página Definições de Regra do Analisador de Integridade na Administração Central do SharePoint. Regras configuráveis são as regras para as quais você pode alterar os limites de ativação. Para obter mais informações, consulte [Configurar regras de integridade do Power Pivot](../../analysis-services/power-pivot-sharepoint/configure-power-pivot-health-rules.md). O Reparo Automático indica que há uma solução interna que você pode clicar de dentro da página de relatórios de problemas para resolver o problema.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 &#124; SharePoint 2010|  
  
 **Observação:** [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] instala diferentes conjuntos de regras de integridade para diferentes versões do SharePoint. Consulte a coluna "versão" na tabela a seguir, ou execute o comando do Windows PowerShell a seguir para ver as regras instaladas.  
  
```  
Get-SPHealthAnalysisRule | select name, enabled, summary | where {$_.summary -like “*power*”}  | format-table -property * -autosize | out-default  
```  
  
|Regra|Configurável|Reparo automático|Versão|Description|  
|----------|------------------|-----------------|-------------|-----------------|  
|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]: o provedor OLE DB do Analysis Services não está instalado neste computador.|Não|Não|SharePoint 2010|O provedor OLE DB do Analysis Services ou não está instalado no servidor ou é da versão errada. Essa regra aparece quando seu farm do SharePoint inclui instâncias de Serviços do Excel em servidores de aplicativos que não têm o [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] para SharePoint. A regra avisa que o provedor OLE DB do Analysis Services usado pelos Serviços do Excel para se conectar a dados [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] não está instalado. Para resolver esse problema, instale o provedor OLE DB em cada servidor de Serviços do Excel que não tiver o provedor OLE DB do Analysis Services. Você pode baixar e instalar o provedor OLE DB do Analysis Services do Centro de Download da Microsoft. Para obter mais informações, consulte [Instalar o Provedor OLE DB do Analysis Services nos Servidores SharePoint](http://msdn.microsoft.com/pt-br/2c62daf9-1f2d-4508-a497-af62360ee859).|  
|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]: configurações de Registro para Microsoft.AnalysisServices.ChannelTransport.dll não são válidas após a instalação da versão SQL Server 2008 R2 do provedor MSOLAP neste computador.|Não|Sim|SharePoint 2010|Este é um problema de configuração de servidor. É provável que o ChannelTransport.dll não esteja registrado no assembly global. Execute o reparo automático dessa regra para registrar o .dll em cada servidor que tiver uma instalação do [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] para SharePoint. Como alternativa, você pode executar o regasm.exe manualmente para registrar o arquivo. Se o serviço de timer do SharePoint não estiver sendo executado como administrador local, pode ser necessário realizar o registro manual. Se houver falha para atualizar as configurações do Registro, haverá comunicação lenta com o servidor entre Serviços do Excel e Serviço de Sistema [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , e poderá haver falhas de conexão em determinadas configurações de segurança.|  
|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]: o aplicativo de serviço [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] não tem permissão para concluir a operação.|Não|Não|SharePoint 2010|Essa regra verifica se a identidade do aplicativo de serviço [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] é proprietário do banco de dados de aplicativo de servidor [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] e se tem permissões administrativas na instância local do SQL Server Analysis Services. Essas permissões são concedidas automaticamente durante a instalação e a implantação, mas se esta etapa não for concluída, esta regra de integridade ocorrerá.|  
|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]: a identidade do aplicativo de serviço [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] não deve ser membro do grupo local Administradores.|Não|Não|SharePoint 2010|Esta é uma prática recomendada que melhora a segurança global de sua implantação. Se você configurou o aplicativo de serviço [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] para ser executado usando uma conta que pertence ao grupo de Administrador local, será preciso alterar a conta de serviço para uma que não pertença a esse grupo. A recomendação é usar uma conta dedicada e com privilégios mínimos para cada serviço. Ao fazer isso, você fornece isolamento de serviço e facilita a auditoria de logons. Para obter mais informações sobre a alteração da conta de serviço, consulte [Configure Power Pivot Service Accounts](../../analysis-services/power-pivot-sharepoint/configure-power-pivot-service-accounts.md).|  
|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]: a instância do Analysis Services é executada no modo Tabular, mas o parâmetro de configuração que especifica esse modo está desativado.|Não|Não|SharePoint 2010|Essa regra verifica se a instância do SQL Server Analysis Services em uma instalação do [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] para SharePoint tem a propriedade de servidor **DeploymentMode** definida como 1. Se a propriedade for definida como outro valor, ou se o serviço de timer do SharePoint que executa o verificador de regra não tiver permissão para abrir o arquivo, esta regra falhará. Para obter mais informações sobre a propriedade do modo de implantação, consulte [Determinar o modo de servidor de uma instância do Analysis Services](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md).|  
|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]: o Trabalho de Timer da Atualização de Dados [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] está desabilitado.|Não|Não|SharePoint 2013<br /><br /> SharePoint 2010|Verifique as configurações de trabalho de timer para verificar se o trabalho de timer está habilitado. Se não estiver usando o recurso de atualização de dados [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , você poderá ignorar essa regra. Para saber mais, confira [Atualização de dados Power Pivot com SharePoint 2010](http://msdn.microsoft.com/pt-br/01b54e6f-66e5-485c-acaa-3f9aa53119c9).|  
|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]: as informações de conta de serviço do SQL Server Analysis Services ([!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]) gerenciadas pelo SQL Server Configuration Manager são diferentes das informações de conta gerenciadas pela Administração Central.|Não|Não|SharePoint 2010|Esta regra verifica se as informações de conta de serviço no SQL Server Configuration Manager são idênticas às informações de conta gerenciadas na Administração Central para a mesma instância do Analysis Services. Se as contas forem diferentes, uma entrada será adicionada ao relatório de Problema e Resolução, de modo que você possa alterar as informações de conta de serviço no SQL Server Configuration Manager de volta para a conta especificada na Administração Central. O SQL Server Configuration Manager não é uma ferramenta compatível para alterar um nome de usuário ou uma senha da conta de serviço em uma instalação do [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] para SharePoint. Usar a Administração Central habilita o uso do recurso de contas gerenciadas no SharePoint. E, o que é mais importante, se seu farm incluir vários servidores [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] para SharePoint, ter configurações de conta de serviço inconsistentes pode interromper o processamento e as operações de consulta no servidor que tiver informações de serviço incorretas.<br /><br /> Em um único servidor, as pastas de trabalho [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] funcionarão temporariamente quando essa regra for disparada, mas é aconselhável que você corrija o problema o mais cedo possível. As permissões de banco de dados e de sistema de arquivos são atualizadas usando as informações de conta especificadas na Administração Central.|  
|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]: a solução de farm implantada não está atualizada.|Não|Sim|SharePoint 2010|Uma instalação do [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] para SharePoint usa uma solução de nível de farm e uma solução de nível de aplicativo Web para instalar seus recursos. Esta regra indica que a solução do farm não é a atual em relação à versão ou ao servidor ou possivelmente a solução de Web. É provável que este seja um problema de implantação do servidor. Para solucionar esse problema, execute a Instalação do SQL Server para reparar uma das instalações do [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] para SharePoint no farm. Para obter mais informações sobre as soluções em um [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] para a instalação do SharePoint, consulte [Implantar soluções do Power Pivot no SharePoint](../../analysis-services/power-pivot-sharepoint/deploy-power-pivot-solutions-to-sharepoint.md).|  
|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]: o uso geral da CPU é muito alto.|Sim|Não|SharePoint 2010|Esta regra relata o consumo da CPU em nível de sistema. O uso geral da CPU é monitorado porque o Serviço do Sistema do [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] utiliza-o como uma medida de integridade de servidor, para o balanceamento de carga baseado em integridade em vários servidores [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] para SharePoint em um farm. Adicione outro servidor de aplicativos ao farm e mova os aplicativos que utilizam intensamente a CPU para esse servidor.|  
|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]: o Analysis Services não tem recursos suficientes de CPU para executar as operações solicitadas.|Sim|Não|SharePoint 2010|A quantidade de recursos de CPU disponíveis para o processo do Analysis Services (msmdsrv.exe) não é suficiente para o nível de atividade neste servidor. Considere a adição de outro servidor [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] para SharePoint ao farm. Para obter mais informações, consulte [Lista de verificação de implantação: Expandir adicionando servidores do Power Pivot a um farm do SharePoint 2010](../Topic/Deployment%20Checklist:%20Scale-out%20by%20adding%20Power%20Pivot%20Servers%20to%20a%20SharePoint%202010%20farm.md).|  
|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]: o Analysis Services não tem memória suficiente para executar as operações solicitadas.|Não|Não|SharePoint 2010|Esta regra é disparada quando restarem somente 5% de memória para o Analysis Services. Em um servidor de aplicativos do SharePoint, uma instância do SQL Server Analysis Services deve ter sempre uma pequena quantidade de memória reservada que nunca é usada. Como o servidor é associado à memória na maioria de suas operações, o servidor apresenta execução melhor quando não é executado no limite máximo.<br /><br /> Por padrão, os avisos de memória insuficientes ocorrem quando a memória disponível estiver abaixo de 5%. Você pode alterar este valor para ser mais alto ou mais baixo ajustando as configurações na instância do Analysis Services. Para obter mais informações, consulte [Configurar regras de integridade do Power Pivot](../../analysis-services/power-pivot-sharepoint/configure-power-pivot-health-rules.md).<br /><br /> Os 5% de memória não usados são calculados como um percentual de memória alocada para o Analysis Services. Por exemplo, se você tiver 200 GB de memória total, e for alocado 80% (ou 160 GB) para o Analysis Services, os 5% de memória não usada serão 5% de 160 GB (ou 8 GB).|  
|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]: o número alto de conexões indica que mais servidores devem ser implantados para tratar a carga atual.|Sim|Não|SharePoint 2010|Por padrão, esta regra de integridade é disparada quando o número de conexões distintas de usuários exceder 100. Este valor padrão é arbitrário (não é baseado nas especificações de hardware de seu servidor ou na atividade do usuário), portanto, você pode aumentá-lo ou abaixá-lo dependendo da capacidade do servidor e da atividade do usuário em seu ambiente. Para obter mais informações, consulte [Configurar regras de integridade do Power Pivot](../../analysis-services/power-pivot-sharepoint/configure-power-pivot-health-rules.md).|  
|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]: a taxa de eventos de carga para conexões é muito alta.|Sim|Não|SharePoint 2013<br /><br /> SharePoint 2010|Por padrão, esta regra de integridade será disparada quando o percentual de eventos de carga para eventos de conexão exceder 50% no período inteiro de coleta de dados (por padrão, 4 horas). Uma taxa alta assim indica um número muito alto de conexões para pastas de trabalho exclusivas ou configurações de redução de cache muito agressivas (onde pastas de trabalho são descarregadas e removidas rapidamente do sistema, enquanto as solicitações para os dados ainda estão ativas). Para evitar contar falsos positivos, deve haver pelo menos 20 conexões por período de 4 horas antes de a taxa ser calculada. Você pode basear esta regra de integridade em uma taxa diferente. Para obter mais informações, consulte [Configurar regras de integridade do Power Pivot](../../analysis-services/power-pivot-sharepoint/configure-power-pivot-health-rules.md). Para obter mais informações sobre como configurar o cache, consulte [Configurar o uso do espaço em disco &#40;Power Pivot para SharePoint&#41;](../../analysis-services/power-pivot-sharepoint/configure-disk-space-usage-power-pivot-for-sharepoint.md).|  
|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]: foram localizados um ou mais arquivos de minidespejo no diretório Logs, indicando uma falha no programa.|Não|Não|SharePoint 2013<br /><br /> SharePoint 2010|Os arquivos de minidespejo são gerados durante uma falha de programa para capturar informações sobre o estado do aplicativo de serviço [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] antes da falha. Estas informações podem ser enviadas à Microsoft e usadas para solucionar problemas. Esta regra é disparada quando os arquivos .dmp são detectados no servidor. A regra fornece um link para o arquivo, que pode ser localizado na pasta \OLAP\Log da instância do [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] para SharePoint. Observe que você não pode usar um editor de texto para exibir o conteúdo do arquivo. Exibir um arquivo de minidespejo exige que você baixe e instale uma ferramenta de depuração separada. Para obter mais informações, consulte [Ferramentas de depuração para Windows](http://go.microsoft.com/fwlink/?linkID=208266).|  
|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]: o espaço em disco é insuficiente na unidade onde os dados [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] estão armazenados em cache.|Sim|Não|SharePoint 2010|Por padrão, esta regra de integridade é disparada quando o espaço em disco é inferior a 5% na unidade de disco onde a pasta de backup está localizada. Para obter mais informações sobre como configurar esse percentual, consulte [Configurar regras de integridade do Power Pivot](../../analysis-services/power-pivot-sharepoint/configure-power-pivot-health-rules.md). Para obter mais informações sobre o uso do disco, consulte [Configurar o uso do espaço em disco &#40;Power Pivot para SharePoint&#41;](../../analysis-services/power-pivot-sharepoint/configure-disk-space-usage-power-pivot-for-sharepoint.md).|  
|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]: dados de uso não são atualizados com a frequência esperada.|Sim|Não|SharePoint 2013<br /><br /> SharePoint 2010|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] para SharePoint usa o sistema interno de coleta de dados de uso para coletar métricas sobre conexões, atualização de dados e tempos de resposta de consultas. Ele armazena esses dados de uso no banco de dados do aplicativo do serviço [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] que, por sua vez, atualiza uma pasta de trabalho do [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ([!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Management Data.xlsx) que fornece dados para relatórios no Painel de Gerenciamento do [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]. Essa regra indica que dados de uso não são movidos para o arquivo [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Management Data.xlsx com frequência suficiente. A regra usa o carimbo de data/hora no arquivo .xlsx como prova de que o arquivo está atualizado. Se houver outros problemas no sistema de coleta de dados de uso que distorcerem a exatidão dos dados, esta regra não detectará. Para solucionar este erro, verifique se os trabalhos de timer estão em execução. Para obter mais informações sobre a coleta de dados de uso, consulte [Configurar a coleta de dados de uso para o &#40;Power Pivot para SharePoint](../../analysis-services/power-pivot-sharepoint/configure-usage-data-collection-for-power-pivot-for-sharepoint.md).|  
|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]: a conta de processo Midtier deve ter permissão de 'Leitura Completa' em todos os SPWebApplications associados.|Não|Sim|SharePoint 2013<br /><br /> SharePoint 2010|A identidade do aplicativo de serviço [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] deve ter permissões **Leitura Completa** para acessar os bancos de dados de conteúdo do SharePoint em nome dos usuários que têm permissões Exibir Apenas em um documento.<br /><br /> Para determinar qual conta é usada como identidade do aplicativo de serviço [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , abra a página **Configurar contas de serviço** na Administração Central. Provavelmente, o aplicativo de serviço é executado no pool de aplicativos de serviço **Sistema de Serviços Web do SharePoint** ou em um pool de aplicativos dedicado.<br /><br /> Embora essa regra forneça a opção **Reparar Automaticamente** , você obterá melhores resultados se conceder as permissões manualmente:<br /><br /> <br /><br /> 1) Em Administração Central, clique em **Gerenciar aplicativos Web**.<br /><br /> 2) Selecione um site e clique em **Política de Usuário**.<br /><br /> 3) Clique em **Adicionar Usuários**.<br /><br /> 4) Selecione (Todas as zonas) e clique em **Avançar**.<br /><br /> 5) Em Usuários, insira a identidade do aplicativo de serviço [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] e clique na caixa de seleção **Leitura Completa**. Clique em **6) Concluir**.<br /><br /> 6) Verifique o reparo. Em Monitoramento, clique em **Revisar definições de regra**. Localize e abra a regra do [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Clique em **Executar Agora**. Volte para **Revisar problemas e soluções** para verificar se a regra não aparece mais.|  
|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]: o serviço de Logon Secundário (seclogon) está desabilitado|Não|Não|SharePoint 2013<br /><br /> SharePoint 2010|O serviço de Logon Secundário é usado para gerar imagens em miniatura de pastas de trabalho [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] na Galeria do [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Por padrão, o serviço de Logon Secundário é definido como inicialização manual. Se o serviço for desabilitado, a geração de miniaturas falhará. Além disso, os logs do ULS conterão o seguinte erro: "O erro 1058 pode ter como uma causa raiz o fato de o Serviço do Windows "Logon Secundário" ser desabilitado."<br /><br /> Para verificar a configuração de serviço, use o aplicativo de console Serviços para localizar o Logon Secundário e alterar seu **Tipo de Inicialização** para **Manual**. Se você não puder habilitar o serviço, sua organização poderá ter uma política de grupo que desabilita isto. Pergunte a um administrador para determinar se este é o caso.<br /><br /> Depois que você habilitar o serviço, imagens de miniatura ou instantâneo serão atualizadas com o passar do tempo. Como opção, você pode forçar uma atualização reiniciando o serviço e abrindo e em seguida salvando novamente as páginas de propriedades de um relatório específico. Para saber mais, confira [How to Use Power Pivot Gallery](http://go.microsoft.com/fwlink/?LinkId=246462)(Como usar a Galeria Power Pivot).|  
|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]: ADOMD.NET não está instalado em um WFE autônomo que está configurado para administração central|Não|Não|SharePoint 2013<br /><br /> SharePoint 2010|O ADOMD.NET é uma biblioteca de cliente do Analysis Services que dá suporte a conexões com um banco de dados do Analysis Services. Em uma implantação do [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] para SharePoint, o ADOMD.NET fornece acesso aos relatórios internos no painel de gerenciamento do [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] na Administração Central. Os relatórios internos são, na verdade, pastas de trabalho do [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] que contêm dados inseridos do Analysis Services. O painel de gerenciamento usa o ADOMD.NET para enviar uma solicitação de conexão para o servidor que carrega dados contidos na pasta de trabalho.<br /><br /> Em topologias que incluem a Administração Central que é executada em um servidor Web front-end autônomo, você deve instalar o ADOMD.NET manualmente se quiser exibir estes relatórios no painel de gerenciamento. Para obter mais informações, confira [Instalar o ADOMD.NET em servidores Web front-end executando a Administração Central](http://msdn.microsoft.com/pt-br/c2372180-e847-4cdb-b267-4befac3faf7e).|  
  
  