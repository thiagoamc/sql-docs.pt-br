---
title: Driver do OLE DB para SQL Server Support for High Availability, Disaster Recovery | Microsoft Docs
description: Suporte de OLE DB Driver para SQL Server para alta disponibilidade, recuperação de desastres
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 9e2d236030dd77f2902e2e13575cc4aea2bc39ae
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2018
---
# <a name="ole-db-driver-for-sql-server-support-for-high-availability-disaster-recovery"></a>Driver do OLE DB para SQL Server Support for High Availability, Disaster Recovery
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Este tópico discute o Driver do OLE DB para o suporte do SQL Server (adicionado no [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]) para [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]. Para obter mais informações sobre [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], consulte [Ouvintes do Grupo de Disponibilidade, Conectividade do Cliente e Failover do Aplicativo &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md), [Criação e Configuração de Grupos de Disponibilidade &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/creation-and-configuration-of-availability-groups-sql-server.md), [Clustering de Failover e Grupos de Disponibilidade AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md) e [Secundárias Ativas: Réplicas Secundárias Legíveis&#40;Grupos de Disponibilidade AlwaysOn&#41;](../../../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md).  
  
 Você pode especificar o ouvinte de um determinado grupo de disponibilidade na cadeia de conexão. Se um Driver OLE DB para o aplicativo do SQL Server está conectado a um banco de dados em um grupo de disponibilidade faz failover, a conexão original será interrompida e o aplicativo deverá abrir uma nova conexão para continuar o trabalho após o failover.  
  
 Se você não estiver se conectando a um ouvinte de grupo de disponibilidade e se vários endereços IP estiverem associados um nome de host, o OLE DB Driver para SQL Server irá iterar em sequência por todos os endereços IP associados à entrada DNS. Isso pode demorar muito se o primeiro endereço IP retornado pelo servidor DNS não estiver associado a nenhuma NIC (placa de interface de rede). Ao se conectar a um ouvinte de grupo de disponibilidade, OLE DB Driver para SQL Server tenta estabelecer conexões com todos os endereços IP em paralelo e se uma tentativa de conexão for bem-sucedida, o driver descartará qualquer tentativa de conexão pendente.  
  
> [!NOTE]  
>  O aumento do tempo limite de conexão e a implementação de lógica de repetição de conexão aumentarão a probabilidade de um aplicativo se conectar a um grupo de disponibilidade. Além disso, como uma conexão pode falhar devido a um failover de grupo de disponibilidade, você deve implementar lógica de repetição de conexão, repetindo uma conexão com falha até se reconectar.  
  
## <a name="connecting-with-multisubnetfailover"></a>Conectando-se ao MultiSubnetFailover  
 Sempre especifique **MultiSubnetFailover=Yes** quando for se conectar a um ouvinte de grupo de disponibilidade do SQL Server 2012 ou uma instância de cluster de failover do SQL Server 2012. **MultiSubnetFailover** permite failover mais rápido para todos os grupos de disponibilidade e o cluster de failover da instância do SQL Server 2012 e reduzirá significativamente o tempo de failover de único e de várias sub-redes topologias AlwaysOn. Durante um failover de várias sub-redes, o cliente tentará conexões em paralelo. Durante um failover de sub-rede, o OLE DB Driver para SQL Server repetirá agressivamente a conexão TCP.  
  
 O **MultiSubnetFailover** propriedade de conexão indica que o aplicativo está sendo implantado em um grupo de disponibilidade ou instância de Cluster de Failover, e esse Driver OLE DB para SQL Server tentará se conectar ao banco de dados no primário [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instância tentando se conectar a todos os IPs de endereços. Quando **MultiSubnetFailover=Yes** é especificado para uma conexão, o cliente repete as tentativas de conexão TCP mais rápido do que os intervalos de retransmissão TCP padrão do sistema operacional. Isso permite uma reconexão mais rápida após o failover de um grupo de disponibilidade AlwaysOn ou um sempre na instância de Cluster Failover e é aplicável a sub-redes único e vários grupos de disponibilidade e instâncias de Cluster de Failover.  
  
 Para obter mais informações sobre palavras-chave de cadeia de caracteres de conexão, consulte [usando Conexão String Keywords com OLE DB para SQL Server](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md).  
  
 A especificação de **MultiSubnetFailover=Yes** durante a conexão a algo que não seja um ouvinte de grupo de disponibilidade ou uma Instância de Cluster de Failover pode resultar em um impacto de desempenho negativo e não há suporte para isso.  
  
 Use as diretrizes a seguir para conectar-se a um servidor em um grupo de disponibilidade ou Instância de Cluster de Failover:  
  
-   Use a propriedade de conexão **MultiSubnetFailover** quando estiver se conectando a uma ou várias sub-redes; isso melhorará o desempenho em ambos os casos.  
  
-   Para conectar-se a um grupo de disponibilidade, especifique o ouvinte do grupo de disponibilidade como o servidor em sua cadeia de conexão.  
  
-   Conectar-se a uma instância do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] configurada com mais de 64 endereços IP causará uma falha de conexão.  
  
-   O comportamento de um aplicativo que usa a propriedade de conexão **MultiSubnetFailover** não é afetado com base no tipo de autenticação: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Autenticação, Autenticação Kerberos ou Autenticação do Windows.  
  
-   Você pode aumentar o valor de **loginTimeout** para acomodar o tempo de failover e reduzir as tentativas de repetição de conexão do aplicativo.  
  
-   Não há suporte a transações distribuídas.  
  
 Se o roteamento somente leitura não estiver em ação, conectar-se a um local de réplica secundária em um grupo de disponibilidade apresentará falha nas seguintes situações:  
  
1.  Se o local de réplica secundário não for configurado para aceitar conexões.  
  
2.  Se um aplicativo usar **ApplicationIntent=ReadWrite** (discutido abaixo) e o local de réplica secundária estiver configurado para acesso somente leitura.  
  
 Uma conexão falhará se uma réplica primária for configurada para rejeitar cargas de trabalho somente leitura e a cadeia de conexão contiver **ApplicationIntent=ReadOnly**.  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>Atualizando para usar clusters de várias sub-redes a partir do espelhamento de banco de dados  
 Um erro de conexão ocorrerá se as palavras-chave de conexão **MultiSubnetFailover** e **Failover_Partner** estiverem presentes na cadeia de conexão. Um erro também ocorrerá se a palavra-chave **MultiSubnetFailover** for usada e o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] retornar uma resposta de parceiro de failover indicando que ela faz parte de um par de espelhamento de banco de dados.  
  
 Se você atualizar um Driver OLE DB para o aplicativo do SQL Server que atualmente usa espelhamento de banco de dados em um cenário de várias sub-redes, você deve remover o **Failover_Partner** propriedade de conexão e substituí-lo por  **MultiSubnetFailover** definida como **Sim** e substitua o nome do servidor na cadeia de conexão com um ouvinte de grupo de disponibilidade. Se uma cadeia de conexão usa **Failover_Partner** e **MultiSubnetFailover=Yes**, o driver gerará um erro. No entanto, se uma cadeia de conexão usar **Failover_Partner** e **MultiSubnetFailover=No** (ou **ApplicationIntent=ReadWrite**), o aplicativo usará o espelhamento de banco de dados.  
  
 O driver retornará um erro se o espelhamento de banco de dados for usado no banco de dados primário no AG e se **MultiSubnetFailover=Yes** for usado na cadeia de conexão que se conecta a um banco de dados primário, em vez de ao ouvinte de um grupo de disponibilidade.  
  
