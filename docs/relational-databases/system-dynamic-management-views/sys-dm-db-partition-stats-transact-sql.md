---
title: dm_db_partition_stats (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 05/31/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_db_partition_stats
- dm_db_partition_stats_TSQL
- sys.dm_db_partition_stats_TSQL
- sys.dm_db_partition_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_partition_stats dynamic management view
ms.assetid: 9db9d184-b3a2-421e-a804-b18ebcb099b7
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: cb9ab9e3cbf5948e5e832171c179d6daa2c0bc28
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68096282"
---
# <a name="sysdm_db_partition_stats-transact-sql"></a>sys.dm_db_partition_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  現在のデータベースのパーティションごとに、ページ数と行数の情報を返します。  
  
> [!NOTE]  
>  またはから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]これを[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]呼び出すには、 **dm_pdw_nodes_db_partition_stats**という名前を使用します。 Dm_pdw_nodes_db_partition_stats の partition_id は、Azure SQL Data Warehouse のための、sys. パーティションカタログビューの partition_id とは異なります。
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**partition_id**|**bigint**|パーティションの ID。 データベース内で一意です。 この値は、Azure SQL Data Warehouse を除き、[**パーティション**] カタログビューの**partition_id**と同じです。|  
|**object_id**|**int**|パーティションが属するテーブルまたはインデックス付きビューのオブジェクト ID。|  
|**index_id**|**int**|パーティションが属するヒープまたはインデックスの ID。<br /><br /> 0 = ヒープ<br /><br /> 1 = クラスター化インデックス<br /><br /> > 1 = 非クラスター化インデックス|  
|**partition_number**|**int**|インデックスまたはヒープ内の、1 から始まるパーティション番号。|  
|**in_row_data_page_count**|**bigint**|パーティションで行内データの格納に使用されているページ数。 パーティションがヒープに属している場合、値はヒープのデータ ページ数になります。 パーティションがインデックスに属している場合、値はリーフ レベルのページ数になります。 (B-tree の非リーフページはカウントに含まれません)。どちらの場合も、IAM (Index Allocation Map) ページは含まれません。 xVelocity メモリ最適化列ストア インデックスでは、常に 0 です。|  
|**in_row_used_page_count**|**bigint**|パーティションで行内データの格納と管理に使用されているページの合計数。 この数には、非リーフ B-tree ページ、IAM ページ、および **in_row_data_page_count** 列内にあるすべてのページが含まれます。 列ストア インデックスでは、常に 0 です。|  
|**in_row_reserved_page_count**|**bigint**|パーティションで行内データの格納と管理に予約されているページの合計数。ページが使用されているかどうかは考慮されません。 列ストア インデックスでは、常に 0 です。|  
|**lob_used_page_count**|**bigint**|パーティションで行外の **text**、**ntext**、**image**、**varchar(max)**、**nvarchar(max)**、**varbinary(max)**、**xml** 型列の格納と管理に使用されているページ数。 IAM ページは含まれます。<br /><br /> パーティションで列ストア インデックスの格納と管理に使用されている LOB の合計数。|  
|**lob_reserved_page_count**|**bigint**|パーティションで行外の **text**、**ntext**、**image**、**varchar(max)**、**nvarchar(max)**、**varbinary(max)**、**xml** 型列の格納と管理に予約されているページの合計数。ページが使用されているかどうかは考慮されません。 IAM ページは含まれます。<br /><br /> パーティションで列ストア インデックスの格納と管理のために予約されている LOB の合計数。|  
|**row_overflow_used_page_count**|**bigint**|パーティションで行オーバーフローの **varchar**、**nvarchar**、**varbinary**、**sql_variant** 型列の格納と管理に使用されているページ数。 IAM ページは含まれます。<br /><br /> 列ストア インデックスでは、常に 0 です。|  
|**row_overflow_reserved_page_count**|**bigint**|パーティションで行オーバーフローの **varchar**、**nvarchar**、**varbinary**、**sql_variant** 型列の格納と管理に予約されているページの合計数。ページが使用されているかどうかは考慮されません。 IAM ページは含まれます。<br /><br /> 列ストア インデックスでは、常に 0 です。|  
|**used_page_count**|**bigint**|パーティションで使用されているページの合計数。 **In_row_used_page_count** + **lob_used_page_count**lob_used_page_count + **row_overflow_used_page_count**として計算されます。|  
|**reserved_page_count**|**bigint**|パーティションで予約されているページの合計数。 **In_row_reserved_page_count** + **lob_reserved_page_count**lob_reserved_page_count + **row_overflow_reserved_page_count**として計算されます。|  
|**row_count**|**bigint**|パーティション内の行数の概算値です。|  
|**pdw_node_id**|**int**|**適用対象**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> このディストリビューションが配置されているノードの識別子。|  
|**distribution_id**|**int**|**適用対象**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> 分布に関連付けられている一意の数値 id です。|  
  
