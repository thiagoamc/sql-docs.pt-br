---
title: sp_add_jobschedule (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 07/28/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_add_jobschedule
- sp_add_jobschedule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_jobschedule
ms.assetid: ffce19d9-d1d6-45b4-89fd-ad0f60822ba0
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: b2da9a4bf2bc1fb7e2768922b6b5dd4d93452571
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2018
---
# <a name="spaddjobschedule-transact-sql"></a>sp_add_jobschedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Cria uma agenda para um trabalho.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Convenções da sintaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
sp_add_jobschedule [ @job_id = ] job_id, | [ @job_name = ] 'job_name', [ @name = ] 'name'  
     [ , [ @enabled = ] enabled_flag ]  
     [ , [ @freq_type = ] frequency_type ]  
     [ , [ @freq_interval = ] frequency_interval ]  
     [ , [ @freq_subday_type = ] frequency_subday_type ]  
     [ , [ @freq_subday_interval = ] frequency_subday_interval ]  
     [ , [ @freq_relative_interval = ] frequency_relative_interval ]  
     [ , [ @freq_recurrence_factor = ] frequency_recurrence_factor ]  
     [ , [ @active_start_date = ] active_start_date ]  
     [ , [ @active_end_date = ] active_end_date ]  
     [ , [ @active_start_time = ] active_start_time ]  
     [ , [ @active_end_time = ] active_end_time ]  
     [ , [ @schedule_id = ] schedule_id OUTPUT ]  
```  
  
## <a name="arguments"></a>Argumentos  
 [ **@job_id=** ] *job_id*  
 Número de identificação do trabalho para o qual a agenda é adicionada. *job_id* é **uniqueidentifier**, sem padrão.  
  
 [ **@job_name=** ] **'***job_name***'**  
 Nome do trabalho ao qual a agenda é adicionada. *job_name* é **nvarchar (128)**, sem padrão.  
  
> [!NOTE]  
>  O *job_id* ou *job_name* devem ser especificados, mas não é possível especificar ambos.  
  
 [ **@name=** ] **'***name***'**  
 Nome da agenda. *nome* é **nvarchar (128)**, sem padrão.  
  
 [ **@enabled=** ] *enabled_flag*  
 Indica o status atual da agenda. *enabled_flag* é **tinyint**, com um padrão de **1** (habilitado). Se **0**, o agendamento não está habilitado. Se a agenda estiver desabilitada, o trabalho não será executado.  
  
 [ **@freq_type=** ] *frequency_type*  
 Valor que indica quando o trabalho será executado. *frequency_type* é **int**, com um padrão de **0**, e pode ser um dos seguintes valores:  
  
|Value|Descrição|  
|-----------|-----------------|  
|**1**|Uma vez|  
|**4**|Diariamente|  
|**8**|Semanalmente|  
|**16**|Mensalmente|  
|**32**|Mensalmente, relativo a *frequency_interval.*|  
|**64**|Executar ao iniciar o serviço do Agente do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**128**|Executar quando o computador estiver ocioso.|  
  
 [ **@freq_interval=** ] *frequency_interval*  
 Dia em que o trabalho é executado. *frequency_interval* é **int**, com um padrão de 0 e depende do valor de *frequency_type* conforme indicado na tabela a seguir:  
  
|Value|Efeito|  
|-----------|------------|  
|**1** (uma vez)|*frequency_interval* não é usado.|  
|**4** (diariamente)|Cada *frequency_interval* dias.|  
|**8** (semanal)|*frequency_interval* é um ou mais dos seguintes (combinados com um operador lógico OR):<br /><br /> 1 = Domingo<br /><br /> 2 = Segunda-feira<br /><br /> 4 = terça-feira<br /><br /> 8 = quarta-feira<br /><br /> 16 = quinta-feira<br /><br /> 32 = sexta-feira<br /><br /> 64 = sábado|  
|**16** (mensalmente)|Sobre o *frequency_interval* dia do mês.|  
|**32** (mensal relativo)|*frequency_interval* é um dos seguintes:<br /><br /> 1 = Domingo<br /><br /> 2 = Segunda-feira<br /><br /> 3 = Terça-feira<br /><br /> 4 = Quarta-feira<br /><br /> 5 = Quinta-feira<br /><br /> 6 = Sexta-feira<br /><br /> 7 = Sábado<br /><br /> 8 = Dia<br /><br /> 9 = Dia útil<br /><br /> 10 = Dia de fim de semana|  
|**64** (quando o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] início do serviço de agente)|*frequency_interval* não é usado.|  
|**128**|*frequency_interval* não é usado.|  
  
 [ **@freq_subday_type=** ] *frequency_subday_type*  
 Especifica as unidades para *frequency_subday_interval*. *frequency_subday_type* é **int**, sem padrão e pode ser um dos seguintes valores:  
  
|Value|Descrição (unidade)|  
|-----------|--------------------------|  
|**0x1**|Na hora especificada|  
|**0x4**|Minutes (minutos)|  
|**0x8**|Hours (horas)|  
  
 [ **@freq_subday_interval=** ] *frequency_subday_interval*  
 Número de *frequency_subday_type* períodos devem ocorrer entre cada execução do trabalho. *frequency_subday_interval* é **int**, com um padrão de 0.  
  
 [ **@freq_relative_interval=** ] *frequency_relative_interval*  
 Define ainda mais o *frequency_interval* quando *frequency_type* é definido como **32** (mensal relativo).  
  
 *frequency_relative_interval* é **int**, sem padrão e pode ser um dos seguintes valores:  
  
|Value|Descrição (unidade)|  
|-----------|--------------------------|  
|**1**|First|  
|**2**|Segundo|  
|**4**|Terceiro|  
|**8**|Quarto|  
|**16**|Last|  
  
 *frequency_relative_interval* indica a ocorrência do intervalo. Por exemplo, se *frequency_relative_interval* é definido como **2**, *frequency_type* é definido como **32**, e *frequency_ intervalo de* é definido como **3**, o trabalho agendado deve ocorrer na segunda terça-feira de cada mês.  
  
 [ **@freq_recurrence_factor=** ] *frequency_recurrence_factor*  
 Número de semanas ou meses entre execuções agendadas do trabalho. *frequency_recurrence_factor* é usado somente se *frequency_type* é definido como **8**, **16**, ou **32**. *frequency_recurrence_factor* é **int**, com um padrão de 0.  
  
 [ **@active_start_date=** ] *active_start_date*  
 Data na qual a execução do trabalho pode começar. *active_start_date* é **int**, sem padrão. A data é formatada como DDMMAAAA. Se *active_start_date* está definida, a data deve ser maior que ou igual a 19900101.  
  
 Depois que a agenda estiver criada, reveja a data de início e confirme se essa é a data correta. Para obter mais informações, consulte a seção "Agendando datas de início" em [criar e anexar agendamentos a trabalhos](http://msdn.microsoft.com/library/079c2984-0052-4a37-a2b8-4ece56e6b6b5).  
  
 [ **@active_end_date=** ] *active_end_date*  
 Data na qual a execução do trabalho pode parar. *active_end_date* é **int**, sem padrão. A data é formatada como DDMMAAAA.  
  
 [ **@active_start_time=** ] *active_start_time*  
 Hora em qualquer dia entre *active_start_date* e *active_end_date* para começar a execução do trabalho. *active_start_time* é **int**, sem padrão. A hora é formatada como HHMMSS em um relógio de 24 horas.  
  
 [**@active_end_time= * active_end_time*  
 Hora em qualquer dia entre *active_start_date* e *active_end_date* para execução do trabalho final. *active_end_time* é **int**, sem padrão. A hora é formatada como HHMMSS em um relógio de 24 horas.  
  
 [  **@schedule_id=***schedule_id***saída**  
 Número de identificação atribuído à agenda se ela for criada com êxito. *schedule_id* é uma variável de saída do tipo **int**, sem padrão.  
  
 [  **@schedule_uid** =] *schedule_uid * saída**  
 Um identificador exclusivo da agenda. *schedule_uid* é uma variável do tipo **uniqueidentifier**.  
  
## <a name="return-code-values"></a>Valores do código de retorno  
 0 (êxito) ou 1 (falha)  
  
## <a name="result-sets"></a>Conjuntos de resultados  
 Nenhuma  
  
## <a name="remarks"></a>Remarks  
 As agendas de trabalho podem ser gerenciadas independentemente dos trabalhos. Para adicionar uma agenda para um trabalho, use **sp_add_schedule** para criar a agenda e **sp_attach_schedule** para anexar a agenda a um trabalho.  
  
## <a name="permissions"></a>Permissões  
 Por padrão, os membros da função de servidor fixa **sysadmin** podem executar este procedimento armazenado. Deve ser concedida a outros usuários uma das seguintes funções de banco de dados fixas do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent no banco de dados **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Para obter detalhes sobre as permissões dessas funções, consulte [Funções de banco de dados fixas do SQL Server Agent](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
 
 ## <a name="example"></a>Exemplo
 O exemplo a seguir atribui uma agenda de trabalho para `SaturdayReports` que executará todos os sábados às 2:00 AM.
```sql  
EXEC msdb.dbo.sp_add_jobschedule 
        @job_name = N'SaturdayReports', -- Job name
        @name = N'Weekly_Sat_2AM',  -- Schedule name
        @freq_type = 8, -- Weekly
        @freq_interval = 64, -- Saturday
        @freq_recurrence_factor = 1, -- every week
        @active_start_time = 20000 -- 2:00 AM
```
  
## <a name="see-also"></a>Consulte também  
 [Criar e anexar agendas para trabalhos](http://msdn.microsoft.com/library/079c2984-0052-4a37-a2b8-4ece56e6b6b5)   
 [Agendar um trabalho](http://msdn.microsoft.com/library/f626390a-a3df-4970-b7a7-a0529e4a109c)   
 [Criar uma agenda](http://msdn.microsoft.com/library/8c7ef3b3-c06d-4a27-802d-ed329dc86ef3)   
 [Agente do SQL Server armazenados procedimentos &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_update_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-schedule-transact-sql.md)   
 [sp_delete_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)   
 [sp_help_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-schedule-transact-sql.md)   
 [sp_attach_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md)  
  
  
