---
title: "Concedendo permissões de banco de dados do processo | Microsoft Docs"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 69ba952e-09ae-49a9-9297-00e32e8e89a8
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c741d808288dbead490c48e569ad55e9b6895d78
ms.contentlocale: pt-br
ms.lasthandoff: 09/01/2017

---
# <a name="lesson-10---granting-process-database-permissions"></a>Lição 10 - concedendo permissões de banco de dados de processo
Depois da instalação de uma instância do [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], todos os membros da função do administrador de servidor do [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] nessa instância têm permissões em todo o servidor para executar qualquer tarefa na instância do [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Por padrão, nenhum outro usuário tem qualquer permissão para administrar ou exibir objetos na instância do [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
Um membro da função de administrador de servidor pode conceder acesso administrativo aos usuários no servidor tornando-os membros da função. Um membro da função de administrador de servidor também pode conceder acesso mais limitado aos usuários. Para isso, ele deve conceder permissões de acesso ou administrativas totais ou limitadas no nível de banco de dados. Permissões administrativas limitadas incluem permissões para processar ou ler definição no nível de banco de dados, cubo ou dimensão.  
  
Nas tarefas deste tópico, você definirá uma função de segurança Processar objetos de banco de dados que concede aos membros dessa função permissão para processar todos os objetos de banco de dados, mas não para exibir dados contidos nesse banco de dados.  
  
## <a name="defining-a-process-database-objects-security-role"></a>Definindo uma função de segurança Processar objetos de banco de dados  
  
1.  No Gerenciador de Soluções, clique com o botão direito do mouse em **Funções** e clique em **Nova Função** para abrir o Designer de Função.  
  
2.  Clique na caixa de seleção **Processar banco de dados** .  
  
3.  Na janela Propriedades, altere a propriedade **Nome** dessa nova função para **Função Processar objetos de banco de dados**.  
  
    ![Designer de função](../analysis-services/media/l10-security-1.png "Designer de função")  
  
4.  Alterne para a guia **Associação** do Designer de Função e clique em **Adicionar**.  
  
5.  Insira as contas dos usuários ou grupos do domínio do Windows que serão membros dessa função. Clique em **Verificar Nomes** para verificar as informações das contas e clique em **OK**.  
  
6.  Alterne para a guia **Cubos** do Designer de Função.  
  
    Observe que os membros dessa função têm permissão para processar este banco de dados, mas não para acessar os dados no cubo do Tutorial do [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] e também não têm acesso ao cubo/detalhamento local, conforme mostrado na imagem a seguir:  
  
    ![Guia cubos do Designer de função](../analysis-services/media/l10-security-2.png "guia cubos do Designer de função")  
  
7.  Alterne para a guia **Dimensões** do Designer de Função.  
  
    Observe que os membros dessa função têm permissões para processar todos os objetos da dimensão neste banco de dados e, por padrão, têm permissão de leitura para acessar cada objeto de dimensão no banco de dados do Tutorial do [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
8.  No menu **Compilar** , clique em **Implantar Tutorial do Analysis Services**.  
  
    Você definiu e implantou com êxito a função de segurança Processar objetos de banco de dados. Depois que o cubo for implantado no ambiente de produção, os administradores desse cubo poderão adicionar usuários a essa função, conforme necessário para delegar responsabilidades de processamento a determinados usuários.  
  
> [!NOTE]  
> Um projeto completo para a Lição 10 pode ser obtido por meio do download e instalação dos exemplos. Para obter mais informações, consulte [Install Sample Data and Projects for the Analysis Services Multidimensional Modeling Tutorial](../analysis-services/install-sample-data-and-projects.md).  
  
## <a name="see-also"></a>Consulte também  
[Funções e permissões &#40;Analysis Services&#41;](../analysis-services/multidimensional-models/roles-and-permissions-analysis-services.md)  
  
  
  
