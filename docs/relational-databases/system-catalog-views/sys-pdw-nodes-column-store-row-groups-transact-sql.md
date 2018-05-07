---
title: sys.pdw_nodes_column_store_row_groups (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/03/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 17a4c925-d4b5-46ee-9cd6-044f714e6f0e
caps.latest.revision: 10
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 99577a71d2819ca0d2ce86d901eecf5ce87ae7ab
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="syspdwnodescolumnstorerowgroups-transact-sql"></a>sys.pdw_nodes_column_store_row_groups (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  管理者が下すシステム管理に役立つセグメント単位でクラスター化列ストア インデックス情報を提供[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]です。 **sys.pdw_nodes_column_store_row_groups** has a column for the total number of rows physically stored (including those marked as deleted) and a column for the number of rows marked as deleted. 使用して**sys.pdw_nodes_column_store_row_groups**行を判断するグループが削除された行の割合が高いと、再構築する必要があります。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|基になるテーブルの ID です。 これは、コンピューティング ノードで、コントロールのノード上の論理のテーブルの object_id いない物理テーブルです。 たとえば、object_id は、sys.tables の object_id と一致しません。<br /><br /> Sys.tables で参加するには、sys.pdw_index_mappings を使用します。|  
|**index_id**|**int**|上のクラスター化列ストア インデックスの ID *object_id*テーブル。|  
|**partition_number**|**int**|行グループを保持するテーブルのパーティションの ID *row_group_id*です。 使用することができます*partition_number*この DMV を sys.partitions に結合します。|  
|**row_group_id**|**int**|この行グループの ID です。 この番号はパーティション内で一意です。|  
|**dellta_store_hobt_id**|**bigint**|デルタ行グループの hobt_id で、行グループの種類がデルタではない場合は NULL。 デルタ行グループとは、新しいレコードを受け入れる読み取り/書き込み行グループのことです。 デルタ行グループには、**開く**状態です。 デルタ行グループは、行ストア形式のままであり、列ストア形式に圧縮されていません。|  
|**状態**|**tinyint**|state_description に関連付けられている ID 番号。<br /><br /> 1 = OPEN <br /><br /> 2 = CLOSED <br /><br /> 3 = COMPRESSED|  
|**state_desccription**|**nvarchar(60)**|行グループの永続的な状態の説明:<br /><br /> OPEN - 新しいレコードを受け入れる読み取り/書き込み行グループ。 OPEN の行グループは、行ストア形式のままであり、列ストア形式に圧縮されていません。<br /><br /> CLOSED - いっぱいになったが、組ムーバー プロセスによってまだ圧縮されていない行グループ。<br /><br /> COMPRESSED - いっぱいになり、圧縮された行グループ。|  
|**total_rows**|**bigint**|行グループに物理的に格納されている行の合計。 削除された行がまだ格納されていることがあります。 1 つの行グループの最大行数は 1,048,576 (16 進数では FFFFF) です。|  
|**deleted_rows**|**bigint**|削除対象としてマークされた行グループ内に物理的に格納されている行の数。<br /><br /> 常にデルタの場合は 0 の行グループ。|  
|**size_in_bytes**|**int**|この行グループ内のすべてのページのバイト単位の合計サイズ。 このサイズでは、メタデータと共有辞書の格納に必要なサイズは含まれません。|  
|**pdw_node_id**|**int**|一意の id、[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]ノード。|  
|**distribution_id**|**int**|分布の一意の id。|
  
## <a name="remarks"></a>解説  
 クラスター化または非クラスター化列ストア インデックスがある各テーブルの列ストア行グループごとに 1 つの行を返します。  
  
 使用して**sys.pdw_nodes_column_store_row_groups**行グループおよび行グループのサイズに含まれる行の数を決定します。  
  
 行グループ内の削除済みの行の数が合計行数に対して占める割合が高くなると、テーブルの効率が低下します。 テーブルのサイズが小さくなるよう列ストア インデックスを再構築して、テーブルを読み取るために必要なディスク I/O を削減します。 使用して列ストア インデックスを再構築する、**リビルド**のオプション、 **ALTER INDEX**ステートメントです。  
  
 更新可能な列ストアが最初に新規データを挿入、**開く**状態の行グループが行ストア形式とも呼ばれることに、デルタ テーブルとして。  開いている行グループがいっぱいの状態に変わります**CLOSED**です。 Closed 行グループは、組ムーバーによって列ストア形式に圧縮し、状態が**圧縮**です。  組ムーバーは、定期的に起動され、列ストア行グループに圧縮する準備ができている CLOSED 状態の行グループがあるかどうかを確認するバックグラウンド プロセスです。  また、組ムーバーは、すべての行が削除された行グループの割り当てを解除します。 割り当てが解除された行グループとしてマークされている**廃止**です。 組ムーバーを直ちに実行するを使用して、 **REORGANIZE**のオプション、 **ALTER INDEX**ステートメントです。  
  
 列ストア行グループは、いっぱいになると圧縮され、新しい行の受け入れを停止します。 圧縮されたグループから行が削除されると、削除された行は、保持されますが、削除済みとしてマークされます。 圧縮されたグループに対する更新は、圧縮されたグループからの削除、および OPEN 状態のグループへの挿入として実装されます。  
  
## <a name="permissions"></a>権限  
 **VIEW SERVER STATE** アクセス許可が必要です。  
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>例: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] および [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の例の結合、 **sys.pdw_nodes_column_store_row_groups**特定のテーブルに関する情報を返すには、他のシステム テーブル。 計算済みの `PercentFull` 列は、行グループの効率の推定値を示します。 1 つのテーブルの削除については、WHERE 句の前にあるコメント ハイフンを検索し、テーブル名を指定します。  
  
```  
SELECT IndexMap.object_id,   
  object_name(IndexMap.object_id) AS LogicalTableName,   
  i.name AS LogicalIndexName, IndexMap.index_id, NI.type_desc,   
  IndexMap.physical_name AS PhyIndexNameFromIMap,   
  CSRowGroups.*,  
  100*(ISNULL(deleted_rows,0))/total_rows AS PercentDeletedRows   
FROM sys.tables AS t  
JOIN sys.indexes AS i  
    ON t.object_id = i.object_id  
JOIN sys.pdw_index_mappings AS IndexMap  
    ON i.object_id = IndexMap.object_id  
    AND i.index_id = IndexMap.index_id  
JOIN sys.pdw_nodes_indexes AS NI  
    ON IndexMap.physical_name = NI.name  
    AND IndexMap.index_id = NI.index_id  
JOIN sys.pdw_nodes_column_store_row_groups AS CSRowGroups  
    ON CSRowGroups.object_id = NI.object_id   
    AND CSRowGroups.pdw_node_id = NI.pdw_node_id  
AND CSRowGroups.index_id = NI.index_id      
--WHERE t.name = '<table_name>'   
ORDER BY object_name(i.object_id), i.name, IndexMap.physical_name, pdw_node_id;  
```  

次[!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)]多数の行は、開く、終了、または圧縮行グループには、クラスター化列ストアにもについて、例がパーティションあたりの行数をカウントします。  

```
SELECT
    s.name AS [Schema Name]
    ,t.name AS [Table Name]
    ,rg.partition_number AS [Partition Number]
    ,SUM(rg.total_rows) AS [Total Rows]
    ,SUM(CASE WHEN rg.State = 1 THEN rg.Total_rows Else 0 END) AS [Rows in OPEN Row Groups]
    ,SUM(CASE WHEN rg.State = 2 THEN rg.Total_Rows ELSE 0 END) AS [Rows in Closed Row Groups]
    ,SUM(CASE WHEN rg.State = 3 THEN rg.Total_Rows ELSE 0 END) AS [Rows in COMPRESSED Row Groups]
FROM sys.pdw_nodes_column_store_row_groups rg
JOIN sys.pdw_nodes_tables pt
ON rg.object_id = pt.object_id AND rg.pdw_node_id = pt.pdw_node_id AND pt.distribution_id = rg.distribution_id
JOIN sys.pdw_table_mappings tm
ON pt.name = tm.physical_name
INNER JOIN sys.tables t
ON tm.object_id = t.object_id
INNER JOIN sys.schemas s
ON t.schema_id = s.schema_id
GROUP BY s.name, t.name, rg.partition_number
ORDER BY 1, 2
```
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と並列データ ウェアハウスのカタログ ビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [列ストア インデックスを作成する&#40;TRANSACT-SQL&#41;](../../t-sql/statements/create-columnstore-index-transact-sql.md)   
 [sys.pdw_nodes_column_store_segments &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-segments-transact-sql.md)   
 [sys.pdw_nodes_column_store_dictionaries &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-dictionaries-transact-sql.md)  
  
  
