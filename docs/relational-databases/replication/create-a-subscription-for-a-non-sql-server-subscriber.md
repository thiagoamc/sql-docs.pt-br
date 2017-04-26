---
title: "Criar uma assinatura para um Assinante n&#227;o SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "subscriptions [SQL Server replication], non-SQL Server Subscribers"
  - "Subscribers [SQL Server replication], non-SQL Server Subscribers"
  - "Assinantes não SQL Server, assinaturas"
ms.assetid: 5020ee68-b988-4d57-8066-67d183e61237
caps.latest.revision: 28
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 28
---
# Criar uma assinatura para um Assinante n&#227;o SQL Server
  Este tópico descreve como criar uma assinatura para um Assinante não SQL Server no [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] usando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou [!INCLUDE[tsql](../../includes/tsql-md.md)]. Dados de publicação de suporte a replicação transacional e de instantâneo para Assinantes não [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Para obter informações sobre plataformas com suporte do assinante, consulte [assinantes não-SQL Server](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md).  
  
 **Neste tópico**  
  
-   **Para criar uma assinatura para um Assinante não SQL Server, usando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="SSMSProcedure"></a> Usando o SQL Server Management Studio  
 Para criar uma assinatura para um Assinante não [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
1.  Instale e configure o software de cliente Oracle e o provedor OLE DB apropriados no Distribuidor [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Para obter mais informações, consulte [Oracle Subscribers](../../relational-databases/replication/non-sql/oracle-subscribers.md) e [IBM DB2 Subscribers](../../relational-databases/replication/non-sql/ibm-db2-subscribers.md).  
  
2.  Crie uma publicação usando o Assistente para Nova Publicação. Para obter mais informações sobre a criação de publicações, consulte [criar uma publicação](../../relational-databases/replication/publish/create-a-publication.md) e [criar uma publicação de um banco de dados Oracle](../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md). Especifique as opções a seguir no Assistente para Nova Publicação:  
  
    -   Na página **Tipo de Publicação** , selecione **Publicação de Instantâneo** ou **Publicação Transacional**.  
  
    -   Na página **Snapshot Agent** , desmarque **Criar um instantâneo imediatamente.**  
  
         Você cria o instantâneo após a publicação estar habilitada para Assinantes não [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para garantir que o Snapshot Agent gere scripts de instantâneo e de inicialização adequados para os Assinantes não [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
3.  Habilitar a publicação de não -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] os assinantes que usam o **Propriedades de publicação - \< Nome_da_publicação>** caixa de diálogo. Consulte [Publication Properties, Subscription Options](../../relational-databases/replication/publication-properties-subscription-options.md) para obter mais informações sobre essa etapa.  
  
4.  Crie uma assinatura usando o Assistente para Nova Assinatura. Esse tópico proporciona mais informações sobre essa etapa.  
  
5.  (Opcional) Alterar o **pre_creation_cmd** propriedade para reter as tabelas no assinante do artigo. Esse tópico proporciona mais informações sobre essa etapa.  
  
6.  Gere um instantâneo para a publicação. Esse tópico proporciona mais informações sobre essa etapa.  
  
7.  Sincronize a assinatura. Para obter mais informações, consulte [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
#### Para habilitar uma publicação para Assinantes não SQL Server  
  
1.  Conecte-se ao Publicador no [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]e expanda o nó do servidor.  
  
2.  Expanda a pasta **Replicação** e, em seguida, a pasta **Publicações Locais** .  
  
3.  Com o botão direito na publicação e, em seguida, clique em **propriedades**.  
  
4.  Sobre o **Opções de assinatura** selecione um valor de **True** para a opção **Permitir assinantes não - SQL Server**. A seleção dessa opção altera várias propriedades de forma que a publicação seja compatível com Assinantes não [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    > [!NOTE]  
    >  Selecionando **True** define o valor da **pre_creation_cmd** propriedade para 'Descartar' do artigo. Essa definição especifica que a replicação deve descartar uma tabela no Assinante se coincidir com o nome de tabela no artigo. Se você tiver tabelas existentes no assinante que você deseja manter, use o [sp_changearticle](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md) o procedimento armazenado para cada artigo, especifique um valor 'Nenhum' para **pre_creation_cmd**: `sp_changearticle @publication= 'MyPublication', @article= 'MyArticle', @property='pre_creation_cmd', @value='none'`.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)] Você será solicitado a criar um novo instantâneo para a publicação. Se não quiser criar um neste momento, use mais tarde as etapas descritas no próximo procedimento “Como”.  
  
#### Para criar uma assinatura para um Assinante não SQL Server  
  
1.  Expanda a pasta **Replicação** e, em seguida, a pasta **Publicações Locais** .  
  
2.  Com o botão direito na publicação apropriada e, em seguida, clique em **novas assinaturas**.  
  
3.  Na página **Local do Distribution Agent** , certifique-se de que **Executar todos os agentes no Distribuidor** esteja selecionado. Assinantes não -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] não têm suporte para os agentes executando no Assinante.  
  
4.  Sobre o **assinantes** clique em **Adicionar assinante** e, em seguida, clique em **Adicionar assinante não-SQL Server**.  
  
5.  Na **Adicionar assinante não-SQL Server** caixa de diálogo, selecione o tipo de assinante.  
  
6.  Digite um valor no **Nome da fonte de dados**:  
  
    -   Para o Oracle, esse é o nome do substrato transparente de rede (TNS) que você configurou.  
  
    -   Para a IBM, esse pode ser qualquer nome. É comum especificar o endereço de rede do Assinante.  
  
     O nome da fonte de dados digitado nesta etapa e as credenciais especificadas na etapa 9 não são validados por este assistente. Não são usados pela replicação até que o Distribution Agent execute para uma assinatura. Certifique-se de que todos os valores foram testados conectando-se ao assinante usando uma ferramenta de cliente (como **sqlplus** para Oracle). Para obter mais informações, consulte [Oracle Subscribers](../../relational-databases/replication/non-sql/oracle-subscribers.md) e [IBM DB2 Subscribers](../../relational-databases/replication/non-sql/ibm-db2-subscribers.md).  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)] No **assinantes** página do assistente, o assinante é exibida agora no **assinante** coluna com somente leitura **(destino padrão)** no **banco de dados de assinatura** coluna:  
  
    -   Para o Oracle, um servidor tem, no máximo, um banco de dados, assim não é necessário especificar o banco de dados.  
  
    -   Para a IBM DB2, o banco de dados é especificado na propriedade **Catálogo Inicial** da cadeia de caracteres da conexão DB2, que pode ser digitada no campo **Opções de conexões adicionais** descrito mais adiante neste processo.  
  
8.  Sobre o **segurança do Distribution Agent** clique no botão de propriedades (**...**) próximo ao assinante para acessar o **segurança do Distribution Agent** caixa de diálogo.  
  
9. Na caixa de diálogo **Segurança do Distribution Agent** :  
  
    -   Nos campos **Processar conta**, **Senha**e **Confirmar senha** , digite a conta e a senha do [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows sob as quais o Distribution Agent deve executar e realizar conexões locais ao Distribuidor.  
  
         A conta requer essas permissões mínimas: membro o **db_owner** fixo de função de banco de dados no banco de dados de distribuição, membro da lista de acesso à publicação (PAL); permissões de leitura no compartilhamento de instantâneo; e permissão de leitura no diretório de instalação do provedor OLE DB. Para obter mais informações sobre a PAL, consulte [proteger o publicador](../../relational-databases/replication/security/secure-the-publisher.md).  
  
    -   No **Conectar ao Assinante**, nos campos **Logon**, **Senha**e **Confirmar senha** , digite o logon e a senha que devem ser usados para se conectar ao Assinante. Esse logon já deverá estar configurado e ter permissões suficientes para criar objetos no banco de dados de assinatura.  
  
    -   No **Opções adicionais de conexão** especifique as opções de conexão para o assinante na forma de uma cadeia de caracteres de conexão (Oracle não requer opções adicionais). Cada opção deverá estar separada por um ponto-e-vírgula. A seguir um exemplo de uma cadeia de conexão DB2 (as quebras de linha são para facilitar a leitura):  
  
        ```  
        Provider=DB2OLEDB;Initial Catalog=MY_SUBSCRIBER_DB;Network Transport Library=TCP;Host CCSID=1252;  
        PC Code Page=1252;Network Address=MY_SUBSCRIBER;Network Port=50000;Package Collection=MY_PKGCOL;  
        Default Schema=MY_SCHEMA;Process Binary as Character=False;Units of Work=RUW;DBMS Platform=DB2/NT;  
        Persist Security Info=False;Connection Pooling=True;  
        ```  
  
         A maioria das opções na cadeia de caracteres é específica do servidor DB2 que você está configurando, mas a opção **Processar Binário como Caractere** sempre deve ser definida como **False**. Um valor é necessário para a opção **Catálogo Inicial** para identificar o banco de dados de assinatura.  
  
10. No **agenda de sincronização** selecione uma agenda para o Distribution Agent no **agenda do agente** menu (a agenda é tipicamente **executar continuamente**).  
  
11. Na página **Inicializar Assinaturas** , especifique se a assinatura deve ser inicializada e caso positivo, onde deve ser inicializada.  
  
    -   Desmarque **Inicializar** só se você criou todos os objetos e adicionou todos os dados necessários no banco de dados de assinatura.  
  
    -   Selecione **imediatamente** da lista suspensa no **inicializar quando** coluna para que o agente de distribuição transfira arquivos para o assinante de instantâneo depois que o assistente for concluído. Selecione **Na primeira sincronização** para que o agente transfira os arquivos da próxima vez em que for agendado para executar.  
  
12. Na página **Ações do Assistente** , opcionalmente faça o script da assinatura. Para obter mais informações, consulte [Scripting Replication](../../relational-databases/replication/scripting-replication.md).  
  
#### Para reter tabelas no Assinante  
  
-   Por padrão, habilitando uma publicação para não -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] assinantes define o valor da **pre_creation_cmd** propriedade para 'Descartar' do artigo. Essa definição especifica que a replicação deve descartar uma tabela no Assinante se coincidir com o nome de tabela no artigo. Se você tiver tabelas existentes no assinante que você deseja manter, use o [sp_changearticle](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md) o procedimento armazenado para cada artigo, especifique um valor 'Nenhum' para **pre_creation_cmd**. `sp_changearticle @publication= 'MyPublication', @article= 'MyArticle', @property='pre_creation_cmd', @value='none'`.  
  
#### Para gerar um instantâneo para a publicação  
  
1.  Expanda a pasta **Replicação** e, em seguida, a pasta **Publicações Locais** .  
  
2.  Com o botão direito na publicação e, em seguida, clique em **Exibir o Status do Snapshot Agent**.  
  
3.  No **Exibir Status do Snapshot Agent - \< publicação>** caixa de diálogo, clique em **Iniciar**.  
  
 Quando o Agente de Instantâneo terminar de gerar o instantâneo, uma mensagem será exibida, como "[100%] Um instantâneo de 17 artigos foi gerado".  
  
##  <a name="TsqlProcedure"></a> Usando Transact-SQL  
 Crie assinaturas push para Assinantes não [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de forma programática, usando procedimentos armazenados de replicação.  
  
> [!IMPORTANT]  
>  Quando possível, solicite que os usuários insiram as credenciais de segurança em tempo de execução. Se for necessário armazenar credenciais em um arquivo de script, você deverá proteger o arquivo para impedir acesso não autorizado.  
  
#### Para criar uma assinatura push para uma publicação transacional ou de instantâneo para um assinante não SQL Server  
  
1.  Instale o mais recente provedor OLE DB para o Assinante não [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no Publicador e no Distribuidor. Para os requisitos de replicação para um provedor OLE DB, consulte [assinantes não-SQL Server](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md), [os assinantes Oracle](../../relational-databases/replication/non-sql/oracle-subscribers.md), [os assinantes do IBM DB2](../../relational-databases/replication/non-sql/ibm-db2-subscribers.md).  
  
2.  O publicador do banco de dados de publicação, verifique se que suporta a publicação não[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] assinantes executando [sp_helppublication & #40. O Transact-SQL e 41;](../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md).  
  
    -   Se o valor de **enabled_for_het_sub** é 1, não -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] há suporte para assinantes.  
  
    -   Se o valor de **enabled_for_het_sub** é 0, execute [sp_changepublication & #40. O Transact-SQL e 41;](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md), especificando **enabled_for_het_sub** para **@property** e **true** para **@value**.  
  
        > [!NOTE]  
        >  Antes de alterar **enabled_for_het_sub** para **true**, você deve descartar todas as assinaturas existentes na publicação. Não é possível definir **enabled_for_het_sub** para **true** quando a publicação também oferece suporte para assinaturas de atualização. Alterar **enabled_for_het_sub** afetará outras propriedades de publicação. Para obter mais informações, consulte [assinantes não-SQL Server](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md).  
  
3.  No publicador do banco de dados de publicação, execute [sp_addsubscription & #40. O Transact-SQL e 41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Especifique **@publication**, **@subscriber**, um valor de **(destino padrão)** para **@destination_db**, um valor de **push** para **@subscription_type**, e um valor de 3 para **@subscriber_type** (Especifica um provedor OLE DB).  
  
4.  No publicador do banco de dados de publicação, execute [sp_addpushsubscription_agent & #40. O Transact-SQL e 41;](../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md). Especifique o seguinte:  
  
    -   Os parâmetros **@subscriber**e **@publication** .  
  
    -   Um valor de **(destino padrão)** para **@subscriber_db**,  
  
    -   As propriedades de não[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da fonte de dados para **@subscriber_provider**, **@subscriber_datasrc**, **@subscriber_location**, **@subscriber_provider_string**, e **@subscriber_catalog**.  
  
    -   O [!INCLUDE[msCoName](../../includes/msconame-md.md)] as credenciais do Windows sob as quais o Distribution Agent no distribuidor executa **@job_login** e **@job_password**.  
  
        > [!NOTE]  
        >  As conexões feitas usando a autenticação integrada do Windows sempre usam as credenciais do Windows especificadas por **@job_login** e **@job_password**. O Distribution Agent sempre faz a conexão local com o Distribuidor usando a Autenticação Integrada do Windows. Por padrão, o agente se conecta ao Assinante usando a Autenticação Integrada do Windows.  
  
    -   Um valor de **0** para **@subscriber_security_mode** e as informações de logon do provedor OLE DB para **@subscriber_login** e **@subscriber_password**.  
  
    -   Agenda para o trabalho do Distribution Agent para essa assinatura. Para obter mais informações, consulte [Specify Synchronization Schedules](../../relational-databases/replication/specify-synchronization-schedules.md).  
  
    > [!IMPORTANT]  
    >  Ao criar uma inscrição de envio em um publicador com um distribuidor remoto, os valores fornecidos para todos os parâmetros, inclusive *job_login* e *job_password*, são enviados ao distribuidor como texto sem formatação. Você deve criptografar a conexão entre o Publicador e seu Distribuidor remoto antes de executar esse procedimento armazenado. Para obter mais informações, consulte [Habilitar conexões criptografadas para o mecanismo de banco de dados e 40; SQL Server Configuration Manager & 41;](../../database-engine/configure-windows/enable encrypted connections to the database engine.md).  
  
## Consulte também  
 [Assinantes do IBM DB2](../../relational-databases/replication/non-sql/ibm-db2-subscribers.md)   
 [Assinantes Oracle](../../relational-databases/replication/non-sql/oracle-subscribers.md)   
 [Outros assinantes não SQL Server](../../relational-databases/replication/non-sql/other-non-sql-server-subscribers.md)   
 [Conceitos dos procedimentos armazenados do sistema de replicação](../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Práticas recomendadas em relação à segurança de replicação](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  