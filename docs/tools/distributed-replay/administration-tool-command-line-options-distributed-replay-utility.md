---
title: "Op&#231;&#245;es de linha de comando da ferramenta de administra&#231;&#227;o (Distributed Replay Utility) | Microsoft Docs"
ms.custom: ""
ms.date: "08/12/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c01b0ed3-67e4-4561-92d2-a8fbb086aca8
caps.latest.revision: 35
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 35
---
# Op&#231;&#245;es de linha de comando da ferramenta de administra&#231;&#227;o (Distributed Replay Utility)
  A ferramenta de administração [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay, **DReplay.exe**, é uma ferramenta de linha de comando para se comunicar com o controlador de reprodução distribuída. Use a ferramenta de administração para iniciar, monitorar e cancelar operações no controlador.  
  
 ![Ícone de vínculo de tópico](../../database-engine/configure-windows/media/topic-link.png "Ícone de vínculo de tópico") Para obter mais informações sobre as convenções de sintaxe usadas com a sintaxe da ferramenta de administração, consulte [Convenções de sintaxe do Transact-SQL &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
## Sintaxe  
  
```  
  
dreplay {preprocess|replay|status|cancel} [options] [-?]}  
  
Usage:  
  
  dreplay preprocess [-m controller] -i input_trace_file  
    -d controller_working_dir [-c config_file] [-f status_interval]  
  
  dreplay replay [-m controller] -d controller_working_dir [-o]  
    [-s target_server] -w clients [-c config_file]  
    [-f status_interval]  
  
  dreplay status [-m controller] [-f status_interval]  
  
  dreplay cancel [-m controller] [-q]   
```  
  
## Comentários  
 É possível emitir as seguintes opções de linha de comando com **DReplay.exe**:  
  
 **preprocess**  
 Inicia o estágio de pré-processamento. O controlador prepara os dados de rastreamento de entrada que você capturou do ambiente de produção para a reprodução contra o servidor de destino.  
  
 **reproduzir**  
 Inicia o estágio de reprodução do evento. O controlador despacha dados de reprodução aos clientes especificados, inicia a reprodução distribuída e sincroniza os clientes. Opcionalmente, cada cliente selecionado registra a atividade de reprodução e salva arquivos de rastreamento de resultado localmente.  
  
 **status**  
 Consulta o controlador e exibe o status atual.  
  
 **cancel**  
 Cancela a operação atual em execução no controlador.  
  
 Para obter informações detalhadas de sintaxe, incluindo argumentos e exemplos de comandos, consulte os seguintes tópicos:  
  
-   [Opção Pré-processamento &#40;Ferramenta de administração de reprodução distribuída&#41;](../../tools/distributed-replay/preprocess-option-distributed-replay-administration-tool.md)  
  
-   [Opção Reprodução &#40;Ferramenta de administração de reprodução distribuída&#41;](../../tools/distributed-replay/replay-option-distributed-replay-administration-tool.md)  
  
-   [Opção Status &#40;Ferramenta de administração de reprodução distribuída&#41;](../../tools/distributed-replay/status-option-distributed-replay-administration-tool.md)  
  
-   [Opção Cancelamento &#40;Ferramenta de administração de reprodução distribuída&#41;](../../tools/distributed-replay/cancel-option-distributed-replay-administration-tool.md)  
  
 Os RPCs são executados novamente como RPCs e não como eventos de idioma.  
  
## Permissões  
 Você deve executar a ferramenta de administração como um usuário interativo, um usuário local ou uma conta de usuário de domínio. Para usar uma conta de usuário local, a ferramenta de administração e o controlador devem estar em execução no mesmo computador.  
  
 Para saber mais, confira [Distributed Replay Security](../../tools/distributed-replay/distributed-replay-security.md).  
  
## Consulte também  
 [SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md)  
  
  