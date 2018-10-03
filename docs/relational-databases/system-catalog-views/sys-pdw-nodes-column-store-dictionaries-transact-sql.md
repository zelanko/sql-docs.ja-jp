---
title: sys.pdw_nodes_column_store_dictionaries (TRANSACT-SQL) |Microsoft Docs
ms.date: 03/03/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.custom: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 7ae1c2e4-45c0-4880-a692-1f299fbcfd19
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: eeed58e54510748969b1111e09c3791a9320d23c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47732776"
---
# <a name="syspdwnodescolumnstoredictionaries-transact-sql"></a>sys.pdw_nodes_column_store_dictionaries (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  列ストア インデックスで使用される各ディクショナリの行が含まれています。 ディクショナリは、すべてのデータ型ではなく一部のデータ型のエンコードに使用されるため、列ストア インデックスのすべての列にディクショナリがあるわけではありません。 ディクショナリは、プライマリ ディクショナリ (すべてのセグメント用) として、および列のセグメントのサブセットに対して使用される別のセカンダリ ディクショナリ用として存在する可能性があります。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**partition_id**|**bigint**|パーティション ID を示します。 データベース内で一意です。|  
|**hobt_id**|**bigint**|この列ストア インデックスを保持するテーブルのヒープまたは B ツリー インデックス (hobt) の ID。|  
|**column_id**|**int**|列ストアの列の ID。|  
|**dictionary_id**|**int**|ディクショナリの ID。|  
|**version**|**int**|ディクショナリの形式のバージョン。|  
|**type**|**int**|ディクショナリの種類:<br /><br /> 1 – 含むハッシュ ディクショナリ**int**値<br /><br /> 2 – 使用されていません<br /><br /> 3 - 文字列値を含むハッシュ ディクショナリ<br /><br /> 4 – ハッシュ ディクショナリを格納している**float**値|  
|**last_id**|**int**|ディクショナリの最後のデータ ID。|  
|**entry_count**|**bigint**|ディクショナリ内のエントリの数。|  
|**on_disc_size**|**bigint**|ディクショナリのサイズ (バイト単位)。|  
|**pdw_node_id**|**int**|一意の識別子、[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]ノード。|  
  
## <a name="permissions"></a>アクセス許可  
 VIEW SERVER STATE 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と Parallel Data Warehouse カタログ ビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [列ストア インデックスを作成&#40;TRANSACT-SQL&#41;](../../t-sql/statements/create-columnstore-index-transact-sql.md)   
 [sys.pdw_nodes_column_store_segments &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-segments-transact-sql.md)   
 [sys.pdw_nodes_column_store_row_groups &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-row-groups-transact-sql.md)  
  
  
