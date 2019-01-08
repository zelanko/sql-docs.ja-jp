---
title: sp_helpsubscriberinfo (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpsubscriberinfo
- sp_helpsubscriberinfo_TSQL
helpviewer_keywords:
- sp_helpsubscriberinfo
ms.assetid: fbabe1ec-57cf-425c-bae7-af7f5d3198fd
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 14ab67bb9d69272960bbce3e1a7cfa059c609e3f
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/18/2018
ms.locfileid: "53589806"
---
# <a name="sphelpsubscriberinfo-transact-sql"></a>sp_helpsubscriberinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サブスクライバーに関する情報を表示します。 このストアド プロシージャは、任意のデータベース上のパブリッシャー側で実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helpsubscriberinfo [ [ @subscriber =] 'subscriber']  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@subscriber =** ] **'**_サブスクライバー_**'**  
 サブスクライバーの名前です。 *サブスクライバー*は**sysname**、既定値は**%**、すべての情報が返されます。  
  
 [  **@publisher =** ] **'**_パブリッシャー_**'**  
 パブリッシャーの名前です。 *パブリッシャー*は**sysname**、および既定値は、現在のサーバーの名前。  
  
> [!NOTE]  
>  *パブリッシャー* Oracle パブリッシャーの場合を除き、指定するされません。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**パブリッシャー**|**sysname**|パブリッシャーの名前。|  
|**サブスクライバー**|**sysname**|サブスクライバーの名前です。|  
|**type**|**tinyint**|サブスクライバーの種類。<br /><br /> **0**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース**1** = ODBC データ ソース|  
|**login**|**sysname**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証のログイン ID。|  
|**password**|**sysname**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証のパスワード。|  
|**commit_batch_size**|**int**|サポートされていません。|  
|**status_batch_size**|**int**|サポートされていません。|  
|**flush_frequency**|**int**|サポートされていません。|  
|**frequency_type**|**int**|ディストリビューション エージェントを実行する頻度。<br /><br /> **1** = 1 回<br /><br /> **2** = 要求時<br /><br /> **4** = 毎日<br /><br /> **8** = 毎週<br /><br /> **16**毎月を =<br /><br /> **32** = 月単位<br /><br /> **64** = 自動開始<br /><br /> **128** = 定期的|  
|**frequency_interval**|**int**|設定した頻度に適用される値*frequency_type*します。|  
|**frequency_relative_interval**|**int**|ディストリビューション エージェントの日で使用されるときに*frequency_type*に設定されている**32** (月単位)。<br /><br /> **1**最初を =<br /><br /> **2**秒を =<br /><br /> **4** = サード<br /><br /> **8**第 4 を =<br /><br /> **16**最後を =|  
|**frequency_recurrence_factor**|**int**|使用される定期実行係数*frequency_type*します。|  
|**frequency_subday**|**int**|定義した期間にスケジュールを組み直す頻度。<br /><br /> **1** = 1 回<br /><br /> **2**秒を =<br /><br /> **4**分を =<br /><br /> **8**時間を =|  
|**frequency_subday_interval**|**int**|間隔*frequency_subday*します。|  
|**active_start_time_of_day**|**int**|ディストリビューション エージェントを最初にスケジュールに組み込んだ時刻。形式は HHMMSS です。|  
|**active_end_time_of_day**|**int**|ディストリビューション エージェントのスケジュールへの組み込みを停止した時刻。形式は HHMMSS です。|  
|**active_start_date**|**int**|ディストリビューション エージェントを最初にスケジュールに組み込んだ日付。形式は YYYYMMDD です。|  
|**active_end_date**|**int**|ディストリビューション エージェントのスケジュールへの組み込みを停止した日付。形式は YYYYMMDD です。|  
|**retryattempt**|**int**|サポートされていません。|  
|**retrydelay**|**int**|サポートされていません。|  
|**description**|**nvarchar (255)**|サブスクライバーのテキストによる説明。|  
|**security_mode**|**int**|実装されているセキュリティ モード。<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証<br /><br /> **1**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 認証|  
|**frequency_type2**|**int**|マージ エージェントを実行する頻度。<br /><br /> **1** = 1 回<br /><br /> **2** = 要求時<br /><br /> **4** = 毎日<br /><br /> **8** = 毎週<br /><br /> **16**毎月を =<br /><br /> **32** = 月単位<br /><br /> **64** = 自動開始<br /><br /> **128** = 定期的|  
|**frequency_interval2**|**int**|設定した頻度に適用される値*frequency_type*します。|  
|**frequency_relative_interval2**|**int**|マージ エージェントの日付が使用されるときに*frequency_type* 32 (月単位) に設定されます。<br /><br /> **1**最初を =<br /><br /> **2**秒を =<br /><br /> **4** = サード<br /><br /> **8**第 4 を =<br /><br /> **16**最後を =|  
|**frequency_recurrence_factor2**|**int**|使用される定期実行係数*frequency_type * *。*|  
|**frequency_subday2**|**int**|定義した期間にスケジュールを組み直す頻度。<br /><br /> **1** = 1 回<br /><br /> **2**秒を =<br /><br /> **4**分を =<br /><br /> **8**時間を =|  
|**frequency_subday_interval2**|**int**|間隔*frequency_subday*します。|  
|**active_start_time_of_day2**|**int**|マージ エージェントを最初にスケジュールに組み込んだ時刻。形式は HHMMSS です。|  
|**active_end_time_of_day2**|**int**|マージ エージェントのスケジュールへの組み込みを停止した時刻。形式は HHMMSS です。|  
|**active_start_date2**|**int**|マージ エージェントを最初にスケジュールに組み込んだ日付。形式は YYYYMMDD です。|  
|**active_end_date2**|**int**|マージ エージェントのスケジュールへの組み込みを停止した日付。形式は YYYYMMDD です。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_helpsubscriberinfo**はスナップショット レプリケーション、トランザクション レプリケーション、およびマージ レプリケーションで使用します。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロール、 **db_owner**固定データベース ロール、またはパブリケーションのパブリケーション アクセス リストが実行できる**sp_helpsubscriberinfo**.  
  
## <a name="see-also"></a>参照  
 [sp_adddistpublisher &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_addpullsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md)   
 [sp_changesubscriber &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changesubscriber-transact-sql.md)   
 [sp_dropsubscriber &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscriber-transact-sql.md)   
 [sp_helpdistributor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql.md)   
 [sp_helpserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
