---
title: "Alterar o nome de uma regra de neg&#243;cio (Master Data Services) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "regras de negócios [Master Data Services], alterando nome"
ms.assetid: cffcae43-a208-443f-9f43-a0ec9e05f79c
caps.latest.revision: 7
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 7
---
# Alterar o nome de uma regra de neg&#243;cio (Master Data Services)
  No [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], altere o nome de uma regra de negócio quando o nome atribuído não atender às suas necessidades comerciais.  
  
## Pré-requisitos  
 Para executar esse procedimento:  
  
-   Você deve ter permissão para acessar a área funcional **Administração do Sistema** .  
  
-   Você deve ser um administrador de modelo. Para obter mais informações, veja [Administradores &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   Uma regra de negócios deve existir. Para obter mais informações, consulte [Criar e publicar uma regra de negócio &#40;Master Data Services&#41;](../master-data-services/create-and-publish-a-business-rule-master-data-services.md).  
  
### Para alterar o nome de uma regra de negócios  
  
1.  No [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], clique em **Administração do Sistema**.  
  
2.  Na barra de menus, aponte para **Gerenciar** e clique em **Regras de Negócios**.  
  
3.  Na página **Regras de Negócio**, na lista suspensa **Modelo**, selecione um modelo.  
  
4.  Na lista suspensa **Entidade**, escolha uma entidade.  
  
5.  Na lista suspensa **Tipos de Membro**, escolha um tipo de membro.  
  
6.  Na grade, selecione a linha da regra de negócio que deseja alterar o nome e clique em **Editar**.  
  
7.  Digite o novo nome para a regra de negócios.  
  
8.  Clique em **Salvar**.  
  
9. Clique em **Publicar Tudo**.  
  
10. Na caixa de diálogo de confirmação, clique em **OK**. O valor da coluna **Estado da Regra de Negócio** é **Ativo**.  
  
## Consulte também  
 [Regras de negócio &#40;Master Data Services&#41;](../master-data-services/business-rules-master-data-services.md)  
  
  