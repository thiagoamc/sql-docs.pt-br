---
title: "Propriedades do SQL Server Agent (guia Servi&#231;o) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 452857fb-be1b-4e1e-851c-dd2216640f35
caps.latest.revision: 22
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 22
---
# Propriedades do SQL Server Agent (guia Servi&#231;o)
  Este é o serviço [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Os valores de propriedade em cinza claro não podem ser alterados com o uso deste aplicativo.  
  
## Opções  
 **Caminho Binário**  
 Exibe o local dos arquivos de programas usados por este serviço.  
  
 **Controle de Erro**  
 1 indica `SERVICE_ERROR_NORMAL`. Se o serviço não for iniciado durante a inicialização do computador, o programa de inicialização registrará o erro em log e exibirá uma caixa de mensagem pop-up, mas continuará a operação de inicialização. Esse valor não pode ser alterado.  
  
 **Código de Saída**  
 Quando ocorre um erro, o número do erro é exibido nesta caixa. Use esse número para solucionar problemas de falhas procurando-o na Base de Dados de Conhecimento [!INCLUDE[msCoName](../../includes/msconame-md.md)] ou forneça o número à sua equipe de suporte técnico.  
  
 **Host Name**  
 Exibe o nome do computador ou cluster que está executando o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
 **Nome**  
 Indica o nome para exibição do serviço.  
  
 **ID do Processo**  
 Exibe a identificação do processo do [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
 **Tipo de Serviço do SQL**  
 Exibe o tipo de serviço fornecido a processos de chamada. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instala vários serviços.  
  
 **Modo Inicial**  
 Defina este serviço com as seguintes opções:  
  
-   Manual: este serviço não é iniciado automaticamente na inicialização do computador. Você deve iniciá-lo usando o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager ou outra ferramenta.  
  
-   Automático: este serviço tenta ser iniciado na inicialização do computador.  
  
-   Desabilitado: este serviço não pode ser iniciado.  
  
 **Estado**  
 Indica se este serviço está sendo executado, se está parado ou desabilitado. "**…**" indica que uma alteração no estado está pendente.  
  
  