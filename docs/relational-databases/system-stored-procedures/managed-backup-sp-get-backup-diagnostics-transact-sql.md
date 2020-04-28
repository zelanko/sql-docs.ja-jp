---
title: managed_backup。 sp_get_backup_diagnostics (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_get_backup_diagnostics_TSQL
- sp_get_backup_diagnostics
- smart_admin.sp_get_backup_diagnostics_TSQL
- smart_admin.sp_get_backup_diagnostics
dev_langs:
- TSQL
helpviewer_keywords:
- sp_get_backup_diagnostics
- smart_admin.sp_get_backup_diagnostics
ms.assetid: 2266a233-6354-464b-91ec-824ca4eb9ceb
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5e967ae5b46ec703da4e8b1fff64f298fdf8a081
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67942043"
---
# <a name="managed_backupsp_get_backup_diagnostics-transact-sql"></a>managed_backup。 sp_get_backup_diagnostics (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Smart Admin によってログに記録された拡張イベントを返します。  
  
 Smart Admin によってログに記録された拡張イベントを監視するには、このストアドプロシージャを使用します。[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]イベントはこのシステムでログに記録され、このストアドプロシージャを使用して確認および監視できます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```sql  
managed_backup.sp_get_backup_diagnostics [@xevent_channel = ] 'event type' [, [@begin_time = ] 'time1' ] [, [@end_time = ] 'time2'VARCHAR(255) = 'Xevent',@begin_time DATETIME = NULL,@end_time DATETIME = NULL  
```  
  
##  <a name="arguments"></a><a name="Arguments"></a>数値  
 @xevent_channel  
 拡張イベントの種類。 既定値は、それまでの 30 分間にログに記録されたすべてのイベントを返すよう設定されています。 ログに記録されるイベントは、有効になっている拡張イベントの種類によって異なります。 このパラメーターを使用すると、特定の種類のイベントのみが表示されるようにストアド プロシージャにフィルターを適用できます。 完全なイベント名を指定するか、部分文字列 ( **' admin**'、' analytics **'**、 **' Operational '**、 **' Debug '** など) を指定することができます。 @event_channelは**VARCHAR (255)** です。  
  
 現在有効になっているイベントの種類の一覧を取得するには、 **managed_backup. fn_get_current_xevent_settings**関数を使用します。  
  
 [@begin_time  
 イベントが表示対象となる期間の開始時刻。 パラメーター @begin_timeは DATETIME で、既定値は NULL です。 これが指定されていない場合は、過去30分間のイベントが表示されます。  
  
 @end_time  
 イベントが表示対象となる期間の終了時刻。 パラメーター @end_timeは DATATIME で、既定値は NULL です。  これを指定しない場合は、現在までのイベントが表示されます。  
  
## <a name="table-returned"></a>返されるテーブル  
 このストアドプロシージャは、次の情報を含むテーブルを返します。  
  
||||  
|-|-|-|  
|列名|データ型|説明|  
|event_type|NVARCHAR (512)|拡張イベントの種類。|  
|event|NVARCHAR (512)|イベント ログの概要|  
|Timestamp|timestamp|イベントの発生時刻を示す、イベントのタイムスタンプ|  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>アクセス許可  
 ストアドプロシージャに対する**EXECUTE**権限が必要です。 また、この権限を必要とする他のシステムオブジェクトを内部で呼び出すため、 **VIEW SERVER STATE**権限も必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、過去 30 分間にログに記録されたすべてのイベントが返されます。  
  
```  
Use msdb  
Go  
EXEC managed_backup.sp_get_backup_diagnostics  
  
```  
  
 次の例では、特定の時間範囲についてログに記録されたすべてのイベントを返します。  
  
```  
Use msdb  
Go  
EXEC managed_backup.sp_get_backup_diagnostics @xevent_channel = 'Admin',  
  @begin_time = '2013-06-01', @end_time = '2013-06-10'  
  
```  
  
 次の例では、過去 30 分間にログに記録されたすべての分析イベントが返されます。  
  
```  
Use msdb  
Go  
EXEC managed_backup.sp_get_backup_diagnostics @xevent_channel = 'Analytic'  
  
```  
  
  
