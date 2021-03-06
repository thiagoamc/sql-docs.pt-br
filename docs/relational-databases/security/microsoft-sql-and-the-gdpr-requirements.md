---
title: Microsoft SQL e os requisitos de GDPR | Microsoft Docs
ms.custom: 
ms.date: 05/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: security
ms.reviewer: 
ms.suite: sql
ms.technology: sql-security
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 
author: barbkess
ms.author: ronitr
manager: craigg
ms.openlocfilehash: a98e19f8bea8b8a1d1679cee6bb7a86215c48450
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="guide-to-enhancing-privacy-and-addressing-gdpr-requirements-with-the-microsoft-sql-platform"></a>Guia para aprimorar a privacidade e atender aos requisitos de GDPR com a plataforma Microsoft SQL
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

## <a name="summary"></a>Resumo
Em 25 de maio de 2018, entrará em vigor uma lei de privacidade europeia que estabelecerá um novo padrão global de direitos de privacidade, segurança e conformidade. A Regulamentação de Proteção de Dados Gerais ou GDPR, visa proteger e habilitar os direitos de privacidade dos indivíduos, estabelecendo rígidos requisitos globais de privacidade que regem como os dados pessoais como são gerenciados e protegidos, respeitando as escolhas do indivíduo. 

Os clientes do Microsoft SQL que estão sujeitos à GDPR, seja pelo gerenciamento de bancos de dados locais, em nuvem ou ambos, precisarão garantir que os dados qualificados em seus sistemas de banco de dados estão sendo devidamente tratados e protegidos de acordo com os princípios da GDPR. Isso significa que muitos clientes precisarão examinar ou modificar seus procedimentos de gerenciamento de banco de dados e manipulação de dados, especialmente com relação à segurança do processamento de dados conforme estipulados pela GDPR.

As tecnologias da Microsoft baseadas em SQL oferecem vários recursos de segurança internos que podem ajudar a reduzir os riscos para dados e melhorar a proteção e a capacidade de gerenciamento dos dados no nível do banco de dados e além. Este artigo examina esses recursos e compartilha algumas abordagens da Microsoft usando o Microsoft SQL para atingir as metas de privacidade de dados da GDPR.
   
  
**Autor:** Ronit Reger

**Revisores técnicos:** Conor Cunningham, Joachim Hammer, Shai Kariv, Julie Koesmarno, Alice Kupcik, Ron Matchoro, Gilad Mittelman, Dan Rediske e Tomer Weisberg 
  
**Publicação:** maio de 2017  
  
**Aplica-se a:** SQL Server (todas as versões), Banco de Dados SQL do Azure, SQL Data Warehouse do Azure, Analytics Platform System 
  
Para ler o documento, baixe o [Guia para aprimorar a privacidade e atender aos requisitos de GDPR com a plataforma Microsoft SQL](http://download.microsoft.com/download/4/9/4/4948194B-A613-49ED-90A5-5144313549AB/microsoft-sql-and-the-gdpr.pdf).   
