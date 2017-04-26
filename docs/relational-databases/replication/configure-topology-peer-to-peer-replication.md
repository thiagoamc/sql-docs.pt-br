---
title: "Configurar Topologia (replica&#231;&#227;o ponto a ponto) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.p2pwizard.peers.f1"
ms.assetid: 5377c59f-2e25-4852-a306-c87ae3dca9fd
caps.latest.revision: 29
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 29
---
# Configurar Topologia (replica&#231;&#227;o ponto a ponto)
  Use o **Configurar topologia** página para executar tarefas de configuração comuns, como adicionar novos nós, excluir nós e adicionar novas conexões entre nós existentes. O nó selecionado no **publicação** página desse assistente é exibida na superfície de design. Para especificar opções de configuração, clique com o botão direito do mouse em um nó, em uma conexão ou na superfície de design.  
  
> [!NOTE]  
>  O Assistente para Configurar Topologia Ponto a Ponto solicita as informações da topologia quando o assistente é fechado. Se o assistente for fechado e reaberto antes de todos os nós responderem à solicitação de informações, o assistente poderá mostrar uma rede parcial.  
  
## Opções  
 O **Configurar topologia** página contém os elementos de interface e opções que estão disponíveis quando você clica um elemento. A tabela a seguir descreve cada elemento de interface.  
  
|Elemento de interface|Descrição|  
|-----------------------|-----------------|  
|Superfície de design|Exibe outros elementos de interface. Para adicionar elementos, clique com o botão direito do mouse na superfície de design.|  
|![O primeiro nó em uma topologia](../../relational-databases/replication/media/p2pwizard-firstnode.png "O primeiro nó em uma topologia")|O nó original na topologia. Novos nós são iniciados usando uma cópia do banco de dados de publicação do nó original.|  
|![Um nó para o qual temos informações completas](../../relational-databases/replication/media/p2pwizard-complete.png "Um nó para o qual temos informações completas")|Um nó que está executando uma instância de [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ou uma versão posterior, para que a replicação tem informações completas. Para especificar opções de configuração, clique com o botão direito do mouse no nó.|  
|![Um nó para o qual temos informações incompletas](../../relational-databases/replication/media/p2pwizard-incomplete.png "Um nó para o qual temos informações incompletas")|Um nó para o qual a replicação tem informações incompletas. Para especificar opções de configuração, clique com o botão direito do mouse no nó.<br /><br /> A replicação tem informações incompletas por um dos seguintes motivos:<br /><br /> -O nó está executando uma instância de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], que não armazena todos os metadados exigidos pelo assistente.<br /><br /> -O nó está executando uma versão posterior do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], mas a replicação não é possível recuperar informações de assinatura do nó. Para solucionar essa situação:<br /><br /> Verifique se o banco de dados do nó está online e se você pode se conectar a ele usando as mesmas credenciais que os Agente de Distribuiçãos que se conectaram ao nó.<br /><br /> Verifique se o Agente de Leitor de Log e todos os Agente de Distribuiçãos conectados ao nó estão em execução.<br /><br /> Verifique se a definição do tempo limite de atualização é suficientemente alta para coletar todas as informações de topologia. Para definir o tempo limite, clique na superfície de design e clique em **Definir tempo limite de atualização**.|  
|Linhas cinza com setas|Conexão entre dois nós. Para adicionar uma conexão, clique com o botão direito do mouse em um dos nós que você quer conectar. Para remover uma conexão, clique com o botão direito do mouse na conexão.<br /><br /> Se a linha tiver uma única seta, a replicação terá informações incompletas para um dos nós.|  
  
### Opções para a superfície de design  
 **Redesenhar Gráfico**  
 Redesenhe os objetos na superfície de design sem atualizar a topologia. O novo desenho deverá fornecer uma exibição melhor da topologia.  
  
 **Atualizar Topologia**  
 Consulte cada nó na topologia e exiba informações atualizadas sobre cada nó. Se houver muitos nós, esse processo pode levar vários minutos.  
  
 Se o assistente solicitar informações de topologia, e, você fechar e reabrir o assistente, antes que todos os nós respondam à solicitação, essa página poderá não exibir todos os nós na topologia.  
  
 **Adicionar Novo Nó de Computador Par**  
 Adicionar uma instância de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à topologia ponto a ponto. A adição de uma instância, como um nó, cria uma publicação nessa instância depois que o assistente é concluído. Depois de adicionar o nó, clique com o botão direito do mouse, para adicionar uma conexão entre o nó novo e um nó existente.  
  
 Para participar de uma topologia ponto a ponto, a instância deve satisfazer os seguintes requisitos:  
  
