---
title: sp_addsubscriber_schedule (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_addsubscriber_schedule_TSQL
- sp_addsubscriber_schedule
helpviewer_keywords:
- sp_addsubscriber_schedule
ms.assetid: a6225033-5c3b-452f-ae52-79890a3590ed
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4dd092a18fb8265e6ce8d29fe68d2f3b13445cd0
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="spaddsubscriberschedule-transact-sql"></a>sp_addsubscriber_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ディストリビューション エージェントとマージ エージェントのスケジュールを追加します。 このストアド プロシージャは、任意のデータベース上のパブリッシャー側で実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_addsubscriber_schedule [ @subscriber = ] 'subscriber'  
    [ , [ @agent_type = ] agent_type ]  
    [ , [ @frequency_type = ] frequency_type ]  
    [ , [ @frequency_interval = ] frequency_interval ]  
    [ , [ @frequency_relative_interval = ] frequency_relative_interval ]  
    [ , [ @frequency_recurrence_factor = ] frequency_recurrence_factor ]  
    [ , [ @frequency_subday = ] frequency_subday ]  
    [ , [ @frequency_subday_interval = ] frequency_subday_interval ]  
    [ , [ @active_start_time_of_day = ] active_start_time_of_day ]  
    [ , [ @active_end_time_of_day = ] active_end_time_of_day ]  
    [ , [ @active_start_date = ] active_start_date ]  
    [ , [ @active_end_date = ] active_end_date ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@subscriber =** ] **'***サブスクライバー***'**  
 サブスクライバーの名前です。 *サブスクライバー*は**sysname**です。 サブスクライバーの名前は、データベース内で一意であること、既存の名前でないこと、NULL でないことが必要です。  
  
 [  **@agent_type =** ] *agent_type*  
 エージェントの種類を指定します。 *agent_type*は**smallint**、これらの値のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|**0** (既定値)|ディストリビューション エージェント|  
|**1**|マージ エージェント|  
  
 [  **@frequency_type =** ] *frequency_type*  
 ディストリビューション エージェントをスケジュールに組み込む頻度を指定します。 *frequency_type*は**int**、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|指定日時|  
|**2**|[要求時]|  
|**4**|毎日。|  
|**8**|毎週。|  
|**16**|毎月。|  
|**32**|月単位|  
|**64** (既定値)|自動的に起動|  
|**128**|定期的|  
  
 [  **@frequency_interval =** ] *frequency_interval*  
 設定した頻度に適用する値は、 *frequency_type*です。 *frequency_interval*は**int**、既定値は**1**です。  
  
 [  **@frequency_relative_interval =** ] *frequency_relative_interval*  
 ディストリビューション エージェントを実行する日付です。 このパラメーターが使用されるときに*frequency_type*に設定されている**32** (月単位)。 *frequency_relative_interval*は**int**、これらの値のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|**1** (既定値)|First|  
|**2**|第 2 週|  
|**4**|第 3 週|  
|**8**|第 4 週|  
|**16**|Last|  
  
 [  **@frequency_recurrence_factor =** ] *frequency_recurrence_factor*  
 によって使用される定期実行係数*frequency_type*です。 *frequency_recurrence_factor*は**int**、既定値は**0**します。  
  
 [  **@frequency_subday =** ] *frequency_subday*  
 定義した期間にスケジュールを組み直す頻度を指定します。 *frequency_subday*は**int**、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|1 回。|  
|**2**|第 2 週|  
|**4** (既定値)|Minute|  
|**8**|Hour|  
  
 [  **@frequency_subday_interval =** ] *frequency_subday_interval*  
 間隔は、 *frequency_subday*です。 *frequency_subday_interval*は**int**、既定値は**5**です。  
  
 [  **@active_start_time_of_day =** ] *active_start_time_of_day*  
 ディストリビューション エージェントを最初にスケジュール設定する時刻を HHMMSS 形式で指定します。 *active_start_time_of_day*は**int**、既定値は**0**します。  
  
 [  **@active_end_time_of_day =** ] *active_end_time_of_day*  
 ディストリビューション エージェントのスケジュール設定を停止する時刻を HHMMSS 形式で指定します。 *active_end_time_of_day*は**int**、既定値は 235959、午後 11時 59分: 59 を意味 24 時間制です。  
  
 [ **@active_start_date =** ] *active_start_date*  
 ディストリビューション エージェントを最初にスケジュール設定する日付を YYYYMMDD 形式で指定します。 *active_start_date*は**int**、既定値は**0**します。  
  
 [ **@active_end_date =** ] *active_end_date*  
 ディストリビューション エージェントのスケジュール設定を停止する日付を YYYYMMDD 形式で指定します。 *active_end_date*は**int**99991231、既定値は 9999 年 12 月 31 日です。  
  
 [  **@publisher =** ] **'***パブリッシャー***'**  
 指定以外[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 *パブリッシャー*は**sysname**、既定値は NULL です。  
  
> [!NOTE]  
>  *パブリッシャー*を指定しないで、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_addsubscriber_schedule**はスナップショット レプリケーション、トランザクション レプリケーション、およびマージ レプリケーションで使用します。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_addsubscriber_schedule**です。  
  
## <a name="see-also"></a>参照  
 [sp_changesubscriber_schedule &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changesubscriber-schedule-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
