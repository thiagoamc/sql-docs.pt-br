---
title: catalog.add_execution_worker (Banco de dados SSISDB) | Microsoft Docs
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d587cedd-6402-4d5c-9526-7cd25627a037
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 42d1332c727f26b6850c7fd7227c3a124ebc50a9
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2018
---
# <a name="catalogaddexecutionworker-ssisdb-database"></a>catalog.add_execution_worker (Banco de dados SSISDB)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Adiciona um Trabalho do Scale Out do [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] a uma instância de execução no Scale Out.

## <a name="syntax"></a>Sintaxe

```sql
catalog.add_execution_worker [@execution_id = ] execution_id, [@workeragent_id = ] workeragent_id
```

## <a name="arguments"></a>Argumentos
[ @execution_id = ] *execution_id*  
 O identificador exclusivo da instância de execução. O *execution_id* é **bigint**.  
 
[@workeragent_id = ] *workeragent_id*  
A ID do agente de trabalho de um Trabalho do Scale Out. O *workeragent_id* é **uniqueIdentifier**.

## <a name="return-code-value"></a>Valor do código de retorno  
 0 (êxito)  
  
## <a name="result-sets"></a>Conjuntos de resultados  
 Nenhum  

## <a name="permissions"></a>Permissões  
 Este procedimento armazenado exige uma das seguintes permissões:  
  
-   Permissões READ e MODIFY na instância de execução  
  
-   Associação à função de banco de dados **ssis_admin**  
  
-   Associação à função de servidor **sysadmin**  
 
## <a name="errors-and-warnings"></a>Erros e avisos  
 A lista a seguir descreve algumas condições que podem gerar um erro ou um aviso:  
 
- O usuário não tem as permissões apropriadas.

- O identificador da execução não é válido.

- A ID do agente de trabalho não é válida.

- A execução não está no Scale Out.

## <a name="see-also"></a>Consulte Também
[Execute pacotes no Scale Out](~/integration-services/scale-out/run-packages-in-integration-services-ssis-scale-out.md).

