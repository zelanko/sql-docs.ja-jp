---
title: sys.pdw_nodes_column_store_segments (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/28/2018
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: e2fdf8e9-1b74-4682-b2d4-c62aca053d7f
author: hirokib
ms.author: elbutter
manager: jrj
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: c98898560d4b2f523974065831f0d316a390f7b7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47682530"
---
# <a name="syspdwnodescolumnstoresegments-transact-sql"></a>sys.pdw_nodes_column_store_segments (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

列ストア インデックスに各列の行を格納します。  

| 列名                 | データ型  | 説明                                                  |
| --------------------------- | ---------- | ------------------------------------------------------------ |
| **partition_id**            | **bigint** | パーティション ID を示します。 データベース内で一意です。     |
| **hobt_id**                 | **bigint** | この列ストア インデックスを保持するテーブルのヒープまたは B ツリー インデックス (hobt) の ID。 |
| **column_id**               | **int**    | 列ストアの列の ID。                                |
| **segment_id**              | **int**    | 列セグメントの ID。 旧バージョンと互換性のため、列名が行グループ ID です。 この場合でも、segment_id を呼び出せる続けます < Hobt_id で、partition_id、column_id > を使用してセグメントを一意に識別できます < segment_id >。 |
| **version**                 | **int**    | 列セグメント形式のバージョン。                        |
| **encoding_type**           | **int**    | そのセグメントを使用するエンコードの種類です。<br /><br /> 1 = VALUE_BASED - 非文字列/バイナリないディクショナリ (内部のいくつかのバリエーションを 4 に似ています)<br /><br /> 2 = VALUE_HASH_BASED - の一般的な値がディクショナリ内の文字列/バイナリ列<br /><br /> 3 = STRING_HASH_BASED - の一般的な値がディクショナリ内の文字列/バイナリ列<br /><br /> 4 = STORE_BY_VALUE_BASED - 非文字列/バイナリない辞書で<br /><br /> 5 = STRING_STORE_BY_VALUE_BASED - ない辞書で文字列/バイナリ<br /><br /> すべてのエンコーディングでは、可能な場合のエンコード ビット パッキングと実行の長さの活用します。 |
| **row_count**               | **int**    | 行グループ内の行の数。                             |
| **has_nulls**               | **int**    | 列セグメントに NULL 値がある場合は 1。                     |
| **base_id**                 | **bigint** | エンコードの種類 1 が使用されている場合は、ベース値 ID。  エンコードの種類 1 が、使用されていない場合、base_id は 1 に設定します。 |
| **magnitude**               | **float**  | エンコードの種類 1 が使用されている場合は大きさ。  エンコードの種類 1 が、使用されていない場合は、絶対値が 1 に設定されます。 |
| **primary__dictionary_id**  | **int**    | プライマリ辞書の ID。 0 以外の値は、この列に現在のセグメント (つまり行グループ) のローカルのディクショナリを指します。 値-1 は、このセグメントのローカルのディクショナリがないことを示します。 |
| **secondary_dictionary_id** | **int**    | セカンダリ辞書の ID。 0 以外の値は、この列に現在のセグメント (つまり行グループ) のローカルのディクショナリを指します。 値-1 は、このセグメントのローカルのディクショナリがないことを示します。 |
| **min_data_id**             | **bigint** | 列セグメントの最小データ ID。                       |
| **max_data_id**             | **bigint** | 列セグメントの最大データ ID。                       |
| **null_value**              | **bigint** | NULL を表すために使用される値。                               |
| **on_disk_size**            | **bigint** | セグメントのサイズ (バイト単位)。                                    |
| **pdw_node_id**             | **int**    | 一意の識別子、[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]ノード。 |

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
,           sm.name
```

## <a name="permissions"></a>アクセス許可  
 **VIEW SERVER STATE** アクセス許可が必要です。  

## <a name="see-also"></a>参照  
 [SQL Data Warehouse と Parallel Data Warehouse カタログ ビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [列ストア インデックスを作成&#40;TRANSACT-SQL&#41;](../../t-sql/statements/create-columnstore-index-transact-sql.md)   
 [sys.pdw_nodes_column_store_row_groups &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-row-groups-transact-sql.md)   
 [sys.pdw_nodes_column_store_dictionaries &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-dictionaries-transact-sql.md)  

  

