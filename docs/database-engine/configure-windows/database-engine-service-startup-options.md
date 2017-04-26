---
title: "Op&#231;&#245;es de inicializa&#231;&#227;o do servi&#231;o Mecanismo de Banco de Dados | Microsoft Docs"
ms.custom: ""
ms.date: "07/21/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modo de usuário único [SQL Server], opção de inicialização"
  - "substituindo opções de inicialização padrão"
  - "modo de configuração mínima [SQL Server], opção de inicialização"
  - "opções de inicialização padrão"
  - "substituir temporariamente as opções de inicialização [SQL Server]"
  - "opções de inicialização [SQL Server]"
  - "iniciando o SQL Server, opções"
ms.assetid: d373298b-f6cf-458a-849d-7083ecb54ef5
caps.latest.revision: 80
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 80
---
# Op&#231;&#245;es de inicializa&#231;&#227;o do servi&#231;o Mecanismo de Banco de Dados
  As opções de inicialização designam certos locais de arquivos necessários durante inicialização e especificam algumas condições que abrangem o servidor. A maioria dos usuários não precisa especificar opções de inicialização a menos que você esteja solucionando problemas do [!INCLUDE[ssDE](../../includes/ssde-md.md)] ou tenha um problema incomum e é instruído a usar uma opção de inicialização pelo Suporte de Cliente do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!WARNING]  
>  O uso impróprio de opções de inicialização pode afetar o desempenho do servidor e impedir o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de iniciar.  
  
