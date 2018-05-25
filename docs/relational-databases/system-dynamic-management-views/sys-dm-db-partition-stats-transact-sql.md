---
title: sys.dm_db_partition_stats (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
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
caps.latest.revision: 30
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 99e0d57f7d2bf82b0bffaf7ae97ba0181459290d
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmdbpartitionstats-transact-sql"></a>sys.dm_db_partition_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  現在のデータベースのパーティションごとに、ページ数と行数の情報を返します。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して**sys.dm_pdw_nodes_db_partition_stats**です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**partition_id**|**bigint**|パーティションの ID。 これは、データベース内で一意です。 これは、同じ値として、 **partition_id**で、 **sys.partitions**カタログ ビュー|  
|**object_id**|**int**|パーティションが属するテーブルまたはインデックス付きビューのオブジェクト ID。|  
|**index_id**|**int**|パーティションが属するヒープまたはインデックスの ID。<br /><br /> 0 = ヒープ<br /><br /> 1 = クラスター化インデックス<br /><br /> > 1 = 非クラスター化インデックス|  
|**partition_number**|**int**|インデックスまたはヒープ内の、1 から始まるパーティション番号。|  
|**in_row_data_page_count**|**bigint**|パーティションで行内データの格納に使用されているページ数。 パーティションがヒープに属している場合、値はヒープのデータ ページ数になります。 パーティションがインデックスに属している場合、値はリーフ レベルのページ数になります。 B-Tree の非リーフ ページは含まれません。どちらの場合も、IAM (Index Allocation Map) ページは含まれません。 xVelocity メモリ最適化列ストア インデックスでは、常に 0 です。|  
|**in_row_used_page_count**|**bigint**|パーティションで行内データの格納と管理に使用されているページの合計数。 この数には、非リーフ b-tree ページ、IAM ページ、およびに含まれるすべてのページが含まれています、 **in_row_data_page_count**列です。 列ストア インデックスでは、常に 0 です。|  
|**in_row_reserved_page_count**|**bigint**|パーティションで行内データの格納と管理に予約されているページの合計数。ページが使用されているかどうかは考慮されません。 列ストア インデックスでは、常に 0 です。|  
|**lob_used_page_count**|**bigint**|格納して、行外を管理するために使用されているページ数**テキスト**、 **ntext**、**イメージ**、 **varchar (max)**、 **nvarchar(max)**、 **varbinary (max)**、および**xml**パーティション内の列です。 IAM ページは含まれます。<br /><br /> パーティションで列ストア インデックスの格納と管理に使用されている LOB の合計数。|  
|**lob_reserved_page_count**|**bigint**|合計を格納して、行外を管理するために予約ページ数**テキスト**、 **ntext**、**イメージ**、 **varchar (max)**、 **nvarchar (max)**、 **varbinary (max)**、および**xml**かどうかは、ページで使用するかに関係なく、パーティション内の列です。 IAM ページは含まれます。<br /><br /> パーティションで列ストア インデックスの格納と管理のために予約されている LOB の合計数。|  
|**row_overflow_used_page_count**|**bigint**|格納および行オーバーフローの管理に使用されているページ数**varchar**、 **nvarchar**、 **varbinary**、および**sql_variant**列内でのパーティション。 IAM ページは含まれます。<br /><br /> 列ストア インデックスでは、常に 0 です。|  
|**row_overflow_reserved_page_count**|**bigint**|格納および行オーバーフローの管理に予約されているページの合計数**varchar**、 **nvarchar**、 **varbinary**、および**sql_variant**かどうかは、ページで使用するかに関係なく、パーティション内の列です。 IAM ページは含まれます。<br /><br /> 列ストア インデックスでは、常に 0 です。|  
|**used_page_count**|**bigint**|パーティションで使用されているページの合計数。 として計算**in_row_used_page_count** + **lob_used_page_count** + **row_overflow_used_page_count**です。|  
|**reserved_page_count**|**bigint**|パーティションで予約されているページの合計数。 として計算**in_row_reserved_page_count** + **lob_reserved_page_count** + **row_overflow_reserved_page_count**です。|  
|**row_count**|**bigint**|パーティション内の行数の概算値です。|  
|**pdw_node_id**|**int**|**適用されます**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この分布はでは、ノードの識別子。|  
|**distribution_id**|**int**|**適用されます**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> 分布に関連付けられている一意の数値 id です。|  
  
## <a name="remarks"></a>解説  
 **sys.dm_db_partition_stats**格納し、行内データ、LOB データ、および行オーバーフロー データをデータベース内のすべてのパーティションを管理するために使用領域に関する情報が表示されます。 ここではパーティションごとに 1 行が表示されます。  
  
 出力の基になる数字は、メモリにキャッシュされるか、各種システム テーブルのディスクに格納されます。  
  
 行内データ、LOB データ、行オーバーフロー データは、パーティションを構成する 3 つのアロケーション ユニットです。 [Sys.allocation_units](../../relational-databases/system-catalog-views/sys-allocation-units-transact-sql.md)カタログ ビューは、データベースの各アロケーション ユニットに関するメタデータに対してクエリを実行できます。  
  
 パーティション分割されていないヒープまたはインデックスは、1 つのパーティション (パーティション番号 = 1) で構成されています。したがって、このようなヒープまたはインデックスの場合は 1 行だけが返されます。 [Sys.partitions](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)カタログ ビューはすべてのテーブルと、データベース内のインデックスの各パーティションに関するメタデータに対してクエリを実行できます。  
  
 各テーブルまたはインデックスの合計数は、関連するすべてのパーティションにおける数を加算することで取得されます。  
  
## <a name="permissions"></a>権限  
 クエリに VIEW DATABASE STATE 権限が必要です、 **sys.dm_db_partition_stats**動的管理ビュー。 動的管理ビューに対するアクセス許可の詳細については、次を参照してください。[動的管理ビューおよび関数&#40;TRANSACT-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-returning-all-counts-for-all-partitions-of-all-indexes-and-heaps-in-a-database"></a>A. データベースにあるすべてのインデックスとヒープに関するすべてのパーティションについて、ページ数や行数の情報を返す  
 次の例は、すべてのすべてのインデックスのすべてのパーティション数が表示し、ヒープ、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT * FROM sys.dm_db_partition_stats;  
GO  
```  
  
### <a name="b-returning-all-counts-for-all-partitions-of-a-table-and-its-indexes"></a>B. テーブルとテーブルのインデックスに関するすべてのパーティションについて、ページ数や行数の情報を返す  
 次の例では、`HumanResources.Employee` テーブルとテーブルのインデックスに関するすべてのパーティションについて、ページ数や行数を表示します。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT * FROM sys.dm_db_partition_stats   
WHERE object_id = OBJECT_ID('HumanResources.Employee');  
GO  
```  
  
### <a name="c-returning-total-used-pages-and-total-number-of-rows-for-a-heap-or-clustered-index"></a>C. ヒープまたはクラスター化インデックスについて、合計使用ページ数と合計行数を返す  
 次の例では、ヒープまたはクラスター化インデックスの合計使用ページと行の合計数を返します、`HumanResources.Employee`テーブル。 `Employee`既定ではテーブルがパーティション分割されていない、合計には、1 つのパーティションが含まれています。  
  
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
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [データベース関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  


