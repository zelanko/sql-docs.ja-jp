---
title: sys.dm_db_column_store_row_group_physical_stats (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_db_column_store_row_group_physical_stats_TSQL
- sys.dm_db_column_store_row_group_physical_stats
- dm_db_column_store_row_group_physical_stats
- dm_db_column_store_row_group_physical_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dm_db_column_store_row_group_physical_stats
- sys.dm_db_column_store_row_group_physical_stats dynamic management view
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: a6eaa2759ac911f748da143dbd592abc5de066b9
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39533852"
---
# <a name="sysdmdbcolumnstorerowgroupphysicalstats-transact-sql"></a>sys.dm_db_column_store_row_group_physical_stats (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  すべての現在のデータベースで列ストア インデックスに関する現在の行グループ レベルの情報を提供します。  
  
 ここで、カタログ ビューは拡張[sys.column_store_row_groups &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-row-groups-transact-sql.md)します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|基になるテーブルの ID です。|  
|**index_id**|**int**|この列ストア インデックスの ID *object_id*テーブル。|  
|**partition_number**|**int**|保持するテーブルのパーティションの ID *row_group_id*します。 この DMV を sys.partitions に結合するには、partition_number を使用できます。|  
|**row_group_id**|**int**|この行グループの ID です。 パーティション分割されたテーブルの場合、パーティション内で一意です。<br /><br /> メモリ内の末尾に達すると-1 です。|  
|**delta_store_hobt_id**|**bigint**|デルタ ストアの行グループの hobt_id でします。<br /><br /> 行グループがデルタ ストアにない場合は NULL です。<br /><br /> メモリ内のテーブルの末尾の NULL を表します。|  
|**state**|**tinyint**|関連付けられている ID 番号*state_description*します。<br /><br /> 0 = INVISIBLE<br /><br /> 1 = OPEN <br /><br /> 2 = CLOSED <br /><br /> 3 = COMPRESSED<br /><br /> 4 = 廃棄 (TOMBSTONE)<br /><br /> 圧縮は、メモリ内のテーブルに適用する唯一の状態です。|  
|**state_desc**|**nvarchar(60)**|行グループの状態の説明。<br /><br /> 構築される非表示 – A の行グループ。 以下に例を示します。 <br />列ストア行グループは、データが圧縮されるときに、非表示です。 圧縮のメタデータのスイッチの変更が完了すると、列ストア行の状態グループから非表示に圧縮、および [終了] から廃棄 (tombstone) に、デルタストア行グループの状態。<br /><br /> 開く – デルタストア行グループを新しい行を受け入れます。 OPEN の行グループは、行ストア形式のままであり、列ストア形式に圧縮されていません。<br /><br /> CLOSED-行の最大数を格納し、列ストアに圧縮する組ムーバー プロセスが待機しているデルタ ストア行グループ。<br /><br /> COMPRESSED-行グループを列ストア圧縮で圧縮され、列ストアに格納されています。<br /><br /> 廃棄 (tombstone) – デルタストアにあったし、不要になった行グループが使用されます。|  
|**total_rows**|**bigint**|物理的な行の数が、行グループに格納されています。 圧縮された行グループの場合は、削除とマークされている行が含まれます。|  
|**deleted_rows**|**bigint**|圧縮された行グループに物理的に保存、削除対象としてマークされた行の数。<br /><br /> デルタ ストア行グループは 0 です。|  
|**size_in_bytes**|**bigint**|この行グループ内のすべてのページのバイト単位の合計サイズ。 このサイズでは、メタデータと共有辞書の格納に必要なサイズは含まれません。|  
|**trim_reason**|**tinyint**|圧縮の行グループに付与をトリガーした理由が行の最大数未満です。<br /><br /> 0 ～ UNKNOWN_UPGRADED_FROM_PREVIOUS_VERSION<br /><br /> 1-NO_TRIM<br /><br /> 2-一括読み込み<br /><br /> 3 – の再構成<br /><br /> 4 – DICTIONARY_SIZE<br /><br /> 5 – MEMORY_LIMITATION<br /><br /> 6 – RESIDUAL_ROW_GROUP<br /><br /> 7-STATS_MISMATCH<br /><br /> 8-スピル オーバー|  
|**trim_reason_desc**|**nvarchar(60)**|説明*trim_reason*します。<br /><br /> 0 ~ UNKNOWN_UPGRADED_FROM_PREVIOUS_VERSION: の以前のバージョンからアップグレードするときに発生した[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。<br /><br /> 1-NO_TRIM: 行グループは切り捨てられませんでした。 行グループは、1,048,476 行の最大値で圧縮されました。  行の数が小さくするデルタ行グループが閉じた後、subsset の行が削除された場合<br /><br /> 2 – 一括読み込み: 一括読み込みのバッチ サイズでは、行の数が制限されます。<br /><br /> 3 – の再構成: 強制 REORG コマンドの一部として圧縮されます。<br /><br /> 4 – DICTIONARY_SIZE: すべての行を一緒に圧縮するには大きすぎるディクショナリのサイズが成長しました。<br /><br /> 5 – MEMORY_LIMITATION: 使用可能なメモリ不足のすべての行を一緒に圧縮します。<br /><br /> 6 – RESIDUAL_ROW_GROUP: 閉じられた最後の行グループの一部として行 < 1 件のインデックス構築操作中に<br /><br /> STATS_MISMATCH: のみをメモリ内テーブルで列ストア。 統計は正しくないに示される場合は、> = 末尾での 100万行が少ないわかりました、圧縮された行グループが < 1, 000, 000 行<br /><br /> スピル オーバー: のみをメモリ内テーブルで列ストア。 カウントが 100 k と 100万の間にある場合に、最後のバッチ残りの行を圧縮する場合、> 1, 000, 000 行を末尾には、|  
|**transition_to_compressed_state**|TINYINT|この行グループを列ストアに圧縮された状態に、デルタストアから移動した方法を示しています。<br /><br /> 1-NOT_APPLICABLE<br /><br /> 2 – INDEX_BUILD<br /><br /> 3 – TUPLE_MOVER<br /><br /> 4 – REORG_NORMAL<br /><br /> 5 – REORG_FORCED<br /><br /> 6-一括読み込み<br /><br /> 7-マージ|  
|**transition_to_compressed_state_desc**|nvarchar(60)|NOT_APPLICABLE –、操作は、デルタストアには適用されません。 または、アップグレードする前に、行グループが圧縮された[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]場合、履歴は保持されません。<br /><br /> INDEX_BUILD –、インデックスの作成またはインデックスの再構築は、行グループを圧縮します。<br /><br /> TUPLE_MOVER –、組ムーバーは、バック グラウンドで実行するには、行グループが圧縮されています。 これは、行グループは、終了開くから状態を変更した後に発生します。<br /><br /> REORG_NORMAL – ALTER INDEX の再構成操作しています. デルタストアから列ストアに CLOSED 行グループを移動伴わないを再編成します。 これには、前に、組ムーバーがある、行グループの移動にかかる時間が発生しました。<br /><br /> REORG_FORCED – この行グループは、デルタストアに開かれていたし、前に、完全行数が必要があるが、列ストアに強制されました。<br /><br /> 一括読み込み: 一括読み込み操作では、デルタストアを使用せずに直接、行グループが圧縮されています。<br /><br /> マージ – マージ操作は、この行グループに 1 つまたは複数の行グループを統合し、列ストア圧縮を実行します。|  
|**has_vertipaq_optimization**|bit|Vertipaq の最適化では、高い圧縮率を実現するために、行グループ内の行の順序を並べ替えることで、列ストア圧縮が向上します。 ほとんどの場合は、この最適化が自動的に行われます。 Vertipaq の最適化は使用されませんが 2 つのケースがあります。<br/>  A. デルタ行グループが columnstore に移動し、列ストア インデックスの 1 つまたは複数の非クラスター化インデックスがあるときにここでは Vertipaq の最適化はスキップされますマッピング インデックスへの変更を最小限にするには<br/> B. メモリ最適化テーブルで列ストア インデックス。 <br /><br /> 0 = いいえ<br /><br /> 1 = はい|  
|**生成**|BIGINT|この行グループに関連付けられている行グループの生成。|  
|**created_time**|datetime2|この行グループの作成時のクロック時間。<br /><br /> NULL – をクリックし、メモリ内のテーブルに列ストア インデックスになります。|  
|**closed_time**|datetime2|この行グループが閉じられたときのクロック時間。<br /><br /> NULL – をクリックし、メモリ内のテーブルに列ストア インデックスになります。|  
  
## <a name="results"></a>[結果]  
 現在のデータベース内には、それぞれの行グループの 1 つの行を返します。  
  
## <a name="permissions"></a>アクセス許可  
 これらのアクセス許可が必要です。  
  
-   テーブルに対する CONTROL 権限。  
  
-   データベースに対する VIEW DATABASE STATE 権限。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-calculate-fragmentaton-to-decide-when-to-reorganize-or-rebuild-a-columnstore-index"></a>A. 再構成または列ストア インデックスを再構築するタイミングを決定する fragmentaton を計算します。  
 列ストア インデックスでは、削除された行の割合は、行グループ内の断片化の効果的な手段です。 断片化が 20% 以上、削除された行を削除することをお勧めします。 場合です。  例については、次を参照してください。[列ストア インデックスの最適化](~/relational-databases/indexes/columnstore-indexes-defragmentation.md)します。  
  
 この例では結合**sys.dm_db_column_store_row_group_physical_stats**他のシステム テーブルし、計算、`Fragmentation`列として、現在のデータベース内の各の行グループの効率の推定値です。     コメントのハイフンの前後に 1 つのテーブルの削除に関する情報、**場所**句とテーブル名を指定します。  
  
```sql  
SELECT i.object_id,   
    object_name(i.object_id) AS TableName,   
    i.name AS IndexName,   
    i.index_id,   
    i.type_desc,   
    CSRowGroups.*,  
    100*(ISNULL(deleted_rows,0))/total_rows AS 'Fragmentation'  
FROM sys.indexes AS i  
JOIN sys.dm_db_column_store_row_group_physical_stats AS CSRowGroups  
    ON i.object_id = CSRowGroups.object_id AND i.index_id = CSRowGroups.index_id   
-- WHERE object_name(i.object_id) = 'table_name'   
ORDER BY object_name(i.object_id), i.name, row_group_id;  
```  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [SQL Server のシステム カタログよく寄せられる質問のクエリを実行します。](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.all_columns &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys.computed_columns &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-computed-columns-transact-sql.md)   
 [列ストア インデックス ガイド](~/relational-databases/indexes/columnstore-indexes-overview.md)   
 [sys.column_store_dictionaries &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-dictionaries-transact-sql.md)   
 [sys.column_store_segments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-segments-transact-sql.md)  
  
