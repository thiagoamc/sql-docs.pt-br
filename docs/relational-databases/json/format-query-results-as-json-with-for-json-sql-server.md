---
title: Formatar os resultados da consulta como JSON com o FOR JSON (SQL Server) | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 01/31/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FOR JSON
- JSON, exporting
- exporting JSON
ms.assetid: 15b56365-58c2-496c-9d4b-aa2600eab09a
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: c439a76e3e925d00e88adaaefa616e59f8529a40
ms.lasthandoff: 04/11/2017

---
# <a name="format-query-results-as-json-with-for-json-sql-server"></a>Formatar os resultados da consulta como JSON com o FOR JSON (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Formate os resultados da consulta ou exporte os dados do SQL Server como JSON adicionando a cláusula **FOR JSON** a uma instrução **SELECT**. Use a cláusula **FOR JSON** para delegar a formatação da saída JSON de aplicativos cliente ao [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
 Ao usar a cláusula **FOR JSON** , você pode especificar explicitamente a estrutura da saída ou permitir que a estrutura da instrução SELECT determine a saída.  
  
-   Use o modo **PATH** com a cláusula **FOR JSON** para manter o controle completo sobre o formato da saída JSON. Você pode criar objetos wrapper e aninhar propriedades complexas.  
  
-   Use o modo **AUTO** com a cláusula **FOR JSON** para formatar a saída JSON automaticamente com base na estrutura da instrução SELECT.  
  
Aqui está um exemplo de uma instrução **SELECT** com a cláusula **FOR JSON** e sua saída.
  
 ![FOR JSON](../../relational-databases/json/media/jsonslides2forjson.png "FOR JSON")  
  
## <a name="maintain-control-over-json-output-with-path-mode"></a>Manter o controle sobre a saída JSON com o modo PATH  
No modo **PATH** , você pode usar a sintaxe de ponto, por exemplo, `'Item.Price'` , para formatar a saída aninhada. O exemplo a seguir também usa a opção **ROOT** para especificar um elemento de raiz nomeado.  

Veja um exemplo de consulta que usa o modo **PATH** com a cláusula **FOR JSON** .
  
 ![Diagrama de fluxo da saída FOR JSON](../../relational-databases/json/media/forjson-example1.png "Diagrama de fluxo da saída FOR JSON")  

