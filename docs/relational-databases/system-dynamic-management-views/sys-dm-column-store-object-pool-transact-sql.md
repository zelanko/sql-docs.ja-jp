---
title: dm_column_store_object_pool (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: a8a58ca7-0a7d-4786-bfd9-e8894bd345dd
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c6bd55fb4bf466352a3aac861844669e70b762a1
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82824690"
---
# <a name="sysdm_column_store_object_pool-transact-sql"></a>dm_column_store_object_pool (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

 列ストアインデックスオブジェクトのさまざまな種類のオブジェクトメモリプール使用率のカウントを返します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|`database_id`|`int`|データベースの ID です。 これは、SQL Server データベースまたは Azure SQL データベースサーバーのインスタンス内で一意です。 |  
|`object_id`|`int`|オブジェクトの ID。 オブジェクトは object_types の1つです。 | 
|`index_id`|`int`|列ストアインデックスの ID。|  
|`partition_number`|`bigint`|インデックスまたはヒープ内の、1 から始まるパーティション番号。 すべてのテーブルまたはビューには、少なくとも1つのパーティションがあります。| 
|`column_id`|`int`|列ストア列の ID。 これは DELETE_BITMAP の場合は NULL です。| 
|`row_group_id`|`int`|行グループの ID。|
|`object_type`|`smallint`|1 = COLUMN_SEGMENT<br /><br /> 2 = COLUMN_SEGMENT_PRIMARY_DICTIONARY<br /><br /> 3 = COLUMN_SEGMENT_SECONDARY_DICTIONARY<br /><br /> 4 = COLUMN_SEGMENT_BULKINSERT_DICTIONARY<br /><br /> 5 = COLUMN_SEGMENT_DELETE_BITMAP|  
|`object_type_desc`|`nvarchar(60)`|COLUMN_SEGMENT-列セグメント。 `object_id`セグメント ID を示します。 セグメントは、1つの行グループ内の1つの列のすべての値を格納します。 たとえば、テーブルに10個の列がある場合、行グループごとに10個の列セグメントがあります。 <br /><br /> COLUMN_SEGMENT_PRIMARY_DICTIONARY-テーブル内のすべての列セグメントの参照情報を格納するグローバルディクショナリ。<br /><br /> COLUMN_SEGMENT_SECONDARY_DICTIONARY-1 つの列に関連付けられているローカルディクショナリ。<br /><br /> COLUMN_SEGMENT_BULKINSERT_DICTIONARY-グローバルディクショナリの別の表現。 これにより、dictionary_id する値の逆参照が提供されます。 組ムーバーまたは一括読み込みの一部として圧縮セグメントを作成するために使用されます。<br /><br /> COLUMN_SEGMENT_DELETE_BITMAP-セグメントの削除を追跡するビットマップ。 パーティションごとに1つの削除ビットマップがあります。|  
|`access_count`|`int`|このオブジェクトへの読み取りまたは書き込みアクセスの数。|  
|`memory_used_in_bytes`|`bigint`|オブジェクトプール内のこのオブジェクトによって使用されるメモリ。|  
|`object_load_time`|`datetime`|Object_id がオブジェクトプールに取り込まれた時刻。|  
  
## <a name="permissions"></a>アクセス許可  

で [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] は、 `VIEW SERVER STATE` 権限が必要です。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]Premium レベルでは、データベースの権限が必要です `VIEW DATABASE STATE` 。 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]Standard レベルおよび Basic レベルでは、**サーバー管理**者または**Azure Active Directory 管理者**アカウントが必要です。   
 
## <a name="see-also"></a>参照  
  
 [Transact-sql&#41;&#40;インデックス関連の動的管理ビューおよび関数](../../relational-databases/system-dynamic-management-views/index-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)   
 [dm_db_index_operational_stats &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql.md)   
 [SQL&#41;&#40;Transact-sql のインデックス](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [パフォーマンスの監視とチューニング](../../relational-databases/performance/monitor-and-tune-for-performance.md)  
  
  
