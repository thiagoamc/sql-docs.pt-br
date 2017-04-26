---
title: Como o FOR JSON ignora os caracteres especiais e os caracteres de controle (SQL Server) | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FOR JSON, special characters
ms.assetid: 4ba90025-5a09-4f0a-836a-54c886324530
caps.latest.revision: 16
author: douglaslMS
ms.author: douglasl
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 1b2a6a10c3aa3ec3caa432a208be4b3023072046
ms.lasthandoff: 04/11/2017

---
# <a name="how-for-json-escapes-special-characters-and-control-characters-sql-server"></a>Como o FOR JSON ignora os caracteres especiais e os caracteres de controle (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Este tópico descreve como a cláusula **FOR JSON** de uma instrução **SELECT** do SQL Server ignora os caracteres especiais e representa os caracteres de controle na saída JSON.  

> [!IMPORTANT]
> Esta página descreve o suporte interno para JSON no Microsoft SQL Server. Para obter informações gerais sobre escape e codificação em JSON, consulte a seção 2.5 de RFC JSON – [http://www.ietf.org/rfc/rfc4627.txt](http://www.ietf.org/rfc/rfc4627.txt).

## <a name="escaping-of-special-characters"></a>Ignorando os caracteres especiais  
Se os dados de origem contiverem caracteres especiais, a cláusula **FOR JSON** ignorará os caracteres especiais na saída JSON com `\`, conforme mostrado na tabela a seguir. Este escape ocorre nos nomes das propriedades e em seus valores.  
  
|**Caractere especial**|**Saída de escape**|  
|---------------------------|--------------------------|  
|Aspas (")|\\"|  
|Barra invertida (\\)|\\\|  
|Barra (/)|\\/|  
|Backspace|\b|  
|Avanço de formulário|\f|  
|Linha nova|\n|  
|Retorno de carro|\r|  
|Guia horizontal|\t|  
  
## <a name="control-characters"></a>Caracteres de controle  
Se os dados de origem contiverem caracteres de controle, a cláusula **FOR JSON** fará a codificação na saída JSON no formato `\u<code>`, conforme mostrado na tabela a seguir.  
  
|**Caractere de controle**|**Saída codificada**|  
|---------------------------|--------------------------|  
|CHAR(0)|\u0000|  
|CHAR(1)|\u0001|  
|…|…|  
|CHAR(31)|\u001f|  
  
## <a name="example"></a>Exemplo  
 Aqui está um exemplo da a saída **FOR JSON** para os dados de origem que inclui caracteres especiais e caracteres de controle.  
  
 Consulta:  
  
```tsql  
SELECT  
  'VALUE\    /  
  "' as [KEY\/"],  
  CHAR(0) as '0',  
  CHAR(1) as '1',  
  CHAR(31) as '31'  
FOR JSON PATH  
```  
  
 Resultado:  
  
```json  
{
    "KEY\\\t\/\"": "VALUE\\\t\/\r\n\"",
    "0": "\u0000",
    "1": "\u0001",
    "31": "\u001f"
}
```  
  
## <a name="see-also"></a>Consulte também  
 [Formatar os resultados da consulta como JSON com o FOR JSON &#40;SQL Server&#41;](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)  
[Cláusula FOR](../../t-sql/queries/select-for-clause-transact-sql.md)