-   Deverá estar configurada como um Distribuidor ou associada a um Distribuidor remoto.  
  
-   Deve conter uma cópia do banco de dados envolvido na replicação. Essa cópia é normalmente um backup restaurado do banco de dados de publicação original.  
  
 **Selecionar Nó(s) para Exibição**  
 Selecione quais nós exibir na superfície de design. Essa opção será útil se a topologia tiver um grande número de nós. Observe que você só poderá adicionar conexões entre nós visíveis na superfície de design.  
  
 **Selecionar Tempo Limite de Atualização**  
 Especifique o tempo que processo de atualização tem para executar antes da operação expirar.  
  
### Opções para cada nó  
 **Adicionar Nova Conexão de Computador Par**  
 Adicione uma conexão entre dois nós. Por exemplo, se você adicionar uma conexão entre o Nó A e o Nó B, a replicação adicionará duas assinaturas: a primeira habilitará o Nó A a receber alterações de publicação no Nó B e a segunda habilitará o Nó B a receber alterações de publicação no Nó A.  
  
 **Excluir Nó de Computador Par**  
 Remove um nó da topologia. Por exemplo, se você remover Nó C, a publicação desse nó será removida. As assinaturas entre Nó A e Nó C, Nó B e Nó C também serão removidas. O banco de dados no Nó C não é excluído, e, a publicação e a distribuição não são desabilitadas.  
  
> [!NOTE]  
>  Quando você configurar replicação ponto a ponto, especifique uma ID para cada nó. Essa ID, que deve ser exclusivo entre todos os nós na topologia, é armazenado na coluna originator_id o [MSpeer_originatorid_history](../../relational-databases/system-tables/mspeer-originatorid-history-transact-sql.md) tabela do sistema. Se um nó for removido da topologia, a ID ainda será mantida na tabela de histórico. A ID é mantida para impedir a ocorrência de falsos conflitos caso sejam feitas alterações do nó removido que ainda sejam replicadas na topologia. Se você quiser reutilizar a ID para um novo nó, primeiro exclua manualmente a ID da tabela MSpeer_originatorid_history em todos os nós. Antes de excluir uma ID para um nó, execute [sp_requestpeerresponse](../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md) para verificar se todas as alterações originadas desse nó foram replicadas.  
  
 **Conectar-se a TODOS os Nós Exibidos**  
 Adiciona conexões entre o nó selecionado e todos os outros nós. Por exemplo, se você selecionou essa opção para o Nó C em uma topologia de nós de árvore, a replicação adicionará quatro assinaturas: duas para habilitar o Nó A e Nó B a receber alterações da publicação no Nó C, e, duas para habilitar o Nó C a receber alterações de publicações no Nó A e Nó B.  
  
 **Selecionar Nó(s) para Exibição**  
 Selecione quais nós exibir na superfície de design. Essa opção será útil se a topologia tiver um grande número de nós. Observe que você só poderá adicionar conexões entre nós visíveis na superfície de design.  
  
### Opções para as setas de conexão  
 **Remover Conexão de Computador Par**  
 Remova uma conexão entre dois nós. Por exemplo, se você remover uma conexão entre o Nó A e o Nó B, a replicação descartará duas assinaturas: a que habilita o Nó A a receber alterações de publicação no Nó B e a que habilita o Nó B a receber alterações de publicação no Nó A.  
  
## Consulte também  
 [Configure Publishing and Distribution](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [Administrar uma topologia ponto a ponto e 40; Programação Transact-SQL de replicação e 41;](../../relational-databases/replication/administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)   
 [Replicação transacional ponto a ponto](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)  
  
  