## <a name="specifying-application-intent"></a>Especificando a intenção do aplicativo  
 Quando **ApplicationIntent = ReadOnly**, o cliente solicita uma carga de trabalho de leitura ao se conectar a um banco de dados do Always On habilitado. O servidor irá impor a intenção no momento da conexão e durante uma instrução USE de banco de dados, mas somente para um banco de dados habilitado para AlwaysOn.  
  
 A palavra-chave **ApplicationIntent** não funciona com bancos de dados herdados somente leitura.  
  
 Um banco de dados pode permitir ou impedir que cargas de trabalho de leitura no banco de dados de sempre no destino. (Isso é feito com a cláusula **ALLOW_CONNECTIONS** das instruções **PRIMARY_ROLE** e **SECONDARY_ROLE**[!INCLUDE[tsql](../../../includes/tsql-md.md)].)  
  
 A palavra-chave **ApplicationIntent** é usada para habilitar o roteamento somente leitura.  
  
## <a name="read-only-routing"></a>Roteamento somente leitura  
 O roteamento somente leitura é um recurso que pode assegurar a disponibilidade de uma réplica somente leitura de um banco de dados. Para habilitar roteamento somente leitura:  
  
1.  Você deve conectar-se a um ouvinte de grupo de disponibilidade AlwaysOn.  
  
2.  A palavra-chave de cadeia de conexão **ApplicationIntent** deve ser definida como **ReadOnly**.  
  
3.  O grupo de disponibilidade deve ser configurado pelo administrador de banco de dados para permitir o roteamento somente leitura.  
  
 É possível que nem todas as várias conexões que usam roteamento somente leitura se conectem à mesma réplica somente leitura. Alterações na sincronização de banco de dados ou alterações na configuração de roteamento de servidor podem resultar em conexões de cliente com réplicas somente leitura diferentes. Para garantir que todas as solicitações somente leitura conectem-se à mesma réplica somente leitura, não transmita um ouvinte de grupo de disponibilidade à palavra-chave de cadeia de conexão **Server**. Em vez disso, especifique o nome da instância somente leitura.  
  
 O roteamento somente leitura pode demorar mais tempo do que a conexão ao primário porque o roteamento somente leitura conecta-se primeiramente ao primário e depois procura o melhor secundário legível disponível. Por isso, você deve aumentar seu tempo limite de logon.  

  
