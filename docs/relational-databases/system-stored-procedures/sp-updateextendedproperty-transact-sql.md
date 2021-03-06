---
title: sp_updateextendedproperty (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 04/12/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_updateextendedproperty_TSQL
- sp_updateextendedproperty
dev_langs:
- TSQL
helpviewer_keywords:
- sp_updateextendedproperty
ms.assetid: 7f02360f-cb9e-48b4-b75f-29b4bc9ea304
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 284eb1e8d95ff94091df493048826e3a958ffb8c
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="spupdateextendedproperty-transact-sql"></a>sp_updateextendedproperty (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Atualiza o valor de uma propriedade estendida existente.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Convenções da sintaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
sp_updateextendedproperty  
    [ @name = ]{ 'property_name' }   
    [ , [ @value = ]{ 'value' }  
        [, [ @level0type = ]{ 'level0_object_type' }  
         , [ @level0name = ]{ 'level0_object_name' }  
              [, [ @level1type = ]{ 'level1_object_type' }  
               , [ @level1name = ]{ 'level1_object_name' }  
                     [, [ @level2type = ]{ 'level2_object_type' }  
                      , [ @level2name = ]{ 'level2_object_name' }  
                     ]  
              ]  
        ]  
    ]  
```  
  
## <a name="arguments"></a>Argumentos  
 [ @name=] {'*property_name*'}  
 É o nome da propriedade a ser atualizada. *Property_Name* é **sysname**, e não pode ser NULL.  
  
 [ @value=] {'*valor*'}  
 É o valor associado à propriedade. *valor* é **sql_variant**, com um padrão NULL. O tamanho de *valor* não pode ser maior que 7.500 bytes.  
  
 [ @level0type=] {'*level0_object_type*'}  
 É o usuário ou tipo definido pelo usuário. *level0_object_type* é **varchar (128)**, com um padrão NULL. As entradas válidas são ASSEMBLY, contrato, notificação de eventos, grupo de arquivos, tipo de mensagem, função de partição, o esquema de partição, guia de plano, REMOTE SERVICE BINDING, ROTA, esquema, serviço, usuário, GATILHO, tipo e NULL.  
  
> [!IMPORTANT]  
>  USER e TYPE como tipos de nível 0 serão removidos em uma versão futura do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Evite usar esses recursos em novo trabalho de desenvolvimento e planeje modificar os aplicativos que os usam atualmente. Use SCHEMA como o tipo de nível 0 em vez de USER. Para TYPE, use SCHEMA como o tipo de nível 0 e TYPE como o tipo de nível 1.  
  
 [ @level0name=] {'*level0_object_name*'}  
 É o nome do tipo de objeto de nível 1 especificado. *level0_object_name* é **sysname** com um padrão NULL.  
  
 [ @level1type=] {'*level1_object_type*'}  
 É o tipo de objeto de nível 1. *level1_object_type* é **varchar (128)** com um padrão NULL. As entradas válidas são AGGREGATE, DEFAULT, FUNCTION, LOGICAL FILE NAME, PROCEDURE, QUEUE, RULE, SYNONYM, TABLE, TABLE_TYPE, TYPE, VIEW, XML SCHEMA COLLECTION e NULL.  
  
 [ @level1name=] {'*level1_object_name*'}  
 É o nome do tipo de objeto de nível 1 especificado. *level1_object_name* é **sysname** com um padrão NULL.  
  
 [ @level2type=] {'*level2_object_type*'}  
 É o tipo de objeto de nível 2. *level2_object_type* é **varchar (128)** com um padrão NULL. As entradas válidas são COLUMN, CONSTRAINT, EVENT NOTIFICATION, INDEX, PARAMETER, TRIGGER e NULL.  
  
 [ @level2name=] {'*level2_object_name*'}  
 É o nome do tipo de objeto de nível 2 especificado. *level2_object_name* é **sysname**, com um padrão NULL.  
  
## <a name="return-code-values"></a>Valores do código de retorno  
 0 (êxito) ou 1 (falha)  
  
## <a name="remarks"></a>Comentários  
 Com o propósito de especificar as propriedades estendidas, os objetos em um banco de dados do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] são classificados em três níveis (0, 1 e 2). O nível 0 é o mais alto e é definido como objetos que estão contidos no escopo do banco de dados. Os objetos de nível 1 estão contidos em um esquema ou escopo de usuário e os objetos de nível 2 estão contidos pelos objetos de nível 1. As propriedades estendidas podem ser definidas para os objetos em qualquer um desses níveis. As referências a um objeto de um nível precisam ser qualificadas com os nomes dos objetos de nível superior que as possua ou contenha.  
  
 Dado um válido *property_name* e *valor*, se todos os nomes e tipos de objeto forem nulos, a propriedade atualizada pertencerá ao banco de dados atual.  
  
## <a name="permissions"></a>Permissões  
 Os membros das funções de banco de dados fixas db_owner e db_ddladmin podem atualizar as propriedades estendidas de qualquer objeto, com a seguinte exceção: db_ddladmin não pode adicionar propriedades ao banco de dados em si ou a usuários ou funções.  
  
 Os usuários podem atualizar as propriedades estendidas dos objetos que possuírem ou para os quais tenham as permissões ALTER ou CONTROL.  
  
## <a name="examples"></a>Exemplos  
  
### <a name="a-updating-an-extended-property-on-a-column"></a>A. Atualizando uma propriedade estendida em uma coluna  
 O exemplo a seguir atualiza o valor de propriedade `Caption` na coluna `ID` da tabela `T1`.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE T1 (id int , name char (20));  
GO  
EXEC sp_addextendedproperty   
    @name = N'Caption'  
    ,@value = N'Employee ID'  
    ,@level0type = N'Schema', @level0name = dbo  
    ,@level1type = N'Table',  @level1name = T1  
    ,@level2type = N'Column', @level2name = id;  
GO  
--Update the extended property.  
EXEC sp_updateextendedproperty   
    @name = N'Caption'  
    ,@value = 'Employee ID must be unique.'  
    ,@level0type = N'Schema', @level0name = dbo  
    ,@level1type = N'Table',  @level1name = T1  
    ,@level2type = N'Column', @level2name = id;  
GO  
```  
  
### <a name="b-updating-an-extended-property-on-a-database"></a>B. Atualizando uma propriedade estendida em um banco de dados  
 O exemplo a seguir primeiro cria uma propriedade estendida no banco de dados de exemplo [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] e atualiza o valor dessa propriedade.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_addextendedproperty   
@name = N'NewCaption', @value = 'AdventureWorks2012 Sample OLTP Database';  
GO  
USE AdventureWorks2012;  
GO  
EXEC sp_updateextendedproperty   
@name = N'NewCaption', @value = 'AdventureWorks2012 Sample Database';  
GO  
```  
  
## <a name="see-also"></a>Consulte também  
 [Mecanismo de banco de dados armazenados procedimentos &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sys.fn_listextendedproperty &#40; Transact-SQL &#41;](../../relational-databases/system-functions/sys-fn-listextendedproperty-transact-sql.md)   
 [sp_addextendedproperty &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addextendedproperty-transact-sql.md)   
 [procedimento sp_addextendedproperty &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproperty-transact-sql.md)   
 [extended_properties &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/extended-properties-catalog-views-sys-extended-properties.md)  
  
  
