---
title: "Considerações de segurança do diagrama de atualização (SQLXML 4.0) | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQLXML, updategrams
- security [SQLXML], updategrams
- updategrams [SQLXML], security
ms.assetid: 00dc6cf4-a2e8-4cca-bdd6-d5122102a82d
caps.latest.revision: "22"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3b6379e6407e8e2821ed34fc8f2137b9b1d170ee
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2017
---
# <a name="updategram-security-considerations-sqlxml-40"></a>Considerações sobre segurança para diagramas de atualização (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]A seguir estão as diretrizes de segurança para o uso de diagramas de atualização:  
  
-   Evite usar mapeamento padrão quando usar diagramas de atualização para atualizar dados. Quando você usar mapeamento padrão, um nome de elemento em um diagrama de atualização será mapeado para um nome de tabela e um nome de atributo será mapeado para uma coluna. Isso expõe as informações de coluna e de tabela de banco de dados no banco de dados, o que pode representar um risco de segurança potencial. Se, em vez disso, você especificar um esquema de mapeamento separado que mapeie os elementos e os atributos em um diagrama de atualização para colunas e tabelas do banco de dados, os nomes dos atributos e dos elementos do diagrama de atualização poderão ser arbitrários e o esquema fará o mapeamento necessário desses nomes para colunas e tabelas do banco de dados. Assim, as informações do banco de dados não serão expostas em um diagrama de atualização.  
  
-   Não permita que os usuários criem e executem seus diagramas de atualização. É recomendável que os diagramas de atualização existam como modelos em um servidor, em vez de serem criados dinamicamente em aplicativos do tipo ASP, o que poderia colocar os dados do banco de dados em risco. Permitir que os usuários acessem os dados somente por meio dos diagramas de atualização fornecidos como modelos poderá eliminar esse risco.  
  
## <a name="see-also"></a>Consulte também  
 [Usando diagramas de atualização para modificar dados no SQLXML 4.0](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/using-updategrams-to-modify-data-in-sqlxml-4-0.md)  
  
  