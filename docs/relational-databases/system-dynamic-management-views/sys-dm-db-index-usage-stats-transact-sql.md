---
title: dm_db_index_usage_stats (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_db_index_usage_stats_TSQL
- sys.dm_db_index_usage_stats
- sys.dm_db_index_usage_stats_TSQL
- dm_db_index_usage_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_index_usage_stats dynamic management view
ms.assetid: d06a001f-0f72-4679-bc2f-66fff7958b86
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 491ec37d96cf6bdb2b074efb42a54406beb1fd20
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68264402"
---
# <a name="sysdm_db_index_usage_stats-transact-sql"></a>dm_db_index_usage_stats (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  さまざまな種類のインデックス操作の数と、各種の操作が前回実行された時刻を返します。  
  
 
  [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] では、動的管理ビューは、データベースの包含に影響する情報を公開することも、ユーザーがアクセスできる他のデータベースに関する情報を公開することもできません。 この情報を公開しないように、接続されたテナントに属していないデータを含むすべての行がフィルターで除外されます。  
  
> [!NOTE]  
>  **dm_db_index_usage_stats**は、メモリ最適化インデックスに関する情報を返しません。 メモリ最適化インデックスの使用の詳細については、「 [dm_db_xtp_index_stats &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-index-stats-transact-sql.md)」を参照してください。  
  
> [!NOTE]  
>  またはから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]このビューを[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]呼び出すには、 **dm_pdw_nodes_db_index_usage_stats**を使用します。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**database_id**|**smallint**|テーブルまたはビューが定義されているデータベースの ID。|  
|**object_id**|**int**|インデックスが定義されているテーブルまたはビューの ID。|  
|**index_id**|**int**|インデックスの ID。|  
|**user_seeks**|**bigint**|ユーザー クエリによるシーク数。|  
|**user_scans**|**bigint**|' Seek ' 述語を使用していないユーザークエリによるスキャン数。|  
|**user_lookups**|**bigint**|ユーザー クエリによるブックマーク参照数。|  
|**user_updates**|**bigint**|ユーザー クエリによる更新数。 これには、影響を受けた実際の行ではなく、実行された操作の数を表す挿入、削除、および更新が含まれます。 たとえば、1つのステートメントで1000行を削除した場合、このカウントは1ずつ増加します。|  
|**last_user_seek**|**DATETIME**|前回のユーザー シークの時刻。|  
|**last_user_scan**|**DATETIME**|前回のユーザー スキャンの時刻。|  
|**last_user_lookup**|**DATETIME**|前回のユーザー参照の時刻。|  
|**last_user_update**|**DATETIME**|前回のユーザー更新の時刻。|  
|**system_seeks**|**bigint**|システム クエリによるシーク数。|  
|**system_scans**|**bigint**|システム クエリによるスキャン数。|  
|**system_lookups**|**bigint**|システム クエリによる参照数。|  
|**system_updates**|**bigint**|システム クエリによる更新数。|  
|**last_system_seek**|**DATETIME**|前回のシステム シークの時刻。|  
|**last_system_scan**|**DATETIME**|前回のシステム スキャンの時刻。|  
|**last_system_lookup**|**DATETIME**|前回のシステム参照の時刻。|  
|**last_system_update**|**DATETIME**|前回のシステム更新の時刻。|  
|pdw_node_id|**int**|**適用対象**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> このディストリビューションが配置されているノードの識別子。|  
  
## <a name="remarks"></a>解説  
 指定したインデックスに対し、1 回のクエリ実行でシーク、スキャン、参照、または更新が行われるたび、その操作はインデックスの使用としてカウントされ、このビュー内の対応するカウンターが 1 増えます。 情報は、ユーザーが送信したクエリによる操作と、統計収集のスキャンなど内部生成されたクエリによる操作の両方についてレポートされます。  
  
 
  **user_updates** カウンターでは、基になるテーブルまたはビューで行われた挿入、更新、または削除操作に基づく、インデックスのメンテナンスのレベルが示されます。 このビューを使用して、アプリケーションであまり使用されないインデックスを特定できます。 また、メンテナンスのオーバーヘッドの原因になっているインデックスも特定できます。 メンテナンスのオーバーヘッドの原因になっており、クエリでほとんどまたはまったく使用されないインデックスが特定できれば、インデックスの削除を検討することもできます。  
  
 カウンターは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER) サービスが開始されるたびに空に初期化されます。 また、AUTO_CLOSE が ON に設定されているなどの理由によりデータベースがデタッチまたはシャットダウンされるときに、そのデータベースに関連付けられたすべての行が削除されます。  
  
 インデックスを使用しているときは、そのインデックスにまだ行が存在しない場合に、行が **sys.dm_db_index_usage_stats** に追加されます。 行が追加されるときに、カウンターが 0 に初期設定されます。  
  
 、 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、または[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]へのアップグレード中に、dm_db_index_usage_stats のエントリが削除されます。 以降で[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]は、エントリは以前と同じように[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]保持されます。  
  
## <a name="permissions"></a>アクセス許可  
で[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]は、 `VIEW SERVER STATE`権限が必要です。   
Premium [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]レベルでは、データベース`VIEW DATABASE STATE`の権限が必要です。 Standard [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]レベルおよび Basic レベルでは、**サーバー管理**者または**Azure Active Directory 管理者**アカウントが必要です。  
  
## <a name="see-also"></a>参照  

 [Transact-sql&#41;&#40;インデックス関連の動的管理ビューおよび関数](../../relational-databases/system-dynamic-management-views/index-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)   
 [dm_db_index_operational_stats &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql.md)   
 [SQL&#41;&#40;Transact-sql のインデックス](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [パフォーマンスの監視とチューニング](../../relational-databases/performance/monitor-and-tune-for-performance.md)  
  
  


