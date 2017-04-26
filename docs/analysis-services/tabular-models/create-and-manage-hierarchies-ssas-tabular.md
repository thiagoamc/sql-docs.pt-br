---
title: "Criar e Gerenciar hierarquias (SSAS tabular) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8dd30cd0-a831-4d25-b577-648d7f3c7fa6
caps.latest.revision: 10
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 10
---
# Criar e Gerenciar hierarquias (SSAS tabular)
  As hierarquias podem ser criadas e gerenciadas no designer modelo em Exibição de Diagrama. Par exibir o designer de modelos na Exibição de Diagrama no [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], clique no menu **Model** , aponte para **Exibição de Modelo**e clique em **Exibição de Diagrama**.  
  
 Este tópico inclui as seguintes tarefas:  
  
-   [Criar uma hierarquia](#bkmk_create)  
  
-   [Editar uma hierarquia](#bkmk_edit)  
  
-   [Excluir uma hierarquia](#bkmk_delete)  
  
##  <a name="bkmk_create"></a> Criar uma hierarquia  
 Você pode criar uma hierarquia usando as colunas e o menu de contexto de tabela. Quando você criar uma hierarquia, um novo nível pai é exibido com as colunas selecionadas como níveis filho.  
  
#### Para criar uma hierarquia no menu de contexto  
  
1.  No designer modelo (Exibição de Diagrama), em uma janela de tabela, clique com o botão direito do mouse em uma coluna e clique em **Criar Hierarquia**.  
  
     Para selecionar várias colunas, clique em cada coluna, clique com o botão direito do mouse para abrir o menu de contexto e clique em **Criar Hierarquia**.  
  
     Um nível de hierarquia pai é criado na parte inferior da janela da tabela e as colunas selecionadas são copiadas sob a hierarquia como níveis filho.  
  
2.  Digite um nome para a hierarquia.  
  
 Você pode arrastar colunas adicionais no nível pai de sua hierarquia, que copia as colunas. Remova o nível filho para colocá-lo onde você desejar que ele seja exibido na hierarquia.  
  
> [!NOTE]  
>  O comando Criar Hierarquia estará desabilitado no menu de contexto se você fizer multisseleção de uma medida junto com uma ou mais colunas, ou se você selecionar colunas de várias tabelas.  
  
##  <a name="bkmk_edit"></a> Editar uma hierarquia  
 Você pode renomear uma hierarquia, renomear um nível filho, alterar a ordem dos níveis filho, adicionar colunas adicionais como níveis filho, remover um nível filho de uma hierarquia, mostrar o nome de origem de um nível filho (o nome da coluna) e ocultar um nível filho se tiver o mesmo nome como o nível pai da hierarquia.  
  
#### Para alterar o nome de uma hierarquia ou nível filho  
  
1.  Clique com o botão direito do mouse no nível pai ou nível filho da hierarquia e clique em **Renomear**.  
  
2.  Digite um novo nome ou edite o nome existente.  
  
#### Para alterar a ordem de um nível filho em uma hierarquia  
  
-   Clique e arraste um nível filho para uma nova posição na hierarquia.  
  
-   Ou clique com o botão direito em um nível filho da hierarquia e clique em Mover para Cima para mover o nível na lista ou clique em Mover para Baixo para mover para baixo na lista.  
  
-   Ou clique em um nível filho para selecioná-lo e pressione Alt + Seta para Cima para mover o nível para cima, ou pressione Alt + Seta para Baixo para mover o nível para baixo na lista.  
  
#### Para adicionar outro nível filho a uma hierarquia  
  
-   Clique e arraste uma coluna para o nível pai ou um local específico da hierarquia. A coluna é copiada como um nível filho da hierarquia.  
  
-   Ou clique com o botão direito do mouse em uma coluna, aponte para **Adicionar à Hierarquia** e clique na hierarquia.  
  
> [!NOTE]  
>  Você pode adicionar uma coluna oculta (uma coluna que é oculta de relatórios) como um nível filho à hierarquia. O nível filho não está oculto.  
  
#### Para remover um nível filho de uma hierarquia  
  
-   Clique com o botão direito do mouse no nível filho e clique em **Remover da Hierarquia**.  
  
-   Ou clique no nível filho e pressione **Excluir**.  
  
> [!NOTE]  
>  Se você renomear um nível filho da hierarquia, ele não mais terá o mesmo nome que a coluna da qual foi copiado. Use o comando **Mostrar Nome de Origem** para ver de qual coluna ela foi copiada.  
  
#### Para mostrar um nome de origem  
  
-   Clique com o botão direito do mouse no nível filho da hierarquia e clique em **Show Source Name (Mostrar Nome de Origem)**. O nome da coluna da qual ela foi copiada é exibido.  
  
##  <a name="bkmk_delete"></a> Excluir uma hierarquia  
  
#### Para excluir uma hierarquia e remover seus níveis filho  
  
-   Clique com o botão direito no nível pai da hierarquia e clique em Excluir Hierarquia.  
  
-   Ou clique no nível pai da hierarquia e pressione Excluir. Isto também remove todos os níveis filho.  
  
## Consulte também  
 [Designer de Modelos de Tabela &#40;SSAS&#41;](../../analysis-services/tabular-models/tabular-model-designer-ssas.md)   
 [Hierarquias &#40;SSAS de Tabela&#41;](../../analysis-services/tabular-models/hierarchies-ssas-tabular.md)   
 [Medidas &#40;SSAS de Tabela&#41;](../../analysis-services/tabular-models/measures-ssas-tabular.md)  
  
  