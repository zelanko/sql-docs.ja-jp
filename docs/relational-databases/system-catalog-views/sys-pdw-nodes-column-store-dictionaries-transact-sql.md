---
title: システムの起動 (_s) (Transact-sql) (_d) |Microsoft Docs
ms.date: 03/03/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.custom: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 7ae1c2e4-45c0-4880-a692-1f299fbcfd19
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 618a92cfd0f1602753b9fcfd61ac232eff5cecd4
ms.sourcegitcommit: 43c3d8939f6f7b0ddc493d8e7a643eb7db634535
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305185"
---
# <a name="syspdw_nodes_column_store_dictionaries-transact-sql"></a>システム辞書 (Transact-sql) (_d) (_s)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  列ストアインデックスで使用されるディクショナリごとに1行の値を格納します。 ディクショナリは、すべてのデータ型ではなく一部のデータ型のエンコードに使用されるため、列ストア インデックスのすべての列にディクショナリがあるわけではありません。 ディクショナリは、プライマリ ディクショナリ (すべてのセグメント用) として、および列のセグメントのサブセットに対して使用される別のセカンダリ ディクショナリ用として存在する可能性があります。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**partition_id**|**bigint**|パーティション ID を示します。 データベース内で一意です。|  
|**hobt_id**|**bigint**|この列ストアインデックスを持つテーブルのヒープまたは B ツリーインデックス (HoBT) の ID。|  
|**column_id**|**int**|列ストア列の ID。|  
|**dictionary_id**|**int**|ディクショナリの Id。|  
|**version**|**int**|ディクショナリの形式のバージョン。|  
|**type**|**int**|ディクショナリの種類:<br /><br /> 1- **int**値を含むハッシュディクショナリ<br /><br /> 2-使用されていません<br /><br /> 3-文字列値を含むハッシュディクショナリ<br /><br /> 4- **float**値を含むハッシュディクショナリ|  
|**last_id**|**int**|ディクショナリ内の最後のデータ id。|  
|**entry_count**|**bigint**|ディクショナリ内のエントリの数。|  
|**on_disc_size**|**bigint**|ディクショナリのサイズ (バイト単位)。|  
|**pdw_node_id**|**int**|@No__t 0 ノードの一意識別子。|  
  
## <a name="permissions"></a>アクセス許可  
 `VIEW SERVER STATE` 権限が必要です。  
  
## <a name="see-also"></a>関連項目  
 [SQL Data Warehouse and Parallel Data Warehouse Catalog Views (SQL Data Warehouse および Parallel Data Warehouse のカタログ ビュー)](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [CREATE 列ストア&#40;インデックス transact-sql&#41;](../../t-sql/statements/create-columnstore-index-transact-sql.md)   
 [SQL server &#40;&#41;の transact-sql](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-segments-transact-sql.md)  を再分割する (_d)  
 [SQL server の配置 (_s) &#40;transact-sql (_s)&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-row-groups-transact-sql.md)  
  
  
