---
title: Criar e gerenciar KPIs | Microsoft Docs
ms.custom: 
ms.date: 02/22/2018
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.asvs.bidtoolset.kpi.f1
ms.assetid: c96026c2-4394-4c3c-986b-4c95a4421900
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: b16307f79552529c2afc0c1d298c68a85ff1f2a1
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/23/2018
---
# <a name="create-and-manage-kpis"></a>Criar e gerenciar KPIs 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
Este artigo descreve como criar, editar ou excluir um KPI (indicador chave de desempenho) em um modelo de tabela. Para criar um KPI, selecione uma medida que seja avaliada como o valor base do KPI. Use a caixa de diálogo Indicador Chave de Desempenho para selecionar uma segunda medida ou um valor absoluto que seja avaliado para um valor de destino. Em seguida, você pode definir os limites de status que abrangem o desempenho entre as medidas Base e Destino.  
  
## <a name="tasks"></a>Tarefas  
  
> [!IMPORTANT]  
>  Antes de criar um KPI, primeiro você deve criar uma Medida base que será avaliada como valor. Em seguida, você estenderá a medida Base para um KPI. Como criar medidas são descritos em outro tópico, [criar e gerenciar medidas](../../analysis-services/tabular-models/create-and-manage-measures-ssas-tabular.md). Um KPI também exige um valor de destino. Este valor pode ser de outra medida pré-definida ou um valor absoluto. Depois de estender uma Medida base para um KPI, você pode selecionar o valor de destino e pode definir limites de status na caixa de diálogo do Indicador chave de desempenho.  
  
###  <a name="bkmk_create_KPI"></a> Para criar um KPI  
  
1.  Na grade de medida, clique com o botão direito do mouse na medida que servirá como a medida Base (valor) e clique em **Criar KPI**.  
  
2.  Na caixa de diálogo **Indicador Chave de Desempenho** , em **Definir valor de destino**, selecione uma das seguintes opções:  
  
     Selecione **Medida**e, em seguida, selecione uma medida de destino na caixa de listagem.  
  
     Selecione **Valor absoluto**e digite um valor numérico.  
  
3.  Em **Definir limites de status**, clique e deslize os valores de limite baixo e alto.  
  
4.  Em **Selecionar estilo do ícone**, clique em um tipo de imagem.  
  
5.  Clique em **Descrições**e digite as descrições para KPI, Valor, Status e Destino.  
  
> [!TIP]  
>  Você pode usar o recurso Analisar no Excel para testar seu KPI. Para obter mais informações, consulte [analisar no Excel](../../analysis-services/tabular-models/analyze-in-excel-ssas-tabular.md).  
  
###  <a name="bkmk_edit_KPI"></a> Para editar um KPI  
  
-   Na Grade de Medida, clique com o botão direito do mouse na medida que serve como a medida base (valor) do KPI e clique em **Editar Configurações do KPI**.  
  
###  <a name="bkmk_delete"></a> Para excluir um KPI e a medida de base  
  
-   Na grade de medida, clique com o botão direito do mouse na medida que serve como a medida base (valor) do KPI e clique em **Excluir**.  
  
###  <a name="bkmk_delete_KPI"></a> Para excluir um KPI, mas manter a medida de base  
  
-   Na grade de medida, clique com o botão direito do mouse na medida que serve como a medida base (valor) do KPI e clique em **Excluir KPI**.  
  
## <a name="alt-shortcuts"></a>Atalhos ALT  
  
|Seção da Interface do Usuário|Comando de teclas|  
|----------------|-----------------|  
|Medida base do KPI|ALT+B|  
|Status do KPI|ALT+S|  
|Measure|ALT+M|  
|Valor absoluto|ALT+A|  
|Definir limites de status|ALT+U|  
|Selecionar estilo do ícone|ALT+I|  
|Tendência|ALT+T|  
|Descrições|ALT+D|  
|Tendência|ALT+T|  
  
## <a name="see-also"></a>Consulte também  
 [KPIs](../../analysis-services/tabular-models/kpis-ssas-tabular.md)   
 [Medidas](../../analysis-services/tabular-models/measures-ssas-tabular.md)   
 [Criar e managemeasures](../../analysis-services/tabular-models/create-and-manage-measures-ssas-tabular.md)  
  
  