## Sobre as opções de inicialização  
 Quando você instala o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], a Instalação grava um conjunto de opções de inicialização padrão no Registro do [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. Você pode usar essas opções de inicialização para especificar um arquivo de banco de dados  mestre alternado, mestre arquivo de log de banco de dados ou arquivo de log de erros. Se o [!INCLUDE[ssDE](../../includes/ssde-md.md)] não conseguir localizar os arquivos necessários, o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] não será iniciado.  
  
 As opções de inicialização podem ser definidas com o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager. Para obter informações, veja [Configurar opções de inicialização do servidor &#40;SQL Server Configuration Manager&#41;](../../database-engine/configure-windows/configure-server-startup-options-sql-server-configuration-manager.md).  
  
## Lista de opções de inicialização  
  
|Opções de inicialização padrão|Descrição|  
|-----------------------------|-----------------|  
|**-d**  *master_file_path*|O caminho totalmente qualificado para o arquivo de banco de dados mestre (geralmente, C:\Arquivos de Programas\Microsoft SQL Server\MSSQL.*n*\MSSQL\Data\master.mdf). Se você não fornecer essa opção, os parâmetros de registro existentes serão usados.|  
|**-e**  *error_log_path*|O caminho totalmente qualificado para o arquivo de log de erros (normalmente, C:\Arquivos de Programa\Microsoft SQL Server\MSSQL.*n*\MSSQL\LOG\ERRORLOG). Se você não fornecer essa opção, os parâmetros de registro existentes serão usados.|  
|**-l**  *master_log_path*|O caminho totalmente qualificado para o arquivo de log do banco de dados mestre (geralmente, C:\Arquivos de Programas\Microsoft SQL Server\MSSQL.*n*\MSSQL\Data\mastlog.ldf). Se você não especificar essa opção, serão usados os parâmetros de registro existentes.|  
  
|Outras opções de inicialização|Descrição|  
|---------------------------|-----------------|  
|**-c**|Reduz o tempo de inicialização ao iniciar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no prompt de comando. Normalmente, o [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] inicia como um serviço chamando o Gerenciador de Controle de Serviços. Como o [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] não é iniciado como um serviço quando o prompt de comando é iniciado, use **-c** para ignorar esta etapa.|  
|**-f**|Inicia uma instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] com configuração mínima. Isso será útil se a definição de um valor de configuração (por exemplo, sobrecarga de confirmação de memória) impediu o servidor de ser iniciado. Iniciar o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no modo de configuração mínima coloca o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no modo de usuário único. Para obter mais informações, veja a descrição de **-m** a seguir.|  
|**-g**  *memory_to_reserve*|Especifica um número inteiro de megabytes (MB) de memória que o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deixará disponível para alocações de memória dentro do processo do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], mas fora do pool de memória do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. A memória fora do pool de memória é a área usada pelo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para carregar itens, como arquivos .dll de procedimento estendido, os provedores OLE DB referenciados por consultas distribuídas e objetos de automação referenciados em instruções [!INCLUDE[tsql](../../includes/tsql-md.md)]. O padrão é 256 MB.<br /><br /> O uso desta opção pode ajudar a ajustar alocação de memória, mas só quando a memória física excede o limite configurado definido pelo sistema operacional em memória virtual disponível para aplicativos. O uso desta opção pode ser apropriado em configurações de memória grandes nas quais os requisitos de uso de memória de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] são atípicos e o espaço de endereço virtual do processo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] está totalmente em uso. O uso incorreto dessa opção pode conduzir a condições nas quais uma instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pode não ser iniciada ou encontrar erros em tempo de execução.<br /><br /> Use o padrão para o parâmetro **-g**, a menos que você veja algum dos seguintes avisos no log de erros do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:<br /><br /> “Falha dos bytes virtuais alocados: FAIL_VIRTUAL_RESERVE \<tamanho>”<br /><br /> “Falha dos bytes virtuais alocados: FAIL_VIRTUAL_COMMIT \<tamanho>”<br /><br /> <br /><br /> Essas mensagens podem indicar que o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] está tentando liberar partes do pool de memória do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para encontrar espaço para itens, como arquivos .dll de procedimento armazenado estendido ou objetos de automação. Nesse caso, considere aumentar a quantidade de memória reservada pela opção **-g**.<br /><br /> Usar um valor menor que o padrão aumentará a quantidade de memória disponível para o pool de memória gerenciado pelo Gerenciador de Memória do SQL Server e pilhas de thread; isso pode, por sua vez, oferecer algum benefício de desempenho a cargas de trabalho de uso intenso de memória em sistemas que não usam muitos procedimentos armazenados estendidos, consultas distribuídas ou objetos de automação.|  
|**-m**|Inicia uma instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] em modo de usuário único. Quando você inicia uma instância de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] em modo de usuário único, só um único usuário pode conectar e o processo de CHECKPOINT não é iniciado. CHECKPOINT garante que transações concluídas sejam gravadas regularmente do cache de disco para o dispositivo de banco de dados. (Normalmente, essa opção será usada se você perceber problemas com bancos de dados do sistema que devem ser corrigidos.) Habilita a opção sp_configure allow updates. Por padrão, a permissão de atualizações está desabilitada. Iniciar o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no modo de usuário único permite que qualquer membro do grupo de Administradores locais do computador se conecte à instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] como um membro da função de servidor fixa sysadmin. Para obter mais informações, veja [Conectar-se ao SQL Server quando os administradores do sistema estão bloqueados](../../database-engine/configure-windows/connect-to-sql-server-when-system-administrators-are-locked-out.md). Para obter mais informações sobre o modo de usuário único, veja [Iniciar o SQL Server no modo de usuário único](../../database-engine/configure-windows/start-sql-server-in-single-user-mode.md).|  
|**Nome do Aplicativo -mClient**|Limita as conexões a um aplicativo cliente especificado. Por exemplo, `-mSQLCMD` limita conexões a uma única conexão, e essa conexão deve se identificar como o programa cliente SQLCMD. Use essa opção quando estiver iniciando o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no modo de usuário único e se um aplicativo cliente desconhecido estiver usando a única conexão disponível. Use `"Microsoft SQL Server Management Studio - Query" ` para se conectar com o Editor de Consultas do SSMS. A opção Editor de Consultas do SSMS não pode ser configurada com o [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] Configuration Manager, pois ele inclui o caractere traço, que é rejeitado pela ferramenta.<br /><br /> O nome do aplicativo cliente diferencia maiúsculas de minúsculas. Serão necessárias aspas duplas se o nome do aplicativo contiver espaços ou caracteres especiais.<br /><br />**Exemplos ao iniciar na linha de comando:**<br /><br />`C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn\sqlserver -s MSSQLSERVER -m"Microsoft SQL Server Management Studio - Query"` <br /><br />`C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn\sqlserver -s MSSQLSERVER -mSQLCMD` <br /><br /> **\*\* Observação de segurança \*\*** não use esta opção como um recurso de segurança. O aplicativo cliente fornece o nome do aplicativo cliente e pode fornecer um nome falso como parte da cadeia de conexão.|  
|**-n**|Não usa o log de aplicativo do Windows para registrar eventos do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se você iniciar uma instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] com **-n**, recomendamos que você também use a opção de inicialização **-e**. Caso contrário, eventos [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] não são registrados no log.|  
|**-s**|Permite iniciar uma instância nomeada do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Sem o parâmetro **-s** definido, a instância padrão tentará iniciar. Você deve passar para o diretório BINN apropriado da instância em um prompt de comando antes de iniciar o **sqlservr.exe**. Por exemplo, se Instance1 tiver de usar \mssql$Instance1 para seus binários, o usuário deverá estar no diretório \mssql$Instance1\binn para iniciar **sqlservr.exe -s instance1**.|  
|**-T**  *trace#*|Indica que uma instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deve ser iniciada com um sinalizador de rastreamento especificado (*trace#*) em vigor. São usados sinalizadores de rastreamento para iniciar o servidor com comportamento fora do padrão. Para obter mais informações, veja, [Sinalizadores de rastreamento &#40;Transact-SQL&#41;](../Topic/Trace%20Flags%20\(Transact-SQL\).md).<br /><br /> **\*\* Importante \*\*** Ao especificar um sinalizador de rastreamento com a opção **-T**, use um “T” maiúsculo para passar o número do sinalizador de rastreamento. Um "t" minúsculo é aceito através de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], mas isso define outros sinalizadores de rastreamento internos que só são exigidos através de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] engenheiros de suporte. (Parâmetros especificados na janela de inicialização do Painel de Controle não são legíveis.)|  
|**-x**|Desabilita os seguintes recursos de monitoramento:<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Contadores de monitor de desempenho<br /><br /> Manutenção da hora da CPU e as estatísticas de taxa de acertos de cache<br /><br /> Coleta de informações para o comando DBCC SQLPERF<br /><br /> Coleta de informações por algumas exibições de gerenciamento dinâmico<br /><br /> Muitos pontos de evento dos eventos estendidos<br /><br /> <br /><br /> **\*\* Aviso \*\*** Quando você usa a opção de inicialização **–x**, as informações disponíveis para diagnosticar problemas de desempenho e funcionais com o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] são bastante reduzidas.|  
|**-E**|Aumenta o número de extensões alocadas para cada arquivo em um grupo de arquivos. Essa opção pode ser útil para aplicativos de data warehouse que têm um número limitado de usuários que estão executando exames de índices ou de dados. Ela não deve ser usada em outros aplicativos porque pode afetar o desempenho de maneira prejudicial. Essa opção não tem suporte no versões de 32 bits do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
## Usando opções de inicialização para solucionar problemas  
 Algumas opções de inicialização, como o modo de usuário único e o modo de configuração mínima, são usados principalmente durante a solução de problemas. Iniciar o servidor para solucionar problemas com as opções **–m** ou **–f** é mais fácil na linha de comando, enquanto o sqlservr.exe é iniciado manualmente.  
  
