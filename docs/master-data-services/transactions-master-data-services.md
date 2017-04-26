---
title: "Transa&#231;&#245;es (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "01/10/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "transações [Master Data Services], sobre transações"
  - "transações [Master Data Services]"
ms.assetid: 4cd2fa6f-9c76-4b7a-ae18-d4e5fd2f03f5
caps.latest.revision: 15
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 13
---
# Transa&#231;&#245;es (Master Data Services)
  No [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], uma transação é registrada sempre que uma ação é tomada em um membro. Transações podem ser exibidas por todos os usuários e revertidas por administradores. As transações mostram a data, a hora e o usuário que tomou a ação, além de outros detalhes. Usuários podem adicionar uma anotação a uma transação, para indicar por que uma transação aconteceu.  
  
## Quando as transações são registradas  
 As transações são registradas quando os membros:  
  
-   São criados, excluídos ou reativados.  
  
-   Têm valores de atributo alterados.  
  
-   São movidos em uma hierarquia.  
  
 As transações não são gravadas quando as regras de negócios alteram os valores do atributo.  
  
## Exibir e gerenciar transações  
 Na área funcional **Explorer**, você pode exibir e anotar (adicionar comentários) as transações que você mesmo criou.  
  
 Na área funcional **Gerenciamento de Versões**, os administradores podem exibir todas as transações de todos os usuários dos modelos aos quais têm acesso e reverter qualquer uma dessas transações.  
  
 Você pode configurar quanto tempo os dados do log de transações são retidos definindo a propriedade **Retenção de Log em Dias** nas configurações do sistema do banco de dados [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] e definindo **Retenção de Log em Dias** ao criar ou editar um modelo. Para obter mais informações, consulte [Configurações do sistema &#40;Master Data Services&#41;](../master-data-services/system-settings-master-data-services.md) e [Criar um modelo &#40;Master Data Services&#41;](../master-data-services/create-a-model-master-data-services.md).  
  
 O trabalho do SQL Server Agent, MDS_MDM_Sample_Log_Maintenace, aciona a limpeza dos logs de transações e é executado todas as noites. Você pode usar o SQL Server Agent para modificar o agendamento desse trabalho.  
  
 Também é possível chamar os procedimentos armazenados a seguir para limpar os logs de transações.  
  
|Procedimento armazenado|Description|  
|----------------------|-----------------|  
|mdm.udpTransactionsCleanup|Limpa o histórico de transações|  
|mdm.udpValidationsCleanup|Limpa o histórico de validação|  
|mdm.udpEntityStagingBatchTableCleanup|Limpa a tabela de preparo|  
  
 **Amostra**  
  
```  
DECLARE @CleanupOlderThanDate date = '2014-11-11',  
@ModelID INT = 7  
--Clean up Transaction Logs  
EXEC mdm.udpTransactionsCleanup @ModelID, @CleanupOlderThanDate;  
  
--Clean up Validation History  
EXEC mdm.udpValidationsCleanup @ModelID, @CleanupOlderThanDate;  
  
--Clean up EBS tables  
EXEC mdm.udpEntityStagingBatchTableCleanup @ModelID, @CleanupOlderThanDate;  
  
```  
  
## Configurações do sistema  
 Há uma configuração no [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] que afeta se as transações são ou não registradas quando os registros são preparados. É possível ajustar essa configuração no [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] ou diretamente na tabela Configurações do Sistema do banco de dados [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. Para obter mais informações, veja [Configurações do sistema &#40;Master Data Services&#41;](../master-data-services/system-settings-master-data-services.md).  
  
 Ao importar dados nesta versão do [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], você poderá especificar se deseja ou não registrar em log as transações ao iniciar o procedimento armazenado. Para obter mais informações, consulte [Preparando um procedimento armazenado &#40;Master Data Services&#41;](../master-data-services/staging-stored-procedure-master-data-services.md).  
  
## Simultaneidade  
 Se um valor de entidade específico for mostrado simultaneamente em mais de uma sessão do Explorer, as edições simultâneas do mesmo valor serão permitidas. As edições simultâneas não serão detectadas automaticamente pelo MDS. Isso pode ocorrer quando vários usuários utilizarem o MDS Explorer no navegador da Web de várias sessões como, por exemplo, de vários computadores, várias guias ou janelas de navegador ou várias contas de usuário.  
  
 Mais de um usuário pode atualizar os mesmos valores de entidade sem erro apesar das transações habilitadas. Normalmente, a última edição do valor em determinado período terá precedência. O conflito de edição duplicada pode ser observado manualmente no histórico de transação e pode ser revertido manualmente pelo administrador. O histórico de transações mostrará as transações individuais para o **Valor anterior** e o **Novo valor** do atributo em questão de cada sessão, mas não resolverá o conflito automaticamente quando vários **Novos Valores** existirem para o mesmo valor antigo.  
  
## Tarefas relacionadas  
  
|Descrição da tarefa|Tópico|  
|----------------------|-----------|  
|Desfazer uma ação por meio de reversão de uma transação (somente administradores).|[Inverter uma transação &#40;Master Data Services&#41;](../master-data-services/reverse-a-transaction-master-data-services.md)|  
  
## Recursos externos  
 Postagem do blog, [Transactions, Validation Issue and Staging table cleanup](http://go.microsoft.com/fwlink/p/?LinkId=615374) (Transações, problemas de validação e limpeza de tabela de preparo), no msdn.com.  
  
## Conteúdo relacionado  
  
-   [Administradores &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md)  
  
-   [Anotações &#40;Master Data Services&#41;](../master-data-services/annotations-master-data-services.md)  
  
  