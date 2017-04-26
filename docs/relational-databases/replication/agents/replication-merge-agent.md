---
title: "Replication Merge Agent | Microsoft Docs"
ms.custom: ""
ms.date: "08/24/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Agente de Mesclagem, executáveis"
  - "Agente de Mesclagem, referência de parâmetro"
  - "agentes [replicação do SQL Server], Agente de Mesclagem"
  - "prompt de comando [replicação do SQL Server]"
ms.assetid: fe1e7f60-b0c8-45e9-a5e8-4fedfa73d7ea
caps.latest.revision: 64
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 64
---
# Replication Merge Agent
  O Agente de Mesclagem de Replicação é um executável utilitário que aplica o instantâneo inicial contido nas tabelas do banco de dados aos Assinantes. Ele também mescla as alterações incrementais de dados que ocorreram no Publicador depois que o instantâneo inicial foi criado e reconcilia conflitos de acordo com as regras que você configura ou usando um resolvedor personalizado que você cria.  
  
> [!NOTE]  
>  Os parâmetros podem ser especificados em qualquer ordem. Quando não são especificados parâmetros opcionais, são usados valores de configurações de registro predefinidos no computador local.  
  
## Sintaxe  
  
```  
  
replmerg [-?]   
-Publisher server_name[\instance_name]  
-PublisherDB publisher_database  
-Publication publication  
-Subscriber server_name[\instance_name]  
-SubscriberDB subscriber_database  
[-AltSnapshotFolder alt_snapshot_folder_path]  
[-Continuous]  
[-DefinitionFile def_path_and_file_name]  
[-DestThreads number_of_destination_threads]  
[-Distributor server_name[\instance_name]]  
[-DistributorLogin distributor_login]  
[-DistributorPassword distributor_password]  
[-DistributorSecurityMode [0|1]]  
[-DownloadGenerationsPerBatch download_generations_per_batch]  
[-DownloadReadChangesPerBatch download_read_changes_per_batch]  
[-DownloadWriteChangesPerBatch download_write_changes_per_batch]  
[-DynamicSnapshotLocation dynamic_snapshot_location]  
[-EncryptionLevel [0|1|2]]  
[-ExchangeType [1|2|3]]  
[-FastRowCount [0|1]]  
[-FileTransferType [0|1]]  
[-ForceConvergenceLevel [0|1|2 (Publisher|Subscriber|Both)]]  
[-FtpAddress ftp_address]  
[-FtpPassword ftp_password]  
[-FtpPort ftp_port]  
[-FtpUserNameftp_user_name]  
[-HistoryVerboseLevel [0|1|2|3]]  
[-Hostname host_name]  
[-InteractiveResolution [0|1]]  
[-InternetLogin internet_login]  
[-InternetPassword internet_password]  
[-InternetProxyLogin internet_proxy_login]  
[–InternetProxyPassword internet_proxy_password]  
[-InternetProxyServer internet_proxy_server]  
[-InternetSecurityMode [0|1]]  
[-InternetTimeout internet_timeout]  
[-InternetURL internet_url]  
[-KeepAliveMessageInterval keep_alive_message_interval_seconds]  
[-LoginTimeOut login_time_out_seconds]  
[-MakeGenerationInterval make_generation_interval_seconds]  
[-MaxBcpThreads number_of_threads]  
[-MaxDownloadChanges number_of_download_changes]  
[-MaxUploadChanges number_of_upload_changes]  
[-MetadataRetentionCleanup [0|1]]  
[-Output]  
[-OutputVerboseLevel [0|1|2]]  
[-ParallelUploadDownload [0|1]]  
[-PacketSize packet_size]   
[-PollingInterval polling_interval]  
[-ProfileName profile_name]  
[-PublisherFailoverPartner server_name[\instance_name] ]  
[-PublisherLogin publisher_login]  
[-PublisherPassword publisher_password]  
[-PublisherSecurityMode [0|1]]  
[-QueryTimeOut query_time_out_seconds]  
[-SrcThreads number_of_source_threads]  
[-StartQueueTimeout start_queue_timeout_seconds]  
[-SubscriberConflictClean [0|1]]  
[-SubscriberDatabasePath subscriber_path]  
[-SubscriberDBAddOption [0|1|2|3]]  
[-SubscriberLogin subscriber_login]  
[-SubscriberPassword subscriber_password   
[-SubscriberSecurityMode [0|1]]  
[-SubscriberType [0|1|2|3|4|5|6|7|8|9]]  
[-SubscriptionType [0|1|2]]  
[-SyncToAlternate [0|1]  
[-UploadGenerationsPerBatch upload_generations_per_batch]  
[-UploadReadChangesPerBatch upload_read_changes_per_batch]  
[-UploadWriteChangesPerBatch upload_write_changes_per_batch]  
[-UseInprocLoader]  
[-Validate [0|1|2|3]]  
[-ValidateInterval validate_interval]  
```  
  
