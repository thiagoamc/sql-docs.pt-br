---
title: SQLGetConnectOption (Driver ODBC do Visual FoxPro) | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SQLGetConnectOption function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 5703eb39-f3b2-4f3a-8676-a5625ae29a41
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 41fdb44589b0a788591b6d31ee8ff03de965cd37
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="sqlgetconnectoption-visual-foxpro-odbc-driver"></a>SQLGetConnectOption (Driver ODBC do Visual FoxPro)
> [!NOTE]  
>  Este tópico contém informações específicas do Driver ODBC do Visual FoxPro. Para obter informações gerais sobre esta função, consulte o tópico apropriado em [referência da API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Suporte: parcial  
  
 Conformidade de API de ODBC: Nível 1  
  
 Retorna a configuração atual de uma opção de conexão. Essa função tem suporte parcial: O driver dá suporte a todos os valores para o *fOption* argumento mas não oferece suporte a alguns dos *vParam* valores para o *fOption* argumento SQL_TXN_ISOLATION.  
  
 A tabela a seguir descreve apenas os argumentos com comportamento específico para a implementação do Visual FoxPro ODBC Driver de **SQLGetConnectOption**.  
  
|*fOption*|Remarks|  
|---------------|-------------|  
|SQL_AUTOCOMMIT|Se você escolher SQL_AUTOCOMMIT_OFF, seu aplicativo deve confirmar ou reverter transações com explicitamente [SQLTransact](../../odbc/microsoft/sqltransact-visual-foxpro-odbc-driver.md); o Driver de ODBC do Visual FoxPro não executa automaticamente uma instrução transacionáveis após a conclusão. O driver começar uma transação se a instrução for transacionáveis.|  
|SQL_CURRENT_QUALIFIER|Pode ser um nome de banco de dados (arquivo. dbc) totalmente qualificado ou um caminho totalmente qualificado para um diretório que contém zero ou mais tabelas (arquivos. dbf).|  
|SQL_LOGINTIMEOUT|Retorna o erro "Driver não compatível com".|  
|SQL_CURSORS|Retorna o erro "Driver não compatível com".|  
|SQL_PACKET_SIZE|Retorna o erro "Driver não compatível com".|  
|SQL_TXN_ISOLATION|O driver permite apenas SQL_TXN_READ_COMMITTED.<br /><br /> O seguinte *vParam*s não têm suporte:<br /><br /> SQL_TXN_READ_UNCOMMITTED<br /><br /> SQL_TXN_REAPEATABLE_READ<br /><br /> SQL_TXN_SERIALIZABLE|  
  
 Para obter mais informações, consulte [SQLGetConnectOption](../../odbc/reference/syntax/sqlgetconnectoption-function.md) no *referência do programador de ODBC*.
