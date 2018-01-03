---
title: "managed_backup.sp_get_backup_diagnostics (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_get_backup_diagnostics_TSQL
- sp_get_backup_diagnostics
- smart_admin.sp_get_backup_diagnostics_TSQL
- smart_admin.sp_get_backup_diagnostics
dev_langs: TSQL
helpviewer_keywords:
- sp_get_backup_diagnostics
- smart_admin.sp_get_backup_diagnostics
ms.assetid: 2266a233-6354-464b-91ec-824ca4eb9ceb
caps.latest.revision: "12"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 282ee88abfd5ba5a040851f036e363d604bc4b6d
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2018
---
# <a name="managedbackupspgetbackupdiagnostics-transact-sql"></a>managed_backup.sp_get_backup_diagnostics (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Smart Admin によってログに記録される拡張イベントを返します。  
  
 このストアド プロシージャを使用してスマート管理者によって記録される拡張イベントを監視するには[!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]イベントは、このシステムに記録されますと確認できるし、このストアド プロシージャを使用して監視します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```sql  
managed_backup.sp_get_backup_diagnostics [@xevent_channel = ] 'event type' [, [@begin_time = ] 'time1' ] [, [@end_time = ] 'time2'VARCHAR(255) = 'Xevent',@begin_time DATETIME = NULL,@end_time DATETIME = NULL  
```  
  
##  <a name="Arguments"></a> 引数  
 @xevent_channel  
 拡張イベントの種類。 既定値は、それまでの 30 分間にログに記録されたすべてのイベントを返すよう設定されています。 ログに記録されるイベントは、有効にした拡張イベントの種類によって異なります。 このパラメーターを使用すると、特定の種類のイベントのみが表示されるようにストアド プロシージャにフィルターを適用できます。 イベントの完全名を指定するかなどの部分文字列を指定することができます: **'Admin'**、 **"Analytic"**、 **'Operational'**、および**'Debug'**. @event_channelは**VARCHAR (255)**です。  
  
 イベントの型が現在有効になって使用の一覧を取得する、 **managed_backup.fn_get_current_xevent_settings**関数。  
  
 [@begin_time  
 イベントが表示対象となる期間の開始時刻。 @begin_timeで、既定値は NULL のパラメーター型は DATETIME です。 これを指定しない場合は、過去 30 分間のイベントが表示されます。  
  
 @end_time  
 イベントが表示対象となる期間の終了時刻。 @end_timeパラメーターでは、DATATIME は、既定値は NULL です。  これを指定しない場合は、現在までのイベントが表示されます。  
  
## <a name="table-returned"></a>返されるテーブル  
 このストアド プロシージャでは、次の情報を含むテーブルが返されます。  
  
||||  
|-|-|-|  
|列名|データ型|Description|  
|event_type|NVARCHAR (512)|拡張イベントの種類|  
|イベント|NVARCHAR (512)|イベント ログの概要|  
|Timestamp|timestamp|イベントの発生時刻を示す、イベントのタイムスタンプ|  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>アクセス許可  
 必要があります**EXECUTE**ストアド プロシージャに対する権限。 必要もあります**VIEW SERVER STATE**内部的に呼び出すための他のシステム オブジェクトをアクセス許可がこのアクセス許可を必要とします。  
  
## <a name="examples"></a>使用例  
 次の例では、過去 30 分間にログに記録されたすべてのイベントが返されます。  
  
```  
Use msdb  
Go  
EXEC managed_backup.sp_get_backup_diagnostics  
  
```  
  
 次の例では、特定の時間範囲にログに記録されたすべてのイベントが返されます。  
  
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
  
  
