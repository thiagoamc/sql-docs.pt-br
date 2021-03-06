---
title: Read (Mecanismo de Banco de Dados) | Microsoft Docs
ms.custom: 
ms.date: 7/22/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Read_TSQL
- Read
dev_langs:
- TSQL
helpviewer_keywords:
- Read [Database Engine]
ms.assetid: f2b8207c-b69f-4327-a874-100b3a1f27d8
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 72ebda7a9bd00b44983d29db2ef433c9f7d43f94
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="read-database-engine"></a>Read (Mecanismo de Banco de Dados)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

O método Read lê a representação binária de **SqlHierarchyId** do **BinaryReader** passado e define o objeto **SqlHierarchyId** com esse valor. Não é possível chamar Read usando [!INCLUDE[tsql](../../includes/tsql-md.md)]. Em seu lugar, use CAST ou CONVERT.
  
## <a name="syntax"></a>Sintaxe  
  
```sql
void Read( BinaryReader r )   
```  
  
## <a name="arguments"></a>Argumentos  
*r*  
 O objeto **BinaryReader** que produz um fluxo binário correspondente a uma representação binária de um nó **hierarchyid**.  
  
## <a name="return-types"></a>Tipos de retorno
 **Tipo de retorno do CLR: nulo**  
  
## <a name="remarks"></a>Remarks  
 O método Read não valida sua entrada. Se uma entrada binária inválida for fornecida, Read poderá gerar uma exceção. Ou poderá ser bem-sucedido e produzir um objeto **SqlHierarchyId** inválido cujos métodos podem gerar resultados imprevisíveis ou uma exceção.  
  
 O método Read pode ser chamado apenas em um objeto **SqlHierarchyId** recém-criado.  
  
 Read é usado internamente por [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] quando necessário, como ao gravar dados na coluna **hierarchyid**. Read também é chamado internamente quando é feita uma conversão entre **varbinary** e **hierarchyid**.  
  
## <a name="examples"></a>Exemplos  
  
```sql
Byte[] encoding = new byte[] { 0x58 };  
MemoryStream stream = new MemoryStream(encoding, false /*not writable*/);  
BinaryReader br = new BinaryReader(stream);  
SqlHierarchyId hid = new SqlHierarchyId();  
hid.Read(br);   
```  
  
## <a name="see-also"></a>Consulte Também  
[Write &#40;Mecanismo de Banco de Dados&#41;](../../t-sql/data-types/write-database-engine.md)  
[ToString &#40;Mecanismo de Banco de Dados&#41;](../../t-sql/data-types/tostring-database-engine.md)  
[CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[Referência de método de tipo de dados hierarchyid](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)
  
  
