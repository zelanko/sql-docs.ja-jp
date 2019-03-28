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
ms.openlocfilehash: 54098c536fa368c4a2b58d387911e646db15a4d4
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58526804"
---
# <a name="spchangesubscriberschedule-transact-sql"></a>sp_changesubscriber_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サブスクライバーのディストリビューション エージェントまたはマージ エージェントのスケジュールを変更します。 このストアド プロシージャは、任意のデータベースのパブリッシャーで実行されます。  
  
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
`[ @subscriber = ] 'subscriber'` サブスクライバーの名前です。 *サブスクライバー*は**sysname**します。 サブスクライバーの名前は、データベース内で一意である必要があります、既に存在する必要がありますしないおよび NULL にすることはできません。  
  
`[ @agent_type = ] type` エージェントの種類です。 *型*は**smallint**、既定値は**0**します。 **0**配布エージェントを示します。 **1**マージ エージェントを示します。  
  
`[ @frequency_type = ] frequency_type` ディストリビューション タスクをスケジュールする頻度です。 *frequency_type*は**int**、既定値は**64**します。 スケジュールの 10 個の列があります。  
  
`[ @frequency_interval = ] frequency_interval` 設定した頻度に適用される値は、 *frequency_type*します。 *frequency_interval*は**int**、既定値は**1**します。  
  
`[ @frequency_relative_interval = ] frequency_relative_interval` ディストリビューション タスクの日です。 *frequency_relative_interval*は**int**、既定値は**1**します。  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor` 使用される定期実行係数*frequency_type*します。 *frequency_recurrence_factor*は**int**、既定値は**0**します。  
  
`[ @frequency_subday = ] frequency_subday` 定義した期間にスケジュールを組み、分単位でどのくらいの頻度です。 *frequency_subday*は**int**、既定値は**4**します。  
  
`[ @frequency_subday_interval = ] frequency_subday_interval` 間隔は、 *frequency_subday*します。 *frequency_subday_interval*は**int**、既定値は**5**します。  
  
`[ @active_start_time_of_day = ] active_start_time_of_day` ディストリビューション タスクは、最初にスケジュールされた日の時間です。 *active_start_time_of_day*は**int**、既定値は**0**します。  
  
`[ @active_end_time_of_day = ] active_end_time_of_day` ディストリビューション タスクのスケジュール設定が停止する日の時間です。 *active_end_time_of_day*は**int**、既定値は**235959**、つまり、午後 11時 59分: 59 午後 11 時 59 分 59 秒を意味します。  
  
`[ @active_start_date = ] active_start_date` ディストリビューション タスクの最初の日付スケジュール設定を yyyymmdd 形式で指定として書式設定されます。 *active_start_date*は**int**、既定値は**0**します。  
  
`[ @active_end_date = ] active_end_date` ディストリビューション タスクを停止した日付スケジュールに yyyymmdd です。 *active_end_date*は**int**、既定値は**99991231**、9999 年 12 月 31 日。  
  
`[ @publisher = ] 'publisher'` 以外を指定[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 *パブリッシャー*は**sysname**、既定値は NULL です。  
  
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
  
  
