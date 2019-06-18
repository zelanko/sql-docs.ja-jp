---
title: sp_changesubscriber (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changesubscriber
- sp_changesubscriber_TSQL
helpviewer_keywords:
- sp_changesubscriber
ms.assetid: d453c451-e957-490f-b968-5e03aeddaf10
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1f31a00e0c42bc56dffac191ff9a934bb77b95df
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62997801"
---
# <a name="spchangesubscriber-transact-sql"></a>sp_changesubscriber (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サブスクライバーのオプションを変更します。 このパブリッシャーのサブスクライバーに対するディストリビューション タスクはすべて更新されます。 このストアド プロシージャが書き込む、 **MSsubscriber_info**ディストリビューション データベース内のテーブル。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_changesubscriber [ @subscriber= ] 'subscriber'  
    [ , [ @type= ] type ]  
    [ , [ @login= ] 'login' ]  
    [ , [ @password= ] 'password' ]  
    [ , [ @commit_batch_size= ] commit_batch_size ]  
    [ , [ @status_batch_size= ] status_batch_size ]  
    [ , [ @flush_frequency= ] flush_frequency ]  
    [ , [ @frequency_type= ] frequency_type ]  
    [ , [ @frequency_interval= ] frequency_interval ]  
    [ , [ @frequency_relative_interval= ] frequency_relative_interval ]  
    [ , [ @frequency_recurrence_factor= ] frequency_recurrence_factor ]  
    [ , [ @frequency_subday= ] frequency_subday ]  
    [ , [ @frequency_subday_interval= ] frequency_subday_interval ]  
    [ , [ @active_start_time_of_day= ] active_start_time_of_day ]  
    [ , [ @active_end_time_of_day= ] active_end_time_of_day ]  
    [ , [ @active_start_date= ] active_start_date ]  
    [ , [ @active_end_date= ] active_end_date ]  
    [ , [ @description= ] 'description' ]  
    [ , [ @security_mode= ] security_mode ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>引数  
`[ @subscriber = ] 'subscriber'` オプションを変更するサブスクライバーの名前です。 *サブスクライバー*は**sysname**、既定値はありません。  
  
`[ @type = ] type` サブスクライバーの種類です。 *型*は**tinyint**、既定値は NULL です。 **0**を示します、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サブスクライバー。 **1**以外を指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]またはその他の ODBC データ ソース サーバー サブスクライバーです。  
  
`[ @login = ] 'login'` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証ログイン id です。 *login* のデータ型は **sysname** で、既定値は NULL です。  
  
`[ @password = ] 'password'` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証のパスワード。 *パスワード*は**sysname**、既定値は **%** します。 **%** パスワード プロパティに変更がないことを示します。  
  
`[ @commit_batch_size = ] commit_batch_size` 旧バージョンとの互換性を保つのためサポートされています。  
  
`[ @status_batch_size = ] status_batch_size` 旧バージョンとの互換性を保つのためサポートされています。  
  
`[ @flush_frequency = ] flush_frequency` 旧バージョンとの互換性を保つのためサポートされています。  
  
`[ @frequency_type = ] frequency_type` ディストリビューション タスクをスケジュールする頻度です。 *frequency_type*は**int**、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|指定日時|  
|**2**|[要求時]|  
|**4**|毎日。|  
|**8**|毎週。|  
|**16**|毎月。|  
|**32**|月単位|  
|**64**|自動開始|  
|**128**|定期的な|  
  
`[ @frequency_interval = ] frequency_interval` 間隔は、 *frequency_type*します。 *frequency_interval*は**int**、既定値は NULL です。  
  
`[ @frequency_relative_interval = ] frequency_relative_interval` ディストリビューション タスクの日です。 このパラメーターが使用されるときに *frequency_type* に設定されている **32** (月単位)。 *frequency_relative_interval*は**int**、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|First|  
|**2**|第 2 週|  
|**4**|サードパーティ|  
|**8**|4 番目|  
|**16**|Last|  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor` 定義済みの中にディストリビューション タスクを繰り返す頻度*frequency_type*します。 *frequency_recurrence_factor*は**int**、既定値は NULL です。  
  
`[ @frequency_subday = ] frequency_subday` 定義した期間中に再スケジュールするには、多くの場合、方法です。 *frequency_subday*は**int**、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|1 回。|  
|**2**|第 2 週|  
|**4**|Minute|  
|**8**|Hour|  
  
`[ @frequency_subday_interval = ] frequency_subday_interval` 間隔は、 *frequence_subday*します。 *frequency_subday_interval*は**int**、既定値は NULL です。  
  
`[ @active_start_time_of_day = ] active_start_time_of_day` ディストリビューション タスクを最初のスケジュール設定しますする時刻を hhmmss 形式で指定として書式設定。 *active_start_time_of_day* は **int** 、既定値は NULL です。  
  
`[ @active_end_time_of_day = ] active_end_time_of_day` 配布タスクが停止したときの時刻 hhmmss 形式で指定として書式設定、スケジュール設定します。 *active_end_time_of_day*は**int**、既定値は NULL です。  
  
`[ @active_start_date = ] active_start_date` ディストリビューション タスクの最初の日付スケジュール設定を yyyymmdd 形式で指定として書式設定されます。 *active_start_date*は**int**、既定値は NULL です。  
  
`[ @active_end_date = ] active_end_date` ディストリビューション タスクを停止した日付スケジュールに yyyymmdd です。 *active_end_date*は**int**、既定値は NULL です。  
  
`[ @description = ] 'description'` オプションの説明テキストです。 *説明*は**nvarchar (255)** 、既定値は NULL です。  
  
`[ @security_mode = ] security_mode` 実装されているセキュリティ モードです。 *security_mode*は**int**、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**0**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [認証]|  
|**1**|[Windows 認証]|  
  
`[ @publisher = ] 'publisher'` 以外を指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 *パブリッシャー*は**sysname**、既定値は NULL です。  
  
> [!NOTE]  
>  *パブリッシャー*でアーティクルのプロパティを変更する場合、使用されませんが、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_changesubscriber**はあらゆる種類のレプリケーションで使用します。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_changesubscriber**します。  
  
## <a name="see-also"></a>関連項目  
 [sp_addsubscriber &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscriber-transact-sql.md)   
 [sp_dropsubscriber &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscriber-transact-sql.md)   
 [sp_helpdistributiondb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistributiondb-transact-sql.md)   
 [sp_helpserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [sp_helpsubscriberinfo &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
