---
title: "Limpar dados usando o conhecimento do DQS (interno) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dqs.dqproject.interactivecleansing.f1"
  - "sql13.dqs.dqproject.map.f1"
  - "sql13.dqs.dqproject.correction.f1"
  - "sql13.dqs.dqproject.export.f1"
ms.assetid: c96b13ad-02a6-4646-bcc7-b4a8d490f5cc
caps.latest.revision: 26
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 26
---
# Limpar dados usando o conhecimento do DQS (interno)
  Este tópico descreve como limpar seus dados usando um projeto de qualidade de dados no [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). A limpeza de dados é executada na fonte de dados com o uso de uma base de dados de conhecimento que foi criada no DQS a partir de um conjunto de dados de alta qualidade. Para obter mais informações, consulte [Building a Knowledge Base](../data-quality-services/building-a-knowledge-base.md).  
  
 Limpeza de dados é realizada em quatro estágios: um *mapeamento* estágio em que identifique a fonte de dados a serem limpos e mapeá-lo para domínios necessários em uma base de dados de Conhecimento, um *de limpeza auxiliada por computador* estágio em que o DQS aplica a base de conhecimento aos dados a serem limpos e propõe/faz alterações em dados de origem, um *Limpeza interativa* estágio em que os administradores de dados podem analisar as alterações de dados e aceitar/rejeitar as alterações de dados e, finalmente, o *exportar* estágio que lhe permite exportar os dados limpos. Cada um desses processos é executado em uma página separada do assistente da atividade de limpeza, permitindo que você percorra páginas diferentes, para executar o processo novamente, e fechar um processo de limpeza específico e depois retornar ao mesmo estágio do processo. O DQS fornece estatísticas sobre a fonte de dados e os resultados da limpeza que permitem a você tomar decisões conscientes sobre a limpeza de dados.  
  
## Antes de começar  
  
###  <a name="Prerequisites"></a> Pré-requisitos  
  
-   Você deve ter especificado valores de limites apropriados para a atividade de limpeza. Para obter informações sobre como fazer isso, consulte [Configure Threshold Values for Cleansing and Matching](../data-quality-services/configure-threshold-values-for-cleansing-and-matching.md).  
  
-   Uma base de dados de conhecimento do DQS deve estar disponível no [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] em relação ao qual você deseja comparar e limpar sua fonte de dados. Além disso, a base de dados de conhecimento deve conter conhecimento sobre o tipo de dados que você deseja limpar. Por exemplo, se você quiser limpar sua fonte de dados que contém endereços nos EUA, deverá ter uma base de dados de conhecimento que tenha sido criada a partir de dados de exemplo de “alta qualidade” para endereços nos EUA.  
  
-   O Microsoft Excel deverá ser instalado no computador [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] se os dados de origem a serem limpos estiverem em um arquivo do Excel. Caso contrário, você não poderá selecionar o arquivo do Excel no estágio de mapeamento. Os arquivos criados pelo Microsoft Excel podem ter a extensão .xlsx, .xls ou .csv. Se a versão de 64 bits do Excel for usada, somente arquivos do Excel 2003 (.xls) terão suporte; não haverá suporte para os arquivos do Excel 2007 ou 2010 (.xlsx). Se você estiver usando a versão de 64 bits do Excel 2007 ou 2010, salve o arquivo como .xls ou .csv ou instale uma versão de 32 bits do Excel.  
  
###  <a name="Security"></a> Segurança  
  
####  <a name="Permissions"></a> Permissões  
 Você deve ter a função dqs_kb_editor ou dqs_kb_operator no banco de dados DQS_MAIN para executar a limpeza de dados.  
  
##  <a name="Create"></a> Criar um projeto de qualidade de dados de limpeza  
 Você deve usar um projeto de qualidade de dados para executar a operação de limpeza de dados. Para criar um projeto de qualidade de dados de limpeza  
  
1.  Siga as etapas 1 a 3 no tópico [criar um projeto de qualidade de dados](../data-quality-services/create-a-data-quality-project.md).  
  
2.  Na etapa 3.d, selecione a atividade **Limpeza** .  
  
3.  Clique em **Criar** para criar um projeto de qualidade de dados de limpeza.  
  
 Isso cria um projeto de qualidade de dados de limpeza e abre a página **Mapa** do assistente de qualidade de dados de limpeza.  
  
