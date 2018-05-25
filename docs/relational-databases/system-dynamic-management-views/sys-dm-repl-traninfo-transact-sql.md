---
title: sys.dm_repl_traninfo (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_repl_traninfo
- dm_repl_traninfo
- sys.dm_repl_traninfo_TSQL
- dm_repl_traninfo_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_repl_traninfo dynamic management view
ms.assetid: 5abe2605-0506-46ec-82b5-6ec08428ba13
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 20a15bd329da102b45b3f611a9cbe86651ba2b3d
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmrepltraninfo-transact-sql"></a>sys.dm_repl_traninfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  レプリケートされたトランザクションまたは変更データ キャプチャ トランザクションごとの情報を返します。  

|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**fp2p_pub_exists**|**tinyint**|ピアツーピア トランザクション レプリケーションを使用してパブリッシュされるデータベースに、トランザクションがあるかどうかを示します。 true の場合、値は 1 です。それ以外の場合は 0 です。|  
|**db_ver**|**int**|データベースのバージョン。|  
|**comp_range_address**|**varbinary(8)**|スキップする必要がある、部分ロールバックの範囲。|  
|**textinfo_address**|**varbinary(8)**|キャッシュされたテキスト情報構造のメモリ内アドレス。|  
|**fsinfo_address**|**varbinary(8)**|キャッシュされたファイル ストリーム情報構造のメモリ内アドレス。|  
|**begin_lsn**|**nvarchar(64)**|トランザクションに関する最初のログ レコードのログ シーケンス番号 (LSN)。|  
|**commit_lsn**|**nvarchar(64)**|トランザクションに関するコミット ログ レコードの LSN。|  
|**dbid**|**smallint**|データベース ID。|  
|**rows**|**int**|トランザクション内のレプリケートされたコマンドの ID。|  
|**xdesid**|**nvarchar(64)**|トランザクション id。|  
|**artcache_table_address**|**varbinary(8)**|トランザクションで最後に使用されたキャッシュ済みアーティクル テーブル構造のメモリ内アドレス。|  
|**server**|**nvarchar(514)**|サーバー名。|  
|**server_len_in_bytes**|**smallint**|サーバー名の文字長 (バイト単位)。|  
|**データベース (database)**|**nvarchar(514)**|データベース名。|  
|**db_len_in_bytes**|**smallint**|データベース名の文字長 (バイト単位)。|  
|**originator**|**nvarchar(514)**|トランザクションが発生したサーバーの名前。|  
|**originator_len_in_bytes**|**smallint**|トランザクションが発生したサーバーの文字長 (バイト単位)。|  
|**orig_db**|**nvarchar(514)**|トランザクションが発生したデータベースの名前。|  
|**orig_db_len_in_bytes**|**smallint**|トランザクションが発生したデータベースの文字長 (バイト単位)。|  
|**cmds_in_tran**|**int**|現在のトランザクション内のレプリケートされたコマンドの数。論理トランザクションを実行するタイミングを決定するために使用されます。|  
|**is_boundedupdate_singleton**|**tinyint**|一意の列更新が 1 行だけに影響するかどうかを示します。|  
|**begin_update_lsn**|**nvarchar(64)**|一意の列更新で使用される LSN。|  
|**delete_lsn**|**nvarchar(64)**|更新の一部として削除する LSN。|  
|**last_end_lsn**|**nvarchar(64)**|論理トランザクションの最後の LSN。|  
|**fcomplete**|**tinyint**|コマンドが部分更新かどうかを示します。|  
|**fcompensated**|**tinyint**|トランザクションが部分ロールバックに含まれるかどうかを示します。|  
|**fprocessingtext**|**tinyint**|トランザクションにバイナリ ラージ データ型列が含まれるかどうかを示します。|  
|**max_cmds_in_tran**|**int**|ログ リーダー エージェントで指定される、論理トランザクションのコマンドの最大数。|  
|**begin_time**|**datetime**|トランザクションの開始時刻。|  
|**commit_time**|**datetime**|トランザクションがコミットされた時刻。|  
|**session_id**|**int**|変更データ キャプチャのログ スキャン セッションの ID。 この列にマップされて、 **session_id**内の列[sys.dm_cdc_logscan_sessions](../../relational-databases/system-dynamic-management-views/change-data-capture-sys-dm-cdc-log-scan-sessions.md)です。|  
|**session_phase**|**int**|エラー発生時のセッションのフェーズを示す数値。 この列にマップされて、 **phase_number**内の列[sys.dm_cdc_errors](../../relational-databases/system-dynamic-management-views/change-data-capture-sys-dm-cdc-errors.md)です。|  
|**is_known_cdc_tran**|**bit**|トランザクションが変更データ キャプチャで追跡されることを示します。<br /><br /> 0 = トランザクション レプリケーション トランザクション。<br /><br /> 1 = 変更データ キャプチャ トランザクション。|  
|**error_count**|**int**|発生したエラーの数です。|  
  
## <a name="permissions"></a>権限  
 パブリケーション データベースまたは変更データ キャプチャが有効にされたデータベースに対する VIEW DATABASE STATE 権限が必要です。  
  
## <a name="remarks"></a>解説  
 返される情報は、アーティクル キャッシュに現在読み込まれている、レプリケートされたデータベース オブジェクトまたは変更データ キャプチャが有効にされたテーブルの情報だけです。  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [レプリケーション関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/replication-related-dynamic-management-views-transact-sql.md)   
 [変更データ キャプチャに関連した動的管理ビュー &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/2a771d7d-693a-4f56-9227-02cd00e0e200)  
  
  

