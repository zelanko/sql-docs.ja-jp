---
title: sp_changesubscriber_schedule (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changesubscriber_schedule
- sp_changesubscriber_schedule_TSQL
helpviewer_keywords:
- sp_changesubscriber_schedule
ms.assetid: ff84e8e2-d496-482c-b23e-38a6626596e6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 83edeb0c94276e10528b05bc5a1cd8d9474d07aa
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2019
ms.locfileid: "54127912"
---
# <a name="spchangesubscriberschedule-transact-sql"></a>sp_changesubscriber_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サブスクライバーのディストリビューション エージェントまたはマージ エージェントのスケジュールを変更します。 このストアド プロシージャは、任意のデータベース上のパブリッシャー側で実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_changesubscriber_schedule [ @subscriber = ] 'subscriber', [ @agent_type = ] type  
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
 [  **@subscriber=**] **'**_サブスクライバー_**'**  
 サブスクライバーの名前です。 *サブスクライバー*は**sysname**します。 サブスクライバーの名前は、データベース内で一意であること、既存の名前でないこと、NULL でないことが必要です。  
  
 [  **@agent_type=**]*型*  
 エージェントの種類を指定します。 *型*は**smallint**、既定値は**0**します。 **0**配布エージェントを示します。 **1**マージ エージェントを示します。  
  
 [  **@frequency_type=**] *frequency_type*  
 ディストリビューション タスクをスケジュールに組み込む頻度を指定します。 *frequency_type*は**int**、既定値は**64**します。 スケジュール列は 10 列あります。  
  
 [  **@frequency_interval=**] *frequency_interval*  
 設定した頻度に適用される値は、 *frequency_type*します。 *frequency_interval*は**int**、既定値は**1**します。  
  
 [  **@frequency_relative_interval=**] *frequency_relative_interval*  
 ディストリビューション タスクを実施する日を指定します。 *frequency_relative_interval*は**int**、既定値は**1**します。  
  
 [  **@frequency_recurrence_factor=**] *frequency_recurrence_factor*  
 使用される定期実行係数*frequency_type*します。 *frequency_recurrence_factor*は**int**、既定値は**0**します。  
  
 [  **@frequency_subday=**] *frequency_subday*  
 定義した期間にスケジュールを組み直す頻度を分単位で指定します。 *frequency_subday*は**int**、既定値は**4**します。  
  
 [  **@frequency_subday_interval=**] *frequency_subday_interval*  
 間隔は、 *frequency_subday*します。 *frequency_subday_interval*は**int**、既定値は**5**します。  
  
 [  **@active_start_time_of_day=**] *active_start_time_of_day*  
 ディストリビューション タスクを最初にスケジュール設定する時刻を指定します。 *active_start_time_of_day*は**int**、既定値は**0**します。  
  
 [  **@active_end_time_of_day=**] *active_end_time_of_day*  
 ディストリビューション タスクのスケジュール設定を停止する時刻を指定します。 *active_end_time_of_day*は**int**、既定値は**235959**、つまり、午後 11時 59分: 59 午後 11 時 59 分 59 秒を意味します。  
  
 [  **@active_start_date=**] *active_start_date*  
 ディストリビューション タスクを最初にスケジュール設定する日付を YYYYMMDD 形式で指定します。 *active_start_date*は**int**、既定値は**0**します。  
  
 [  **@active_end_date=**] *active_end_date*  
 ディストリビューション タスクのスケジュール設定を停止する日付を YYYYMMDD 形式で指定します。 *active_end_date*は**int**、既定値は**99991231**、9999 年 12 月 31 日。  
  
 [ **@publisher**=] **'**_パブリッシャー_**'**  
 以外を指定[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 *パブリッシャー*は**sysname**、既定値は NULL です。  
  
> [!NOTE]  
>  *パブリッシャー*でアーティクルのプロパティを変更する場合、使用されませんが、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_changesubscriber_schedule**はあらゆる種類のレプリケーションで使用します。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_changesubscriber_schedule**します。  
  
## <a name="see-also"></a>参照  
 [sp_addsubscriber_schedule &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscriber-schedule-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
