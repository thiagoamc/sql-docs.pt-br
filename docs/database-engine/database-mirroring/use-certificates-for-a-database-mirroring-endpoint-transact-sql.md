---
title: "Usar certificados para um ponto de extremidade de espelhamento de banco de dados (Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "05/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "espelhamento de banco de dados [SQL Server], implantação"
  - "certificados [SQL Server], espelhamento de banco de dados"
  - "autenticação [SQL Server], espelhamento de banco de dados"
  - "espelhamento de banco de dados [SQL Server], segurança"
ms.assetid: f7c23cc2-48dc-4b78-b441-89ca29a0bd9e
caps.latest.revision: 34
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 34
---
# Usar certificados para um ponto de extremidade de espelhamento de banco de dados (Transact-SQL)
  Para habilitar a autenticação de certificado para espelhamento de banco de dados em uma determinada instância do servidor, o administrador do sistema deve configurar cada instância do servidor para usar certificados nas conexões de saída e de entrada. As conexões de saída devem ser configuradas primeiro.  
  
> [!NOTE]  
>  Todas as conexões de espelhamento em uma instância do servidor usam um único ponto de extremidade de espelhamento do banco de dados e você deve especificar o método de autenticação da instância do servidor quando criar o ponto de extremidade. Portanto, você pode usar somente um formulário de autenticação por instância do servidor para espelhamento de banco de dados.  
  
## Configurando conexões de saída  
 Siga essas etapas em cada instância do servidor que você está configurando para espelhamento de banco de dados:  
  
1.  No banco de dados **mestre**, crie uma chave mestra de banco de dados.  
  
2.  No banco de dados **mestre** , crie um certificado criptografado na instância de servidor.  
  
3.  Crie um ponto de extremidade para a instância do servidor que usa seu certificado.  
  
4.  Faça o backup do certificado em um arquivo e o copie-o com segurança para outro sistema ou sistemas.  
  
 Você deve completar essas etapas para cada parceiro e para a testemunha, se houver.  
  
 Para obter mais informações, consulte [Permitir que um ponto de extremidade de espelhamento de banco de dados use certificados para conexões de saída &#40;Transact-SQL&#41;](../../database-engine/database-mirroring/database mirroring - use certificates for outbound connections.md).  
  
## Configurando conexões de saída  
 A seguir, siga estas etapas para cada parceiro que você está configurando para espelhamento de banco de dados. No banco de dados **mestre**:  
  
1.  Crie um logon para o outro sistema.  
  
2.  Crie um usuário para aquele logon.  
  
3.  Obtenha o certificado para o ponto de extremidade de espelhamento da outra instância do servidor.  
  
4.  Associe o certificado ao usuário criado na etapa 2.  
  
5.  Conceda permissão CONNECT no logon para aquele ponto de extremidade de espelhamento.  
  
 Se houver uma testemunha, deve-se configurar também conexões de entrada para ela. Isso requer configuração de logons, usuários e certificados para a testemunha nos dois parceiros, e vice-versa.  
  
 Para obter mais informações, consulte [Permitir que um ponto de extremidade de espelhamento de banco de dados use certificados para conexões de entrada &#40;Transact-SQL&#41;](../../database-engine/database-mirroring/database mirroring - use certificates for inbound connections.md).  
  
## Segurança  
 A menos que você possa garantir que sua rede está segura, recomendamos o uso de criptografia para conexões de espelhamento de banco de dados. Para obter mais informações, consulte [O ponto de extremidade de espelhamento de banco de dados &#40;SQL Server&#41;](../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md).  
  
 Ao copiar um certificado para outro sistema, use um método de cópia seguro. Seja extremamente cauteloso para manter todos os seus certificados em segurança.  
  
## Consulte também  
 [Criar uma chave mestra de banco de dados](../../relational-databases/security/encryption/create-a-database-master-key.md)   
 [CREATE MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-master-key-transact-sql.md)   
 [Segurança de transporte para espelhamento de banco de dados e grupos de disponibilidade AlwaysOn &#40;SQL Server&#41;](../../database-engine/database-mirroring/transport security - database mirroring - always on availability.md)   
 [Central de segurança do Mecanismo de Banco de Dados do SQL Server e Banco de Dados SQL do Azure](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)   
 [O ponto de extremidade de espelhamento de banco de dados &#40;SQL Server&#41;](../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md)  
  
  