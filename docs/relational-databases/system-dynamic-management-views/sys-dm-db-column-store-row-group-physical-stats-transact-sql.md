---
title: sys.dm_db_column_store_row_group_physical_stats (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/05/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 836f8b8152e5801ab6bfc382c09a675b3c1e464f
ms.sourcegitcommit: 594cee116fa4ee321e1f5e5206f4a94d408f1576
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/23/2019
ms.locfileid: "70009412"
---
# <a name="sysdm_db_column_store_row_group_physical_stats-transact-sql"></a>sys.dm_db_column_store_row_group_physical_stats (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  すべての現在のデータベースで列ストア インデックスに関する現在の行グループ レベルの情報を提供します。  
  
 これに[より&#40;&#41;](../../relational-databases/system-catalog-views/sys-column-store-row-groups-transact-sql.md)、カタログビュー column_store_row_groups transact-sql が拡張されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|基になるテーブルの ID です。|  
|**index_id**|**int**|*Object_id*テーブルのこの列ストアインデックスの ID。|  
|**partition_number**|**int**|*Row_group_id*を保持するテーブルパーティションの ID。 この DMV を sys.partitions に結合するには、partition_number を使用できます。|  
|**row_group_id**|**int**|この行グループの ID です。 パーティション分割されたテーブルの場合、パーティション内で一意です。<br /><br /> メモリ内の末尾に達すると-1 です。|  
|**delta_store_hobt_id**|**bigint**|デルタ ストアの行グループの hobt_id でします。<br /><br /> 行グループがデルタストアに存在しない場合は NULL になります。<br /><br /> メモリ内のテーブルの末尾の NULL を表します。|  
|**state**|**tinyint**|*State_description*に関連付けられた ID 番号。<br /><br /> 0 = INVISIBLE<br /><br /> 1 = OPEN<br /><br /> 2 = CLOSED<br /><br /> 3 = COMPRESSED<br /><br /> 4 = 廃棄 (TOMBSTONE)<br /><br /> 圧縮は、メモリ内のテーブルに適用する唯一の状態です。|  
|**state_desc**|**nvarchar(60)**|行グループの状態の説明。<br /><br /> 非表示-ビルドされる行グループ。 以下に例を示します。 <br />列ストア行グループは、データが圧縮されるときに、非表示です。 圧縮のメタデータのスイッチの変更が完了すると、列ストア行の状態グループから非表示に圧縮、および [終了] から廃棄 (tombstone) に、デルタストア行グループの状態。<br /><br /> OPEN-新しい行を受け入れる、デルタストアの行グループ。 OPEN の行グループは、行ストア形式のままであり、列ストア形式に圧縮されていません。<br /><br /> CLOSED-最大行数を含むデルタストア内の行グループ。これは、組ムーバープロセスによって列ストアに圧縮されるのを待機しています。<br /><br /> 圧縮-列ストア圧縮を使用して圧縮され、列ストアに格納される行グループ。<br /><br /> 廃棄 (TOMBSTONE)-以前はデルタストア内にあった行グループは使用されなくなりました。|  
|**total_rows**|**bigint**|物理的な行の数が、行グループに格納されています。 圧縮された行グループの場合は、削除とマークされている行が含まれます。|  
|**deleted_rows**|**bigint**|圧縮された行グループに物理的に保存、削除対象としてマークされた行の数。<br /><br /> デルタ ストア行グループは 0 です。|  
|**size_in_bytes**|**bigint**|この行グループ内のすべてのページのバイト単位の合計サイズ。 このサイズでは、メタデータと共有辞書の格納に必要なサイズは含まれません。|  
|**trim_reason**|**tinyint**|圧縮の行グループに付与をトリガーした理由が行の最大数未満です。<br /><br /> 0-UNKNOWN_UPGRADED_FROM_PREVIOUS_VERSION<br /><br /> 1-NO_TRIM<br /><br /> 2-一括読み込み<br /><br /> 3-再組織<br /><br /> 4-DICTIONARY_SIZE<br /><br /> 5-MEMORY_LIMITATION<br /><br /> 6-RESIDUAL_ROW_GROUP<br /><br /> 7-STATS_MISMATCH<br /><br /> 8-スピルオーバー|  
|**trim_reason_desc**|**nvarchar(60)**|*Trim_reason*の説明。<br /><br /> 0-UNKNOWN_UPGRADED_FROM_PREVIOUS_VERSION:以前のバージョンの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]からアップグレードしたときに発生しました。<br /><br /> 1-NO_TRIM:行グループは切り捨てられませんでした。 行グループは、1,048,476 行の最大値で圧縮されました。  行のサブセットが閉じられた後に行のサブセットが削除された場合、行の数が少なくなる可能性があります。<br /><br /> 2-BULKLOAD:一括読み込みバッチのサイズは、行の数に制限されています。<br /><br /> 3-再組織:REORG コマンドの一部としての強制圧縮。<br /><br /> 4-DICTIONARY_SIZE:ディクショナリのサイズが大きすぎて、すべての行をまとめて圧縮できませんでした。<br /><br /> 5-MEMORY_LIMITATION:すべての行をまとめて圧縮するのに十分なメモリがありません。<br /><br /> 6-RESIDUAL_ROW_GROUP:インデックス作成操作中に、行が 100万 < の最後の行グループの一部として閉じられました<br /><br /> STATS_MISMATCH:インメモリテーブルの列ストアにのみ使用できます。 Stats が不適切に示されている場合 > は、末尾に100万の修飾された行を指定しますが、これは少なくとも、圧縮された行グループは100万行を < します。<br /><br /> スピルオーバーインメモリテーブルの列ストアにのみ使用できます。 末尾 > に100万の行が含まれている場合、その数が 10 ~ 100万の場合、残りの行の最後のバッチは圧縮されます。|  
|**transition_to_compressed_state**|tinyint|この行グループを列ストアに圧縮された状態に、デルタストアから移動した方法を示しています。<br /><br /> 1-NOT_APPLICABLE<br /><br /> 2-INDEX_BUILD<br /><br /> 3-TUPLE_MOVER<br /><br /> 4-REORG_NORMAL<br /><br /> 5-REORG_FORCED<br /><br /> 6-BULKLOAD<br /><br /> 7-マージ|  
|**transition_to_compressed_state_desc**|nvarchar(60)|NOT_APPLICABLE-この操作はデルタストアには適用されません。 または、アップグレードする前に、行グループが圧縮された [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] この場合、履歴は保持されません。<br /><br /> INDEX_BUILD-インデックスの作成またはインデックスの再構築は、行グループを圧縮します。<br /><br /> TUPLE_MOVER-バックグラウンドで実行されている組ムーバーが、行グループを圧縮します。 これは、行グループは、終了開くから状態を変更した後に発生します。<br /><br /> REORG_NORMAL-再構成操作、ALTER INDEX...デルタストアから列ストアに CLOSED 行グループを移動伴わないを再編成します。 これには、前に、組ムーバーがある、行グループの移動にかかる時間が発生しました。<br /><br /> REORG_FORCED-この行グループは、デルタストアで開かれており、行の数が多くなる前に列ストアに強制されていました。<br /><br /> BULKLOAD-一括読み込み操作では、デルタストアを使用せずに行グループを直接圧縮しました。<br /><br /> マージ-マージ操作では、1つ以上の行グループをこの行グループに統合し、列ストア圧縮を実行しました。|  
|**has_vertipaq_optimization**|bit|Vertipaq の最適化では、高い圧縮率を実現するために、行グループ内の行の順序を並べ替えることで、列ストア圧縮が向上します。 ほとんどの場合は、この最適化が自動的に行われます。 Vertipaq の最適化は使用されません。<br/>  A. デルタ行グループが列ストアに移動し、列ストアインデックスに1つ以上の非クラスター化インデックスがある場合、この例では、マッピングインデックスへの変更を最小限に抑えるために、Vertipaq の最適化がスキップされます。<br/> B. メモリ最適化テーブルの列ストアインデックスの場合。 <br /><br /> 0 = いいえ<br /><br /> 1 = はい|  
|**generation**|bigint|この行グループに関連付けられている行グループの生成。|  
|**created_time**|datetime2|この行グループの作成時のクロック時間。<br /><br /> NULL-インメモリテーブルの列ストアインデックスの場合。|  
|**closed_time**|datetime2|この行グループが終了した時刻。<br /><br /> NULL-インメモリテーブルの列ストアインデックスの場合。|  
| &nbsp; | &nbsp; | &nbsp; |

## <a name="results"></a>[結果]  
 現在のデータベース内には、それぞれの行グループの 1 つの行を返します。  
  
## <a name="permissions"></a>アクセス許可  
テーブル`CONTROL`に対する権限と`VIEW DATABASE STATE` 、データベースに対する権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-calculate-fragmentation-to-decide-when-to-reorganize-or-rebuild-a-columnstore-index"></a>A. 断片化を計算して、列ストアインデックスを再編成または再構築するタイミングを決定します。  
 列ストアインデックスの場合、行グループの断片化を解消するには、削除された行の割合を使用することをお勧めします。 断片化が 20% 以上の場合は、削除した行を削除することをお勧めします。 他の例については、「[インデックスの再編成と再構築](~/relational-databases/indexes/reorganize-and-rebuild-indexes.md)」を参照してください。  
  
 この例では、他のシステムテーブルと共に、この列を`Fragmentation` 、現在のデータベース内の各行グループの効率の推定値として結合しています。 コメントのハイフンの前後に 1 つのテーブルの削除に関する情報、**WHERE**句とテーブル名を指定します。  
  
```sql  
SELECT i.object_id,   
    object_name(i.object_id) AS TableName,   
    i.name AS IndexName,   
    i.index_id,   
    i.type_desc,   
    CSRowGroups.*,  
    100*(ISNULL(deleted_rows,0))/NULLIF(total_rows,0) AS 'Fragmentation'
FROM sys.indexes AS i  
JOIN sys.dm_db_column_store_row_group_physical_stats AS CSRowGroups  
    ON i.object_id = CSRowGroups.object_id AND i.index_id = CSRowGroups.index_id   
-- WHERE object_name(i.object_id) = 'table_name'   
ORDER BY object_name(i.object_id), i.name, row_group_id;  
```  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [システムカタログビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)      
 [列ストア インデックスのアーキテクチャ](../../relational-databases/sql-server-index-design-guide.md#columnstore_index)         
 [SQL Server システムカタログに対するクエリについてよく寄せられる質問](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.all_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys.computed_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-computed-columns-transact-sql.md)  [sys.column_store_dictionaries &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-dictionaries-transact-sql.md) transact-sql の transact-sql)   
 [sys.column_store_segments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-segments-transact-sql.md)  
  
