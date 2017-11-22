---
title: "sys.pdw_nodes_column_store_dictionaries (TRANSACT-SQL) |Microsoft ドキュメント"
ms.date: 03/03/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 7ae1c2e4-45c0-4880-a692-1f299fbcfd19
caps.latest.revision: "7"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 72c2787caf0a60e6939ba72199329b8ad79103ca
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="syspdwnodescolumnstoredictionaries-transact-sql"></a>sys.pdw_nodes_column_store_dictionaries (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  列ストア インデックスで使用される各ディクショナリの行が含まれています。 ディクショナリは、すべてのデータ型ではなく一部のデータ型のエンコードに使用されるため、列ストア インデックスのすべての列にディクショナリがあるわけではありません。 ディクショナリは、プライマリ ディクショナリ (すべてのセグメント用) として、および列のセグメントのサブセットに対して使用される別のセカンダリ ディクショナリ用として存在する可能性があります。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**partition_id**|**bigint**|パーティション ID を示します。 データベース内で一意です。|  
|**hobt_id で**|**bigint**|この列ストア インデックスを保持するテーブルのヒープまたは B ツリー インデックス (hobt) の ID。|  
|**column_id**|**int**|列ストアの列の ID。|  
|**dictionary_id**|**int**|ディクショナリの ID。|  
|**version**|**int**|ディクショナリの形式のバージョン。|  
|**型**|**int**|ディクショナリの種類:<br /><br /> 1 – 含むハッシュ ディクショナリ**int**値<br /><br /> 2 – 使用されていません<br /><br /> 3 - 文字列値を含むハッシュ ディクショナリ<br /><br /> 4 – 含むハッシュ ディクショナリ**float**値|  
|**持っていない場合**|**int**|ディクショナリの最後のデータ ID。|  
|**entry_count**|**bigint**|ディクショナリ内のエントリの数。|  
|**on_disc_size**|**bigint**|ディクショナリのサイズ (バイト単位)。|  
|**pdw_node_id**|**int**|一意の識別子、[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]ノード。|  
  
## <a name="permissions"></a>Permissions  
 VIEW SERVER STATE 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と並列データ ウェアハウスのカタログ ビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [COLUMNSTORE INDEX &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-columnstore-index-transact-sql.md)   
 [sys.pdw_nodes_column_store_segments と #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-segments-transact-sql.md)   
 [sys.pdw_nodes_column_store_row_groups &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-row-groups-transact-sql.md)  
  
  
