---
title: Criar um projeto Visual c# SMO no Visual Studio .NET | Microsoft Docs
ms.custom: 
ms.date: 08/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: smo
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: Visual C# [SMO]
ms.assetid: 1e7abb16-23a0-4a18-91ad-253261e6bf84
caps.latest.revision: "43"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 2fb8a8bd7527a14df4447fd4c7a49e92647b9e09
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2017
---
# <a name="how-to-create-a-visual-c-smo-project-in-visual-studio-net"></a>Como criar um projeto Visual c# SMO no Visual Studio .NET
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Esta seção descreve como criar um aplicativo de console SMO simples.  
  
 Este exemplo importa namespaces que permitem ao programa referenciar tipos SMO. A importação do **agente** namespace é opcional. Use-a quando estiver gravando um programa que usa o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. O **comuns** namespace é necessário para estabelecer uma conexão segura com a instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. O **SqlClient** namespace é usado para processar erros de exceção SQL.  
  
### <a name="creating-a-visual-c-smo-project-in-visual-studionet"></a>Criando um projeto SMO do Visual C# no Visual Studio .NET  
  
1. Inicie o Visual Studio
  
2. Sobre o **arquivo** menu, clique em **novo** e, em seguida, **projeto**.  A caixa de diálogo **Novo Projeto** será exibida.   
  
3. No [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **instalado** painel, navegue até **modelos**\\**Visual C#**\\**Windows** e selecione **aplicativo de Console**.  
  
4. (Opcional) No **nome** texto, digite o nome do novo aplicativo.  

5. Clique em **Okey** para carregar o modelo de aplicativo de console.  

6. Siga as instruções na [SMO instalando](installing-smo.md) para instalar o pacote para o seu projeto fazer referência.
  
7. No menu **Exibir** , clique em **Código**.
    
8. No código, antes da declaração de namespace, digite o seguinte **usando** instruções para qualificar os tipos no namespace SMO:
  
    ```  
    using Microsoft.SqlServer.Management.Smo;  
    using Microsoft.SqlServer.Management.Common;  
    ```  
  
15. O SMO tem vários namespaces em Microsoft.SqlServer.Management.Smo, como o Microsoft.SqlServer.Management.Smo.Agent. Adicione esses namespaces obrigatórios.  
  
16. Agora você pode adicionar seu código SMO.  
  
  