## <a name="ole-db"></a>OLE DB  
 O Driver OLE DB para SQL Server dá suporte a ambos os **ApplicationIntent** e o **MultiSubnetFailover** palavras-chave.   
  
 As palavras-chave do cadeia de caracteres de conexão do OLE DB duas foram adicionadas para oferecer suporte a [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] no OLE DB Driver para SQL Server:  
  
-   **ApplicationIntent** 
-   **MultiSubnetFailover**  
  
 Para obter mais informações sobre palavras-chave de cadeia de caracteres de conexão no Driver do OLE DB para SQL Server, consulte [usando Conexão String Keywords com OLE DB para SQL Server](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md).  

### <a name="application-intent"></a>Tentativa de aplicativo 

 As propriedades de conexão equivalentes são:  
  
-   **SSPROP_INIT_APPLICATIONINTENT**  
  
-   **DBPROP_INIT_PROVIDERSTRING**  
  
 Um Driver OLE DB para o aplicativo de OLE DB do SQL Server pode usar um dos métodos para especificar intenção do aplicativo:  
  
 **IDBInitialize:: Initialize**  
 **IDBInitialize::Initialize** usa o conjunto previamente configurado de propriedades para inicializar a fonte de dados e criar o objeto de fonte de dados. Especifique a tentativa de aplicativo como uma propriedade de provedor ou como parte da cadeia de caracteres de propriedades estendidas.  
  
 **IDataInitialize:: Getdatasource**  
 **IDataInitialize::GetDataSource** usa uma cadeia de conexão de entrada que pode conter a palavra-chave **Application Intent**.  
  
 **IDBProperties::GetProperties**  
 **IDBProperties::GetProperties** recupera o valor da propriedade atualmente definida na fonte de dados.  Você pode recuperar o valor de **Application Intent** através das propriedades _INIT_PROVIDERSTRING e SSPROP_INIT_APPLICATIONINTENT.  
  
 **IDBProperties::SetProperties**  
 Para definir o valor da propriedade **ApplicationIntent**, chame **IDBProperties::SetProperties** passando a propriedade **SSPROP_INIT_APPLICATIONINTENT** com o valor da propriedade "**ReadWrite**" ou "**ReadOnly**" ou **DBPROP_INIT_PROVIDERSTRING** com o valor contendo "**ApplicationIntent=ReadOnly**" ou "**ApplicationIntent=ReadWrite**".  
  
 Você pode especificar a tentativa de aplicativo no campo Propriedades de Tentativa de Aplicativo da guia Tudo na caixa de diálogo **Propriedades de Vínculo de Dados**.  
  
 Quando forem estabelecidas conexões implícitas, a conexão implícita usará a configuração de tentativa de aplicativo da conexão pai. Da mesma forma, várias sessões criadas a partir da mesma fonte de dados herdarão a configuração de tentativa de aplicativo da fonte de dados.  
  
### <a name="multisubnetfailover"></a>MultiSubnetFailover

A propriedade de conexão equivalente é:  
  
-   **SSPROP_INIT_MULTISUBNETFAILOVER**  

A propriedade SSPROP_INIT_MULTISUBNETFAILOVER é do tipo booliano. A propriedade aceita valores de VARIANT_TRUE ou VARIANT_FALSE.

Para definir o valor da propriedade MultiSubnetFailover, chame **idbproperties:: SetProperties** passando a propriedade SSPROP_INIT_MULTISUBNETFAILOVER com valor **VARIANT_TRUE** ou **VARIANT_ FALSE**. 

#### <a name="example"></a>Exemplo

```
DBPROP rgPropMultisubnet;

rgPropMultisubnet.dwPropertyID = SSPROP_INIT_MULTISUBNETFAILOVER;
rgPropMultisubnet.dwOptions = DBPROPOPTIONS_REQUIRED;
rgPropMultisubnet.dwStatus = DBPROPSTATUS_OK;
rgPropMultisubnet.colid = DB_NULLID;
V_VT(&(rgPropMultisubnet.vValue)) = VT_BOOL;
V_BOOL(&(rgPropMultisubnet.vValue)) = VARIANT_TRUE;

DBPROPSET PropSet;

PropSet.rgProperties = &rgPropMultisubnet;
PropSet.cProperties = 1;
PropSet.guidPropertySet = DBPROPSET_SQLSERVERDBINIT;
IDBProperties* pIDBProperties = NULL;
hr = pIDBInitialize->QueryInterface(IID_IDBProperties, (void **)&pIDBProperties);
pIDBProperties->SetProperties(1, &PropSet);
```



## <a name="see-also"></a>Consulte também  
 [Driver do OLE DB para recursos do SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)    
 [Usando palavras-chave de cadeia de caracteres de Conexão com o Driver do OLE DB para SQL Server](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)  
  
  
