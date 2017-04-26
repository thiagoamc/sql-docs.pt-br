---
title: "Alterar o separador de palavras usado para ingl&#234;s dos EUA e ingl&#234;s do Reino Unido | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-search"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6b5d2177-db98-47f5-b32e-4b80a2f74ffe
caps.latest.revision: 10
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 10
---
# Alterar o separador de palavras usado para ingl&#234;s dos EUA e ingl&#234;s do Reino Unido
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] instala uma nova versão (versão 14.0.4999.1038) do separador de palavras e lematizador para o idioma inglês, substituindo a versão anterior desses componentes (versão 12.0.6828.0). Para obter informações sobre o comportamento alterado dos novos componentes, veja [Alterações de comportamento na pesquisa de texto completo](../Topic/Behavior%20Changes%20to%20Full-Text%20Search.md). Este tópico descreve como alternar da nova versão desses componentes para a versão anterior, ou alternar da versão anterior para a nova versão. Para instalações em cluster, essas alterações devem ser feitas em todos os nós primários e passivos.  
  
 As versões anteriores do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usavam separadores de palavras diferentes representados por CLSIDs distintos para o inglês dos EUA (LCID 1033) e o inglês do Reino Unido (LCID 2057). Nesta versão, ambos o LCIDs usam os mesmos componentes com os mesmos CLSIDs, como é mostrado na seguinte tabela:  
  
|LCID|Separador de palavras instalado por versões anteriores<br /><br /> versão 12.0.6828.0|Lematizador instalado por versões anteriores|Separador de palavras instalado por esta versão<br /><br /> versão 14.0.4999.1038|Lematizador instalado por esta versão|  
|----------|-------------------------------------------------------------------------|--------------------------------------------|-----------------------------------------------------------------------|---------------------------------------|  
|1046<br />(inglês - EUA)|188D6CC5-CB03-4C01-912E-47D21295D77E|EEED4C20-7F1B-11CE-BE57-00AA0051FE20|9faed859-0b30-4434-ae65-412e14a16fb8|e1e5ef84-c4a6-4e50-8188-99aef3de2659|  
|2057<br />(inglês - Reino Unido)|173C97E2-AEBE-437C-9445-01B237ABF2F6|D99F7670-7F1A-11CE-BE57-00AA0051FE20|9faed859-0b30-4434-ae65-412e14a16fb8|e1e5ef84-c4a6-4e50-8188-99aef3de2659|  
  
 Os componentes descritos neste tópico são arquivos DLL instalados na pasta `MSSQL\Binn` para a instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . O caminho completo geralmente é `C:\Program Files\Microsoft SQL Server\<instance>\MSSQL\Binn`.  
  
 Para obter mais informações sobre separadores de palavras e lematizadores, veja [Configurar e gerenciar separadores de palavras e lematizadores para pesquisa](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md).  
  
## Alternando do separador de palavras em inglês atual para os separadores de palavras em inglês anteriores  
  
#### Para alternar da versão atual do separador de palavras em inglês dos EUA para a versão anterior  
  
1.  No Registro, navegue até o nó: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\CLSID**.  
  
2.  Use as etapas a seguir para adicionar novas chaves para as ClassIDs COM para o separador de palavras em inglês dos EUA anterior e interfaces de lematizador para LCID 1033:  
  
    1.  Adicione uma nova chave com o valor **{188D6CC5-CB03-4C01-912E-47D21295D77E}** ao separador de palavras anterior.  
  
    2.  Atualize os dados (Padrão) desse valor de chave para **langwrbk.dll**.  
  
    3.  Adicione uma nova chave com o valor **{EEED4C20-7F1B-11CE-BE57-00AA0051FE20}** ao lematizador anterior.  
  
    4.  Atualize os dados (Padrão) desse valor de chave para **infosoft.dll**.  
  
3.  No Registro, navegue até o seguinte nó: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\Language\enu**.  
  
4.  Atualize o valor de chave **WBreakerClass** para **{188D6CC5-CB03-4C01-912E-47D21295D77E}**.  
  
5.  Atualize o valor de chave **StemmerClass** para **{EEED4C20-7F1B-11CE-BE57-00AA0051FE20}**.  
  
