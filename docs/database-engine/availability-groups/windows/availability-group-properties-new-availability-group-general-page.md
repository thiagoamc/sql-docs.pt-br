---
title: "Propriedades do Grupo de Disponibilidade: Novo Grupo de Disponibilidade (p&#225;gina geral) | Microsoft Docs"
ms.custom: ""
ms.date: "05/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.availabilitygroupproperties.general.f1"
ms.assetid: 9af5379f-91b8-4729-9f75-4a80242a30e9
caps.latest.revision: 15
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 15
---
# Propriedades do Grupo de Disponibilidade: Novo Grupo de Disponibilidade (p&#225;gina geral)
  Este tópico se aplica à guia **Geral** da caixa de diálogo **Novo Grupo de Disponibilidade** e da caixa de diálogo **Propriedades do Grupo de Disponibilidade** .  A caixa de diálogo **Novo Grupo de Disponibilidade** permite criar um novo grupo de disponibilidade sem usar o [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)]. A caixa de diálogo **Propriedades do Grupo de Disponibilidade** permite exibir e alterar a configuração de um grupo de disponibilidade existente.  
  
 **Para exibir as propriedades do grupo de disponibilidade**  
  
-   [Exibir as propriedades do grupo de disponibilidade &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/view-availability-group-properties-sql-server.md)  
  
-   [Usar o Painel AlwaysOn &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
## Lista de elementos de interface do usuário  
 **Nome do grupo de disponibilidade**  
 O nome do grupo de disponibilidade. Esse é um nome especificado pelo usuário que deve ser exclusivo no WSFC (Windows Server Failover Cluster).  
  
## Bancos de dados de disponibilidade  
 **Nome do Banco de Dados**  
 O nome de um banco de dados que foi adicionado ao grupo de disponibilidade.  
  
 **Adicionar**  
 Clique para adicionar um banco de dados ao grupo de disponibilidade.  
  
 **Remover**  
 Clique para remover um banco de dados selecionado do grupo de disponibilidade.  
  
## Réplicas de Disponibilidade  
 **Instância de servidor**  
 O nome de servidor da instância do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] que hospeda essa réplica e, para uma instância não padrão, seu nome de instância.  
  
 **Função**  
 **Primária**  
 Atualmente a réplica primária.  
  
 **Secundário**  
 Atualmente uma réplica secundária.  
  
 **Resolvendo**  
 Atualmente, a função de réplica está no processo de ser resolvida para a função primária ou secundária.  
  
 **Modo de Disponibilidade**  
 O modo de disponibilidade da réplica. Pode ser:  
  
 **Confirmação assíncrona**  
 A réplica primária pode confirmar transações sem esperar que a réplica secundária grave o log no disco.  
  
 **Confirmação síncrona**  
 A réplica primária espera para confirmar uma determinada transação até que a réplica secundária tenha gravado a transação em disco.  
  
 Para obter mais informações, veja [Modos de disponibilidade &#40;Grupos de Disponibilidade AlwaysOn&#41;](../../../database-engine/availability-groups/windows/availability-modes-always-on-availability-groups.md).  
  
 **Modo de Failover**  
 O modo de failover da réplica, um dos seguintes:  
  
 **Automatic**  
 Failover automático. A réplica é um destino para failovers automáticos. Essa opção terá suporte apenas se o modo de disponibilidade estiver definido como confirmação síncrona.  
  
 **Manual**  
 Failover manual. O failover da réplica pode ser feito apenas manualmente pelo administrador do banco de dados.  
  
 **Conexões na Função Primária**  
 O tipo de conexões de cliente com suporte quando a réplica possui a função primária.  
  
 **Permitir todas as conexões**  
 Todas as conexões são permitidas com os bancos de dados na réplica primária. Essa é a configuração padrão.  
  
 **Permitir conexões de leitura/gravação**  
 Conexões em que a propriedade de conexão Application Intent é definida como **ReadOnly** não são permitidas. Quando a propriedade Application Intent está definida como **ReadWrite** ou não está definida, a conexão é permitida. Para obter mais informações sobre a propriedade de conexão Tentativa de Aplicativo, consulte [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 **Secundária Legível**  
 Se uma réplica de disponibilidade que está executando a função primária (isto é, está atuando como uma réplica secundária) pode aceitar conexões de clientes, um dos seguintes:  
  
 **Não**  
 Nenhuma conexão direta é permitida para bancos de dados secundários desta réplica. Eles não estão disponíveis para acesso de leitura. Essa é a configuração padrão.  
  
 **Tentativa de leitura somente**  
 Somente conexões diretas somente leitura são permitidas para bancos de dados secundários desta réplica. Os bancos de dados secundários estão disponíveis para acesso de leitura.  
  
 **Sim**  
 Todas as conexões são permitidas para os bancos de dados secundários desta réplica, mas somente para acesso de leitura. Os bancos de dados secundários estão disponíveis para acesso de leitura.  
  
 **Tempo Limite da Sessão (segundos)**  
 O número de segundos do período de tempo limite de sessão nesta réplica.  
  
 **URL do Ponto de Extremidade**  
 A URL do ponto de extremidade. Para obter informações sobre o formato dessas URLs, veja [Especificar a URL do ponto de extremidade ao adicionar ou modificar uma réplica de disponibilidade &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/specify endpoint url - adding or modifying availability replica.md).  
  
 **Adicionar**  
 Clique para adicionar uma réplica secundária ao grupo de disponibilidade.  
  
 **Remover**  
 Clique para remover uma réplica secundária especificada do grupo de disponibilidade.  
  
## Consulte também  
 [Visão geral dos grupos de disponibilidade AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)  
  
  