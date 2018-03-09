---
title: "sys.column_store_segments (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/15/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- column_store_segments
- sys.column_store_segments_TSQL
- sys.column_store_segments
- column_store_segments_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_store_segments catalog view
ms.assetid: 1253448c-2ec9-4900-ae9f-461d6b51b2ea
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f73379d3ae23570f95209631444d1335279a5ef5
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="syscolumnstoresegments-transact-sql"></a>sys.column_store_segments (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

列ストア インデックスで各列セグメントの 1 つの行を返します。 行グループごとに各列の 1 つの列セグメントがあります。 たとえば、10 行グループと 34 列を含むテーブルには、340 行が返されます。 
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**partition_id**|**bigint**|パーティション ID を示します。 データベース内で一意です。|  
|**hobt_id**|**bigint**|この列ストア インデックスを保持するテーブルのヒープまたは B ツリー インデックス (hobt) の ID。|  
|**column_id**|**int**|列ストアの列の ID。|  
|**segment_id**|**int**|行グループの ID です。 旧バージョンと互換性のため、列名が呼び出す segment_id 行グループ ID です。 この場合でも引き続き 使用してセグメントを一意に識別できる\<hobt_id で、partition_id、column_id >、< segment_id >。|  
|**version**|**int**|列セグメント形式のバージョン。|  
|**encoding_type**|**int**|そのセグメントで使用するエンコードの種類です。<br /><br /> 1 = VALUE_BASED - 非文字列/バイナリないディクショナリ (いくつか内部のバリエーションを 4 に非常に似ています)<br /><br /> 2 = VALUE_HASH_BASED   - non-string/binary column with common values in dictionary<br /><br /> 3 = STRING_HASH_BASED - の一般的な値がディクショナリ内の文字列またはバイナリ列<br /><br /> 4 STORE_BY_VALUE_BASED - 非文字列/バイナリないディクショナリを =<br /><br /> 5 = STRING_STORE_BY_VALUE_BASED - 文字列/にあるバイナリ辞書が見つかりません<br /><br /> すべてのエンコーディング利用可能な場合のエンコード ビット パッキングと実行の長さ。|  
|**row_count**|**int**|行グループ内の行の数。|  
|**has_nulls**|**int**|列セグメントに NULL 値がある場合は 1。|  
|**base_id**|**bigint**|エンコードの種類 1 が使用されている場合は、id をベース値です。  エンコードの種類 1 が使用されていない場合、base_id は-1 に設定します。|  
|**magnitude**|**float**|エンコードの種類 1 が使用されている場合は大きさ。  エンコードの種類 1 が使用されていない場合は大きさが-1 に設定します。|  
|**primary_dictionary_id**|**int**|値 0 は、グローバルの辞書を表します。 値-1 は、この列用に作成されたグローバルの辞書がないことを示します。|  
|**secondary_dictionary_id**|**int**|0 以外の値は、現在のセグメント (つまり、行グループ) のこの列のローカルのディクショナリを指します。 値-1 は、このセグメントのローカルのディクショナリがないことを示します。|  
|**min_data_id**|**bigint**|列セグメントの最小データ ID。|  
|**max_data_id**|**bigint**|列セグメントの最大データ ID。|  
|**null_value**|**bigint**|NULL を表すために使用される値。|  
|**on_disk_size**|**bigint**|セグメントのサイズ (バイト単位)。|  
  
## <a name="remarks"></a>解説  
 次のクエリは、列ストア インデックスのセグメントに関する情報を返します。  
  
```sql  
SELECT i.name, p.object_id, p.index_id, i.type_desc,   
    COUNT(*) AS number_of_segments  
FROM sys.column_store_segments AS s   
INNER JOIN sys.partitions AS p   
    ON s.hobt_id = p.hobt_id   
INNER JOIN sys.indexes AS i   
    ON p.object_id = i.object_id  
WHERE i.type = 5 OR i.type = 6  
GROUP BY i.name, p.object_id, p.index_id, i.type_desc ;  
GO  
```  
  
## <a name="permissions"></a>権限  
 すべての列が少なくとも必要**VIEW DEFINITION**テーブルに対する権限。 ユーザーがあるない限り列は null を返します**選択**権限: has_nulls、base_id、magnitude、min_data_id、max_data_id、および null_value します。  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [SQL Server のシステム カタログよく寄せられる質問のクエリを実行します。](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.all_columns &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys.computed_columns &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-computed-columns-transact-sql.md)   
 [列ストア インデックス ガイド](~/relational-databases/indexes/columnstore-indexes-overview.md)    
 [sys.column_store_dictionaries &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-dictionaries-transact-sql.md)  
  
  

