---
title: "Reordenando dados em uma tabela hierárquica usando métodos hierárquicos | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- HierarchyID
ms.assetid: 7b8064c7-62c6-488d-84d2-57a5828fb907
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a3d15df3ae3bf757b54e2e4d48c55b94285540d9
ms.sourcegitcommit: b09bccd6dfdba55b022355e892c29cb50aadd795
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2018
---
# <a name="lesson-2-4---reordering-data-in-a-hierarchical-table-using-hierarchical-methods"></a>Lição 2-4 – Reordenando dados em uma tabela hierárquica usando métodos hierárquicos
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)] Reorganizar uma hierarquia é uma tarefa de manutenção comum. Nesta tarefa, usaremos a instrução UPDATE com o método [GetReparentedValue](../../t-sql/data-types/getreparentedvalue-database-engine.md) para mover primeiramente uma única linha para um novo local da hierarquia. Em seguida, moveremos uma subárvore inteira para um novo local.  
  
O método `GetReparentedValue` toma dois argumentos. O primeiro argumento descreve a parte da hierarquia a ser modificada. Por exemplo, se uma hierarquia for **/1/4/2/3/** e você desejar alterar a seção **/1/4/** , a hierarquia se tornará **/2/1/2/3/**; se deixar os últimos dois nós (**2/3/**) inalterados, você precisará fornecer os nós que estão sendo alterados (**/1/4/**) como o primeiro argumento. O segundo argumento fornece o novo nível hierárquico, em nosso exemplo **/2/1/**. Os dois argumentos não precisam conter o mesmo número de níveis.  
  
### <a name="to-move-a-single-row-to-a-new-location-in-the-hierarchy"></a>Para mover uma linha única para um novo local hierárquico  
  
1.  Atualmente, Wanida reporta-se a Sariya. Neste procedimento, você move Valentina de seu nó **/1/1/** atual, de modo que ela se reporte a Julieta. Seu novo nó se tornará **/3/1/** e, dessa forma, **/1/** será o primeiro argumento e **/3/** o segundo. Esses correspondem aos valores **OrgNode** de Sara e Julieta. Execute o código a seguir para mover Wanida da organização de Sariya para a organização de Jill:  
  
    ```  
    DECLARE @CurrentEmployee hierarchyid , @OldParent hierarchyid, @NewParent hierarchyid  
    SELECT @CurrentEmployee = OrgNode FROM HumanResources.EmployeeOrg  
      WHERE EmployeeID = 269 ;   
    SELECT @OldParent = OrgNode FROM HumanResources.EmployeeOrg  
      WHERE EmployeeID = 46 ;   
    SELECT @NewParent = OrgNode FROM HumanResources.EmployeeOrg  
      WHERE EmployeeID = 119 ;   
  
    UPDATE HumanResources.EmployeeOrg  
    SET OrgNode = @CurrentEmployee. GetReparentedValue(@OldParent, @NewParent)   
    WHERE OrgNode = @CurrentEmployee ;  
    GO  
    ```  
  
2.  Execute o seguinte código para ver o resultado:  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    GO  
    ```  
  
    Valentina encontra-se agora no nó **/3/1/**.  
  
### <a name="to-reorganize-a-section-of-a-hierarchy"></a>Para reorganizar uma seção de hierarquia  
  
1.  Para demonstrar como mover um grande número de pessoas ao mesmo tempo, execute primeiramente o código a seguir para adicionar um estagiário se reportando a Wanida:  
  
    ```  
    EXEC AddEmp 269, 291, 'Kevin', 'Marketing Intern'  ;  
    GO  
    ```  
  
2.  Kevin agora se reporta a Wanida, que se reporta a Jill, que se reporta a David. Isso significa que Julio se encontra no nível **/3/1/1/**. Para mover todos os subordinados de Julieta para um novo administrador, atualizaremos todos os nós com **/3/** como seus **OrgNode** para um novo valor. Execute o seguinte código para atualizar Wanida, de modo que passe a se reportar a Sariya, mas deixando Kevin se reportando a Wanida:  
  
    ```  
    DECLARE @OldParent hierarchyid, @NewParent hierarchyid  
    SELECT @OldParent = OrgNode FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 119 ; -- Jill  
    SELECT @NewParent = OrgNode FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 46 ; -- Sariya  
    DECLARE children_cursor CURSOR FOR  
    SELECT OrgNode FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.GetAncestor(1) = @OldParent;  
    DECLARE @ChildId hierarchyid;  
    OPEN children_cursor  
    FETCH NEXT FROM children_cursor INTO @ChildId;  
    WHILE @@FETCH_STATUS = 0  
    BEGIN  
    START:  
        DECLARE @NewId hierarchyid;  
        SELECT @NewId = @NewParent.GetDescendant(MAX(OrgNode), NULL)  
        FROM HumanResources.EmployeeOrg WHERE OrgNode.GetAncestor(1) = @NewParent;  
  
        UPDATE HumanResources.EmployeeOrg  
        SET OrgNode = OrgNode.GetReparentedValue(@ChildId, @NewId)  
        WHERE OrgNode.IsDescendantOf(@ChildId) = 1;  
        IF @@error <> 0 GOTO START -- On error, retry  
            FETCH NEXT FROM children_cursor INTO @ChildId;  
    END  
    CLOSE children_cursor;  
    DEALLOCATE children_cursor;  
  
    ```  
  
3.  Execute o seguinte código para ver o resultado:  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    GO  
    ```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Text_OrgNode OrgNode OrgLevel EmployeeID EmpName Title  
------------ ------- -------- ---------- ------- -----------------  
/            Ox      0        6          David   Marketing Manager  
/1/          0x58    1        46         Sariya  Marketing Specialist  
/1/1/        0x5AC0  2        269        Wanida  Marketing Assistant  
/1/1/1/      0x5AD0  3        291        Kevin   Marketing Intern  
/2/          0x68    1        271        John    Marketing Specialist  
/2/1/        0x6AC0  2        272        Mary    Marketing Assistant  
/3/          0x78    1        119        Jill    Marketing Specialist  
```  
  
Toda a árvore organizacional que se reportava a Jill (Wanida e Kevin), agora se reporta a Sariya.  
  
Para ver um procedimento armazenado que reorganiza uma seção de uma hierarquia, consulte a seção “Movendo subárvores” de [Movendo subárvores](../../relational-databases/hierarchical-data-sql-server.md#BKMK_MovingSubtrees).  
  
## <a name="next-task-in-lesson"></a>Próxima tarefa da lição  
[Resumo: Gerenciando dados em uma tabela hierárquica](../../relational-databases/tables/lesson-2-5-summary-managing-data-in-a-hierarchical-table.md)  
  
  
  