##  <a name="Mapping"></a> Estágio de mapeamento  
 No estágio de mapeamento, especifique a conexão com os dados de origem a serem limpos e para mapear as colunas nos dados de origem com os domínios apropriados na base de dados de conhecimento selecionada.  
  
1.  Na página **Mapa** do assistente de qualidade de dados de limpeza, selecione os dados de origem a serem limpos: **SQL Server** ou **Arquivo do Excel**:  
  
    1.  **SQL Server**: selecione **DQS_STAGING_DATA** como a fonte de dados se você tiver copiado sua fonte de dados para este banco de dados e, em seguida, selecione apropriada tabela/exibição que contém seus dados de origem. Caso contrário, selecione seu banco de dados de origem e a tabela/exibição apropriada. Seu banco de dados de origem deve estar presente na instância do SQL Server como [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] para o **banco de dados** lista suspensa.  
  
    2.  **Arquivo do Excel**: clique em **Procurar**e selecione o arquivo do Excel que contém os dados a serem limpos. O Microsoft Excel deverá ser instalado no computador [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] para selecionar um arquivo do Excel. Caso contrário, o botão **Procurar** não estará disponível e você será notificado sob esta caixa de texto de que o Microsoft Excel não está instalado. Além disso, deixe a caixa de seleção **Usar primeira linha como cabeçalho** marcada se a primeira linha do arquivo do Excel contiver dados de cabeçalho.  
  
2.  Em **mapeamentos**, mapear as colunas de dados na fonte de dados com os domínios apropriados na base de dados de Conhecimento, selecionando uma coluna de origem da lista suspensa no **coluna de origem** coluna e, em seguida, selecionando um domínio na lista suspensa no **domínio** coluna na mesma linha. Repita essa etapa para mapear todas as colunas nos dados de origem com os domínios apropriados na base de dados de conhecimento. Se necessário, você pode clicar no ícone **Adicionar um mapeamento de coluna** para adicionar linhas à tabela de mapeamento.  
  
    > [!NOTE]  
    >  Você poderá mapear sua fonte de dados para um domínio DQS para realizar limpeza de dados somente se o tipo de dados de origem tiver suporte no DQS e corresponder ao tipo de dados de domínio do DQS. Para obter informações sobre os tipos de dados de origem com suporte, consulte [Supported SQL Server and SSIS Data Types for DQS Domains](../data-quality-services/supported-sql-server-and-ssis-data-types-for-dqs-domains.md).  
  
3.  Clique no ícone **Visualizar fonte de dados** para visualizar os dados na tabela do SQL Server ou visualizar os dados selecionados ou a planilha do Excel selecionada.  
  
4.  Clique em **Exibir/Selecionar domínios compostos** para exibir uma lista de domínios compostos que são mapeados para uma coluna de origem. Esse botão somente estará disponível se houver pelo menos um domínio composto mapeado para uma coluna de origem.  
  
5.  Clique em **próxima** para prosseguir para o estágio de limpeza auxiliada por computador (**Limpar** página).  
  
##  <a name="ComputerAssisted"></a> Estágio de limpeza auxiliada por computador  
 No estágio de limpeza auxiliada por computador, você executa um processo de limpeza de dados automatizado que analisa os dados de origem nos domínios mapeados na base de conhecimento e faz ou propõe alterações nos dados.  
  
