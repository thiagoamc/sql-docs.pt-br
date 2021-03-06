---
title: MSSQLSERVER_833 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 833 (Database Engine error)
ms.assetid: 14129cc4-be80-4772-9e3f-0e5da4d0696b
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 43a490b6591bb2ded0f331aaf0be8e15ff46fe2b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver833"></a>MSSQLSERVER_833
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Detalhes  
  
|||  
|-|-|  
|Nome do produto|SQL Server|  
|ID do evento|833|  
|Origem do evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbólico|BUF_LONG_IO|  
|Texto da mensagem|O SQL Server encontrou %d ocorrências de solicitações de E/S demorando mais do que %d segundos para serem concluídas no arquivo [%ls] no banco de dados `[%ls] (%d)`.  O identificador de arquivo do SO é 0x%p.  O deslocamento da E/S mais demorada é: %#016I64x.|  
  
## <a name="explanation"></a>Explicação  
Esta mensagem indica que o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] emitiu uma solicitação de leitura ou gravação de disco, e que a solicitação demorou mais de 15 segundos para retornar. Esse erro é informado pelo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e indica um problema com o subsistema de E/S.  
  
### <a name="possible-causes"></a>Causas possíveis  
Esse problema pode ser causado por problemas de desempenho do sistema, erros de hardware, erros de firmware, problemas de driver de dispositivo ou intervenção de driver de filtro no processo de E/S.  
  
## <a name="user-action"></a>Ação do usuário  
Solucione este erro procurando mensagens de erros relacionados a hardware no log de eventos de sistema. Examine também os logs específicos do hardware, se estiverem disponíveis.  
  
Use o Monitor de Desempenho para examinar os seguintes contadores:  
  
-   **Média de seg/transferência do disco**  
  
-   **Média de comprimento da fila do disco**  
  
-   **Comprimento atual da fila do disco**  
  
Por exemplo, o tempo da **Média de seg/transferência do disco** em um computador que está executando o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], normalmente, é inferior a 15 milissegundos. Se o valor da **Média de seg/transferência do disco** aumentar, isso indicará que o subsistema de E/S não está acompanhando a demanda de E/S.  
  
> [!NOTE]  
> O acesso ao disco pode ficar mais lento devido a um programa antivírus. Para aumentar a velocidade de acesso, exclua os arquivos de dados do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] especificados na mensagem de erro das verificações ativas de vírus.  
  
Para obter mais informações sobre erros de E/S, consulte [Microsoft SQL Server I/O Basics, Chapter 2](http://go.microsoft.com/fwlink/?LinkId=69370) (Noções básicas de E/S do Microsoft SQL Server, Capítulo 2) e o artigo da Base de dados de conhecimento em [http://support.microsoft.com/kb/897284/en-us](http://support.microsoft.com/kb/897284/en-us).  
  
