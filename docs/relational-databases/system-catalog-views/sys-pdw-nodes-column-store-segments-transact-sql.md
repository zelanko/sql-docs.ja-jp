---
title: sys.pdw_nodes_column_store_segments (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/28/2018
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: e2fdf8e9-1b74-4682-b2d4-c62aca053d7f
author: julieMSFT
ms.author: jrasnick
manager: jrj
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 399f08e0ebf09ea90c358ae5667b5031ef0cb099
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66822511"
---
# <a name="syspdwnodescolumnstoresegments-transact-sql"></a>sys.pdw_nodes_column_store_segments (TRANSACT-SQL)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

1 行、列ストア インデックス内の各列のデータが含まれています。

| 列名                 | データ型  | 説明                                                  |
| :-------------------------- | :--------- | :----------------------------------------------------------- |
| **partition_id**            | **bigint** | パーティション ID を示します。 データベース内で一意です。     |
| **hobt_id**                 | **bigint** | この列ストア インデックスを保持するテーブルのヒープまたは B ツリー インデックス (hobt) の ID。 |
| **column_id**               | **int**    | 列ストア列の ID。                                |
| **segment_id**              | **int**    | 列セグメントの ID。 旧バージョンと互換性のため、列名が行グループ ID です。 この場合でも、segment_id を呼び出せる続けます < Hobt_id で、partition_id、column_id > を使用してセグメントを一意に識別できます < segment_id >。 |
| **version**                 | **int**    | 列セグメント形式のバージョンです。                        |
| **encoding_type**           | **int**    | そのセグメントを使用するエンコードの種類です。<br /><br /> 1 = VALUE_BASED - 非文字列/バイナリないディクショナリ (内部のいくつかのバリエーションを 4 に似ています)<br /><br /> 2 = VALUE_HASH_BASED - の一般的な値がディクショナリ内の文字列/バイナリ列<br /><br /> 3 = STRING_HASH_BASED - の一般的な値がディクショナリ内の文字列/バイナリ列<br /><br /> 4 = STORE_BY_VALUE_BASED - non-string/binary with no dictionary<br /><br /> 5 = STRING_STORE_BY_VALUE_BASED - string/binary with no dictionary<br /><br /> すべてのエンコーディングでは、可能な場合のエンコード ビット パッキングと実行の長さの活用します。 |
| **row_count**               | **int**    | 行グループ内の行の数。                             |
| **has_nulls**               | **int**    | 列セグメントに null 値がある場合は 1。                     |
| **base_id**                 | **bigint** | エンコードの種類 1 が使用されている場合は、ベース値 ID。  エンコードの種類 1 が使用されていない場合、base_id は 1 に設定されます。 |
| **magnitude**               | **float**  | エンコードの種類 1 が使用されている場合は大きさ。  エンコードの種類 1 が使用されていない場合、magnitude は 1 に設定されます。 |
| **primary__dictionary_id**  | **int**    | プライマリ辞書の ID。 0 以外の値は、この列に現在のセグメント (つまり行グループ) のローカルのディクショナリを指します。 値-1 は、このセグメントのローカルのディクショナリがないことを示します。 |
| **secondary_dictionary_id** | **int**    | セカンダリ辞書の ID。 0 以外の値は、この列に現在のセグメント (つまり行グループ) のローカルのディクショナリを指します。 値-1 は、このセグメントのローカルのディクショナリがないことを示します。 |
| **min_data_id**             | **bigint** | 列セグメントの最小データ ID。                       |
| **max_data_id**             | **bigint** | 列セグメントの最大データ ID。                       |
| **null_value**              | **bigint** | NULL を表すために使用される値。                               |
| **on_disk_size**            | **bigint** | (バイト単位) セグメントのサイズ。                                    |
| **pdw_node_id**             | **int**    | 一意の識別子、[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]ノード。 |
| &nbsp; | &nbsp; | &nbsp; |

## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] および [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]

Sys.pdw_nodes_column_store_segments と 1 つの論理テーブルの列ストア セグメントの数を決定するには、その他のシステム テーブルを結合します。

```sql
SELECT  sm.name           as schema_nm
,       tb.name           as table_nm
,       nc.name           as col_nm
,       nc.column_id
,       COUNT(*)          as segment_count
FROM    sys.[schemas] sm
JOIN    sys.[tables] tb                   ON  sm.[schema_id]          = tb.[schema_id]
JOIN    sys.[pdw_table_mappings] mp       ON  tb.[object_id]          = mp.[object_id]
JOIN    sys.[pdw_nodes_tables] nt         ON  nt.[name]               = mp.[physical_name]
JOIN    sys.[pdw_nodes_partitions] np     ON  np.[object_id]          = nt.[object_id]
                                          AND np.[pdw_node_id]        = nt.[pdw_node_id]
                                          AND np.[distribution_id]    = nt.[distribution_id]
JOIN    sys.[pdw_nodes_columns] nc        ON  np.[object_id]          = nc.[object_id]
                                          AND np.[pdw_node_id]        = nc.[pdw_node_id]
                                          AND np.[distribution_id]    = nc.[distribution_id]
JOIN    sys.[pdw_nodes_column_store_segments] rg  ON  rg.[partition_id]         = np.[partition_id]
                                                      AND rg.[pdw_node_id]      = np.[pdw_node_id]
                                                      AND rg.[distribution_id]  = np.[distribution_id]
                                                      AND rg.[column_id]        = nc.[column_id]
GROUP BY    sm.name
,           tb.name
,           nc.name
,           nc.column_id  
ORDER BY    table_nm
,           nc.column_id
,           sm.name ;
```

## <a name="permissions"></a>アクセス許可

**VIEW SERVER STATE** アクセス許可が必要です。

## <a name="see-also"></a>関連項目

[SQL Data Warehouse と Parallel Data Warehouse カタログ ビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
[CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-columnstore-index-transact-sql.md)  
[sys.pdw_nodes_column_store_row_groups &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-row-groups-transact-sql.md)  
[sys.pdw_nodes_column_store_dictionaries &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-dictionaries-transact-sql.md)