## Argumentos  
 **-?**  
 Imprime todos os parâmetros disponíveis.  
  
 **-Publicador** *nome_do_servidor*[**\\***instance_name*]  
 É o nome do Publicador. Especifique *nome_do_servidor* para a instância padrão do [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nesse servidor. Especifique *nome_do_servidor***\\***nome_da_instância* para uma instância nomeada do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nesse servidor.  
  
 **-PublisherDB** *publisher_database*  
 É o nome do banco de dados Publicador.  
  
 **-Publicação** *publicação*  
 É o nome da publicação. Esse parâmetro só é válido se a publicação estiver definida para ter sempre um instantâneo disponível para assinaturas novas ou reiniciadas.  
  
 **-Assinante** *nome_do_servidor*[**\\***instance_name*]  
 É o nome do Assinante. Especifique *nome_do_servidor* para a instância padrão do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nesse servidor. Especifique *nome_do_servidor***\\***nome_da_instância* para uma instância nomeada do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nesse servidor.  
  
 **-SubscriberDB** *subscriber_database*  
 É o nome do banco de dados do Assinante.  
  
 **-AltSnapshotFolder** *alt_snapshot_folder_path*  
 É o caminho para a pasta que contém o instantâneo inicial para uma assinatura.  
  
 **-Continuous**  
 Especifica se o agente tenta sondar transações replicadas continuamente. Se especificado, o agente sondará as transações replicadas da origem em intervalos de sondagem, mesmo que não haja transações pendentes.  
  
 **-DestThreads** *number_of_destination_threads*  
 Especifica o número de threads de destino que o Merge Agent usa para aplicar alterações ao destino. O destino é o Publicador durante o carregamento e o Assinante durante o download. O padrão é 4.  
  
 **-DefinitionFile** *def_path_and_file_name*  
 É o caminho do arquivo de definição de agente. Um arquivo de definição de agente contém argumentos de prompt de comando para o agente. O conteúdo do arquivo é analisado como um arquivo executável. Use aspas duplas (") para especificar valores de argumentos que contêm caracteres arbitrários.  
  
 **-Distribuidor** *nome_do_servidor*[**\\***instance_name*]  
 É o nome do Distribuidor. Especifique *nome_do_servidor* para a instância padrão do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nesse servidor. Especifique *nome_do_servidor***\\***nome_da_instância* para uma instância nomeada do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nesse servidor. Para distribuição (push) do Distribuidor, o nome assumirá o padrão do nome da instância do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] no computador local.  
  
 **Parâmetros - DistributorLogin** *distributor_login*  
 É o nome de logon do Distribuidor.  
  
 **-DistributorPassword** *distributor_password*  
 É a senha do Distribuidor.  
  
 **-DistributorSecurityMode** [ **0**| **1**]  
 Especifica o modo de segurança do Distribuidor. Um valor de **0** indica [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] modo de autenticação (padrão) e um valor de **1** indica o modo de autenticação do Windows.  
  
 **-DownloadGenerationsPerBatch** *download_generations_per_batch*  
 É o número de gerações a ser processado em um único lote durante o download de alterações do Publicador para o Assinante. Uma geração está definida como um grupo lógico de alterações por artigo. O padrão para um vínculo de comunicação confiável é 100. O padrão para um vínculo de comunicação não confiável é 10.  
  
 **-DownloadReadChangesPerBatch** *download_read_changes_per_batch*  
 É o número de alterações a ser lido em um único lote durante o download de alterações do Publicador para o Assinante. O padrão é 100.  
  
 **-DownloadWriteChangesPerBatch** *download_write_changes_per_batch*  
 É o número de alterações a ser aplicado em um único lote durante o download de alterações do Publicador para o Assinante. O padrão é 100.  
  
 **-DynamicSnapshotLocation** *dynamic_snapshot_location*  
 É o local dos arquivos de instantâneo de dados filtrados quando a publicação usa filtros de linha com parâmetros.  
  
 **-EncryptionLevel** [ **0** | **1** | **2** ]  
 É o nível da criptografia SSL (Secure Sockets Layer) usada pelo Merge Agent ao fazer conexões.  
  
|Valor EncryptionLevel|Descrição|  
|---------------------------|-----------------|  
|**0**|Especifica que o SSL não é usado.|  
|**1**|Especifica que o SSL é usado, mas que +o agente não verifica se o certificado de servidor SSL é assinado por um emissor confiável.|  
|**2**|Especifica que o SSL é usado, e que o certificado é verificado.|  
  
 Para obter mais informações, consulte [Visão geral de segurança e 40; Replicação e 41;](../../../relational-databases/replication/security/security-overview-replication.md).  
  
 **-ExchangeType** [ **1**| **2**| **3**]  
 > [!WARNING]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../../includes/ssnotedepfuturedontuse-md.md)] Para restringir o carregamento, use o **@subscriber_upload_options** de **sp_addmergearticle** em vez disso.  
  
 Especifica o tipo de troca de dados durante a sincronização, que pode ser um dos seguintes:  
  
