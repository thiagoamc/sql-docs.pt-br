---
title: "Conectar-se ao Oracle | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "connOra"
ms.assetid: 711ac7ff-5d3d-4533-80ca-d1fecdb3048f
caps.latest.revision: 5
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 5
---
# Conectar-se ao Oracle
  Quando você adiciona ou edita as tabelas usadas na instância de CDC pela primeira vez, você deverá se conectar ao banco de dados Oracle. Você deve inserir as credenciais de um usuário Oracle que pode acessar o esquema das tabelas a ser capturado. Insira o seguinte nesta caixa de diálogo:  
  
 **Autenticação**  
  
 Selecione uma destas opções:  
  
-   **Autenticação do Windows**: selecione isto para usar as credenciais de domínio atuais do Windows. Você só poderá usar esta opção se o banco de dados Oracle estiver configurado para funcionar com autenticação do Windows.  
  
-   **Autenticação do Oracle**: se você selecionou esta opção, deve digitar o **Nome de usuário** e **Senha** para o usuário no banco de dados Oracle ao qual você está se conectando.  
  
## Consulte também  
 [Adicionar tabelas a uma instância CDC](../../integration-services/change-data-capture/add-tables-to-a-cdc-instance.md)  
  
  