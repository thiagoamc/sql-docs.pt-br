---
title: "Propriedades do SQL Server (guia Par&#226;metros de Inicializa&#231;&#227;o) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 16942624-5374-446c-8de4-ee6ed34d6e94
caps.latest.revision: 10
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 10
---
# Propriedades do SQL Server (guia Par&#226;metros de Inicializa&#231;&#227;o)
  Use esta caixa de diálogo para adicionar ou remover parâmetros de inicialização do [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Os parâmetros de inicialização podem ter um grande efeito no desempenho do [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Antes de adicionar ou alterar os parâmetros de inicialização, consulte o tópico "Usando as opções de inicialização do Serviço [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] " nos Manuais Online do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## Opções  
 **Especificar um parâmetro de inicialização**  
 Para adicionar um parâmetro, digite o parâmetro e clique em **Adicionar**.  
  
 Para modificar um dos parâmetros necessários, selecione o parâmetro na caixa **Parâmetros existentes** , altere os valores da caixa **Especificar um parâmetro de inicialização** e clique em **Atualizar**.  
  
 **Parâmetros existentes**  
 Para remover um parâmetro, selecione um parâmetro e clique em **Remover**.  
  
## Formato do parâmetro  
 Não insira um separador entre parâmetros. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager adiciona o separador automaticamente. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager impõe os seguintes requisitos de parâmetros.  
  
-   Espaços à direita e à esquerda são cortados de qualquer parâmetro de inicialização.  
  
-   Todos os parâmetros de inicialização começam com um - (traço) e o segundo valor é uma letra.  
  
## Parâmetros necessários  
 As seguintes parâmetros são necessários. Eles podem ser alterados, mas não poder ser removidos.  
  
-   -d é o caminho do arquivo **master.mdf** (o arquivo de dados do banco de dados mestre).  
  
-   -l é o caminho do arquivo **master.ldf** (o arquivo de log do banco de dados mestre).  
  
-   -e é o caminho dos arquivos de log de erros do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!CAUTION]  
>  Se os parâmetros de caminho de arquivo estiverem incorretos, talvez o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] não possa ser iniciado.  
  
 Para obter mais informações sobre como mover o banco de dados mestre, consulte o tópico "Movendo bancos de dados do sistema" nos Manuais Online do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## Parâmetros opcionais  
 Todos os parâmetros de inicialização com suporte são descritos no tópico "Usando as opções de inicialização do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ", nos Manuais Online do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Um parâmetro de inicialização -T*trace#* indica que uma instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deve ser iniciada com um sinalizador de rastreamento (*trace#*) em vigor. São usados sinalizadores de rastreamento para iniciar o servidor com comportamento fora do padrão. Para obter mais informações sobre sinalizadores de rastreamento, consulte o tópico “Sinalizadores de rastreamento ([!INCLUDE[tsql](../../includes/tsql-md.md)])” nos Manuais Online do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!CAUTION]  
>  Talvez você veja parâmetros de inicialização e sinalizadores de rastreamento adicionais não documentados na Internet. Os parâmetros de inicialização e os indicadores de rastreamento não documentados são criados para resolver problemas ou para forçar determinas condições necessárias para testes. O uso de parâmetros de inicialização não documentados pode ter resultados inesperados. Não use parâmetros não documentados a não ser quando direcionado pelos Serviços de Atendimento ao Cliente da Microsoft.  
  
 A lista a seguir descreve alguns parâmetros opcionais comuns.  
  
|Parâmetro|Descrição breve|  
|---------------|-----------------------|  
|-m|Inicia uma instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] em modo de usuário único.|  
|-T1204|Retorna os recursos e tipos de bloqueios que participam de um deadlock e também o comando atual afetado.|  
|-T1224|Desabilita o escalonamento de bloqueios com base no número de bloqueios.|  
|-T3608|Impede que o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] inicie ou recupere automaticamente qualquer banco de dados, exceto o banco de dados mestre.|  
|-T7806|Habilita uma conexão de administrador dedicada (DAC) no [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].|  
  
> [!CAUTION]  
>  Alguns parâmetros opcionais podem alterar o comportamento do servidor e afetar o desempenho.  
  
## Permissões  
 O uso desta página é restrito a usuários que podem alterar as entradas relacionadas no Registro. Isso inclui os seguintes usuários.  
  
-   Membros do grupo Administradores local.  
  
-   A conta de domínio usada pelo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], se o [!INCLUDE[ssDE](../../includes/ssde-md.md)] estiver configurado para ser executado em uma conta de domínio.  
  
## Referências dos Manuais Online  
 Para obter mais informações sobre os parâmetros de inicialização do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consulte “Como configurar as opções de inicialização do servidor ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager)” nos Manuais Online do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
  