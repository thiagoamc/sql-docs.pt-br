---
title: "Criar gr&#225;ficos, alertas, logs e relat&#243;rios | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Monitor do Sistema [SQL Server], gráficos e relatórios"
  - "gráficos [SQL Server]"
  - "relatórios [SQL Server]"
  - "relatórios [SQL Server], criando"
  - "Monitor do Sistema Windows [SQL Server], gráficos e relatórios"
  - "logs [SQL Server], Monitor do Sistema"
  - "Monitor do Sistema [SQL Server], logs"
  - "Monitor do Sistema do Windows [SQL Server], logs"
ms.assetid: c9162b37-e5dc-43d1-a3aa-1e9ebc69fecc
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# Criar gr&#225;ficos, alertas, logs e relat&#243;rios
  O Monitor do Sistema permite criar gráficos, alertas, logs e relatórios para monitorar uma instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## Gráficos  
 Os gráficos podem monitorar o desempenho atual de objetos e contadores selecionados; por exemplo, o uso da CPU ou E/S em disco. É possível adicionar diversas combinações de objetos e contadores a um gráfico do Monitor do Sistema. Também é possível adicionar objetos e contadores do [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows a um gráfico.  
  
 Cada gráfico representa um subconjunto de informações a monitorar. Por exemplo, um gráfico pode rastrear estatísticas de uso de memória e um outro gráfico pode rastrear estatísticas de E/S em disco.  
  
 Usar um gráfico pode ser útil para as seguintes tarefas:  
  
-   Investigar por que um computador ou aplicativo está lento ou ineficiente.  
  
-   Monitorar continuamente os sistemas para localizar problemas de desempenho intermitentes.  
  
-   Descobrir por que a capacidade precisa ser aumentada.  
  
-   Exibir uma tendência na forma de um gráfico de linhas.  
  
-   Exibir uma comparação na forma de um gráfico de histograma.  
  
 Gráficos são úteis para o monitoramento de curto prazo em tempo real de um computador local ou remoto (por exemplo, quando se deseja monitorar um evento enquanto ele ocorre).  
  
## Alertas  
 Usando alertas, o Monitor do Sistema rastreia eventos específicos e emite notificações a seu respeito conforme solicitado. Um log de alertas pode monitorar o desempenho atual de contadores e instâncias de objetos selecionados no [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Quando um contador excede um determinado valor, o log registra a data e a hora do evento. Um evento também pode gerar um alerta de rede. Você pode fazer com que um programa especificado seja executado na primeira vez ou em todas as vezes que o evento ocorrer. Por exemplo, um alerta pode enviar uma mensagem de rede a todos os administradores do sistema avisando que a instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] está ficando com pouco espaço em disco.  
  
## Logs  
 Os logs permitem registrar informações sobre a atividade atual de objetos e computadores selecionados para visualização e análise posteriores. É possível coletar dados de vários sistemas em um mesmo arquivo de log. Por exemplo, é possível criar logs diferentes que coletem informações sobre o desempenho de objetos selecionados em diversos computadores para análise futura. Você pode salvar essas seleções sob um nome de arquivo e reutilizá-las quando quiser criar um outro log de informações similares para comparação.  
  
 Arquivos de log fornecem informações preciosas para a solução de problemas ou planejamento. Enquanto que gráficos, alertas e relatórios sobre a atividade atual propiciam um feedback instantâneo, os arquivos de log permitem rastrear os contadores por um longo intervalo de tempo. Assim, você pode examinar as informações mais minuciosamente e documentar o desempenho do sistema.  
  
## Relatórios  
 Os relatórios permitem exibir valores de instâncias e contadores de objetos selecionados que mudam constantemente. Os valores aparecem em colunas para cada instância. É possível ajustar os intervalos do relatório, imprimir instantâneos e exportar dados. Use relatórios quando precisar exibir os números brutos.  
  
 Para obter mais informações sobre como criar gráficos, alertas, logs e relatórios ou sobre objetos e contadores do Windows, consulte a documentação do Windows.  
  
## Consulte também  
 [Monitorar o uso de recursos &#40;Monitor do Sistema&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  