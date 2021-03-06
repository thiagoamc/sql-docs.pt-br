---
title: "Migração de dados MySQL para o SQL Server - banco de dados do SQL Azure (MySQLToSQL) | Microsoft Docs"
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-mysql
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Data Migration, server side data migration
- Data Migration,client side data migration
ms.assetid: a6a7f4d6-68aa-4a38-93bf-53eba0d7dc82
caps.latest.revision: "24"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0887825cf16986b78cad5d1889a04d73dacf222a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="migrating-mysql-data-into-sql-server---azure-sql-db-mysqltosql"></a>Migração de dados MySQL para o SQL Server - banco de dados do SQL Azure (MySQLToSQL)
Depois de ter sincronizado com êxito os objetos convertidos com [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou SQL Azure, você pode migrar dados do MySQL para [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou do SQL Azure.  
  
> [!IMPORTANT]  
> Se o mecanismo que está sendo usado é mecanismo de migração de dados do lado do servidor, em seguida, antes de migrar dados, você deve instalar o SSMA para os provedores do MySQL no computador que está executando o SSMA e pacote de extensão do MySQL. O [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] também deve estar executando o serviço de agente. Para obter mais informações sobre como instalar o pacote de extensão, consulte [instalar componentes do SSMA no SQL Server (MySQL para o SQL)](http://msdn.microsoft.com/en-us/6772d0c5-258f-4d7b-afb0-b5f810e71af1)  
  
## <a name="setting-migration-options"></a>Definindo opções de migração  
Antes de migrar dados para [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou do SQL Azure, examine as opções de migração de projeto no **configurações de projeto** caixa de diálogo.  
  
-   Usando essa caixa de diálogo, você pode definir opções, como tamanho de lote de migração, bloqueio de tabela, verificação de restrição, manipulação de valor nulo e manipulação de valor de identidade. Para obter mais informações sobre as configurações de projeto de migração, consulte [configurações do projeto (migração)](http://msdn.microsoft.com/en-us/2a3cba9e-cd54-4a8b-b858-8fc4cf2580d9).  
  
    Para obter mais informações sobre **configurações de migração de dados estendido**, consulte [configurações de migração de dados](http://msdn.microsoft.com/en-us/9c396df4-5676-4f32-9c57-70d4f15f9b7a)  
  
-   O **mecanismo de migração** no **configurações de projeto** caixa de diálogo permite que o usuário execute o processo de migração usando dois tipos de mecanismos de migração de dados:  
  
    1.  Mecanismo de migração de dados do lado cliente  
  
    2.  Mecanismo de migração de dados do lado servidor  
  
**Migração de dados do lado do cliente:**  
  
-   Para iniciar a migração de dados no lado do cliente, selecione o **mecanismo de migração de dados do lado do cliente** opção o **configurações de projeto** caixa de diálogo.  
  
-   Em **configurações de projeto**, o **mecanismo de migração de dados do lado do cliente** opção é definida.  
  
    > [!NOTE]  
    > O **mecanismo de migração de dados do lado do cliente** reside dentro do aplicativo do SSMA e, portanto, não depende da disponibilidade do pacote de extensão.  
  
**Migração de dados do lado do servidor:**  
  
-   Durante a migração de dados do lado do servidor, o mecanismo reside no banco de dados de destino. Ele é instalado por meio do pacote de extensão. Para obter mais informações sobre como instalar o pacote de extensão, consulte [instalar componentes do SSMA no SQL Server (MySQL para o SQL)](http://msdn.microsoft.com/en-us/6772d0c5-258f-4d7b-afb0-b5f810e71af1)  
  
-   Para iniciar a migração no lado do servidor, selecione o **mecanismo de migração de dados do lado do servidor** opção o **configurações de projeto** caixa de diálogo.  
  
> [!IMPORTANT]  
> **A migração de dados do lado do cliente** opção só está disponível para o SQL Azure.  
  
## <a name="migrating-data-to-sql-server-or-sql-azure"></a>Migrando dados para o SQL Server ou SQL Azure  
Migração de dados são uma operação de carregamento em massa que move linhas de dados de tabelas do MySQL em [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou tabelas SQL Azure em transações. O número de linhas carregado no [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] em cada transação é configurado nas configurações do projeto.  
  
Para exibir mensagens de migração, certifique-se de que o painel de saída está visível. Caso contrário, do **exibição** menu, selecione **saída**.  
  
**Para migrar dados**  
  
1.  Verifique o seguinte:  
  
    -   Os provedores de MySQL estão instalados no computador que está executando o SSMA.  
  
    -   Você sincronizou objetos convertidos com o banco de dados de destino (SQL Server / SQL Azure).  
  
2.  No Gerenciador de metadados do MySQL, selecione os objetos que contêm os dados que você deseja migrar:  
  
    -   Para migrar dados para todos os esquemas, selecione a caixa de seleção ao lado de **esquemas**.  
  
    -   Para migrar dados ou omitir tabelas individuais, primeiro expanda o esquema, **tabelas**e, em seguida, marque ou desmarque a caixa de seleção ao lado da tabela.  
  
3.  Para migrar dados, podem surgir dois casos:  
  
    **Migração de dados do lado do cliente:**  
  
    -   Para executar **a migração de dados do lado do cliente**, selecione o **mecanismo de migração de dados do lado do cliente** opção o **configurações de projeto** caixa de diálogo.  
  
    **Migração de dados do lado do servidor:**  
  
    -   Antes de executar a migração de dados no lado do servidor, certifique-se:  
  
        1.  O SSMA para o pacote de extensão do MySQL é instalado na instância do SQL Server.  
  
        2.  O [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent está em execução na instância do SQL Server  
  
    -   Para executar **migração de dados do lado do servidor**, selecione o **mecanismo de migração de dados do lado do servidor** opção o **configurações de projeto** caixa de diálogo.  
  
4.  Clique com botão direito **esquemas** no Gerenciador de metadados do MySQL e clique **migrar dados**. Também é possível migrar dados para objetos individuais ou as categorias de objetos: com o botão direito do objeto ou sua pasta pai; Selecione o **migrar dados** opção.  
  
    > [!NOTE]  
    > Se o SSMA para o pacote de extensão MySQL não está instalado na instância do SQL Server e se **mecanismo de migração de dados do lado do servidor** for selecionado, em seguida, ao migrar os dados para o banco de dados de destino, o seguinte erro: ' componentes de migração de dados do SSMA não foram encontrados no SQL Server, não será possível realizar a migração de dados do servidor. Verifique se o pacote de extensão está instalado corretamente '. Clique em **Cancelar** para finalizar a migração de dados.  
  
5.  No **conectar ao MySQL** caixa de diálogo, insira as credenciais de conexão e, em seguida, clique em **conectar**. Para obter mais informações sobre como se conectar ao MySQL, consulte [conectar ao MySQL &#40; MySQLToSQL &#41;](../../ssma/mysql/connect-to-mysql-mysqltosql.md)  
  
    Se o banco de dados de destino for SQL Server, em seguida, insira as credenciais de conexão no **conectar ao SQL Server** caixa de diálogo e clique em **conectar**. Para obter mais informações sobre como se conectar ao SQL Server, consulte [conectar ao SQL Server](http://msdn.microsoft.com/en-us/bb8c4bde-cfc2-4636-92ae-5dd24abe9536)  
  
    Se o banco de dados de destino do SQL Azure, em seguida, insira as credenciais de conexão no **conectar-se ao SQL Azure** caixa de diálogo e clique em **conectar**. Para obter mais informações sobre como se conectar ao SQL Azure, consulte [conectar-se ao banco de dados de SQL do Azure &#40; MySQLToSQL &#41;](../../ssma/mysql/connect-to-azure-sql-db-mysqltosql.md)  
  
    As mensagens serão exibidas no **saída** painel. Quando a migração for concluída, o **relatório de migração de dados** é exibida. Se todos os dados não migrar, clique na linha que contém os erros e, em seguida, clique em **detalhes**. Quando tiver terminado com o relatório, clique em **fechar**. Para obter mais informações sobre o relatório de migração de dados, consulte [o relatório de dados de migração (SSMA comuns)](http://msdn.microsoft.com/en-us/bbfb9d88-5a98-4980-8d19-c5d78bd0d241)  
  
> [!NOTE]  
> Quando o SQL Express edition é usado como o banco de dados de destino, é permitida somente cliente lado migração de dados e não há suporte para a migração de dados do lado de servidor.  
  
## <a name="see-also"></a>Consulte Também  
[Migrando bancos de dados MySQL para o SQL Server - banco de dados SQL do Azure &#40; MySQLToSql &#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