|Valor ExchangeType |Descrição|  
|------------------------|-----------------|  
|**1**|O agente deve carregar alterações de dados do Assinante para o Publicador.|  
|**2**|O agente deve baixar alterações de dados do Publicador para o Assinante.|  
|**3** (padrão)|A agente deve primeiro carregar alterações de dados do Assinante ao Publicador e em seguida baixar alterações de dados do Publicador para o Assinante. Você deve usar essa opção com sincronização da Web.|  
  
 Artigos somente download permitem controlar o comportamento da sincronização de artigos individuais em uma publicação e podem beneficiar o desempenho. Para obter mais informações, consulte [otimizar o desempenho de replicação de mesclagem com artigos Download-Only](../../../relational-databases/replication/merge/optimize-merge-replication-performance-with-download-only-articles.md).  
  
 Se usando **ExchangeType** para separar o carregamento e download fase da replicação de mesclagem em sessões separadas, você deve executar o agente de mesclagem com **ExchangeType** definido como 1 primeiro e, em seguida, execute o agente de mesclagem novamente com o valor 2. Se houver falha ao executar o agente de mesclagem com ambos os parâmetros, isso fará os metadados serem excluídos e exigirá que você reinicialize a assinatura (sem carregamento).  
  
 **-FastRowCount** [**0**|**1**]  
 Especifica que tipo de método de cálculo de número de linhas deve ser usado para validação de número de linhas. Um valor de **1** (padrão) indica que o método rápido. Um valor de **0** indica o método de contagem de linhas completa.  
  
 **-FileTransferType** [**0**|**1**]  
 Especifica o tipo de transferência de arquivo. Um valor de **0** indica UNC (convenção de nomenclatura universal) e um valor de **1** indica FTP (protocolo de transferência de arquivo).  
  
 **-ForceConvergenceLevel** [**0**|**1**|**2** ( **Publisher**| **assinante**| **ambos**)]  
 Especifica o nível de convergência que o Merge Agent deve usar e pode ser um dos seguintes:  
  
|Valor ForceConvergenceLevel |Descrição|  
|---------------------------------|-----------------|  
|**0** (padrão)|Padrão. Executa uma mesclagem padrão sem convergência adicional.|  
|**1**|Impõe convergência para todas as gerações.|  
|**2**|Impõe convergência para todas as gerações e linhagens corruptas corretas. Ao especificar esse valor, especifique onde as linhagens devem ser corrigidas: no Publicador, no Assinante ou em ambos.|  
  
 **-FtpAddress** *ftp_address*  
 É o endereço de rede do serviço FTP para o Distribuidor. Quando não especificado, **distribuidor** é usado.  
  
 **-FtpPassword** *ftp_password*  
 É a senha de usuário usada para se conectar ao serviço FTP.  
  
 **-FtpPort** *ftp_port*  
 É o número da porta do serviço FTP para o Distribuidor. Quando não especificado, o número da porta padrão para serviço de FTP (21) é usado.  
  
 **-FtpUserName** *ftp_user_name*  
 É o nome de usuário usado para se conectar ao serviço FTP. Quando não especificado, anônimo é usado.  
  
 **-HistoryVerboseLevel** [**1**|**2**|**3**]  
 Especifica a quantidade de histórico registrada durante uma operação de mesclagem. Você pode minimizar o efeito de registro de histórico no desempenho selecionando **1**.  
  