1.  Sobre o **Limpar** página do Assistente de qualidade de dados, clique em **Iniciar** para executar o processo de limpeza auxiliada por computador. O DQS usa algoritmos avançados e níveis de confiança baseados nos níveis de limite especificados para analisar os dados em relação à base de dados de conhecimento selecionada e depois limpá-los. Para obter informações detalhadas sobre limpeza como auxiliada por computador ocorre no DQS, consulte [Limpeza auxiliada por computador](../data-quality-services/data-cleansing.md#ComputerAssisted) em [Limpeza de dados](../data-quality-services/data-cleansing.md).  
  
    > [!IMPORTANT]  
    >  -   Após a conclusão da análise de dados, o botão **Iniciar** se transforma em um botão **Iniciar** . Se os resultados da análise anterior ainda não tiverem sido salvos, clicar em **Reiniciar** causará a perda dos dados anteriores. Durante a execução da análise, não saia da página; do contrário, o processo de análise será encerrado.  
    > -   Se a base de dados de conhecimento usada para o projeto de limpeza fosse atualizada e publicada após a criação do projeto de limpeza, clicar em **Iniciar** exibirá uma caixa perguntando se você deseja utilizar a base de dados de conhecimento mais recente para limpeza. Normalmente isso pode acontecer se você criou um projeto de qualidade de dados usando uma base de Conhecimento, fechado o limpeza projeto no meio do caminho clicando **Fechar**, e, em seguida, reaberto o projeto de qualidade de dados em um momento posterior para executar a limpeza. Enquanto isso, a base de dados de conhecimento usada no projeto de limpeza foi atualizada e publicada.  
    >   
    >      Da mesma forma, se a base de Conhecimento usada para o projeto de limpeza foi atualizada e publicada após a última vez que você executou a limpeza auxiliada por computador, clicando em **reinicie** solicita que você quer usar a base de dados de conhecimento mais recente para limpeza.  
    >   
    >      Em ambos os casos, clique em **Sim** para usar a base de dados de conhecimento atualizada para a limpeza auxiliada por computador. Além disso, se houver conflitos entre os mapeamentos atuais e a base de dados de conhecimento atualizada (como exclusão de domínios ou alteração do tipo de dados), a mensagem também solicitará que você corrija os mapeamentos atuais para usar a base de dados de conhecimento atualizada. Clicar em **Sim** leva você para a **mapa** página onde você pode corrigir os mapeamentos antes de continuar com a limpeza auxiliada por computador.  
  
2.  Durante o estágio de limpeza auxiliada por computador, você pode alternar no criador de perfil clicando o **Profiler** guia para exibir o perfil de dados em tempo real e notificações. Para obter mais informações, consulte [Estatísticas do criador de perfil](#Profiler).  
  
3.  Se você não estiver satisfeito com os resultados, clique em **Voltar** para retornar à página **Mapa** , modifique um ou mais mapeamentos conforme o necessário, volte à página **Limpar** e clique em **Reiniciar**.  
  
4.  Após concluir o processo de limpeza auxiliada por computador, clique em **próxima** para prosseguir para o estágio de limpeza interativa (**Gerenciar e exibir resultados** página).  
  
##  <a name="Interactive"></a> Estágio de limpeza interativa  
 No estágio de limpeza interativa, você pode visualizar as alterações que o DQS propôs e decidir se deseja implementá-las ou não, aprovando ou rejeitando as alterações. No painel esquerdo do **Gerenciar e exibir resultados** página, o DQS exibe uma lista de todos os domínios mapeados anteriormente no estágio de mapeamento junto com o número de valores na fonte de dados analisados em cada domínio durante o estágio de limpeza auxiliada por computador. No painel direito da página **Gerenciar e exibir resultados** , com base na conformidade com as regras de domínio, regras de erro de sintaxe e algoritmos avançados, o DQS categoriza os dados em cinco guias usando o *nível de confiança*. O nível de confiança indica a extensão da certeza do DQS para a correção ou sugestão e se baseia nos seguintes valores de limite:  
  
-   **Limite de Correção Automático**: qualquer valor que tenha um nível de confiança acima desse limite será corrigido automaticamente pelo DQS. No entanto, o administrador de dados pode substituir a alteração durante a limpeza interativa. Você pode especificar o valor de limite de correção automática na guia **Configurações Gerais** na tela **Configuração** . Para obter mais informações, consulte [Configure Threshold Values for Cleansing and Matching](../data-quality-services/configure-threshold-values-for-cleansing-and-matching.md).  
  
-   **Limite de Sugestão Automático**: qualquer valor que tenha um nível de confiança acima deste limite, mas abaixo do limite de correção automático, será sugerido como um valor de substituição. O DQS só fará a alteração se o administrador de dados aprová-la. Você pode especificar o valor de limite de sugestão automática na guia **Configurações Gerais** na tela **Configuração** . Para obter mais informações, consulte [Configure Threshold Values for Cleansing and Matching](../data-quality-services/configure-threshold-values-for-cleansing-and-matching.md).  
  
-   **Outro**: qualquer valor abaixo do valor de limite de sugestão automática é mantido sem alteração pelo DQS.  
  
 Com base no nível de confiança, os valores são exibidos nas cinco guias a seguir:  
  
|Tab|Descrição|  
|---------|-----------------|  
|**Sugerido**|Exibe os valores de domínio para o qual o DQS localizou os valores sugeridos que têm um nível de confiança maior do que o *limite de sugestão automática* valor mas menor do que o *limite de correção automática* valor.<br /><br /> Os valores sugeridos são exibidos na coluna **Corrigir para** em relação ao valor original. Você pode clicar no botão de opção na coluna **Aprovar** ou **Rejeitar** em relação a um valor na grade superior para aceitar ou rejeitar a sugestão para todas as instâncias do valor. Nesse caso, o valor aceito passa para a guia **Corrigido** e o valor rejeitado passa para a guia **Inválido** .|  
|**Nova**|Exibe o domínio válido para o qual o DQS não tem informações suficientes e, portanto, não pode ser mapeado para nenhuma outra guia. Além disso, essa guia também contém valores que têm um nível de confiança menor do que o *limite de sugestão automática* valor, porém alto o suficiente para ser marcado como válido.<br /><br /> Se você considerar o valor correto, clique no botão de opção na coluna **Aprovar** . Ou clique no botão de opção na coluna **Rejeitar** . O valor aceito passa para a guia **Corrigir** e o valor rejeitado passa para a guia **Inválido** . Também é possível digitar manualmente o valor correto como um substituto do valor original na coluna **Corrigir para** em relação ao valor e depois clicar no botão de opção na coluna **Aprovar** para aceitar a alteração. Nesse caso, o valor passa para a guia **Corrigido** .|  
|**Inválido**|Exibe os valores de domínio que foram marcados como inválidos no domínio na base de dados de conhecimento ou os valores que falharam em uma regra de domínio. Essa guia também contém valores que foram rejeitados pelo usuário em qualquer uma das quatro guias.<br /><br /> No entanto, se você considerar o valor correto, clique no botão de opção na coluna **Aprovar** . O valor aceito passa para a guia **Corrigido** . Também é possível digitar manualmente o valor correto como um substituto do valor original na coluna **Corrigir para** em relação ao valor e depois clicar no botão de opção na coluna **Aprovar** para aceitar a alteração. Nesse caso, o valor passa para a guia **Corrigido** .|  
|**Corrigido**|Exibe os valores de domínio corrigidos pelo DQS durante o processo de limpeza automatizado uma vez que o DQS localizou uma correção para o valor com um nível de confiança acima do valor de limite de correção automática.<br /><br /> Os valores corrigidos são exibidos na coluna **Corrigir para** em relação ao valor original. Por padrão, o botão de opção na coluna **Aprovar** em relação ao valor está selecionado. Se necessário, você poderá rejeitar a correção proposta clicando no botão de opção na coluna **Rejeitar** para passar para a guia **Inválido** ou digitar manualmente o valor correto na coluna **Corrigir para** e clicar no botão de opção na coluna **Aprovar** para aceitar a alteração e passá-la para a guia **Corrigido** .|  
|**Corrigir**|Exibe os valores de domínio que foram considerados corretos. Por exemplo, o valor correspondeu a um valor de domínio. Essa guia também contém os valores que foram aprovados pelo usuário clicando no botão de opção na coluna **Aprovar** nas guias **Novo** e **Inválido** .<br /><br /> Por padrão, o botão de opção na coluna **Aprovar** está selecionado em relação a cada valor. No entanto, se você achar que um valor nessa guia está incorreto, poderá clicar no botão de opção na coluna **Rejeitar** em relação ao valor para passá-lo para a guia **Inválido** ou digitar manualmente o valor correto como um substituto para o valor na coluna **Corrigir para** do valor e depois clicar no botão de opção na coluna **Aprovar** para aceitar a alteração e passá-la para a guia **Corrigido** .|  
  
 Para limpar os dados interativamente:  
  
1.  Na página **Gerenciar e exibir resultados** do assistente de qualidade de dados de limpeza, clique em um nome de domínio no painel esquerdo.  
  
2.  Examine os valores de domínio nas cinco guias e execute a ação apropriada conforme explicado antes.  
  
    -   O painel superior direito exibe as seguintes informações para cada valor no domínio selecionado: valor original, número de instâncias (registros), uma caixa para especificar outro valor (correto), o nível de confiança (não está disponível para os valores sob o **correto** guia), o motivo para a ação do DQS sobre o valor e a opção de aprovar ou rejeitar as correções e sugestões para o valor.  
  
        > [!TIP]  
        >  Você pode aprovar ou rejeitar todos os valores no domínio selecionado no painel superior direito clicando **Aprovar todos os termos** ou **Rejeitar todos os termos** ícone respectivamente. Como alternativa, clique em um valor no domínio selecionado e clique em **aceite todos** ou **Rejeitar todas** no menu de atalho.  
  
    -   O painel inferior exibe ocorrências individuais do valor de domínio selecionadas no painel superior direito. As seguintes informações são exibidas: uma caixa para especificar outro valor (correto), o nível de confiança (não está disponível para os valores sob o **correto** guia), o motivo para a ação do DQS no valor e a opção de aprovar ou rejeitar as correções e sugestões para o valor e o valor original.  
  
3.  Se você habilitou o recurso **Verificador Ortográfico** para um domínio ao criá-lo, sublinhados vermelhos ondulados são exibidos nos valores de domínio identificados como erros potenciais. O sublinhado é exibido para o valor inteiro. Por exemplo, se “New York” estivesse escrito incorretamente como “Neu York”, o verificador ortográfico exibiria o sublinhado vermelho em “Neu York” e não apenas em “Neu”. Se você clicar com o botão direito do mouse no valor, as correções sugeridas serão exibidas. Se houver mais de 5 sugestões, você poderá clicar em **Mais sugestões** no menu de contexto para exibir o resto delas. Assim como ocorre com a exibição de erro, as sugestões são substitutos para todo o valor. Por exemplo, “New York” será exibido como uma sugestão no exemplo anterior e não apenas “New”. Você pode escolher uma das sugestões ou adicionar um valor ao dicionário a ser exibido para esse valor. Os valores são armazenados em dicionário em um nível de conta de usuário. Quando você seleciona uma sugestão no menu de contexto do verificador ortográfico, a sugestão selecionada será adicionada à coluna **Corrigir para** . No entanto, se você selecionar uma sugestão na coluna **Corrigir para** , o valor na coluna será substituído pela sugestão selecionada.  
  
     O recurso do verificador ortográfico está habilitado por padrão no estágio de limpeza interativa. Você pode desabilitar o verificador ortográfico no estágio de limpeza interativa clicando o **Habilitar/desabilitar o verificador ortográfico** ícone, ou clicando duas vezes na área de valores de domínio e, em seguida, clicando em **verificador ortográfico** no menu de atalho. Para habilitá-lo novamente, faça o mesmo.  
  
    > [!NOTE]  
    >  O recurso do verificador ortográfico somente está disponível no painel superior (valores de domínio). Além disso, você não pode habilitar ou desabilitar o verificador ortográfico para domínios compostos. Os domínios filho em um domínio composto que são do tipo cadeia de caracteres e estão habilitados para o recurso do verificador ortográfico terão a funcionalidade de verificador ortográfico habilitada no estágio de limpeza interativa, por padrão.  
  
4.  Durante o estágio de limpeza interativa, você pode alternar no criador de perfil clicando o **Profiler** guia para exibir o perfil de dados em tempo real e notificações. Para obter mais informações, consulte [Estatísticas do criador de perfil](#Profiler).  
  
5.  Depois que você examinar todos os valores de domínio, clique em **Avançar** para passar para o estágio de exportação.  
  
##  <a name="Export"></a> Estágio de exportação  
 No estágio de exportação, você especifica os parâmetros para exportação dos dados limpos: o que e para onde exportar.  
  
1.  Na página **Exportar** do assistente de qualidade de dados de limpeza, selecione o tipo de destino para exportação dos dados limpos: **SQL Server**, **Arquivo CSV**ou **Arquivo do Excel**.  
  
    > [!IMPORTANT]  
    >  Se você estiver usando uma versão de 64 bits do Excel, não poderá exportar os seus dados limpos para um arquivo do Excel; você só poderá exportar para um banco de dados do SQL Server ou para um arquivo .csv.  
  
    1.  **SQL Server**: selecione **DQS_STAGING_DATA** como o destino do banco de dados se você quiser exportar seus dados aqui e, em seguida, especifique um nome de tabela que será criado para armazenar os dados exportados. Caso contrário, selecione outro banco de dados se você quiser exportar dados para um banco de dados diferente e depois especifique um nome da tabela que será criada para armazenar os dados exportados. Seu banco de dados de destino deve estar presente na instância do SQL Server como [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] para o **banco de dados** lista suspensa.  
  
    2.  **Arquivo CSV**: clique em **Procurar**e especifique o nome e o local do arquivo .csv para o qual você deseja exportar os dados limpos. Também é possível digitar o nome do arquivo .csv junto com o caminho completo para o qual você deseja exportar os dados limpos. Por exemplo, "c:\ExportedData.csv." O arquivo é salvo no computador em que o [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] está instalado.  
  
    3.  **Arquivo do Excel**: clique em **Procurar**e especifique o nome e o local do arquivo do Excel para o qual você deseja exportar os dados limpos. Também é possível digitar o nome do arquivo do Excel junto com o caminho completo para o qual você deseja exportar os dados limpos. Por exemplo, "c:\ExportedData.xlsx". O arquivo é salvo no computador em que o [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] está instalado.  
  
2.  Marque a caixa de seleção **Padronizar Saída** para padronizar a saída com base no formato de saída selecionado para o domínio. Por exemplo, altere o valor da cadeia de caracteres para maiúsculas ou coloque a primeira letra da palavra em maiúscula. Para obter informações sobre como especificar o formato de saída de um domínio, consulte a lista **Saída de Formato para** em [Set Domain Properties](../data-quality-services/set-domain-properties.md).  
  
3.  Em seguida, selecione a saída de dados: exporte apenas os dados limpos ou exporte os dados limpos junto com as informações limpas.  
  
    -   **Somente Dados**: clique no botão de opção para exportar apenas os dados limpos.  
  
    -   **Dados e Informações de Limpeza**: clique no botão de opção para exportar os seguintes dados para cada domínio:  
  
        -   **\< domínio>Source**: O valor original no domínio.  
  
        -   **\< domínio>Output**: os valores limpos no domínio.  
  
        -   **\< domínio>_Reason**: A razão especificada para a correção do valor.  
  
        -   **\< domínio>Confidence**: O nível de confiança para todos os termos que foram corrigidos. É exibida como o valor decimal equivalente ao valor percentual correspondente. Por exemplo, um nível de confiança de 95% será exibido como .9500000.  
  
        -   **\< domínio>status**: O status do valor de domínio após a limpeza de dados. Por exemplo, **Sugerido**, **Novo**, **Inválido**, **Corrigido**ou **Correto**.  
  
        -   **Registrar Status**: além de ter um campo de status para cada domínio mapeado **(\< nome_do_domínio>status**), o **Status do registro** campo exibe o status de um registro. Se algum status de domínio no registro for *Novo* ou *Correto*, o **Status do Registro** será definido como *Correto*. Se algum status de domínio no registro for *Sugerido*, *Inválido*ou *Corrigido*, o **Status do Registro** será definido com o respectivo valor. Por exemplo, se algum status de domínio no registro for *Sugerido*, o **Status do Registro** será definido como *Sugerido*.  
  
            > [!NOTE]  
            >  Se você usar o serviço de dados de referência para a operação de limpeza, alguns dados adicionais sobre o valor de domínio também estarão disponíveis para exportação. Para obter mais informações, consulte [Limpar dados usando dados de referência e 40; 41; & externos Conhecimento](../data-quality-services/cleanse-data-using-reference-data-external-knowledge.md).  
  
4.  Clique em **Exportar** para exportar dados para o destino de dados selecionado. Se você tiver selecionado:  
  
    -   **SQL Server** como o destino de dados, uma nova tabela com o nome especificado será criada no banco de dados selecionado.  
  
    -   **Arquivo CSV** como o destino de dados, um arquivo .csv será criado no local no computador [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] com o nome do arquivo especificado anteriormente na caixa de nome do **Arquivo CSV** .  
  
    -   **Arquivo do Excel** como o destino de dados, um arquivo do Excel será criado no local no computador [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] com o nome do arquivo especificado anteriormente na caixa **Nome do arquivo do Excel** .  
  
5.  Clique em **Concluir** para fechar o projeto de qualidade de dados.  
  
##  <a name="Profiler"></a> Estatísticas do criador de perfil  
 A guia **Criador de Perfil** fornece estatísticas que indicam a qualidade dos dados de origem. A criação de perfil o ajuda a avaliar a efetividade da atividade de limpeza de dados e você pode determinar a extensão até a qual a limpeza de dados pôde aprimorar a qualidade dos dados.  
  
 A guia **Criador de Perfil** fornece as seguintes estatísticas para os dados de origem, por campo e domínio:  
  
-   **Registros**: quantos registros na amostra de dados foram analisados para a atividade de limpeza de dados  
  
-   **Corrigir Registros**: quantos registros foram considerados corretos  
  
-   **Registros Corrigidos**: quantos registros foram corrigidos  
  
-   **Registros Sugeridos**: quantos registros foram sugeridos  
  
-   **Registros Inválidos**: quantos registros estavam inválidos  
  
 As estatísticas de campo incluem o seguinte:  
  
-   **Campo**: o nome do campo nos dados de origem  
  
-   **Domínio**: o nome do domínio que é mapeado para o campo  
  
-   **Valores Corrigidos**: o número de valores de domínio que foram corrigidos  
  
-   **Valores Sugeridos**: o número de valores de domínio que foram sugeridos  
  
-   **Integridade**: a integridade de cada campo de origem mapeado para a atividade de limpeza  
  
-   **Exatidão**: a exatidão de cada campo de origem mapeado para a atividade de limpeza  
  
 Criação de perfil do DQS fornece duas dimensões de qualidade de dados: *integridade* (a extensão à qual os dados estão presentes) e *precisão* (o grau ao qual os dados podem ser usados para o uso pretendido). Se a criação de perfil estiver informando que um campo está relativamente incompleto, talvez você queira removê-lo da base de dados de conhecimento de um projeto de qualidade de dados. A criação de perfil talvez não forneça estatísticas confiáveis de integridade para domínios compostos. Se você precisar de estatísticas de integridade, use domínios únicos, em vez de domínios compostos. Para utilizar domínios compostos, talvez você queira criar uma base de dados de conhecimento com domínios únicos para a criação de perfil, a fim de determinar a integridade e criar outro domínio com um domínio composto para o processo de limpeza. Por exemplo, a criação de perfil pode mostrar 95% de integridade para registros de endereço usando um domínio composto, mas pode haver um nível muito mais alto de não integridade para uma das colunas, por exemplo, uma coluna de CEP. Neste exemplo, talvez você queira medir a integridade da coluna de CEP com um domínio único. A criação de perfil provavelmente fornecerá estatísticas de exatidão confiáveis para domínios compostos, pois é possível medir a exatidão para várias colunas juntas. O valor desses dados está na agregação composta, de modo que talvez você queira medir a exatidão com um domínio composto.  
  
 As estatísticas de exatidão provavelmente exigirão mais interpretação se você não estiver usando um serviço de dados de referência. Se você estiver usando um serviço de dados de referência para a limpeza de dados, terá um nível de confiança nas estatísticas de exatidão. Para obter mais informações sobre dados de limpeza usando o serviço de dados de referência, consulte [Limpar dados usando dados de referência e 40; 41; & externos Conhecimento](../data-quality-services/cleanse-data-using-reference-data-external-knowledge.md).  
  
### Limpando notificações  
 As condições seguintes resultam em notificações:  
  
-   Não há nenhuma correção ou sugestão para um campo. Talvez você queira removê-las do mapeamento, executar a descoberta da base de dados de conhecimento primeiro ou utilizar outra base de dados de conhecimento.  
  
-   Há relativamente poucas correções ou sugestões para um campo. Talvez você queira removê-las do mapeamento, executar a descoberta da base de dados de conhecimento primeiro ou utilizar outra base de dados de conhecimento.  
  
-   O nível de exatidão do campo é muito baixo. Talvez você queira verificar o mapeamento ou considerar a execução da descoberta da base de dados de conhecimento primeiro.  
  
 Para obter mais informações sobre a criação de perfil, consulte [Data Profiling and Notifications in DQS](../data-quality-services/data-profiling-and-notifications-in-dqs.md).  
  
  