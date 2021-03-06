---
title: "Habilitar, desabilitar e excluir pontos de interrupção | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 357b5874-273f-43a9-8e30-83872bdea5dc
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2c78a83bbf85641580f05d08af7272bce554bff2
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2018
---
# <a name="enable-disable-and-delete-breakpoints"></a>Habilitar, desabilitar e excluir pontos de interrupção
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Para exibir e gerenciar todos os pontos de interrupção abertos, você pode usar a janela **Pontos de Interrupção**. Use a janela para exibir informações de ponto de interrupção e executar ações como excluir, desabilitar ou habilitar pontos de interrupção.  
  
## <a name="the-breakpoints-window"></a>Janela Pontos de Interrupção  
 A janela **Pontos de Interrupção** lista informações como a linha de código em que o ponto de interrupção é localizado. Na janela **Pontos de Interrupção** , você também pode excluir, desabilitar e habilitar pontos de interrupção. Para obter mais informações sobre a janela **Pontos de Interrupção** , consulte [Pontos de Interrupção Window](../../relational-databases/scripting/transact-sql-debugger-breakpoints-window.md).  
  
 A desabilitação de um ponto de interrupção impede a pausa da execução, mas deixa a definição no local caso você deseje habilitar o ponto de interrupção mais tarde. A exclusão de um ponto de interrupção remove isso permanentemente. Você deve alternar um novo ponto de interrupção para pausar execução na instrução.  
  
## <a name="to-open-the-breakpoints-window"></a>Para abrir a janela Pontos de Interrupção  
 **To open the Breakpoints window**  
  
 Você pode abrir a janela **Pontos de Interrupção** de uma das seguintes maneiras:  
  
-   No menu **Depurar** , clique em **Janelas**e em **Pontos de Interrupção**.  
  
-   Na barra de ferramentas **Depurar** , clique no botão **Pontos de Interrupção** .  
  
-   Pressione CTRL+ALT+B.  
  
## <a name="to-disable-a-single-breakpoint"></a>Para desabilitar um único ponto de interrupção  
 **To disable a single breakpoint**  
  
 Você pode desabilitar um único ponto de interrupção de uma das seguintes maneiras:  
  
-   Na janela Editor de Consultas, clique com o botão direito do mouse no ponto de interrupção e clique em **Desabilitar Ponto de Interrupção**.  
  
-   Na janela Pontos de Interrupção, desmarque a caixa de seleção à esquerda do ponto de interrupção.  
  
## <a name="to-disable-all-breakpoints"></a>Para desabilitar todos os pontos de interrupção  
 **To disable all breakpoints**  
  
 Você pode desabilitar todos os pontos de interrupção de uma das seguintes maneiras:  
  
-   No menu **Depurar** , clique em **Desabilitar Todos os Pontos de Interrupção**.  
  
-   Na barra de ferramentas da janela **Pontos de Interrupção** , clique no botão **Desabilitar Todos os Pontos de Interrupção** .  
  
## <a name="to-enable-a-single-breakpoint"></a>Para habilitar um único ponto de interrupção  
 **To enable a single breakpoint**  
  
 Você pode habilitar um único ponto de interrupção de uma das seguintes maneiras:  
  
-   Na janela Editor de Consultas, clique com o botão direito do mouse no ponto de interrupção e clique em **Habilitar Ponto de Interrupção**.  
  
-   Na janela Pontos de Interrupção, clique na caixa à esquerda do ponto de interrupção.  
  
## <a name="to-enable-all-breakpoints"></a>Para habilitar todos os pontos de interrupção  
 **To enable all breakpoints**  
  
 Você pode habilitar todos os pontos de interrupção de uma das seguintes maneiras:  
  
-   No menu **Depurar** , clique em **Habilitar Todos os Pontos de Interrupção**.  
  
-   Na barra de ferramentas da janela **Pontos de Interrupção** , clique no botão **Habilitar Todos os Pontos de Interrupção** .  
  
## <a name="to-delete-a-single-breakpoint"></a>Para excluir um único ponto de interrupção  
 **To delete a single breakpoint**  
  
 Você pode excluir um único ponto de interrupção de uma das seguintes maneiras:  
  
-   Na janela Editor de Consultas, clique com o botão direito do mouse no ponto de interrupção e clique em **Excluir Ponto de Interrupção**.  
  
-   Na janela Pontos de Interrupção, clique com o botão direito do mouse no ponto de interrupção e em **Excluir** no menu de atalho.  
  
-   Na janela Pontos de Interrupção, selecione o ponto de interrupção e pressione DELETE.  
  
## <a name="to-delete-all-breakpoints"></a>Para excluir todos os pontos de interrupção  
 **To delete all breakpoints**  
  
 Você pode excluir todos os pontos de interrupção de uma das seguintes maneiras:  
  
-   No menu **Depurar** , clique em **Excluir Todos os Pontos de Interrupção**.  
  
-   Na barra de ferramentas da janela **Pontos de Interrupção** , clique no botão **Excluir Todos os Pontos de Interrupção** .  
  
## <a name="see-also"></a>Consulte Também  
 [Alternar um ponto de interrupção](../../relational-databases/scripting/toggle-a-breakpoint.md)  
  
  
