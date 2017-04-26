---
title: "Solucionando problemas de Publicadores Oracle | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "publicação Oracle [replicação do SQL Server], solução de problemas"
  - "solução de problemas [replicação do SQL Server], publicação Oracle"
ms.assetid: be94f1c1-816b-4b1d-83f6-2fd6f5807ab7
caps.latest.revision: 62
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 62
---
# Solucionando problemas de Publicadores Oracle
  Este tópico lista diversos problemas que poderiam surgir ao configurar e usar um Publicador Oracle.  
  
## É gerado um erro relativo ao software de rede e de cliente Oracle  
 A conta sob a qual [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] é executado no distribuidor deve ser concedido permissões read e execute para o diretório (e todos os subdiretórios) em que o software de rede de cliente Oracle está instalado. Se as permissões não forem concedidas ou os componentes de cliente Oracle não estiverem adequadamente instalados, você receberá a seguinte mensagem de erro:  
  
 "Falha na conexão ao servidor com [Microsoft OLE DB Provider for Oracle]. Cliente Oracle e componentes de rede não foram localizados. Esses componentes são fornecidos pela Oracle Corporation e são parte da instalação de software de cliente Oracle Versão 7.3.3 ou posterior. O provedor está incapaz de funcionar até que esses componentes estejam instalados."  
  
 Se um cliente Oracle apropriado houver sido instalado no Distribuidor, certifique-se de que o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] foi interrompido e reiniciado depois que a instalação do cliente estiver concluída. Isso é requerido para que o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] reconheça os componentes de cliente.  
  
 Se você houver se certificado de que as permissões foram concedidas e que os componentes foram instalados corretamente, mas esse erro persiste, verifique se as configurações de registro em HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDTC\MTxOCI estão corretas:  
  
-   Para Oracle 10g, as configurações corretas são  
  
    -   OracleOciLib = oci.dll  
  
    -   OracleSqlLib = orasql10.dll  
  
    -   OracleXaLib = oraclient10.dll  
  
-   Para Oracle 9i, as configurações corretas são  
  
    -   OracleOciLib = oci.dll  
  
    -   OracleSqlLib = orasql9.dll  
  
    -   OracleXaLib = oraclient9.dll  
  
## O Distribuidor do SQL Server não pode se conectar à instância do banco de dados Oracle  
 Se o Distribuidor do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] não pode se conectar ao Publicador Oracle, certifique-se de que:  
  
-   O software Oracle necessário esteja instalado no Distribuidor.  
  
-   O banco de dados de Oracle esteja online e você possa conectar-se a ele usando uma ferramenta como SQL*Plus.  
  
-   A replicação de logon usada para se conectar ao Publicador Oracle tenha permissões adequadas. Para obter mais informações, consulte [Configurar um editor Oracle](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md).  
  
-   Os nomes TNS definidos durante a configuração de Publicador Oracle estejam listados no arquivo tnsnames.ora.  
  
-   O Oracle Home e o caminho corretos estejam sendo usados. Mesmo se você tiver um conjunto de binários Oracle instalados no Distribuidor do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , certifique-se de que as variáveis do ambiente relacionadas ao Oracle Home tenham sido adequadamente configuradas. Se você alterar valores de variáveis do ambiente, deverá parar e reiniciar o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] para que a alteração entre em vigor.  
  
 Para obter mais informações sobre como configurar e testar a conectividade, consulte "Instalando e configurando Software de rede de cliente Oracle no [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] distribuidor" em [Configurar um editor Oracle](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md).  
  
## O Publicador Oracle está associado a outro Distribuidor  
 Um Publicador Oracle só pode estar associado a um Distribuidor do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Se um Distribuidor diferente estiver associado ao Publicador Oracle, ele deve ser descartado antes que o outro Distribuidor possa ser usado. Se o Distribuidor não for descartado primeiro, você receberá uma das seguintes mensagens de erro:  
  
