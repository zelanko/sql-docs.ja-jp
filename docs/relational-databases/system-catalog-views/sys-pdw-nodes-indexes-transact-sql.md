---
title: sys.pdw_nodes_indexes (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 261bcb7f-a906-4979-b274-bc5f1aa66426
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 1eb00d935eccd8f6af4d4ffef1c01fe42824f355
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47856410"
---
# <a name="syspdwnodesindexes-transact-sql"></a>sys.pdw_nodes_indexes (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  インデックスを返します[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]します。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|object_id|**int**|このインデックスが属しているオブジェクトの id です。||  
|NAME|**sysname**|インデックスの名前です。 名前は、オブジェクト内でのみ一意です。 NULL = ヒープ||  
|index_id|**int**|インデックスの id です。 index_id は、オブジェクト内でのみ一意です。<br /><br /> 0 = ヒープ<br /><br /> 1 = クラスター化インデックス<br /><br /> > 1 = 非クラスター化インデックス||  
|type|**tinyint**|インデックスの種類です。<br /><br /> 0 = ヒープ<br /><br /> 1 = クラスター化<br /><br /> 2 = の非クラスター化<br /><br /> 5 = クラスター化 xVelocity メモリ最適化列ストア インデックス|  
|type_desc|**nvarchar(60)**|インデックスの種類の説明。<br /><br /> HEAP<br /><br /> CLUSTERED<br /><br /> NONCLUSTERED<br /><br /> クラスター化列ストア||  
|is_unique|**bit**|0 = インデックスは一意ではありません。|常に 0 です。|  
|data_space_id|**int**|このインデックスのデータ領域の id です。 データ領域は、ファイル グループまたはパーティション構成です。<br /><br /> 0 = object_id には、テーブル値関数です。||  
|ignore_dup_key|**bit**|0 = IGNORE_DUP_KEY はオフです。|常に 0 です。|  
|is_primary_key|**bit**|1 = インデックスは PRIMARY KEY 制約の一部です。|常に 0 です。|  
|is_unique_constraint|**bit**|1 = インデックスは UNIQUE 制約の一部です。|常に 0 です。|  
|fill_factor|**tinyint**|> 0 = インデックスが作成または再構築された場合に使用される FILLFACTOR のパーセンテージです。<br /><br /> 0 = 既定値|常に 0 です。|  
|is_padded|**bit**|0 = PADINDEX がオフです。|常に 0 です。|  
|is_disabled|**bit**|1 = インデックスは無効です。<br /><br /> 0 = インデックスは無効ではありません。||  
|is_hypothetical|**bit**|0 = インデックスは仮想的ではありません。|常に 0 です。|  
|allow_row_locks|**bit**|1 = インデックスは行ロックを許可します。|常に 1 です。|  
|allow_page_locks|**bit**|1 = インデックスはページ ロックを許可します。|常に 1 です。|  
|has_filter|**bit**|0 = インデックスにフィルターはありません。|常に 0 です。|  
|filter_definition|**nvarchar(max)**|フィルター選択されたインデックスに含まれる行のサブセットの式。|常に NULL になります。|  
|pdw_node_id|**int**|一意の識別子、[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]ノード。|NOT NULL|  
  
## <a name="permissions"></a>アクセス許可  
 CONTROL SERVER 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と Parallel Data Warehouse カタログ ビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
