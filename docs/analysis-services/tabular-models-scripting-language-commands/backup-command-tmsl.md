---
title: Fazer backup de comando (TMSL) | Microsoft Docs
ms.custom: 
ms.date: 05/30/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: fae1b267-0750-4dc5-9bf0-80ac4d8487a3
caps.latest.revision: "9"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 50e6f8e6f5b01fce2eb0bb6a5dbcd84dd631d994
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2018
---
# <a name="backup-command-tmsl"></a>Comando de backup (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]Faz backup de um banco de dados do Analysis Services em um arquivo de backup. abf.  
  
## <a name="request"></a>Solicitação  
  
```  
    {  
        "backup": {  
            "description": "Parameters of Backup command of Analysis Services JSON API",  
            "properties": {  
            "database": {  
                "type": "string"  
            },  
            "file": {  
                "type": "string"  
            },  
            "password": {  
                "type": "string"  
            },  
            "allowOverwrite": {  
                "type": "boolean"  
            },  
            "applyCompression": {  
                "type": "boolean"  
            }  
            },  
. . .   
```  
  
 **Backup** tem várias propriedades.  
  
||||  
|-|-|-|  
|**Propriedade**|**Default**|**Descrição**|  
|Banco de Dados|[Obrigatório]|O nome do objeto de banco de dados de backup.|  
|file|[Obrigatório]|O nome do arquivo de backup/caminho.|  
|password|Empty (vazio)|A senha a ser usada para criptografar o arquivo de backup.|  
|allowOverwrite|Falso|Um booliano que, quando for verdadeiro, indica que um arquivo de backup já existente será substituído; Caso contrário, false.|  
|applyCompression|True|Um booliano que, quando for verdadeiro, indica que os arquivos de backup são compactados. Caso contrário, false.|  
  
## <a name="response"></a>Resposta  
 Retorna um resultado vazio quando o comando terá êxito. Caso contrário, uma exceção XMLA é retornada.  
  
## <a name="examples"></a>Exemplos  
 **Exemplo 1** -fazer Backup de um arquivo para a pasta de backup padrão.  
  
```  
{   
   "backup": {   
      "database":"AS_AdventureWorksDW2014",  
      "file":"AS_AdventureWorksDW2014.abf",  
      "password":"secret"  
   }  
}  
```  
  
## <a name="usage-endpoints"></a>Uso (pontos de extremidade)  
 Esse elemento de comando é usado em uma instrução do [executar método &#40; XMLA &#41; ](../../analysis-services/xmla/xml-elements-methods-execute.md) chamada por um ponto de extremidade do XMLA, exposto das seguintes maneiras:  
  
-   Como uma janela de XMLA no SQL Server Management Studio (SSMS)  
  
-   Como um arquivo de entrada para o **invoke-ascmd** cmdlet do PowerShell  
  
-   Como uma entrada para um trabalho do SQL Server Agent ou uma tarefa do SSIS  
  
 Você pode gerar um script pronto para este comando do SSMS, clique no botão de Script na caixa de diálogo banco de dados de Backup.  
  
 O [ \[MS-SSAS-T\]: SQL Server Analysis Services Tabular (protocolo técnicos do SQL Server)](http://go.microsoft.com/fwlink/p/?LinkId=784855) documento inclui seção 3.1.5.2.2 que descreve a estrutura de objetos e comandos de metadados de tabela do JSON. Atualmente, esse documento aborda recursos ainda não implementados no script TMSL e comandos. Consulte o tópico [linguagem de script de modelo de tabela &#40; TMSL &#41; Referência](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md) para fins de esclarecimento sobre o que tem suporte  

## <a name="see-also"></a>Consulte Também  
 [Referência de TMSL &#40;Linguagem de Scripts de Modelo de Tabela&#41;](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Backup e restauração de bancos de dados do Analysis Services](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