-   "Instância de servidor oracle ' \<*OraclePublisherName*>' foi configurado anteriormente para usar ' \<*SQLServerDistributorName*>' como distribuidor. Para começar a usar ' \<*Novo_nome_do_distribuidor_do_sql_server*>' como distribuidor, você deve remover a configuração atual de replicação na instância do servidor Oracle, o que excluirá todas as publicações nessa instância do servidor. "  
  
-   "Servidor oracle ' \<*OracleServerName*>' já está definido como publicador ' \<*OraclePublisherName*>' no distribuidor ' \<*SQLServerDistributorName*>.*\< Nome_da_base_de_dados_de_distribuição>*'. Descarte o publicador ou o sinônimo público '*\< Nome_do_sinônimo>*' para recriar. "  
  
 Quando um Publicador Oracle é descartado, os objetos de replicação no banco de dados Oracle são automaticamente limpos. No entanto, a limpeza manual dos objetos de replicação Oracle é necessária em alguns casos. Para limpar manualmente objetos de replicação Oracle criados por replicação:  
  
1.  Conecte-se ao Publicador Oracle com permissões DBA.  
  
2.  Emita o comando SQL `DROP PUBLIC SYNONYM MSSQLSERVERDISTRIBUTOR;`.  
  
3.  Emita o comando SQL `DROP USER <replication_administrative_user_schema>``CASCADE;`.  
  
## É gerado o erro SQL Server 21663, relativo à falta de uma chave primária  
 Os artigos em publicações transacionais devem ter uma chave primária válida. Se não tiverem uma chave primária válida, você receberá a seguinte mensagem de erro ao tentar adicionar um artigo:  
  
 "Nenhuma chave primária válida encontrada para a tabela de origem [\<*TableOwner*>]. [ \<*TableName*>] "  
  
 Para obter informações sobre requisitos para chaves primárias, consulte a seção "Índices e Restrições Exclusivos" no tópico [Design Considerations and Limitations for Oracle Publishers](../../../relational-databases/replication/non-sql/design-considerations-and-limitations-for-oracle-publishers.md).  
  
