---
title: sp_add_jobschedule (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 07/28/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_add_jobschedule
- sp_add_jobschedule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_jobschedule
ms.assetid: ffce19d9-d1d6-45b4-89fd-ad0f60822ba0
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 502b37d8131994e1f6ecc8b65576bc2001870559
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spaddjobschedule-transact-sql"></a>sp_add_jobschedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ジョブのスケジュールを作成します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
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
  
## <a name="arguments"></a>引数  
 [ **@job_id=** ] *job_id*  
 スケジュールを追加するジョブの識別番号を指定します。 *job_id*は**uniqueidentifier**、既定値はありません。  
  
 [ **@job_name=** ] **'***job_name***'**  
 スケジュールを追加するジョブの名前です。 *job_name*は**nvarchar (128)**、既定値はありません。  
  
> [!NOTE]  
>  いずれか*job_id*または*job_name*指定する必要がありますが、両方を指定することはできません。  
  
 [ **@name=** ] **'***name***'**  
 スケジュールの名前。 *名前*は**nvarchar (128)**、既定値はありません。  
  
 [ **@enabled=** ] *enabled_flag*  
 スケジュールの現在の状態を指定します。 *enabled_flag*は**tinyint**、既定値は**1** (有効) です。 場合**0**スケジュールが有効になっていません。 スケジュールが無効な場合は、ジョブは実行されません。  
  
 [ **@freq_type=** ] *frequency_type*  
 いつジョブを実行するかを示す値を指定します。 *frequency_type*は**int**、既定値は**0**値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|1 回。|  
|**4**|毎日。|  
|**8**|毎週。|  
|**16**|毎月。|  
|**32**|毎月、に対して相対的な*frequency_interval です。*|  
|**64**|実行時に、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント サービスを開始します。|  
|**128**|コンピューターがアイドル状態のときに実行します。|  
  
 [ **@freq_interval=** ] *frequency_interval*  
 ジョブを実行する日を指定します。 *frequency_interval*は**int**、既定値は 0 の値に依存して*frequency_type*次の表に記載されています。  
  
|値|結果|  
|-----------|------------|  
|**1** (1 回)|*frequency_interval*は使用されません。|  
|**4** (毎日)|各*frequency_interval*日数。|  
|**8** (毎週)|*frequency_interval*は (OR 論理演算子で結合)、次の 1 つ以上。<br /><br /> 1 = 日曜日<br /><br /> 2 = 月曜日<br /><br /> 4 = 火曜日<br /><br /> 8 = 水曜日<br /><br /> 16 = 木曜日<br /><br /> 32 = 金曜日<br /><br /> 64 = 土曜日|  
|**16** (毎月)|*Frequency_interval*します月の日です。|  
|**32** (月単位)|*frequency_interval*は、次のいずれか。<br /><br /> 1 = 日曜日<br /><br /> 2 = 月曜日<br /><br /> 3 = 火曜日<br /><br /> 4 = 水曜日<br /><br /> 5 = 木曜日<br /><br /> 6 = 金曜日<br /><br /> 7 = 土曜日<br /><br /> 8 = 日<br /><br /> 9 = 平日<br /><br /> 10 = 土日|  
|**64** (ときに、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント サービスを開始)|*frequency_interval*は使用されません。|  
|**128**|*frequency_interval*は使用されません。|  
  
 [ **@freq_subday_type=** ] *frequency_subday_type*  
 単位を指定*frequency_subday_interval*です。 *frequency_subday_type*は**int**, で、既定値はありませんは、次の値のいずれかを指定します。  
  
|値|説明 (単位)|  
|-----------|--------------------------|  
|**0x1**|指定した時間|  
|**0x4**|Minutes|  
|**0x8**|Hours|  
  
 [ **@freq_subday_interval=** ] *frequency_subday_interval*  
 数*frequency_subday_type*ジョブの各実行間に発生する期間。 *frequency_subday_interval*は**int**、既定値は 0 です。  
  
 [ **@freq_relative_interval=** ] *frequency_relative_interval*  
 さらに定義、 *frequency_interval*とき*frequency_type*に設定されている**32** (月単位)。  
  
 *frequency_relative_interval*は**int**, で、既定値はありませんは、次の値のいずれかを指定します。  
  
|値|説明 (単位)|  
|-----------|--------------------------|  
|**1**|First|  
|**2**|第 2 週|  
|**4**|第 3 週|  
|**8**|第 4 週|  
|**16**|Last|  
  
 *frequency_relative_interval*間隔の発生を示します。 たとえば場合、 *frequency_relative_interval*に設定されている**2**、 *frequency_type*に設定されている**32**、および*frequency_間隔*に設定されている**3**、スケジュールされたジョブは毎月の第 2 火曜日で問題が発生します。  
  
 [ **@freq_recurrence_factor=** ] *frequency_recurrence_factor*  
 週間隔または月間隔は、ジョブのスケジュールされた実行の数。 *frequency_recurrence_factor*場合にのみ使用*frequency_type*に設定されている**8**、 **16**、または**32**です。 *frequency_recurrence_factor*は**int**、既定値は 0 です。  
  
 [ **@active_start_date=** ] *active_start_date*  
 どのジョブの実行を開始できる日付。 *active_start_date*は**int**、既定値はありません。 日付は yyyymmdd です。 場合*active_start_date*が設定されている、日付は 19900101 以上する必要があります。  
  
 スケジュールの作成後は、開始日が正しい日付であることを確認するようにしてください。 詳細については、「開始日のスケジュール設定」セクションを参照してください[作成とジョブにスケジュールをアタッチ](http://msdn.microsoft.com/library/079c2984-0052-4a37-a2b8-4ece56e6b6b5)です。  
  
 [ **@active_end_date=** ] *active_end_date*  
 ジョブの実行を停止できる日付を指定します。 *active_end_date*は**int**、既定値はありません。 日付は yyyymmdd です。  
  
 [ **@active_start_time=** ] *active_start_time*  
 間の日で時間*active_start_date*と*active_end_date*ジョブの実行を開始します。 *active_start_time*は**int**、既定値はありません。 時間が 24 時間制で hhmmss 形式で指定として書式設定します。  
  
 [ **@active_end_time=***active_end_time*  
 間の日で時間*active_start_date*と*active_end_date*ジョブの実行を終了します。 *active_end_time*は**int**、既定値はありません。 時間が 24 時間制で hhmmss 形式で指定として書式設定します。  
  
 [ **@schedule_id=***schedule_id***OUTPUT**  
 スケジュールの作成が成功したときにスケジュールに割り当てられるスケジュール ID 番号を指定します。 *schedule_id*型の output 変数は、 **int**、既定値はありません。  
  
 [ **@schedule_uid**= ] *schedule_uid***OUTPUT**  
 スケジュールの一意識別子を指定します。 *schedule_uid*型の変数は、 **uniqueidentifier**です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 ジョブ スケジュールはジョブとは別々に管理できます。 ジョブにスケジュールを追加するには、使用**sp_add_schedule**スケジュールを作成し、 **sp_attach_schedule**ジョブにスケジュールをアタッチします。  
  
## <a name="permissions"></a>権限  
 既定では、このストアド プロシージャを実行できるのは、 **sysadmin** 固定サーバー ロールのメンバーです。 他のユーザーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **データベースの次のいずれかの** エージェント固定データベース ロールが許可されている必要があります。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 これらのロールの権限の詳細については、「 [SQL Server エージェントの固定データベース ロール](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79)」を参照してください。  
 
 ## <a name="example"></a>例
 次の例では、ジョブ スケジュールを`SaturdayReports`毎週土曜日の午前 2 時に実行します。
```sql  
EXEC msdb.dbo.sp_add_jobschedule 
        @job_name = N'SaturdayReports', -- Job name
        @name = N'Weekly_Sat_2AM',  -- Schedule name
        @freq_type = 8, -- Weekly
        @freq_interval = 64, -- Saturday
        @freq_recurrence_factor = 1, -- every week
        @active_start_time = 20000 -- 2:00 AM
```
  
## <a name="see-also"></a>参照  
 [作成し、ジョブにスケジュールをアタッチ](http://msdn.microsoft.com/library/079c2984-0052-4a37-a2b8-4ece56e6b6b5)   
 [ジョブのスケジュール設定します。](http://msdn.microsoft.com/library/f626390a-a3df-4970-b7a7-a0529e4a109c)   
 [スケジュールを作成します。](http://msdn.microsoft.com/library/8c7ef3b3-c06d-4a27-802d-ed329dc86ef3)   
 [SQL Server エージェント ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_add_schedule &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_update_schedule &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-schedule-transact-sql.md)   
 [sp_delete_schedule &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)   
 [sp_help_schedule &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-schedule-transact-sql.md)   
 [sp_attach_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md)  
  
  
