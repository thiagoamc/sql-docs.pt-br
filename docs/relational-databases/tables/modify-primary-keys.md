---
title: "Modificar chaves prim&#225;rias | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-tables"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modificando chaves primárias"
  - "chaves primárias [SQL Server], modificando"
ms.assetid: 8e2a15ba-1cd1-4408-b860-16c3ee37d635
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# Modificar chaves prim&#225;rias
[!INCLUDE[tsql-appliesto-ss2016-all_md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Você pode modificar uma chave primária no [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] usando o [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou o [!INCLUDE[tsql](../../includes/tsql-md.md)]. Você pode modificar a chave primária de uma tabela alterando a ordem das colunas, o nome do índice, a opção clusterizada ou o fator de preenchimento.  
  
 **Neste tópico**  
  
-   **Antes de começar:**  
  
     [Segurança](#Security)  
  
-   **Para modificar uma chave primária usando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Antes de começar  
  
###  <a name="Security"></a> Segurança  
  
####  <a name="Permissions"></a> Permissões  
 Exige a permissão ALTER na tabela.  
  
##  <a name="SSMSProcedure"></a> Usando o SQL Server Management Studio  
  
#### Para modificar uma chave primária  
  
1.  Abra o Designer de Tabela da tabela cuja chave primária você quer modificar, clique com o botão direito do mouse no Designer de Tabela e escolha **Índices/Chaves** no menu de atalho.  
  
2.  Na caixa de diálogo **Índices/Chaves**, selecione o índice de chave primária na lista **Índice ou Chave Exclusiva/Primária Selecionada**.  
  
3.  Complete uma ação da seguinte tabela:  
  
    |Para|Siga estas etapas|  
    |--------|------------------------|  
    |Renomeie a chave primária|Digite um novo nome na caixa **Nome** . Verifique se seu novo nome não duplica um nome na lista **Índice ou Chave Exclusiva/Primária Selecionada**.|  
    |Definir a opção clustered|Para criar um índice clusterizado para a chave primária, selecione **Criar como CLUSTERED** e selecione a opção na caixa de listagem suspensa. Só pode existir um índice clusterizado por tabela. Se essa opção não estiver disponível para seu índice, você deve desmarcar essa configuração no primeiro índice clusterizado existente.<br /><br /> Se essa opção não for selecionada, um índice exclusivo não clusterizado será criado.|  
    |Definir um fator de preenchimento|Expanda a categoria **Especificação de Preenchimento** e digite um inteiro de 0 a 100 na caixa **Fator de Preenchimento** . Para obter mais informações sobre fatores de preenchimento e seus usos, veja [Especificar fator de preenchimento para um índice](../../relational-databases/indexes/specify-fill-factor-for-an-index.md).|  
    |Altere a ordem da coluna|Selecione **Colunas** e clique nas reticências **(…)** à direita da propriedade. Na caixa de diálogo  **Colunas de Índices** , remova as colunas da chave primária. Depois, adicione as colunas de novo na ordem desejada. Para remover uma coluna da chave, simplesmente remova o nome de coluna da lista de nomes **Coluna** .|  
  
4.  No menu **Arquivo** , clique em **Salvar***table name*.  
  
##  <a name="TsqlProcedure"></a> Usando Transact-SQL  
 **Para modificar uma chave primária**  
  
 Para modificar uma restrição PRIMARY KEY usando o Transact-SQL, exclua primeiramente a PRIMARY KEY já existente e, em seguida, recrie essa restrição com a nova definição. Para obter mais informações, consulte [Delete Primary Keys](../../relational-databases/tables/delete-primary-keys.md) e [Create Primary Keys](../../relational-databases/tables/create-primary-keys.md).  
  
###  <a name="TsqlExample"></a>  