6.  Reinicie o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
#### Para alternar da versão atual do separador de palavras em inglês do Reino Unido para a versão anterior  
  
1.  No Registro, navegue até o nó: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\CLSID**.  
  
2.  Use as etapas a seguir para adicionar uma nova chave para as ClassIDs COM para o separador de palavras em inglês do Reino Unido anterior e interfaces de lematizador para LCID 2057:  
  
    1.  Adicione uma nova chave com o valor **{173C97E2-AEBE-437C-9445-01B237ABF2F6}** ao separador de palavras anterior.  
  
    2.  Atualize os dados (Padrão) desse valor de chave para **langwrbk.dll**.  
  
    3.  Adicione uma nova chave com o valor **{D99F7670-7F1A-11CE-BE57-00AA0051FE20}** ao lematizador anterior.  
  
    4.  Atualize os dados (Padrão) desse valor de chave para **infosoft.dll**.  
  
3.  No Registro, navegue até o seguinte nó: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\Language\eng**.  
  
4.  Atualize o valor de chave **WBreakerClass** para **{173C97E2-AEBE-437C-9445-01B237ABF2F6}**.  
  
5.  Atualize o valor de chave **StemmerClass** para **{D99F7670-7F1A-11CE-BE57-00AA0051FE20}**.  
  
6.  Reinicie o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## Alternando de separadores de palavras em inglês dos EUA anteriores para o separador de palavras em inglês atual  
  
#### Para alternar da versão anterior do separador de palavras em inglês dos EUA para a versão atual  
  
1.  No Registro, navegue até o nó: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\CLSID**.  
  
2.  Se as chaves a seguir não existirem, use as etapas a seguir para adicionar uma nova chave para as ClassIDs COM para o separador de palavras em inglês dos EUA atual e interfaces de lematizador para LCID 1033:  
  
    1.  Adicione uma nova chave com o valor **{9faed859-0b30-4434-ae65-412e14a16fb8}** para o separador de palavras atual.  
  
    2.  Atualize os dados (Padrão) desse valor de chave para **MsWb7.dll**.  
  
    3.  Adicione uma nova chave com o valor **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}** para o lematizador atual.  
  
    4.  Atualize os dados (Padrão) desse valor de chave para **MsWb7.dll**.  
  
3.  No Registro, navegue até o seguinte nó: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\Language\eng**.  
  
4.  Atualize o valor de chave **WBreakerClass** para **{9faed859-0b30-4434-ae65-412e14a16fb8}**.  
  
5.  Atualize o valor de chave **StemmerClass** para **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}**.  
  
6.  Reinicie o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
#### Para alternar da versão anterior do separador de palavras em inglês do Reino Unido para a versão atual  
  
1.  No Registro, navegue até o nó: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\CLSID**.  
  
2.  Se as chaves a seguir não existirem, use as etapas a seguir para adicionar uma nova chave para as ClassIDs COM para o separador de palavras em inglês do Reino Unido atual e interfaces de lematizador para LCID 2057:  
  
    1.  Adicione uma nova chave com o valor **{9faed859-0b30-4434-ae65-412e14a16fb8}** para o separador de palavras atual.  
  
    2.  Atualize os dados (Padrão) desse valor de chave para **MsWb7.dll**.  
  
    3.  Adicione uma nova chave com o valor **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}** para o lematizador atual.  
  
    4.  Atualize os dados (Padrão) desse valor de chave para **MsWb7.dll**.  
  
3.  No Registro, navegue até o seguinte nó: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\Language\eng**.  
  
4.  Atualize o valor de chave **WBreakerClass** para **{9faed859-0b30-4434-ae65-412e14a16fb8}**.  
  
5.  Atualize o valor de chave **StemmerClass** para **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}**.  
  
6.  Reinicie o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## Consulte também  
 [Reverter os separadores de palavras usados por pesquisa à versão anterior](../../relational-databases/search/revert-the-word-breakers-used-by-search-to-the-previous-version.md)   
 [Alterações de comportamento em pesquisa de texto completo](../Topic/Behavior%20Changes%20to%20Full-Text%20Search.md)  
  
  