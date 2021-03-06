---
title: Tratamento de erros na API de TOM (Analysis Services AMO-TOM) | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ec44daa0-a90e-42ad-b70d-6a7a7a4e4b7b
caps.latest.revision: "4"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: fe73f11bb44968e7091fe522f4905e3640c95282
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2018
---
# <a name="handling-errors-in-the-tom-api-analysis-services-amo-tom"></a>Tratamento de erros na API de TOM (Analysis Services AMO-TOM)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]Uma prática comum para as bibliotecas gerenciadas como o modelo de objeto Tabular do Analysis Services Management Objects (AMO) (TOM) é usar exceções como um mecanismo de relatório de condições de erro para o usuário.  

Quando for detectado um erro no AMO TOM, além de gerar algumas exceções .NET padrão como **ArgumentException** e **InvalidOperationException**, TOM também pode gerar várias exceções específicas de TOM.  

TOM exceções são derivadas de [classe AmoException](http://msdn.microsoft.com/library/microsoft.analysisservices.amoexception.aspx), que abrangem as duas exceções específicas de TOM e AMO. 

Para ilustrar a manipulação de exceção no TOM, vamos examinar uma das exceções mais comuns, que é [OperationException classe](http://msdn.microsoft.com/library/microsoft.analysisservices.operationexception.aspx).

**OperationException** é lançada quando um usuário inicia uma operação no servidor do Analysis Services e o servidor não pode executar uma operação, porque a ação foi ilegal ou devido a outro erro interno ou externo. 

Quando lançada, * * OperationException * * o objeto contém uma lista de erros XMLA retornados pelo servidor. 

Observe que o servidor não aceitará as alterações que são inválidas. Se isso ocorrer, reverta a **modelo** árvore de volta para o último estado bom conhecido usando o [UndoLocalChanges método](http://msdn.microsoft.com/library/microsoft.analysisservices.tabular.model.undolocalchanges.aspx), corrija o modelo e envie novamente. 

## <a name="code-example-handle-exceptions"></a>Exemplo de código: manipular exceções 
 
```
 try 
 { 
  // Change the Model, for example create a table. 
  // … 
   model.saveChanges(); 
 } 
  catch(operationException ex) 
 { 
  foreach(XmlaError err in ex.Results.OfType<XmlaError>().cast<XmlaError>()) 
  { 
   Console.WriteLine(“Error returned from the server:” + err.Messsage ); 
  } 
 } 
```

## <a name="next-steps"></a>Próximas etapas

Outras exceções relevantes incluem o seguinte:

- [Classe TomInternalException](http://msdn.microsoft.com/library/microsoft.analysisservices.tabular.tominternalexception.aspx)
- [Classe TomValidationException](http://msdn.microsoft.com/library/microsoft.analysisservices.tabular.tomvalidationexception.aspx)
- [Classe JsonSerializationException](http://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_JsonSerializationException.htm)