> [!NOTE]  
>  Quando o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] é iniciado usando o **net start**, as opções de inicialização usam uma barra (/) em vez de hífen (-).  
  
## Usando opções de inicialização durante operações normais  
 Você pode desejar usar algumas opções de inicialização sempre que iniciar o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Essas opções, como **–g** ou inicialização com um sinalizador de rastreamento, são mais fáceis com a configuração dos parâmetros de inicialização usando o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager. Essas ferramentas salvam as opções de inicialização como chaves do Registro, habilitando o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para sempre ser iniciado com as opções de inicialização.  
  
## Suporte de compatibilidade  
 Não há suporte para o parâmetro **-h** no [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Este parâmetro foi usado em versões anteriores de instâncias de 32 bits do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para reservar espaço de endereço de memória virtual para metadados de inclusão de memória a quente quando AWE é habilitado. Para obter mais informações, veja [Recursos descontinuados do SQL Server no SQL Server 2016](../Topic/Discontinued%20SQL%20Server%20Features%20in%20SQL%20Server%202016.md).  
  
## Tarefas relacionadas  
 [Configurar a opção de configuração de servidor scan for startup procs](../../database-engine/configure-windows/configure-the-scan-for-startup-procs-server-configuration-option.md)  
  
 [Iniciar, parar, pausar, retomar, reiniciar o mecanismo de banco de dados, o SQL Server Agent ou o serviço SQL Server Browser](../../database-engine/configure-windows/start, stop, pause, resume, restart sql server services.md)  
  
## Consulte também  
 [CHECKPOINT &#40;Transact-SQL&#41;](../../t-sql/language-elements/checkpoint-transact-sql.md)   
 [Aplicativo sqlservr](../../tools/sqlservr-application.md)  
  
  