## É gerado o erro SQL Server 21642, relativo a um logon de servidor vinculado duplicado  
 Quando um Publicador Oracle é configurado inicialmente, uma entrada de servidor vinculado é criada para a conexão entre o Publicador e o Distribuidor. O servidor vinculado tem o mesmo nome que o serviço TNS Oracle. Se você tentar criar um servidor vinculado com o mesmo nome, a seguinte mensagem de erro será mostrada:  
  
 "Os publicadores heterogêneos exigem um servidor vinculado. Um servidor vinculado chamado '*\< Nome_de_servidor_vinculado>*' já existe. Remova o servidor vinculado ou escolha um nome de publicador diferente."  
  
 Esse erro pode ocorrer se você tentar criar o servidor vinculado diretamente ou se tiver previamente descartado a relação entre o Publicador Oracle e o Distribuidor do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] e estiver agora tentando reconfigurá-lo. Se você receber esse erro ao tentar reconfigurar o publicador, descarte o servidor vinculado com [sp_dropserver & #40. O Transact-SQL e 41;](../../../relational-databases/system-stored-procedures/sp-dropserver-transact-sql.md).  
  
 Se você precisar se conectar ao editor Oracle através de uma conexão de servidor vinculado, crie outro nome do serviço TNS e use esse nome ao chamar [sp_addlinkedserver & #40. O Transact-SQL e 41;](../../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md). Para obter informações sobre como criar nomes de serviço TNS, consulte a documentação do Oracle.  
  
## É gerado o erro SQL Server 21617  
 A publicação Oracle usa o aplicativo SQL*PLUS Oracle para baixar o pacote de código de suporte do Publicador para o banco de dados Oracle. Antes de tentar configurar o publicador Oracle, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verifica se SQL\*PLUS acessível através do caminho de sistema no distribuidor. Se SQL\*PLUS não puder ser carregado, a seguinte mensagem de erro é mostrada:  
  
 "Não é possível executar o SQL*PLUS. Certifique-se de que uma versão atual do código de cliente Oracle esteja instalada no distribuidor."  
  
 Tente localizar o SQL\*PLUS no distribuidor. Para uma instalação de cliente Oracle 10g, o nome desse executável é sqlplus.exe. Normalmente, ele é instalado em %ORACLE_HOME%/bin. Para verificar se o caminho do SQL\*PLUS aparece no caminho do sistema, examine o valor da variável do sistema **caminho**:  
  
1.  Clique com botão direito **Meu computador**, e, em seguida, clique em **propriedades**.  
  
2.  Clique na guia **Avançado** e clique em **Variáveis de Ambiente**.  
  
3.  Na caixa de diálogo **Variáveis de Ambiente** , na lista **Variáveis de Sistema** , selecione a variável **Caminho** e, então, clique em **Editar**.  
  
4.  Na caixa de diálogo **Editar Variável de Sistema** : se o caminho para a pasta que contém sqlplus.exe não estiver presente na caixa de texto **Valor de Variável** , edite a cadeia para incluí-lo.  
  
5.  Clique em **OK** em cada caixa de diálogo aberta para sair e salvar as alterações.  
  
 Se você não puder localizar sqlplus.exe no Distribuidor, instale uma versão atual do software de cliente Oracle no Distribuidor. Para obter mais informações, consulte [Configurar um editor Oracle](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md).  
  
## É gerado o erro SQL Server 21620  
 Se você estiver se conectando a um banco de dados Oracle anterior à versão 8.1, a publicação Oracle requer que o software de cliente Oracle instalado no Distribuidor seja da versão 9. Se você estiver se conectando a um banco de dados Oracle que seja da versão 8.1 ou posterior, recomendamos que o software de cliente Oracle seja da versão 10 ou posterior.  
  
 Antes de tentar configurar o Publicador Oracle, a publicação Oracle verifica se a versão de SQL*PLUS acessível através do caminho do sistema no Distribuidor é a versão 9 ou posterior. Caso não seja, a seguinte mensagem de erro é mostrada:  
  
 A versão de SQL*PLUS acessível através da variável Caminho do Sistema não é atual o suficiente para oferecer suporte à publicação Oracle. Certifique-se de que uma versão atual do código de cliente Oracle esteja instalada no distribuidor."  
  
 Se você tem múltiplas versões de software de cliente Oracle instaladas no Distribuidor, certifique-se de que a versão mais recente seja pelo menos a versão 9 e que a variável Caminho do Sistema se refira primeiro a esta versão (referências a outras versões podem constar, desde que a mais recente apareça primeiro). Para obter mais informações sobre edição da variável Caminho do Sistema, consulte a seção "É gerado o erro SQL Server 21617", acima, neste tópico.  
  
## É gerado o erro SQL Server 21624 ou 21629  
 Para Distribuidores de 64 bits, a publicação Oracle usa o Provedor OLEDB Oracle para Oracle (OraOLEDB.Oracle). Certifique-se de que o provedor OLEDB Oracle esteja instalado e registrado no Distribuidor. Se o provedor não estiver instalado e registrado, uma ou ambas as seguintes mensagens de erro serão mostradas:  
  
-   "Não foi possível localizar o provedor OLEDB Oracle, OraOLEDB.Oracle, registrado no distribuidor '%s.' Certifique-se de que uma versão atual do provedor OLEDB Oracle esteja instalada e registrada no distribuidor."  
  
-   "A chave do Registro CLSID que indica que o Provedor OLEDB Oracle para Oracle, OraOLEDB.Oracle, foi registrado e não está presente no distribuidor. Certifique-se de que o provedor OLEDB Oracle esteja instalado e registrado no distribuidor."  
  
 Se você estiver usando software de cliente Oracle versão 10g, o provedor é OraOLEDB10.dll; para a versão 9i, é OraOLEDB.dll. O provedor é instalado em %ORACLE_HOME%\BIN (por exemplo, C:\oracle\product\10.1.0\Client_1\bin). Se você verificar que o provedor OLEDB Oracle não está instalado no Distribuidor, instale-o a partir do disco de instalação de software de cliente Oracle fornecido pela Oracle. Para obter mais informações, consulte [Configurar um editor Oracle](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md).  
  
 Se o provedor OLEDB Oracle estiver instalado, certifique-se de que esteja registrado. Para registrar o provedor DLL, execute o seguinte comando a partir do diretório em que o DLL está instalado e, então, pare e reinicie a instância do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] :  
  
1.  `regsvr32 OraOLEDB10.dll` ou `regsvr32 OraOLEDB.dll`.  
  
## É gerado o erro SQL Server 21626 ou 21627  
 Para verificar se o ambiente de publicação Oracle está adequadamente configurado, o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tenta conectar o Publicador Oracle com as credenciais de logon que você especificou durante a configuração. Se o Distribuidor do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] não puder conectar-se ao Publicador Oracle, a seguinte mensagem de erro será mostrada:  
  
