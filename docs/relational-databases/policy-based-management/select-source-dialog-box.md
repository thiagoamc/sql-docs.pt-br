---
title: "Caixa de di&#225;logo Selecionar Origem | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.dmf.selectsource.f1"
ms.assetid: d664c2e5-dd0c-4da8-b27d-aa4ee4fc0ffd
caps.latest.revision: 16
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 16
---
# Caixa de di&#225;logo Selecionar Origem
  Use esta caixa de diálogo para selecionar a origem das políticas a serem executadas. Para selecionar um ou mais arquivos XML que contêm políticas, selecione **Arquivos**. Para executar as políticas que são encontradas na instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], selecione **Servidor**.  
  
 Você pode abrir esta caixa de diálogo de vários modos.  
  
 **Para abrir essa caixa de diálogo**  
  
-   Em Servidores Registrados, clique com o botão direito do mouse em **Grupos do Servidor Local** ou em qualquer servidor em **Grupos de Servidores Locais** ou em **Servidores de Gerenciamento Central** e selecione **Avaliar Políticas**. Na página **Seleção de Política** da caixa de diálogo **Avaliar Políticas**, clique no botão Procurar (**...**).  
  
-   No Pesquisador de Objetos, expanda **Gerenciamento**, expanda **Gerenciamento de Políticas**, clique com o botão direito do mouse em **Políticas** e selecione **Importar Política**. Na caixa de diálogo **Importar**, clique no botão Procurar (**...**).  
  
-   No Pesquisador de Objetos, clique com o botão direito do mouse em um servidor, banco de dados ou objeto de banco de dados, selecione **Políticas** e depois **Avaliar**. Na página **Seleção de Política** da caixa de diálogo **Avaliar Políticas**, clique no botão Procurar (**...**).  
  
## Opções  
 **Arquivos**  
 Selecione um ou mais arquivos XML que contenham políticas.  
  
 **Servidor**  
 Permite que você selecione um servidor que contenha as políticas que você deseja executar.  
  
 **Tipo de servidor**  
 Só servidores [!INCLUDE[ssDE](../../includes/ssde-md.md)] contêm políticas. Essa caixa é somente leitura.  
  
 **Nome do servidor**  
 Selecione a instância do servidor com a qual se conectar. Por padrão, é exibida a instância do servidor usada na última conexão.  
  
 **Autenticação**  
 Existem dois modos de autenticação disponíveis quando você se conecta com uma instância do [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 **Modo de Autenticação do Windows (Autenticação do Windows)**  
 O modo de Autenticação do Windows permite que um usuário se conecte por meio de uma conta de usuário Windows.  
  
 **Autenticação do SQL Server**  
 Quando um usuário se conecta com um nome de logon e senha especificados em uma conexão não confiável, o próprio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] efetua a autenticação, verificando se foi definida uma conta de logon do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e se a senha especificada corresponde a uma senha registrada previamente. Se o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] não tiver uma conta de logon definida, ocorrerá falha na autenticação e o usuário receberá uma mensagem de erro.  
  
> [!IMPORTANT]  
>  Quando possível, use a Autenticação do Windows.  
  
 **Nome de usuário**  
 Digite o nome do usuário com o qual se conectar. Essa opção só estará disponível se você tiver optado por conectar-se usando a Autenticação do Windows.  
  
 **Logon**  
 Insira o logon com o qual se conectar. Essa opção só estará disponível se você tiver optado por conectar-se usando a Autenticação do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Senha**  
 Digite a senha do logon. Essa opção poderá ser editada somente se você decidiu conectar-se usando a Autenticação do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## Consulte também  
 [Nó de gerenciamento de política &#40;Pesquisador de Objetos&#41;](../../relational-databases/policy-based-management/policy-management-node-object-explorer.md)   
 [Administrar servidores com Gerenciamento Baseado em Políticas](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  