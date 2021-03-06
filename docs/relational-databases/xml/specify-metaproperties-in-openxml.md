---
title: Especificar metapropriedades no OPENXML | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: xml
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- overflow in XML document [SQL Server]
- metaproperties [XML in SQL Server]
- unconsumed data
- extracting information of XML nodes [SQL Server]
- OPENXML statement, metaproperties
ms.assetid: 29bfd1c6-3f9a-43c4-924a-53d438e442f4
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 968f1a5b32bbc6c2e6f2f955083e8fd247e3fc82
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/12/2018
---
# <a name="specify-metaproperties-in-openxml"></a>Especificar metapropriedades no OPENXML
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
Atributos de metapropriedades em um documento XML são atributos que descrevem as propriedades de um item XML, como elemento, atributo ou qualquer outro nó DOM. Esses atributos não existem fisicamente no documento de texto XML. No entanto o OPENXML fornece essas metapropriedades para todos os itens XML. Essas metapropriedades permitem extrair informações, como posicionamento local e informações de namespace, de nós XML. Essas informações fornecem mais detalhes do que os que estão aparentes na representação textual.  
  
 Você pode mapear essas metapropriedades para as colunas do conjunto de linhas em uma instrução OPENXML usando o parâmetro *ColPattern* . As colunas conterão os valores das metapropriedades para as quais elas são mapeadas. Para obter mais informações sobre a sintaxe do OPENXML, consulte [OPENXML &#40;Transact-SQL&#41;](../../t-sql/functions/openxml-transact-sql.md).  
  
 Para acessar os atributos de metapropriedades, é fornecido um namespace que é específico ao SQL Server. Esse namespace **urn:schemas-microsoft-com:xml-metaprop** permite que o usuário acesse os atributos de metapropriedades. Se o resultado de uma consulta OPENXML for retornado em uma formato de tabela de borda, a tabela de borda conterá uma coluna para cada atributo de metapropriedade, exceto a metapropriedade **xmltext** .  
  
 Alguns dos atributos de metapropriedade são usados para fins de processamento. Por exemplo, o atributo da metapropriedade **xmltext** é usado para manipulação de estouro. A manipulação de estouro faz referência a dados não consumidos e não processados no documento. Uma das colunas no conjunto de linhas gerado por OPENXML pode ser identificada como a coluna de estouro. Isso é feito mapeando a coluna para a metapropriedade **xmltext** usando o parâmetro *ColPattern* . A coluna então recebe os dados excedentes. O parâmetro *flags* determina se a coluna contém tudo ou apenas dados não consumidos.  
  
 A tabela a seguir lista os atributos de metapropriedade que cada elemento XML analisado possui. Esses atributos de metapropriedade podem ser acessados usando o namespace **urn:schemas-microsoft-com:xml-metaprop**. Qualquer valor definido pelo usuário diretamente no documento XML usando essas metapropriedades é ignorado.  
  
> [!NOTE]  
>  Não é possível fazer referência a essas metapropriedades em qualquer navegação XPath.  
  
|Atributo de metapropriedade|Description|  
|----------------------------|-----------------|  
|**@mp:id**|Fornece um identificador de todo o documento gerado pelo sistema do nó DOM. Desde que o documento não seja reanalisado, essa ID faz referência ao mesmo nó XML.<br /><br /> Uma ID de XML de **0** indica que o elemento é um elemento raiz. A ID de XML de seu pai é NULL.|  
|**@mp:localname**|Armazena a parte local do nome do nó. Ele é usado com um URI de namespace e de prefixo para nomear nós de elementos ou atributos.|  
|**@mp:namespaceuri**|Fornece o URI do namespace do elemento atual. Se o valor desse atributo for NULL, nenhum namespace estará presente|  
|**@mp:prefix**|Armazena o prefixo do namespace do nome do elemento atual.<br /><br /> Se nenhum prefixo estiver presente (NULL) e um URI for fornecido, ele indicará que o namespace identificado é o namespace padrão. Se nenhum URI for fornecido, nenhum namespace será anexado.|  
|**@mp:prev**|Armazena o irmão anterior relativo a um nó. Isso fornece informações sobre a ordenação de elementos no documento.<br /><br /> **@mp:prev** contém a ID de XML do irmão anterior que tem o mesmo elemento pai. Se um elemento estiver à frente da lista de irmãos, **@mp:prev** será NULL.|  
|**@mp:xmltext**|Usado para fins de processamento. É a serialização textual do elemento e seus atributos e também dos subelementos, conforme usado na manipulação de estouro do OPENXML.|  
  
 Essa tabela mostra as propriedades pai adicionais que são fornecidas e que permitem recuperar informações sobre a hierarquia.  
  
|Atributo de metapropriedade pai|Description|  
|-----------------------------------|-----------------|  
|**@mp:parentid**|Corresponde a **../@mp:id**|  
|**@mp:parentlocalname**|Corresponde a **../@mp:localname**|  
|**@mp:parentnamespacerui**|Corresponde a **../@mp:namespaceuri**|  
|**@mp:parentprefix**|Corresponde a **../@mp:prefix**|  
  
## <a name="examples"></a>Exemplos  
 Os exemplos seguintes ilustram como o OPENXML é usado para criar exibições de conjunto de linhas diferentes.  
  
### <a name="a-mapping-the-openxml-rowset-columns-to-the-metaproperties"></a>A. Mapeando colunas do conjunto de linhas OPENXML para as metapropriedades  
 Este exemplo usa OPENXML para criar uma exibição do conjunto de linhas do documento XML de exemplo. Especificamente, ele mostra como os vários atributos de metapropriedade podem ser mapeados para colunas do conjunto de linhas em uma instrução OPENXML usando o parâmetro *ColPattern* .  
  
 A instrução OPENXML ilustra o seguinte:  
  
-   O parâmetro **id** é mapeada para o atributo de metapropriedade **@mp:id** e indica que a coluna contém a ID de XML exclusiva do elemento gerado pelo sistema.  
  
-   O parâmetro **parent** é mapeada para o **@mp:parentid** e indica que a coluna contém a ID de XML do pai do elemento.  
  
-   O parâmetro **parentLocalName** é mapeada para o **@mp:parentlocalname** e indica que a coluna contém o nome local do pai.  
  
 Em seguida, a instrução SELECT retorna o conjunto de linhas fornecido por OPENXML:  
  
```  
DECLARE @idoc int  
DECLARE @doc nvarchar(1000)  
-- Sample XML document  
SET @doc = N'<root>  
  <Customer cid= "C1" name="Janine" city="Issaquah">  
      <Order oid="O1" date="1/20/1996" amount="3.5" />  
      <Order oid="O2" date="4/30/1997" amount="13.4">Customer was very satisfied</Order>  
   </Customer>  
   <Customer cid="C2" name="Ursula" city="Oelde" >  
      <Order oid="O3" date="7/14/1999" amount="100" note="Wrap it blue white red">  
          <Urgency>Important</Urgency>  
      </Order>  
      <Order oid="O4" date="1/20/1996" amount="10000"/>  
   </Customer>  
</root>'  
-- Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @idoc OUTPUT, @doc  
  
-- Execute a SELECT statement using OPENXML rowset provider.  
SELECT *  
FROM OPENXML (@idoc, '/root/Customer/Order', 9)  
      WITH (id int '@mp:id',   
            oid char(5),   
            date datetime,   
            amount real,   
            parentIDNo int '@mp:parentid',   
            parentLocalName varchar(40) '@mp:parentlocalname')  
EXEC sp_xml_removedocument @idoc  
```  
  
 Este é o resultado:  
  
```  
id   oid         date                amount    parentIDNo  parentLocalName    
--- ------- ---------------------- ---------- ------------ ---------------  
6    O1    1996-01-20 00:00:00.000     3.5         2        Customer  
10   O2    1997-04-30 00:00:00.000     13.4        2        Customer  
19   O3    1999-07-14 00:00:00.000     100.0       15       Customer  
25   O4    1996-01-20 00:00:00.000     10000.0     15       Customer  
```  
  
### <a name="b-retrieving-the-whole-xml-document"></a>B. Recuperando o documento XML inteiro  
 Neste exemplo, OPENXML é usado para criar a exibição do conjunto de linhas de uma coluna do documento XML de exemplo. Esta coluna, **Col1**, é mapeada para a metapropriedade **xmltext** e se torna uma coluna de estouro. Como resultado, a coluna recebe os dados não consumidos. Nesse caso, o documento inteiro.  
  
 Em seguida, a instrução SELECT retorna o conjunto de linhas completo.  
  
```  
DECLARE @idoc int  
DECLARE @doc nvarchar(1000)  
SET @doc = N'<?xml version="1.0"?>  
<root>  
  <Customer cid= "C1" name="Janine" city="Issaquah">  
      <Order oid="O1" date="1/20/1996" amount="3.5" />  
      <Order oid="O2" date="4/30/1997" amount="13.4">Customer was very   
             satisfied</Order>  
   </Customer>  
   <Customer cid="C2" name="Ursula" city="Oelde" >  
      <Order oid="O3" date="7/14/1999" amount="100" note="Wrap it blue   
             white red">  
     <MyTag>Testing to see if all the subelements are returned</MyTag>  
          <Urgency>Important</Urgency>  
      </Order>  
      <Order oid="O4" date="1/20/1996" amount="10000"/>  
   </Customer>  
</root>'  
-- Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @idoc OUTPUT, @doc  
  
-- Execute a SELECT statement using OPENXML rowset provider.  
SELECT *  
FROM OPENXML (@idoc, '/')  
   WITH (Col1 ntext '@mp:xmltext')  
```  
  
 Para recuperar o documento inteiro sem a declaração XML, a consulta pode ser especificada conforme mostrado no exemplo a seguir:  
  
```  
SELECT *  
FROM OPENXML (@idoc, '/root')  
   WITH (Col1 ntext '@mp:xmltext')  
EXEC sp_xml_removedocument @idoc  
```  
  
 A consulta retorna o elemento raiz que tem a raiz do nome e os dados contidos pelo elemento raiz.  
  
### <a name="c-specifying-the-xmltext-metaproperty-to-retrieve-the-unconsumed-data-in-a-column"></a>C. Especificando a metapropriedade xmltext para recuperar os dados não consumidos em uma coluna  
 Este exemplo usa OPENXML para criar uma exibição do conjunto de linhas do documento XML de exemplo. O exemplo mostra como recuperar os dados XML não consumidos mapeamento o atributo de metapropriedade **xmltext** para uma coluna do conjunto de linhas no OPENXML.  
  
 O parâmetro **comment** é identificada como a coluna de estouro mapeando-a para a metapropriedade **@mp:xmltext** . O parâmetro *flags* é definido como **9** (XML_ATTRIBUTE e XML_NOCOPY). Isso indica mapeamento **centrado em atributo** e indica que apenas os dados não consumidos devem ser copiados para a coluna de estouro.  
  
 Em seguida, a instrução SELECT retorna o conjunto de linhas fornecido por OPENXML:  
  
 Neste exemplo, a metapropriedade **@mp:parentlocalname** é definida para uma coluna, **ParentLocalName**, no conjunto de linhas gerado por OPENXML. Como resultado, essa coluna contém o nome local do elemento pai.  
  
 São especificadas duas colunas adicionais no conjunto de linhas, **parent** e **comment**. O parâmetro **parent** é mapeada para o **@mp:parentid** e indica que a coluna contém a ID de XML do elemento pai do elemento. A coluna comment é identificada como a coluna de estouro mapeando-a para a metapropriedade **@mp:xmltext** .  
  
```  
DECLARE @idoc int  
DECLARE @doc nvarchar(1000)  
-- sample XML document  
SET @doc = N'<root>  
  <Customer cid= "C1" name="Janine" city="Issaquah">  
      <Order oid="O1" date="1/20/1996" amount="3.5" />  
      <Order oid="O2" date="4/30/1997" amount="13.4">Customer was very satisfied</Order>  
   </Customer>  
   <Customer cid="C2" name="Ursula" city="Oelde" >  
      <Order oid="O3" date="7/14/1999" amount="100" note="Wrap it blue white red">  
          <Urgency>Important</Urgency>  
      </Order>  
      <Order oid="O4" date="1/20/1996" amount="10000"/>  
   </Customer>  
</root>  
'  
-- Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @idoc OUTPUT, @doc  
  
-- Execute a SELECT statement using OPENXML rowset provider.  
SELECT *  
FROM OPENXML (@idoc, '/root/Customer/Order', 9)  
      WITH (oid char(5),   
            date datetime,  
            comment ntext '@mp:xmltext')  
EXEC sp_xml_removedocument @idoc  
```  
  
 Este é o resultado. Como as colunas oid e date já estão consumidas, elas não são exibidas na coluna de estouro.  
  
```  
oid   date                        comment                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            
----- --------------------------- ----------------------------------------  
O1    1996-01-20 00:00:00.000     <Order amount="3.5"/>  
O2    1997-04-30 00:00:00.000     <Order amount="13.4">Customer was very   
                                   satisfied</Order>  
O3    1999-07-14 00:00:00.000     <Order amount="100" note="Wrap it blue   
                                   white red"><Urgency>   
                                   Important</Urgency></Order>  
O4    1996-01-20 00:00:00.000     <Order amount="10000"/>  
```  
  
## <a name="see-also"></a>Consulte Também  
 [OPENXML &#40;Transact-SQL&#41;](../../t-sql/functions/openxml-transact-sql.md)   
 [OPENXML &#40;SQL Server&#41;](../../relational-databases/xml/openxml-sql-server.md)  
  
  
