---
title: "sys.dm_db_index_usage_stats (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/20/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 9652e093a6b358a209bb7b84f1c4aa4c6854c328
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmdbindexusagestats-transact-sql"></a>sys.dm_db_index_usage_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  さまざまな種類のインデックス操作の数と、各種の操作が前回 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で実行された時刻を返します。  
  
 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]、動的管理ビューは、データベースの包含に影響を与えるまたはユーザーがアクセスを他のデータベースに関する情報が公開される情報を公開できません。 この情報が公開されないように、接続されたテナントに属していないデータを含む行はすべてフィルターで除外されます。  
  
> [!NOTE]  
>  **sys.dm_db_index_usage_stats**メモリ最適化インデックスに関する情報は返されません。 メモリ最適化インデックスの使用方法については、次を参照してください。 [sys.dm_db_xtp_index_stats &#40;です。TRANSACT-SQL と #41 です](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-index-stats-transact-sql.md)。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して**sys.dm_pdw_nodes_db_index_usage_stats**です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**smallint**|テーブルまたはビューが定義されているデータベースの ID。|  
|**object_id**|**int**|インデックスが定義されているテーブルまたはビューの ID。|  
|**index_id**|**int**|インデックスの ID。|  
|**user_seeks**|**bigint**|ユーザー クエリによるシーク数。|  
|**user_scans**|**bigint**|ユーザー クエリによるスキャン数。 これには、'シーク' 述語を使用していないスキャンを表します。|  
|**user_lookups**|**bigint**|ユーザー クエリによるブックマーク参照数。|  
|**user_updates**|**bigint**|ユーザー クエリによる更新数。 これは、Insert、Delete が含まれていて、実際に影響を受ける行にないを実行する操作の数を表すを更新します。 たとえば場合は、1 つのステートメントで 1000 行を削除すると、この数が 1 ずつ増加は|  
|**last_user_seek**|**datetime**|前回のユーザー シークの時刻。|  
|**last_user_scan**|**datetime**|前回のユーザー スキャンの時刻。|  
|**last_user_lookup**|**datetime**|前回のユーザー参照の時刻。|  
|**last_user_update**|**datetime**|前回のユーザー更新の時刻。|  
|**system_seeks**|**bigint**|システム クエリによるシーク数。|  
|**system_scans**|**bigint**|システム クエリによるスキャン数。|  
|**system_lookups**|**bigint**|システム クエリによる参照数。|  
|**system_updates**|**bigint**|システム クエリによる更新数。|  
|**last_system_seek**|**datetime**|前回のシステム シークの時刻。|  
|**last_system_scan**|**datetime**|前回のシステム スキャンの時刻。|  
|**last_system_lookup**|**datetime**|前回のシステム参照の時刻。|  
|**last_system_update**|**datetime**|前回のシステム更新の時刻。|  
|pdw_node_id|**int**|**適用されます**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この分布はでは、ノードの識別子。|  
  
## <a name="remarks"></a>解説  
 指定したインデックスに対し、1 回のクエリ実行でシーク、スキャン、参照、または更新が行われるたび、その操作はインデックスの使用としてカウントされ、このビュー内の対応するカウンターが 1 増えます。 情報は、ユーザーが送信したクエリによる操作と、統計収集のスキャンなど内部生成されたクエリによる操作の両方についてレポートされます。  
  
 **User_updates**カウンターは、insert によるインデックスのメンテナンスのレベルを示す、更新、または基になるテーブルまたはビューでの delete 操作。 このビューを使用して、アプリケーションであまり使用されないインデックスを特定できます。 また、メンテナンスのオーバーヘッドの原因になっているインデックスも特定できます。 メンテナンスのオーバーヘッドの原因になっており、クエリでほとんどまたはまったく使用されないインデックスが特定できれば、インデックスの削除を検討することもできます。  
  
 カウンターを初期化するたびに空にする、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER) サービスを開始します。 また、AUTO_CLOSE が ON に設定されているなどの理由によりデータベースがデタッチまたはシャットダウンされた場合は常に、そのデータベースに関連付けられた行がすべて削除されます。  
  
 行が追加、インデックスを使用すると**sys.dm_db_index_usage_stats**行が既にインデックスに存在しない場合。 行が追加されるときに、カウンターが 0 に初期設定されます。  
  
 アップグレード中に[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、または[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]sys.dm_db_index_usage_stats 内のエントリが削除されます。 以降で[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]より前のバージョンと同様に、エントリが保持される[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]です。  
  
## <a name="permissions"></a>権限  
[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]が必要です`VIEW SERVER STATE`権限です。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium 階層が必要です、`VIEW DATABASE STATE`データベースの権限です。 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Standard および Basic 階層は、必要があります、**サーバー管理者**または**Azure Active Directory 管理者**アカウント。  
  
## <a name="see-also"></a>参照  

 [インデックス関連の動的管理ビューおよび関数 &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/index-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)   
 [sys.dm_db_index_operational_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.objects &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [パフォーマンスの監視とチューニング](../../relational-databases/performance/monitor-and-tune-for-performance.md)  
  
  


