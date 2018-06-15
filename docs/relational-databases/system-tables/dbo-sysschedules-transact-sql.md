---
title: dbo.sysschedules (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dbo.sysschedules_TSQL
- sysschedules
- sysschedules_TSQL
- dbo.sysschedules
dev_langs:
- TSQL
helpviewer_keywords:
- sysschedules system table
ms.assetid: 4cac9237-7a69-4035-bb3e-928b76aad698
caps.latest.revision: 17
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 877abbc8fb58fbb3a824bb711e0adbb13618f453
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33262838"
---
# <a name="dbosysschedules-transact-sql"></a>dbo.sysschedules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのジョブ スケジュールに関する情報を格納します。 次の表は、 **msdb**データベース。  
  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**schedule_id**|**int**|ID、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント ジョブのスケジュール。|  
|**schedule_uid**|**uniqueidentifier**|ジョブ スケジュールの一意識別子。 この値は分散ジョブのスケジュールを識別するために使用されます。|  
|**originating_server_id**|**int**|ジョブ スケジュールを取得したマスター サーバーの ID。|  
|**name**|**sysname (nvarchar(128))**|ジョブ スケジュールのユーザー定義名。 名前はジョブ内で一意であることが必要です。|  
|**owner_sid**|**varbinary(85)**|Microsoft Windows *security_identifier*ユーザーまたはグループをジョブのスケジュールを所有するのです。|  
|**enabled**|**int**|ジョブ スケジュールのステータス。<br /><br /> **0** = 無効。<br /><br /> **1** = 有効にします。<br /><br /> スケジュールが無効な場合、そのスケジュールでジョブは実行されません。|  
|**freq_type**|**int**|このスケジュールでジョブを実行する間隔。<br /><br /> **1** 1 回だけを =<br /><br /> **4** = 毎日<br /><br /> **8** = 毎週<br /><br /> **16**毎月を =<br /><br /> **32**を基準とする、毎月を = **freq_interval**<br /><br /> **64** = SQL Server エージェント サービスが開始されるときに実行<br /><br /> **128** = コンピューターがアイドル状態のときに実行|  
|**freq_interval**|**int**|ジョブを実行する日数。 値に依存**freq_type**です。 既定値は**0**、ことを示します**freq_interval**は使用されません。 使用可能な値とその効果は、次の表を参照してください。|  
|**freq_subday_type**|**int**|単位、 **freq_subday_interval**です。 使用可能な値とその説明を次に示します。<br /><br /> <br /><br /> **1** : 指定された時刻<br /><br /> **2** : (秒)<br /><br /> **4** : 分<br /><br /> **8** : 時間|  
|**freq_subday_interval**|**int**|数**freq_subday_type**ジョブの各実行間に発生する期間。|  
|**freq_relative_interval**|**int**|ときに**freq_interval**場合は、各月**freq_interval**は**32** (月単位)。 次の値のいずれかです。<br /><br /> **0** = **freq_relative_interval**は使用されません<br /><br /> **1**最初を =<br /><br /> **2**秒を =<br /><br /> **4**サードパーティを =<br /><br /> **8**第 4 を =<br /><br /> **16**最後を =|  
|**freq_recurrence_**<br /><br /> **factor**|**int**|週または月を単位とした、ジョブの予定実行間隔。 **freq_recurrence_factor**場合にのみ使用**freq_type**は**8**、 **16**、または**32**です。 この列が含まれている場合**0**、 **freq_recurrence_factor**は使用されません。|  
|**active_start_date**|**int**|ジョブの実行を開始できる日付。 日付は yyyymmdd です。 NULL は今日の日付を表します。|  
|**active_end_date**|**int**|ジョブの実行を停止できる日付。 日付の形式は YYYYMMDD です。|  
|**active_start_time**|**int**|間の日で時間**active_start_date**と**active_end_date**そのジョブが実行を開始します。 時刻の形式は HHMMSS で、24 時間形式です。|  
|**active_end_time**|**int**|間の日で時間**active_start_date**と**active_end_date**そのジョブの実行は停止します。 時刻の形式は HHMMSS で、24 時間形式です。|  
|**date_created**|**datetime**|スケジュールを作成した日付と時刻。|  
|**date_modified**|**datetime**|スケジュールを最後に変更した日付と時刻。|  
|**version_number**|**int**|スケジュールの現在のバージョン番号。 たとえば、スケジュールが 10 回変更された場合、 **version_number** 10 です。|  
  
|freq_type の値|freq_interval への影響|  
|-------------------------|------------------------------|  
|**1** (1 回)|**freq_interval**は使用されません (**0**)|  
|**4** (毎日)|各**freq_interval**日数|  
|**8** (毎週)|**freq_interval**は、次の 1 つ以上。<br /><br /> **1**日曜日を =<br /><br /> **2**月曜日を =<br /><br /> **4** = 火曜日<br /><br /> **8** = 水曜日<br /><br /> **16** = 木曜日<br /><br /> **32** = 金曜日<br /><br /> **64** = 土曜日|  
|**16** (毎月)|**Freq_interval**します月の日|  
|**32** (月単位、相対パス)|**freq_interval**は、次のいずれか。<br /><br /> **1**日曜日を =<br /><br /> **2**月曜日を =<br /><br /> **3** = 火曜日<br /><br /> **4** = 水曜日<br /><br /> **5** = 木曜日<br /><br /> **6** = 金曜日<br /><br /> **7** = 土曜日<br /><br /> **8** = 日<br /><br /> **9** = 平日<br /><br /> **10** = 土日|  
|**64** (SQL Server エージェント サービスの起動時に開始されます)|**freq_interval**は使用されません (**0**)|  
|**128** (コンピューターがアイドル状態のときに実行されます)|**freq_interval**は使用されません (**0**)|  
  
## <a name="see-also"></a>参照  
 [では & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/dbo-sysjobschedules-transact-sql.md)  
  
  