## <a name="remarks"></a>Remarks  
 **sys.dm_db_partition_stats** では、データベースにあるすべてのパーティションの行内データ、LOB データ、行オーバーフロー データについて、格納と管理に使用されている領域に関する情報が表示されます。 ここではパーティションごとに 1 行が表示されます。  
  
 出力の基になる数字は、メモリにキャッシュされるか、各種システム テーブルのディスクに格納されます。  
  
 行内データ、LOB データ、行オーバーフロー データは、パーティションを構成する 3 つのアロケーション ユニットです。 [sys.allocation_units](../../relational-databases/system-catalog-views/sys-allocation-units-transact-sql.md) カタログ ビューに対して、データベースの各アロケーション ユニットに関するメタデータを取得するクエリを実行できます。  
  
 パーティション分割されていないヒープまたはインデックスは、1 つのパーティション (パーティション番号 = 1) で構成されています。したがって、このようなヒープまたはインデックスの場合は 1 行だけが返されます。 [sys.partitions](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md) カタログ ビューに対して、データベースのすべてのテーブルとインデックスの、各パーティションに関するメタデータを取得するクエリを実行できます。  
  
 各テーブルまたはインデックスの合計数は、関連するすべてのパーティションにおける数を加算することで取得されます。  
  
## <a name="permissions"></a>アクセス許可  
 **sys.dm_db_partition_stats** 動的管理ビューに対してクエリを実行するには、VIEW DATABASE STATE 権限が必要です。 動的管理ビューに対する権限の詳細については、「 [transact-sql&#41;&#40;の動的管理ビューおよび関数](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)」を参照してください。  
  
## <a name="examples"></a>例  
  
### <a name="a-returning-all-counts-for-all-partitions-of-all-indexes-and-heaps-in-a-database"></a>A. データベースにあるすべてのインデックスとヒープに関するすべてのパーティションについて、ページ数や行数の情報を返す  
 次の例では、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベースにあるすべてのインデックスとヒープに関するすべてのパーティションについて、ページ数や行数を表示します。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT * FROM sys.dm_db_partition_stats;  
GO  
```  
  
### <a name="b-returning-all-counts-for-all-partitions-of-a-table-and-its-indexes"></a>B. テーブルとそのインデックスのすべてのパーティションについて、すべてのカウントを返す  
 次の例では、`HumanResources.Employee` テーブルとテーブルのインデックスに関するすべてのパーティションについて、ページ数や行数を表示します。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT * FROM sys.dm_db_partition_stats   
WHERE object_id = OBJECT_ID('HumanResources.Employee');  
GO  
```  
  
### <a name="c-returning-total-used-pages-and-total-number-of-rows-for-a-heap-or-clustered-index"></a>C. ヒープまたはクラスター化インデックスについて、合計使用ページ数と合計行数を返す  
 次の例では、`HumanResources.Employee` テーブルのヒープまたはクラスター化インデックスについて、合計使用ページ数と合計行数を返します。 `Employee` テーブルは既定ではパーティション分割されていないため、合計値には 1 つのパーティションだけが含まれます。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT SUM(used_page_count) AS total_number_of_used_pages,   
    SUM (row_count) AS total_number_of_rows   
FROM sys.dm_db_partition_stats  
WHERE object_id=OBJECT_ID('HumanResources.Employee')    AND (index_id=0 or index_id=1);  
GO  
```  
  
## <a name="see-also"></a>参照  
 [Transact-sql&#41;&#40;の動的管理ビューおよび関数](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Transact-sql&#41;&#40;データベース関連の動的管理ビュー](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  