### <a name="more-info"></a>Obter mais informações
Para mais informações e exemplos, consulte [Formatar a saída JSON aninhada com modo PATH &#40;SQL Server&#41;](../../relational-databases/json/format-nested-json-output-with-path-mode-sql-server.md).

Para sintaxe e uso, consulte [Cláusula FOR &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md).  

## <a name="let-the-select-statement-control-json-output-with-auto-mode"></a>Permitir que a instrução SELECT controle a saída JSON com o modo AUTO  
No modo **AUTO** , a estrutura da instrução SELECT determina o formato da saída JSON. Por padrão, os valores **nulos** não são incluídos na saída. Você pode usar o **INCLUDE_NULL_VALUES** para alterar esse comportamento.  

Veja um exemplo de consulta que usa o modo **AUTO** com a cláusula **FOR JSON** .
 
**Consulta:**  
  
```tsql  
SELECT name, surname  
FROM emp  
FOR JSON AUTO  
```  
  
 **Resultados**  
  
```json  
[{
    "name": "John"
}, {
    "name": "Jane",
    "surname": "Doe"
}]
```  
### <a name="more-info"></a>Obter mais informações
Para mais informações e exemplos, consulte [Formatar a saída JSON automaticamente com o modo AUTO &#40;SQL Server&#41;](../../relational-databases/json/format-json-output-automatically-with-auto-mode-sql-server.md).

Para sintaxe e uso, consulte [Cláusula FOR &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md).  
  
## <a name="control-other-json-output-options"></a>Controlar outras opções de saída JSON  
 Controle a saída da cláusula **FOR JSON** usando as opções a seguir.  
  
-   Para adicionar um único elemento de nível superior à saída JSON, especifique a opção **ROOT** . Se você não especificar a opção **ROOT** , a saída JSON não terá um elemento raiz. Para obter mais informações, consulte [Add a Root Node to JSON Output with the ROOT Option &#40;SQL Server&#41; (Adicionar um nó raiz à saída JSON com a opção ROOT &#40;SQL Server&#41;)](../../relational-databases/json/add-a-root-node-to-json-output-with-the-root-option-sql-server.md).  
  
-   Para incluir valores nulos na saída JSON, especifique a opção **INCLUDE_NULL_VALUES** . Se você não especificar essa opção, a saída não incluirá propriedades JSON para valores NULL nos resultados da consulta. Para obter mais informações, consulte[Include Null Values in JSON Output with the INCLUDE_NULL_VALUES Option &#40;SQL Server&#41; (Incluir valores nulos em uma saída JSON com a opção INCLUDE_NULL_VALUES &#40;SQL Server&#41;)](../../relational-databases/json/include-null-values-in-json-include-null-values-option.md).   

-   Para remover, por padrão, os colchetes que envolvem a saída JSON da cláusula **FOR JSON** , especifique a opção **WITHOUT_ARRAY_WRAPPER** . Use esta opção para gerar um único objeto JSON como saída. Se você não especificar essa opção, a saída JSON será colocada entre colchetes. Para obter mais informações, consulte [Remove Square Brackets from JSON Output with the WITHOUT_ARRAY_WRAPPER Option &#40;SQL Server&#41; (Remover os colchetes da saída JSON com a opção WITHOUT_ARRAY_WRAPPER &#40;SQL Server&#41;)](../../relational-databases/json/remove-square-brackets-from-json-without-array-wrapper-option.md). 
   
## <a name="output-of-the-for-json-clause"></a>Saída da cláusula FOR JSON  
 A saída da cláusula **FOR JSON** tem as seguintes características.  
  
1.  O conjunto de resultados contém uma única coluna. Um conjunto de resultados pequeno pode conter uma única linha. Um conjunto de resultados grande contém várias linhas.  
  
     ![Exemplo de saída FOR JSON](../../relational-databases/json/media/forjson-example2.png "Exemplo de saída FOR JSON")  
  
2.  Os resultados são formatados como uma matriz de objetos JSON.  
  
    -   O número de elementos na matriz é igual ao número de linhas nos resultados.  
  
    -   Cada linha no conjunto de resultados se torna um objeto JSON separado na matriz.  
  
    -   Cada coluna no conjunto de resultados se torna uma propriedade do objeto JSON.  
  
3.  Os dois os nomes das colunas e seus valores são escapados de acordo com a sintaxe JSON. Para obter mais informações, consulte [How FOR JSON escapes special characters and control characters &#40;SQL Server&#41; (Como o FOR JSON ignora os caracteres especiais e os caracteres de controle &#40;SQL Server&#41;)](../../relational-databases/json/how-for-json-escapes-special-characters-and-control-characters-sql-server.md).
  
 Veja um exemplo que demonstra a formatação da saída JSON.  
  
 **Resultados da consulta**  
  
|||||  
|-|-|-|-|  
|**A**|**B**|**C**|**D**|  
|10|11|12|X|  
|20|21|22|S|  
|30|31|32|Z|  
  
 **Saída JSON**  
  
```json  
[{
    "A": 10,
    "B": 11,
    "C": 12,
    "D": "X"
}, {
    "A": 20,
    "B": 21,
    "C": 22,
    "D": "Y"
}, {
    "A": 30,
    "B": 31,
    "C": 32,
    "D": "Z"
}] 
```  
 Para obter mais informações sobre o que você vê na saída da cláusula **FOR JSON**, consulte os seguintes tópicos.  
-   [How FOR JSON converts SQL Server data types to JSON data types &#40;SQL Server&#41; (Como FOR JSON converte tipos de dados do SQL Server para tipos de dados &#40;SQL Server&#41;)](../../relational-databases/json/how-for-json-converts-sql-server-data-types-to-json-data-types-sql-server.md)  
A cláusula **FOR JSON** usa as regras descritas neste tópico para converter os tipos de dados SQL em tipos JSON na saída JSON.  

-   [How FOR JSON escapes special characters and control characters &#40;SQL Server&#41; (Como o FOR JSON ignora os caracteres especiais e os caracteres de controle &#40;SQL Server&#41;)](../../relational-databases/json/how-for-json-escapes-special-characters-and-control-characters-sql-server.md)  
 A cláusula **FOR JSON** ignora os caracteres especiais e representa os caracteres de controle na saída JSON, conforme descrito neste tópico.  

## <a name="learn-more-about-for-json-and-built-in-json-support-in-sql-server"></a>Saiba mais sobre o FOR JSON e o suporte interno a JSON no SQL Server  
 [Postagens no blog por Jovan Popovic, gerente de programas da Microsoft](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/)  
  
## <a name="see-also"></a>Consulte também  
 [Cláusula FOR &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md)   
 [Use FOR JSON output in SQL Server and in client apps &#40;SQL Server&#41; (Usar a saída FOR JSON no SQL Server e em aplicativos cliente &#40;SQL Server&#41;)](../../relational-databases/json/use-for-json-output-in-sql-server-and-in-client-apps-sql-server.md)  
  
  
