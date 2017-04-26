---
title: "Criar uma hierarquia derivada (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "hierarquias derivadas, criando"
  - "criando hierarquias derivadas (Master Data Services)"
ms.assetid: fec653c4-11cc-46a2-8dd8-b605341ebb40
caps.latest.revision: 7
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 7
---
# Criar uma hierarquia derivada (Master Data Services)
  No [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], crie uma hierarquia derivada quando desejar uma hierarquia baseada em nível que assegure que os membros existam no nível correto. As hierarquias derivadas são baseadas em relações de atributos baseados em domínio que existem em um modelo.  
  
> [!NOTE]  
>  Se não existir um valor de atributo baseado em domínio para um membro, o membro não será incluído na hierarquia derivada. Consulte [Exigir valores de atributos &#40;Master Data Services&#41;](../master-data-services/require-attribute-values-master-data-services.md) para exigir um valor de atributo baseado em domínio para todos os membros.  
  
## Pré-requisitos  
 Para executar esse procedimento:  
  
-   Você deve ter permissão para acessar a área funcional **Administração do Sistema** .  
  
-   Você deve ser um administrador de modelo. Para obter mais informações, veja [Administradores &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### Para criar uma hierarquia derivada  
  
1.  No [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], clique em **Administração do Sistema**.  
  
2.  Na barra de menus, aponte para **Gerenciar** e clique em **Hierarquias Derivadas**.  
  
3.  Na página **Manutenção da Hierarquia Derivada** , na lista **Modelo** , selecione um modelo.  
  
4.  Clique em **Adicionar**.  
  
5.  Na página **Adicionar Hierarquia Derivada**, na caixa **Nome da hierarquia derivada**, digite um nome para a hierarquia.  
  
    > [!TIP]  
    >  Use um nome que descreva os níveis na hierarquia, por exemplo, **Produto para Subcategoria para Categoria**.  
  
6.  Clique em **Salvar hierarquia derivada**.  
  
7.  Na página **Editar Hierarquia Derivada**, no painel **Entidades e Hierarquias Disponíveis**, clique em uma entidade ou hierarquia e arraste-a até **Solte o Pai Aqui** no painel **Níveis Atuais**.  
  
8.  Continue a arrastar entidades ou hierarquias até que sua hierarquia esteja completa.  
  
9. Clique em **Voltar**.  
  
## Consulte também  
 [Hierarquias derivadas &#40;Master Data Services&#41;](../master-data-services/derived-hierarchies-master-data-services.md)   
 [Hierarquias derivadas com limites explícitos &#40;Master Data Services&#41;](../master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md)   
 [Atributos baseados em domínio &#40;Master Data Services&#41;](../master-data-services/domain-based-attributes-master-data-services.md)  
  
  