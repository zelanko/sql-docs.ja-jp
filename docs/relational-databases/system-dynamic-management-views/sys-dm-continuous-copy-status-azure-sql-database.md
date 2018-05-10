---
title: sys.dm_continuous_copy_status (Azure SQL データベース) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/03/2017
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: dmv's
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_continuous_copy_status_TSQL
- dm_continuous_copy_status_TSQL
- dm_continuous_copy_status
- sys.dm_continuous_copy_status
dev_langs:
- TSQL
helpviewer_keywords:
- dm_continuous_copy_status
- sys.dm_continuous_copy_status
ms.assetid: 411b2e71-4421-4ef5-900d-5af068750899
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 03a54b1ebebaaca66628fd7ad9817d90787c45be
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="sysdmcontinuouscopystatus-azure-sql-database"></a>sys.dm_continuous_copy_status (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  現在進行中、Geo レプリケーションの連続コピー リレーションシップで各ユーザー データベース (V11) の行を返します。 複数の連続コピー リレーションシップが指定のプライマリ データベースに対して開始された場合、このテーブルにはアクティブなセカンダリ データベースごとに 1 行のデータが格納されます。  
  
場合の SQL Database V12 を使用している必要がありますを使用する[sys.dm_geo_replication_link_status](../../relational-databases/system-dynamic-management-views/sys-dm-geo-replication-link-status-azure-sql-database.md) (ため*sys.dm_continuous_copy_status* V11 にのみ適用されます)。

  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**copy_guid**|**uniqueidentifier**|レプリカ データベースの一意の ID。|  
|**partner_server**|**sysname**|リンクされた SQL データベース サーバーの名前。|  
|**partner_database**|**sysname**|リンクされた SQL データベース サーバー上にあるリンクされたデータベースの名前。|  
|**last_replication**|**datetimeoffset**|最後に適用したレプリケートされたトランザクションのタイムスタンプ。|  
|**replication_lag_sec**|**int**|アクティブなセカンダリ データベースによって確認されていない、プライマリ データベースで最後に正常にコミットされたトランザクションのタイムスタンプと、現在の時刻との間の時間差 (秒単位)。|  
|**replication_state**|**tinyint**|このデータベースの連続コピー レプリケーションの状態。 使用可能な値とその説明を次に示します。<br /><br /> 1: シード処理します。 レプリケーションの対象がシード中であり、トランザクション的に一貫性のない状態になっています。 シードが完了するまで、アクティブなセカンダリ データベースに接続できません。 <br />2: キャッチします。 現在、アクティブなセカンダリ データベースがプライマリ データベースからの遅れを解消しており、トランザクションの一貫性が確保された状態になっています。<br />3: 再シードされます。 復旧不可能なレプリケーションの障害が原因で、アクティブなセカンダリ データベースが自動的に再シードされている最中です。<br />4: 中断します。 これはアクティブな連続コピー リレーションシップではありません。 通常、この状態は、インターリンクに利用できる帯域幅がプライマリ データベース上のトランザクション アクティビティのレベルに対して不十分であることを示します。 ただし、連続コピー リレーションシップはそのまま保持されます。|  
|**replication_state_desc**|**nvarchar (256)**|replication_state の説明。次のいずれかになります。<br /><br /> SEEDING<br /><br /> CATCH_UP<br /><br /> RE_SEEDING<br /><br /> SUSPENDED|  
|**is_rpo_limit_reached**|**bit**|これは常に 0 に設定します。|  
|**is_target_role**|**bit**|0 = コピー リレーションシップのソース<br /><br /> 1 = コピー リレーションシップの対象|  
|**is_interlink_connected**|**bit**|1 = インターリンクは接続されています。<br /><br /> 0 = インターリンクは接続されていません。|  
  
## <a name="permissions"></a>権限  
 データを取得するメンバーシップが必要、 **db_owner**データベース ロール。 メンバー、dbo ユーザー、 **dbmanager**データベース ロール、および、sa ログインがすべてこのビューをクエリにもします。  
  
## <a name="remarks"></a>解説  
 **Sys.dm_continuous_copy_status**にビューが作成、**リソース**データベースにあり、論理マスターを含む、すべてのデータベースで表示します。 ただし、論理マスターでこのビューに対してクエリを実行すると、空のセットが返されます。  
  
 データベースで、そのデータベース内の行の連続コピー リレーションシップが終了した場合、 **sys.dm_continuous_copy_status**ビューは表示されなくなります。  
  
 同様に、 **sys.dm_database_copies**ビュー、 **sys.dm_continuous_copy_status**データベースのプライマリまたはアクティブなのセカンダリ データベースの連続コピー リレーションシップの状態を反映. 異なり**sys.dm_database_copies**、 **sys.dm_continuous_copy_status**操作やパフォーマンスに関する詳細を提供するいくつかの列が含まれています。 これらの列を含める**last_replication**、および**replication_lag_sec**.  
  
## <a name="see-also"></a>参照  
 [sys.dm_database_copies &#40;Azure SQL データベース&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-database-copies-azure-sql-database.md)   
 [アクティブな Geo レプリケーションのストアド プロシージャ&#40;TRANSACT-SQL&#41;](http://msdn.microsoft.com/library/81658ee4-4422-4d73-bf7a-86a07422cb0d)  
  
  