-   "Não foi possível conectar-se ao servidor do banco de dados Oracle '%s' usando o provedor OLEDB Oracle OraOLEDB.Oracle."  
  
 Se essa mensagem de erro for mostrada, verifique a conectividade ao banco de dados Oracle executando SQL*PLUS diretamente usando o mesmo logon e senha especificados durante a configuração do Publicador Oracle. Para obter mais informações, consulte a seção "O Distribuidor do SQL Server não pode se conectar à instância de banco de dados Oracle", acima, neste tópico.  
  
## É gerado o erro SQL Server 21628  
 Para Distribuidores de 64 bits, a publicação Oracle usa o Provedor OLEDB Oracle para Oracle (OraOLEDB.Oracle). [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cria uma entrada de registro para permitir que o provedor Oracle seja executado em processo com o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Se houver um problema ao ler ou gravar essa entrada de registro, a seguinte mensagem de erro será mostrada:  
  
 "Não foi possível atualizar o registro de distribuidor '%s' para permitir que o provedor OLEDB Oracle OraOLEDB.Oracle seja executado em processo com o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Certifique-se de que o logon atual esteja autorizado para modificar chaves de registro pertencentes ao [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ."  
  
 A publicação Oracle requer que a entrada de registro exista e seja definida como **1** para Distribuidores de 64 bits. Se a entrada não existir, o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tentará criá-la. Se a entrada existe, mas estiver definida como **0**, a configuração não será alterada; haverá falha na configuração do Publicador Oracle.  
  
 Para exibir e modificar a configuração de registro:  
  
1.  Clique em **Iniciar**e em **Executar**.  
  
2.  Na caixa de diálogo **Executar** , digite **regedit**e, então, clique em **OK**.  
  
3.  Navegue até HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\*\< nome_da_instância>*\providers..  
  
     Incluída em Provedores deve haver uma pasta nomeada OraOLEDB.Oracle. Dentro dessa pasta deve haver o nome do valor DWORD **AllowInProcess**, com valor **1**.  
  
4.  Se você verificar que **AllowInProcess** está definido como **0**, atualize a entrada de registro para **1**:  
  
    1.  Com o botão direito na entrada e, em seguida, clique em **modificar**.  
  
    2.  Na caixa de diálogo **Editar Cadeia** , digite **1** no campo **Dados do Valor** .  
  
## É gerado o erro SQL Server 21684  
 Se a conta de usuário administrativo não tiver privilégios suficientes, a seguinte mensagem de erro será mostrada:  
  
 "As permissões associadas com o logon de administrador para o publicador Oracle '% s' não é suficiente."  
  
 Para verificar as permissões concedidas ao usuário, execute a seguinte consulta: `SELECT * from session_privs`. A saída deve ser semelhante ao seguinte:  
  
 `PRIVILEGE`  
  
 `------------------`  
  
 `CREATE SESSION`  
  
 `CREATE TABLE`  
  
 `CREATE PUBLIC SYNONYM`  
  
 `DROP PUBLIC SYNONYM`  
  
 `CREATE VIEW`  
  
 `CREATE SEQUENCE`  
  
 `CREATE PROCEDURE`  
  
 `CREATE TRIGGER`  
  
## Você encontra problemas de permissões para o esquema de usuário de replicação  
 O esquema de usuário de replicação deve ter as permissões descritas em "Criar o esquema de usuário manualmente" [Configurar um editor Oracle](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md).  
  
## Erro Oracle ORA-01000  
 A replicação usa cursores no Publicador Oracle durante o processo de adicionar artigos a uma publicação. É possível exceder o número máximo de cursores disponíveis no Publicador durante esse processo. Se isso acontecer, o seguinte erro será gerado:  
  
 "ORA-01000: máximo de cursores abertos excedido"  
  
 Para evitar esse problema, verifique se o **max_open_cursors** configuração nos bancos de dados Oracle é definida como um número suficientemente alto (pelo menos 1000). Para obter mais informações sobre essa configuração, consulte a documentação Oracle.  
  
## Erro Oracle ORA-01555  
 O seguinte erro de banco de dados Oracle não está relacionado à replicação instantânea; está relacionado ao modo como o Oracle constrói exibições de dados de leitura consistente:  
  
 "ORA-01555: Instantâneo muito antigo"  
  
 Usando objetos conhecidos como segmentos de reversão, o Oracle constrói exibições de dados de leitura consistente no point-in-time em que uma instrução SQL é emitida. Um erro "instantâneo muito antigo" pode ocorrer quando uma informação de reversão é substituída por outras sessões simultâneas. Antes do Oracle 9i, o método recomendado para reduzir a frequência desse erro era aumentar o tamanho e/ou o número de segmentos de reversão e atribuir grandes transações a um segmento de reversão específico.  
  
 No Oracle 9i, a Oracle introduziu o conceito de espaço de tabela UNDO, que substitui o segmento de reversão. Para prevenir o erro "instantâneo muito antigo" no Oracle 9i, recomenda-se:  
  
-   Criar um espaço de tabela UNDO com uma quantidade adequada de espaço livre.  
  
-   Definir a garantia de retenção no espaço de tabela (Oracle 10G e maior).  
  
-   Configurar os parâmetros de inicialização Oracle UNDO_MANAGEMENT e UNDO_RETENTION.  
  
 Para obter detalhes adicionais sobre como evitar o erro "instantâneo muito antigo", consulte a documentação do Oracle.  
  
## Erro Oracle ORA-22285  
 Se uma tabela inclui uma coluna BFILE, os dados para a coluna são armazenados no sistema de arquivos. A conta de usuário administrativo da replicação deve dispor de acesso ao diretório no qual os dados estão armazenados, usando a seguinte sintaxe:  
  
 `GRANT READ ON DIRECTORY <directory_name> TO <replication_administrative_user_schema>`  
  
 Se o acesso não for concedido, o seguinte erro será gerado pelo Log Reader Agent:  
  
 "ORA-22285: diretório ou arquivo inexistente para a operação FILEOPEN"  
  
## São feitas alterações que requerem reconfiguração do publicador  
 Alterações às tabelas de metadados de replicação ou a procedimentos requerem que você descarte e reconfigure o Publicador. Para reconfigurar o Publicador, você deve descartar e configurá-lo novamente usando [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], Transact-SQL ou RMO. Para obter informações sobre como configurar o publicador, consulte [Configurar um editor Oracle](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md).  
  
 **Para descartar um publicador Oracle (**SQL Server Management Studio**)**  
  
1.  Conecte-se ao Distribuidor para o Publicador Oracle no [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] e expanda o nó do servidor.  
  
2.  Clique com botão direito **replicação**, e, em seguida, clique em **Propriedades do distribuidor**.  
  
3.  Na página **Publicadores** da caixa de diálogo **Propriedades do Distribuidor** , desmarque a caixa de seleção para o Publicador Oracle.  
  
4.  Clique em **OK**.  
  
 **Para descartar um Publicador Oracle (Transact-SQL)**  
  
-   Executar **sp_dropdistpublisher**. Para obter mais informações, consulte [sp_dropdistpublisher & #40. O Transact-SQL e 41;](../../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md).  
  
## Consulte também  
 [Configurar um publicador Oracle](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)   
 [Visão geral da Publicação Oracle](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md)  
  
  