|Valor HistoryVerboseLevel|Descrição|  
|-------------------------------|-----------------|  
|**0**|Registre a mensagem de status de agente final, detalhes finais da sessão e qualquer erro.|  
|**1**|Registre detalhes incrementais da sessão em cada status da sessão, incluindo porcentagem concluída, além da mensagem de status final do agente, detalhes finais da sessão e qualquer erro.|  
|**2**|Padrão. Registre detalhes incrementais da sessão em cada status da sessão e detalhes da sessão no nível do artigo, incluindo porcentagem concluída, além da mensagem de status final do agente, detalhes finais da sessão e qualquer erro. Mensagens de status de agente também são registradas.|  
|**3**|O mesmo que **- HistoryVerboseLevel** = **2**, exceto que mais mensagens de progresso do agente são registradas.|  
  
 **-Hostname** *host_name*  
 É o nome de rede do computador local. O padrão é o nome do computador local.  
  
 **-InteractiveResolution** [**0**|**1**]  
 Especifica se resolução de conflito interativa é usada quando um conflito ocorre durante a sincronização. O padrão é **0**, indicando que a resolução interativa de conflito não é usada.  
  
 **-InternetLogin** *internet_login*  
 Especifica o nome de logon usado ao conectar a um [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Replication Listener ISAPI DLL que requer autenticação.  
  
 **-InternetPassword** *internet_password*  
 Especifica a senha usada ao conectar a um [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Replication Listener ISAPI DLL que requer autenticação.  
  
 **-InternetProxyLogin**  *internet_proxy_login*  
 Especifica o nome de logon usado ao se conectar a um servidor proxy, definido em *internet_proxy_server*, que requer autenticação.  
  
 **– InternetProxyPassword**  *internet_proxy_password*  
 Especifica a senha usada ao conectar-se a um servidor proxy, definido em *internet_proxy_server*, que requer autenticação.  
  
 **-InternetProxyServer**  *internet_proxy_server*  
 Especifica o servidor proxy para usar quando acessar o recurso HTTP especificado na *internet_url*.  
  
 **-InternetSecurityMode** [**0**|**1**]  
 Especifica o modo de segurança IIS usado ao conectar ao servidor Web durante sincronização da Web. Um valor de **0** indica autenticação básica e um valor de **1** indica a autenticação integrada do Windows (padrão).  
  
 **-InternetTimeout** *internet_timeout*  
 É o número de segundos antes que uma conexão para o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Replication Listener ISAPI DLL expire.  
  
 **-InternetURL** *internet_url*  
 Especifica o URL usado para se conectar ao [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Replication Listener ISAPI DLL. Essa propriedade deve ser especificada.  
  
 **-KeepAliveMessageInterval** *keep_alive_message_interval_seconds*  
 É o número de segundos antes que o thread de histórico verifique se alguma das conexões existentes está esperando por uma resposta do servidor. Esse valor pode ser diminuído para evitar que o agente de verificação marque o Merge Agent como suspeito ao executar um lote de execução longa. O padrão é **300** segundos.  
  
 **-LoginTimeOut** *login_time_out_seconds*  
 É o número de segundos antes que o logon expire. O padrão é **15** segundos.  
  
 **-MakeGenerationInterval** *make_generation_interval_seconds*  
 É o número de segundos a aguardar entre a criação de gerações ou lotes de alterações, para baixar ao cliente. O padrão é **1** segundo.  
  
 Makegeneration é o processo que prepara as alterações do Publicador para download para os assinantes e pode ser um gargalo de desempenho durante os downloads. Se o processo de makegeneration já foi executado dentro do intervalo especificado por **- MakeGenerationInterval**, o processo será ignorado para a sessão de sincronização atual. Isso poderá beneficiar a simultaneidade de sincronização e poderá ser especialmente útil se os Assinantes não esperarem baixar alterações.  
  
 **-MaxBcpThreads** *number_of_threads*  
 Especifica o número de operações de cópia em massa que podem ser executadas em paralelo. O número máximo de threads e conexões ODBC que existe simultaneamente é inferior a **MaxBcpThreads** ou o número de grandes volumes de cópia solicitações que aparecem na tabela do sistema **sysmergeschemachange** no banco de dados de publicação. **MaxBcpThreads** deve ter um valor maior que 0 e não tem nenhum limite superior embutido em código. O padrão é **1**.  
  
 **-MaxDownloadChanges** *number_of_download_changes*  
 Especifica o número máximo de linhas alteradas que deveria ser baixado do Publicador para o Assinante. O número de linhas baixado deve ser maior do que o máximo especificado porque as gerações concluídas são processadas e os threads de destino paralelos podem executar, cada um processando no mínimo 100 alterações na primeira passagem. Por padrão, todas as alterações que estão prontas serem baixadas são enviadas.  
  
 **-MaxUploadChanges** *number_of_upload_changes*  
 Especifica o número máximo de linhas alteradas que deve ser carregado do Assinante para o Publicador. O número de linhas carregado deve ser maior do que o máximo especificado porque as gerações concluídas são processadas e os threads de destino paralelos podem executar, cada um processando no mínimo 100 alterações na primeira passagem. Por padrão, todas as alterações que estão prontas serem carregadas são enviadas.  
  
 **-MetadataRetentionCleanup** [**0**|**1**]  
 Especifica se os metadados são removidos do [MSmerge_genhistory](../../../relational-databases/system-tables/msmerge-genhistory-transact-sql.md), [MSmerge_contents](../../../relational-databases/system-tables/msmerge-contents-transact-sql.md), [MSmerge_tombstone](../../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md), [MSmerge_past_partition_mappings](../../../relational-databases/system-tables/msmerge-past-partition-mappings-transact-sql.md), e [MSmerge_current_partition_mappings](../../../relational-databases/system-tables/msmerge-current-partition-mappings.md) com base no período de retenção da publicação. O padrão é **1**, indicando que a limpeza deve ocorrer. Um valor de **0** indica que a limpeza não deve ocorrer automaticamente.  
  
 **-Saída** *output_path_and_file_name*  
 É o caminho do arquivo de saída do agente. Se o nome de arquivo não for fornecido, a saída será enviada ao console. Se o nome do arquivo especificado existir, a saída será anexada ao arquivo.  
  
 **-OutputVerboseLevel** [**0**|**1**|**2**]  
 Especifica se a saída deve ser detalhada. Se o nível detalhado for **0**, só mensagens de erro serão impressas. Se o nível detalhado for **1**, todos do progresso relatarem mensagens são impressas. Se o nível detalhado for **2** (padrão), todas as mensagens de erro e mensagens de relatório de progresso são impressas, que é útil para depuração.  
  
 **-ParallelUploadDownload** [**0**|**1**]  
 Especifica se o Merge Agent deve processar em paralelo as alterações carregadas para o Publicador e as baixadas no Assinante, que são úteis em ambientes de grandes volumes com alta largura de banda de rede. Se **ParallelUploadDownload** é **1**, processamento paralelo é habilitado.  
  
 **-PacketSize**  
 É o tamanho do pacote, em bytes. O padrão é 4096 (bytes).  
  
 **-PollingInterval** *polling_interval*  
 É a frequência, em segundos, de consulta no Publicador ou no Assinante por alterações de dados. O padrão é 60 segundos.  
  
 **-ProfileName** *profile_name*  
 Especifica um perfil de agente a ser usado para parâmetros de agente. Se **ProfileName** for NULL, o perfil de agente será desabilitado. Se **ProfileName** não for especificado, o perfil padrão de tipo de agente será usado. Para obter informações, consulte [perfis do Replication Agent](../../../relational-databases/replication/agents/replication-agent-profiles.md).  
  
 **-PublisherFailoverPartner** *nome_do_servidor*[**\\***instance_name*]  
 Especifica a instância de parceiro de failover do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] que participa de uma sessão de espelhamento de banco de dados com o banco de dados de publicação. Para obter mais informações, consulte [espelhamento de banco de dados, replicação e 40; SQL Server & 41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md).  
  
 **-PublisherLogin** *publisher_login*  
 É o nome de logon do Publicador. Se **PublisherSecurityMode** é **0** (para [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] autenticação), esse parâmetro deve ser especificado.  
  
 **-PublisherPassword** *publisher_password*  
 É a senha do Publicador. Se **PublisherSecurityMode** é **0** (para [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] autenticação), esse parâmetro deve ser especificado.  
  
 **-PublisherSecurityMode** [**0**|**1**]  
 Especifica o modo de segurança do Publicador. Um valor de **0** indica [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] autenticação (padrão) e um valor de **1** indica o modo de autenticação do Windows.  
  
 **-QueryTimeOut** *query_time_out_seconds*  
 É o número de segundos antes que a consulta expire. O padrão é 300 segundos. O Merge Agent também usa o valor de **QueryTimeout** para determinar o tempo de espera para a geração de um instantâneo particionado quando esse valor é maior do que 1800.  
  
 **-SrcThreads** *number_of_source_threads*  
 Especifica o número de threads de origem que o Merge Agent usa para enumerar alterações da origem. A origem é o Publicador durante o carregamento e o Assinante durante o download. O padrão é **3**.  
  
 **-StartQueueTimeout** *start_queue_timeout_seconds*  
 É o número máximo de segundos que o Merge Agent aguarda quando o número de processos de mesclagem simultâneos em execução está no limite definido **@max_concurrent_merge** propriedade **sp_addmergepublication**. Se o número máximo de segundos for alcançado e o Merge Agent ainda estiver esperando, será fechado. Um valor de 0 significa que o agente espera indefinidamente, embora possa ser cancelado.  
  
 **-SubscriberDatabasePath** *subscriber_database_path*  
 É o caminho para o banco de dados Jet (arquivo. mdb) se **SubscriberType** é **2** (permite uma conexão com um banco de dados Jet sem um nome de fonte de dados de ODBC (DSN)).  
  
 **-SubscriberDBAddOption** [**0**| **1**| **2**| **3**]  
 Especifica se existe um banco de dados do Assinante.  
  
|Valor SubscriberDBAddOption|Descrição|  
|---------------------------------|-----------------|  
|**0**|Use o banco de dados existente (padrão).|  
|**1**|Crie um banco de dados de Assinante novo, vazio.|  
|**2**|Crie um novo banco de dados e anexe-o ao arquivo especificado.|  
|**3**|Crie um novo banco de dados, anexe o banco de dados e habilite todas as assinaturas que possam existir no arquivo.|  
  
> [!NOTE]  
>  Quando você usa valores **2** e **3**, o caminho do banco de dados para o assinante deve ser especificado no **SubscriberDatabasePath** opção.  
  
 **-SubscriberLogin** *subscriber_login*  
 É o nome de logon do Assinante. Se **SubscriberSecurityMode** é **0** (para [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] autenticação), esse parâmetro deve ser especificado.  
  
 **-SubscriberPassword** *subscriber_password*  
 É a senha de Assinante. Se **SubscriberSecurityMode** é **0** (para [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] autenticação), esse parâmetro deve ser especificado.  
  
 **-SubscriberSecurityMode** [ **0**| **1**]  
 Especifica o modo de segurança do Assinante. Um valor de **0** indica [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] autenticação (padrão) e um valor de **1** indica o modo de autenticação do Windows.  
  
 **-SubscriberConflictClean** [ **0**| **1**]  
 É se as tabelas de conflitos são limpas no assinante durante o processo de sincronização, onde um valor de **1** indica que as tabelas de conflitos no assinante são limpas. Esse parâmetro só é usado para assinaturas de publicações com log de conflitos descentralizado.  
  
 **-SubscriberType** [ **0**| **1**| **3**| **4**| **5**| **6**| **7**| **8**]  
 Especifica o tipo de conexão de Assinante usado pelo Merge Agent. Somente o valor padrão de **0** é suportado para esse parâmetro.  
  
 **-SubscriptionType**[ **0**| **1**| **2**]  
 Especifica o tipo de assinatura para distribuição. Um valor de **0** indica uma assinatura push (padrão), um valor de **1** indica uma assinatura pull e um valor de **2** indica uma assinatura anônima.  
  
 **-SyncToAlternate** [ **0 | 1**]  
 Especifica se o Merge Agent está sincronizando entre um Assinante e um Publicador alternativo. Um valor de **1** indica que é um publicador alternativo. O padrão é **0**.  
  
 **-UploadGenerationsPerBatch** *upload_generations_per_batch*  
 É o número de gerações a ser processado em um único lote durante o carregamento de alterações do Assinante para o Publicador. Uma geração está definida como um grupo lógico de alterações por artigo. O padrão para um link de comunicação confiável é **100**. O padrão para um vínculo de comunicação confiável é **1**.  
  
 **-UploadReadChangesPerBatch** *upload_read_changes_per_batch*  
 É o número de alterações a ser lido em um único lote durante o carregamento de alterações do Assinante para o Publicador. O padrão é **100**.  
  
 **-UploadWriteChangesPerBatch** *upload_write_changes_per_batch*  
 É o número de alterações a ser aplicado em um único lote durante o carregamento de alterações do Assinante para o Publicador. O padrão é **100**.  
  
 **-UseInprocLoader**  
 Aprimora o desempenho do instantâneo inicial fazendo com que o Merge Agent use o comando BULK INSERT ao aplicar arquivos de instantâneo no Assinante. Esse parâmetro é preterido porque não é compatível com o tipo de dados de XML. Se você não estiver replicando dados XML, esse parâmetro poderá ser usado. Esse parâmetro não pode ser usado com instantâneos de modo de caractere. Se você usar esse parâmetro, a conta de serviço do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] no Assinante deverá ter permissões de leitura no diretório onde os arquivos de dados .bcp de instantâneo estão localizados. Quando esse parâmetro não é usado, o driver ODBC carregado pelo agente lê a partir dos arquivos, portanto o contexto de segurança da conta de serviço do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] não é usado.  
  
 **-Validate** [**0**|**1**|**2**|**3**]  
 Especifica se a validação deve ser feita no final da mensagem de mesclagem e, se for, o tipo de validação. O valor de **3** é o valor recomendado.  
  
