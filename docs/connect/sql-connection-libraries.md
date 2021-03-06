---
title: Bibliotecas de Conexão para bancos de dados do Microsoft SQL | Microsoft Docs
description: Fornece links de download para os módulos que permitem a conexão ao Microsoft SQL Server e banco de dados SQL Azure, de uma variedade de linguagens de programação do cliente.
author: MightyPen
ms.service: ''
ms.component: connect
ms.suite: sql
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.technology: dbe-data-tier-apps
ms.custom: ''
ms.workload: data-management
ms.topic: article
ms.date: 08/09/2017
ms.author: genemi
ms.openlocfilehash: 33df5e13dcdeb205a1dbc9fa9c1a5dc7efc754c2
ms.sourcegitcommit: 2e130e9f3ce8a7ffe373d7fba8b09e937c216386
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/28/2018
---
# <a name="connection-modules-for-microsoft-sql-databases"></a>Módulos de Conexão para bancos de dados do Microsoft SQL

Este artigo fornece links de download para os módulos de conexão ou *drivers* que seus programas cliente podem usar para interagir com [Microsoft SQL Server](../index.md)e com seu duas na nuvem [Azure Banco de dados SQL](http://docs.microsoft.com/azure/sql-database/). Drivers estão disponíveis para uma variedade de linguagens de programação, em execução em sistemas operacionais a seguir:

- Linux (Ubuntu)
- MacOS
- Windows


#### <a name="oop-to-relational-mismatch"></a>Incompatibilidade de OOP para relacional

*Relacional*: programas de cliente que são escritos em uma linguagem de (OOP) programação orientada a objeto geralmente usam drivers SQL que retornam dados consultados em um formato que seja mais relacional que orientada a objeto. C# usando o ADO.NET é um exemplo. Incompatibilidade de formato OOP relacional torna, às vezes, o código OOP mais difícil de escrever e entender.

*ORM*: outros drivers ou estruturas retornarem dados consultados no formato do OOP, evitando a incompatibilidade. Esses drivers funcionam esperando classes foram definidas para corresponder às colunas de dados de determinadas tabelas SQL. O driver executa a *mapeamento relacional de objeto* (ORM) para retornar dados consultados como uma instância de uma classe. Entity Framework (EF da Microsoft) para c# e hibernação para Java, são dois exemplos.

O presente artigo dedica seções separadas para esses dois tipos de drivers de conexão.


<a name="anchor-20-drivers-relational-access" />

## <a name="drivers-for-relational-access"></a>Drivers para acesso relacional


<!--
Each given Microsoft Download Center page should be enhanced
with a link to the next NEWER version page, on the day that the
original page is no longer the latest because the newer page is being added.
But this policy is not agreed on or observed,
putting the links in the following table at risk for being outdated.

PHP driver in Github.com also uses this FWLink:  http://go.microsoft.com/fwlink/?LinkID=518036 ,
although the FWLink is less precise than is http://github.com/Microsoft/msphpsql/tree/dev#install-unix .
-->


| Idioma | Baixar o driver do SQL |
| :------- | :---------------------- |
| C#       | [ADO.NET](http://www.microsoft.com/net/download/)<br /><br />[Núcleo do .NET, para Ubuntu Linux](https://www.microsoft.com/net/core#Ubuntu)<br />[Núcleo do .NET, para MacOS](https://www.microsoft.com/net/core#macos)<br />[.NET core para Windows](https://www.microsoft.com/net/core) |
| C++      | [ODBC](http://docs.microsoft.com/sql/connect/odbc/download-odbc-driver-for-sql-server) |
| Java     | [JDBC](http://www.microsoft.com/download/details.aspx?id=55539) |
| Node.js  | [Driver do Node. js, instruções de instalação](http://docs.microsoft.com/sql/connect/node-js/step-1-configure-development-environment-for-node-js-development) |
| PHP      | *Sistema Operacional:*<br /><br />[Driver do PHP do Windows](https://www.microsoft.com/download/details.aspx?id=55642)<br />[Driver do PHP Linux ou macOS do Github](http://github.com/Microsoft/msphpsql/) |
| Python   | [pyodbc, instruções de instalação](http://docs.microsoft.com/sql/connect/python/pyodbc/step-1-configure-development-environment-for-pyodbc-python-development)<br />[Baixe o ODBC](http://docs.microsoft.com/sql/connect/odbc/download-odbc-driver-for-sql-server) |
| Ruby     | [Driver Ruby, instruções de instalação](https://docs.microsoft.com/sql/connect/ruby/step-1-configure-development-environment-for-ruby-development)<br />[Página de download Ruby](https://rubyinstaller.org/downloads/) |
| &nbsp; | <br /> |


<a name="anchor-40-drivers-orm-access" />

## <a name="drivers-for-orm-access"></a>Drivers para acesso ORM


A tabela a seguir lista exemplos de estruturas de mapeamento relacional objeto (ORM) que aplicativos cliente usam para se conectar aos bancos de dados do Microsoft SQL.


| Idioma | Download do driver ORM |
| :------- | :------------------ |
| C# | [Entity Framework Core](http://docs.microsoft.com/ef/core/)<br />[Entity Framework (6. x ou posterior)](http://docs.microsoft.com/ef/) |
| Java | [No modo de hibernação ORM](http://hibernate.org/orm)|
| PHP | [Eloquente ORM, incluído na instalação de Laravel](http://laravel.com/docs/) |
| Node.js | [Sequelize ORM](http://docs.sequelizejs.com) |
| Python | [Django](http://www.djangoproject.com/) |
| Ruby | [Ruby nos trilhos](http://rubyonrails.org/) |
| &nbsp; | <br /> |


<a name="anchor-60-build-an-app-webpages" />

## <a name="build-an-app-webpages"></a>Construir um aplicativo páginas da Web


[http://aka.ms/sqldev](http://aka.ms/sqldev) leva para um conjunto de *construir um aplicativo* páginas da Web. Páginas da Web que fornecem informações sobre várias combinações de programação de idioma, o sistema operacional e o driver de conexão de SQL. Entre as informações fornecidas por páginas da Web para construir um aplicativo são os seguintes itens:

- Detalhes sobre como começar do começo, para cada combinação de idioma, o sistema operacional + o driver.
    - Instruções para instalar os drivers mais recentes de conexão SQL.
- Exemplos de código para cada um dos seguintes itens:
    - Exemplos de código de objeto relacional.
    - Exemplos de código do ORM.
    - Demonstrações do índice ColumnStore para um desempenho muito mais rápido.


#### <a name="first-page-of-build-an-app-webpages"></a>Primeira página das páginas de construir um aplicativo da Web

![Construir um aplicativo páginas da Web, primeiro captura de tela de página][image-ref-163-buildanapp-webpages-first-page]


#### <a name="menu-for-java---ubuntu-of-build-an-app-webpages"></a>Menu de Java - Ubuntu das páginas de construir um aplicativo da Web

![Construir um aplicativo páginas da Web, menu Java Ubuntu][image-ref-167-buildanapp-webpages-menu-java-ubuntu]


&nbsp;


## <a name="related-links"></a>Links relacionados

- [Exemplos para se conectar ao banco de dados SQL Azure na nuvem, com o Java e outras linguagens de código](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-java).


<!-- Image references -->

[image-ref-163-buildanapp-webpages-first-page]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-choose-language-g21.png
[image-ref-167-buildanapp-webpages-menu-java-ubuntu]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-java-ubuntu-c31.png
