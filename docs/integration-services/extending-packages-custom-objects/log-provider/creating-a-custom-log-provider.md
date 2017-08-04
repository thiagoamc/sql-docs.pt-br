---
title: Criando um provedor de Log personalizado | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom log providers [Integration Services], creating
ms.assetid: fc20af96-9eb8-4195-8d3f-8a4d7c753f24
caps.latest.revision: 58
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 4e98f1b5a032353c27ffa1438eb7d01bd517892a
ms.contentlocale: pt-br
ms.lasthandoff: 08/03/2017

---
# <a name="creating-a-custom-log-provider"></a>Criando um provedor de log personalizado
  O ambiente de tempo de execução do [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] tem extensas capacidades de log. Um log permite capturar eventos que ocorrem durante a execução de pacotes. O [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] inclui vários provedores de log que permitem a criação e o armazenamento de logs em vários formatos, como XML, texto, banco de dados ou no log de eventos do Windows. Se um desses provedores ou formatos de saída não forem adequados às suas necessidades, você pode criar um provedor de log personalizado.  
  
 As etapas envolvidas na criação de um provedor de log personalizado são semelhantes às etapas de criação de qualquer outro objeto personalizado para o [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]:  
  
-   Crie uma classe nova herdada da classe base. Para um provedor de log, a classe base é <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase>.  
  
-   Aplique o atributo que identifica o tipo de objeto para a classe. Para um provedor de log, o atributo é <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute>.  
  
-   Substitua a implementação de propriedades e métodos da classe base. Para um provedor de log, eles incluem a propriedade <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> e os métodos <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> e <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A>.  
  
-   Interfaces do usuário personalizadas para provedores de log personalizados não são implementadas no [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].  
  
## <a name="getting-started-with-a-custom-log-provider"></a>Guia de Introdução com um provedor de log personalizado  
  
### <a name="creating-projects-and-classes"></a>Criando projetos e classes  
 Como todos os provedores de log gerenciados derivam da classe base <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase>, o primeiro passo para criar um provedor de log personalizado é criar um projeto de biblioteca de classes na linguagem de programação gerenciada de sua preferência e criar uma classe herdada da classe base. Nessa classe derivada, você substituirá os métodos e propriedades da classe base para implementar sua funcionalidade personalizada.  
  
 Configure o projeto para assinar o assembly que será gerado com um arquivo de chave de nome forte.  
  
> [!NOTE]  
>  Muitos [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] provedores de log tem uma interface de usuário personalizada que implementa <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsLogProviderUI> e substitui o **configuração** caixa de texto de **configurar Logs de SSIS** caixa de diálogo com uma lista suspensa filtrada de gerenciadores de conexão disponíveis. Porém, interfaces do usuário personalizadas para provedores de log personalizados não são implementadas no [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].  
  
### <a name="applying-the-dtslogprovider-attribute"></a>Aplicando o atributo DtsLogProvider  
 Aplique o atributo <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> à classe que você criou para identificá-lo como um provedor de log. Esse atributo fornece informações de tempo de design, como o nome e a descrição do provedor de log. O **DisplayName** e **descrição** propriedades do atributo correspondem do **nome** e **descrição** colunas exibidas no **configurar Logs de SSIS** editor, que é exibido ao configurar o log de um pacote de [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].  
  
> [!IMPORTANT]  
>  A propriedade <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute.LogProviderType%2A> do atributo não é usada. Porém, você deve digitar um valor para ela ou o provedor de log personalizado não aparecerá na lista de provedores de log disponíveis.  
  
> [!NOTE]  
>  Como as interfaces do usuário personalizadas para provedores de log personalizados não são implementadas no [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], especificar um valor para a propriedade <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute.UITypeName%2A> do <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> não tem nenhum efeito.  
  
```vb  
<DtsLogProvider(DisplayName:="MyLogProvider", Description:="A simple log provider.", LogProviderType:="Custom")> _  
Public Class MyLogProvider  
     Inherits LogProviderBase  
    ' TODO: Override the base class methods.  
End Class  
```  
  
```csharp  
[DtsLogProvider(DisplayName="MyLogProvider", Description="A simple log provider.", LogProviderType="Custom")]  
public class MyLogProvider : LogProviderBase  
{  
    // TODO: Override the base class methods.  
}  
```  
  
## <a name="building-deploying-and-debugging-a-custom-log-provider"></a>Compilando, implantando e depurando um provedor de log personalizado  
 As etapas para compilar, implantar e depurar um provedor de log personalizado no [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] são muito semelhantes às etapas necessárias para outros tipos de objetos personalizados. Para obter mais informações, consulte [compilando, implantando e Debugging Custom Objects](../../../integration-services/extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md).  
  
## <a name="see-also"></a>Consulte também  
 [Codificando um provedor de Log personalizado](../../../integration-services/extending-packages-custom-objects/log-provider/coding-a-custom-log-provider.md)   
 [Desenvolvendo uma Interface de usuário para um provedor de Log personalizado](../../../integration-services/extending-packages-custom-objects/log-provider/developing-a-user-interface-for-a-custom-log-provider.md)  
  
  