|Valor de validação|Descrição|  
|--------------------|-----------------|  
|**0** (padrão)|Nenhuma validação.|  
|**1**|Validação só de número de linhas.|  
|**2**|Validação de número de linhas e soma de verificação.|  
|**3**|Validação de número de linhas e soma de verificação binária.|  
  
> [!NOTE]  
>  A validação com o uso de soma de verificação binária ou soma de verificação pode reportar incorretamente uma falha se os tipos de dados forem diferentes no Assinante e no Publicador. Para obter mais informações, consulte a seção "Considerações para validação de dados" em [Validar dados replicados](../../../relational-databases/replication/validate-replicated-data.md).  
  
 **-ValidateInterval** *validate_interval*  
 É a frequência, em minutos, com que a assinatura é validada em modo contínuo. O padrão é **60** minutos.  
  
## Comentários  
  
> [!IMPORTANT]  
>  Se você instalou o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent para executar com uma conta Sistema Local em vez de uma conta de usuário de domínio (o padrão), o serviço só poderá acessar o computador local. Se o Merge Agent executado no [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent for configurado para usar o Modo de Autenticação do Windows ao fazer logon no [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], o Merge Agent falhará. A configuração padrão é Autenticação do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
 Para iniciar o Merge Agent, execute **replmerg.exe** no prompt de comando. Para obter informações, consulte [Executáveis do agente de replicação](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
 O histórico do agente de mesclagem para a sessão atual não é removido durante a execução em modo contínuo. Um agente de longa execução pode resultar em um grande número de entradas nas tabelas de histórico de mesclagem, o que pode afetar o desempenho. Para resolver esse problema, alterne para o modo agendado, ou continue a usar o modo contínuo, mas crie um trabalho dedicado para reiniciar periodicamente o agente de mesclagem, ou reduza o detalhamento em nível de histórico para reduzir o número de linhas e, assim, reduzir o impacto sobre o desempenho.  
  
## Consulte também  
 [Administração do agente de replicação](../../../relational-databases/replication/agents/replication-agent-administration.md)  
  
  