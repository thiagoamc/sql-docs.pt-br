---
title: "Criar, alterar e remover &#237;ndices XML seletivos | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-xml"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c398f396-f630-4a2d-a264-f243c5346de1
caps.latest.revision: 8
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 7
---
# Criar, alterar e remover &#237;ndices XML seletivos
  Descreve como criar um novo índice XML seletivo ou alterar ou remover um índice XML seletivo existente.  
  
 Para obter mais informações sobre índices XML seletivos, veja [SXI &#40;Índices XML Seletivos&#41;](../../relational-databases/xml/selective-xml-indexes-sxi.md).  
  
##  <a name="create"></a> Criando um índice XML seletivo  
  
### Como criar um índice XML seletivo  
 **Criar um índice XML seletivo usando Transact-SQL**  
 Crie um índice XML seletivo chamando a instrução CREATE SELECTIVE XML INDEX. Para obter mais informações, veja [CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-selective-xml-index-transact-sql.md).  
  
 **Exemplo**  
  
 O exemplo a seguir mostra a sintaxe para criar um índice XML seletivo. Ele também mostra variações da sintaxe para descrever os caminhos a serem indexados, com dicas de otimização opcionais.  
  
```tsql  
CREATE SELECTIVE XML INDEX sxi_index  
ON Tbl(xmlcol)  
  
FOR(  
    pathab   = '/a/b' as XQUERY 'node()'  
    pathabc  = '/a/b/c' as XQUERY 'xs:double',   
    pathdtext = '/a/b/d/text()' as XQUERY 'xs:string' MAXLENGTH(200) SINGLETON  
    pathabe = '/a/b/e' as SQL NVARCHAR(100)  
)  
```  
  
 [Neste tópico](#top)  
  
##  <a name="alter"></a> Alterando um índice XML seletivo  
  
### Como alterar um índice XML seletivo  
 **Alterar um índice XML seletivo usando Transact-SQL**  
 Altere um índice XML seletivo existente chamando a instrução ALTER INDEX. Para obter mais informações, veja [ALTER INDEX &#40;Índices XML Seletivos&#41;](../../t-sql/statements/alter-index-selective-xml-indexes.md).  
  
 **Exemplo**  
  
 O exemplo a seguir mostra uma instrução ALTER INDEX. Essa instrução adiciona o caminho `'/a/b/m'` à parte XQuery do índice e exclui o caminho `'/a/b/e'` da parte SQL do índice criado no exemplo no tópico [CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-selective-xml-index-transact-sql.md). O caminho a ser excluído é identificado pelo nome atribuído a ele quando foi criado.  
  
```tsql  
ALTER INDEX sxi_index  
ON Tbl  
FOR   
(  
    ADD pathm = '/a/b/m' as XQUERY 'node()' ,  
    REMOVE pathabe  
)  
```  
  
 [Neste tópico](#top)  
  
##  <a name="drop"></a> Removendo um índice XML seletivo  
  
### Como remover um índice XML seletivo  
 **Remover um índice XML seletivo usando Transact-SQL**  
 Remova um índice XML seletivo chamando a instrução DROP INDEX. Para obter mais informações, veja [DROP INDEX &#40;Índices XML Seletivos&#41;](../../t-sql/statements/drop-index-selective-xml-indexes.md).  
  
 **Exemplo**  
  
 O exemplo a seguir mostra uma instrução DROP INDEX.  
  
```tsql  
DROP INDEX sxi_index ON tbl  
```  
  
 [Neste tópico](#top)  
  
  