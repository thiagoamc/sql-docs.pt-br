---
title: Sobre Drivers e fontes de dados | Microsoft Docs
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
helpviewer_keywords: ODBC data source administrator [ODBC], concepts
ms.assetid: 2bb83ef1-4bbe-4be3-8c32-c4d1140aae1d
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 6422e855b126245fd7118ce2518538aa0305484a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="about-drivers-and-data-sources"></a>Sobre Drivers e fontes de dados
*Drivers* são os componentes que processam solicitações ODBC e retornam dados para o aplicativo. Se necessário, drivers de modificar uma solicitação de aplicativo em um formulário que é entendido pela fonte de dados. Você deve usar o programa de instalação do driver para adicionar ou excluir um driver do seu computador.  
  
 *Fontes de dados* são os bancos de dados ou arquivos acessados por um driver e são identificados por um nome de fonte de dados (DSN). Use o administrador de fonte de dados ODBC para adicionar, configurar e excluir fontes de dados do sistema. Os tipos de fontes de dados que podem ser usados são descritos na tabela a seguir.  
  
|Fonte de dados|Description|  
|-----------------|-----------------|  
|Usuário|DSNs do usuário são locais para um computador e podem ser usados somente pelo usuário atual. Eles são registrados na subárvore do registro HKEY_CURRENT_USER.|  
|Sistema|DSNs de sistema são locais para um computador em vez de dedicado a um usuário. O sistema ou qualquer usuário com privilégios pode usar uma fonte de dados configurada com um DSN de sistema. DSNs de sistema são registrados na subárvore de registro HKEY_LOCAL_MACHINE.|  
|Arquivo|DSNs de arquivos são fontes com base em arquivo que podem ser compartilhadas entre todos os usuários que têm os mesmos drivers instalados, portanto, tem acesso ao banco de dados. Essas fontes de dados não precisam ser dedicadas a um usuário, nem ser local para um computador. Nomes de fonte de dados de arquivo não são identificados por entradas do registro dedicado; em vez disso, eles são identificados por um nome de arquivo com uma extensão. DSN.|  
  
 Fontes de dados de usuário e sistema são coletivamente conhecidos como *máquina* fontes de dados porque eles são locais para um computador.  
  
 Cada uma dessas fontes de dados tem uma guia no **administrador de fonte de dados ODBC** caixa de diálogo. Para obter mais informações sobre as fontes de dados disponíveis, veja [Fontes de Dados](../../odbc/reference/data-sources.md).
