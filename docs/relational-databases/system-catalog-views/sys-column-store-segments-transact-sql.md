---
title: column_store_segments (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 01/15/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b8d476e2f21693254eac5fc4712d53ac854e74ff
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68140002"
---
# <a name="syscolumn_store_segments-transact-sql"></a>sys.column_store_segments (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

列ストアインデックスの列セグメントごとに1行の値を返します。 行グループごとに、列ごとに1つの列セグメントがあります。 たとえば、10個の行グループと34列を含むテーブルでは、340行が返されます。 
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**partition_id**|**bigint**|パーティション ID を示します。 データベース内で一意です。|  
|**hobt_id**|**bigint**|この列ストアインデックスを持つテーブルのヒープまたは B ツリーインデックス (hobt) の ID。|  
|**column_id**|**int**|列ストア列の ID。|  
|**segment_id**|**int**|行グループの ID。 旧バージョンとの互換性を維持するために、列名は行グループ ID でも segment_id 呼び出されます。 セグメントを一意に識別するに\<は、hobt_id、partition_id、column_id>、<segment_id> を使用します。|  
|**バージョン**|**int**|列セグメント形式のバージョン。|  
|**encoding_type**|**int**|そのセグメントに使用されるエンコードの種類:<br /><br /> 1 = VALUE_BASED-非文字列/バイナリ (辞書なし) (内部的なバリエーションでは4によく似ています)<br /><br /> 2 = VALUE_HASH_BASED-ディクショナリに共通の値を持つ非文字列/バイナリ列<br /><br /> 3 = ディクショナリに共通の値を持つ STRING_HASH_BASED 文字列/バイナリ列<br /><br /> 4 = STORE_BY_VALUE_BASED-辞書のない文字列/バイナリ<br /><br /> 5 = ディクショナリのない STRING_STORE_BY_VALUE_BASED 文字列/バイナリ<br /><br /> すべてのエンコーディングは、可能であれば、ビットパックと実行時間のエンコーディングを利用します。|  
|**row_count**|**int**|行グループ内の行の数。|  
|**has_nulls**|**int**|列セグメントに null 値が含まれている場合は1。|  
|**base_id**|**bigint**|エンコードの種類1が使用されている場合は、ベース値 id。  エンコードの種類1が使用されていない場合は、base_id が-1 に設定されます。|  
|**桁違い**|**float**|エンコードの種類1が使用されている場合の大きさ。  エンコードの種類1が使用されていない場合、マグニチュードは-1 に設定されます。|  
|**primary_dictionary_id**|**int**|値0はグローバルディクショナリを表します。 値-1 は、この列に対してグローバルディクショナリが作成されていないことを示します。|  
|**secondary_dictionary_id**|**int**|0以外の値は、現在のセグメント (つまり、行グループ) のこの列のローカル辞書を指します。 値-1 は、このセグメントにローカルディクショナリがないことを示します。|  
|**min_data_id**|**bigint**|列セグメントの最小データ ID。|  
|**max_data_id**|**bigint**|列セグメントの最大データ id。|  
|**null_value**|**bigint**|NULL を表すために使用される値。|  
|**on_disk_size**|**bigint**|セグメントのサイズ (バイト単位)。|  
  
## <a name="remarks"></a>解説  
 次のクエリは、列ストアインデックスのセグメントに関する情報を返します。  
  
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
  
## <a name="permissions"></a>アクセス許可  
 すべての列には、少なくともテーブルに対する**VIEW DEFINITION**権限が必要です。 次の列は、ユーザーが**SELECT**権限 (has_nulls、base_id、マグニチュード、min_data_id、max_data_id、および null_value を持っていない限り、null を返します。  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]詳細については、「[メタデータ表示の構成](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [オブジェクトカタログビュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [SQL Server システムカタログに対するクエリについてよく寄せられる質問](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [&#40;Transact-sql&#41;の列](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [all_columns &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [computed_columns &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-computed-columns-transact-sql.md)   
 [列ストアインデックスガイド](~/relational-databases/indexes/columnstore-indexes-overview.md)    
 [column_store_dictionaries &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-column-store-dictionaries-transact-sql.md)  
  
  

