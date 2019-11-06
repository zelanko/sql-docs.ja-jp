---
title: sys.pdw_nodes_column_store_row_groups (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 17a4c925-d4b5-46ee-9cd6-044f714e6f0e
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: e89405e04a06e8171c69b81066be743ee99d4534
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68106707"
---
# <a name="syspdwnodescolumnstorerowgroups-transact-sql"></a>sys.pdw_nodes_column_store_row_groups (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  管理者の下すシステム管理に役立つセグメント単位でクラスター化列ストア インデックス情報を提供[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]します。 **sys.pdw_nodes_column_store_row_groups** has a column for the total number of rows physically stored (including those marked as deleted) and a column for the number of rows marked as deleted. 使用**sys.pdw_nodes_column_store_row_groups**行を判断するグループが削除された行の割合が高いと、再構築する必要があります。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|基になるテーブルの ID です。 これは、コンピューティング ノードで、コントロールのノードの論理テーブルの object_id いない物理テーブルです。 たとえば、object_id は、sys.tables の object_id は一致しません。<br /><br /> Sys.tables を参加させるのには、sys.pdw_index_mappings を使用します。|  
|**index_id**|**int**|上のクラスター化列ストア インデックスの ID *object_id*テーブル。|  
|**partition_number**|**int**|行グループを保持するテーブルのパーティションの ID *row_group_id*します。 使用することができます*partition_number*この DMV を sys.partitions に結合します。|  
|**row_group_id**|**int**|この行グループの ID です。 パーティション内で一意です。|  
|**dellta_store_hobt_id**|**bigint**|デルタ行グループの hobt_id で、行グループの種類がデルタではない場合は NULL。 デルタ行グループとは、新しいレコードを受け入れる読み取り/書き込み行グループのことです。 デルタ行グループが、**オープン**状態。 デルタ行グループは、行ストア形式のままであり、列ストア形式に圧縮されていません。|  
|**state**|**tinyint**|State_description に関連付けられている ID 番号。<br /><br /> 1 = OPEN<br /><br /> 2 = CLOSED<br /><br /> 3 = COMPRESSED|  
|**state_desccription**|**nvarchar(60)**|行グループの永続的な状態の説明です。<br /><br /> 開く - 新しいレコードを受け入れる読み取り/書き込み行グループ。 OPEN の行グループは、行ストア形式のままであり、列ストア形式に圧縮されていません。<br /><br /> 終了 - いっぱいされましたが、組ムーバー プロセスによってまだ圧縮行グループ。<br /><br /> 圧縮 - いっぱいになり、圧縮行グループ。|  
|**total_rows**|**bigint**|行グループに物理的に格納されている行の合計。 いくつか削除されている可能性がありますが、保存されています。 行グループ内の行の最大数は、1,048, 576 (16 進数は FFFFF) です。|  
|**deleted_rows**|**bigint**|削除対象としてマークされた行グループに物理的に格納されている行の数。<br /><br /> 常にデルタの場合は 0 では行グループ。|  
|**size_in_bytes**|**int**|この行グループ内のすべてのページのバイト単位の合計サイズ。 このサイズでは、メタデータと共有辞書の格納に必要なサイズは含まれません。|  
|**pdw_node_id**|**int**|一意の id、[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]ノード。|  
|**distribution_id**|**int**|分布の一意の id。|
  
## <a name="remarks"></a>コメント  
 クラスター化または非クラスター化列ストア インデックスを持つ各テーブルの列ストア行グループごとに 1 つの行を返します。  
  
 使用**sys.pdw_nodes_column_store_row_groups**行グループおよび行グループのサイズに含まれる行の数を決定します。  
  
 行グループ内の削除済みの行の数が合計行数に対して占める割合が高くなると、テーブルの効率が低下します。 テーブルのサイズが小さくなるよう列ストア インデックスを再構築して、テーブルを読み取るために必要なディスク I/O を削減します。 使用して列ストア インデックスを再構築する、**リビルド**のオプション、 **ALTER INDEX**ステートメント。  
  
 更新可能な列ストアが最初に新しいデータを挿入、**オープン**行グループは行ストア形式であり、デルタ テーブルと呼ばれるをこともできます。  Open の行グループがいっぱいの状態に変わります**CLOSED**します。 Closed 行グループが、組ムーバーによって列ストア形式に圧縮され、状態が**圧縮**します。  組ムーバーは、バック グラウンド プロセスに定期的にアクティブになり、列ストア行グループに圧縮することができるすべての closed 行グループがあるかどうかを確認します。  また、組ムーバーは、すべての行が削除された行グループの割り当てを解除します。 行グループの割り当て解除のマーク**廃止**します。 組ムーバーを直ちに実行するを使用して、 **REORGANIZE**のオプション、 **ALTER INDEX**ステートメント。  
  
 列ストア行グループは、いっぱいになると圧縮され、新しい行の受け入れを停止します。 圧縮されたグループから行が削除されると、削除された行は、保持されますが、削除済みとしてマークされます。 圧縮されたグループに対する更新は、圧縮されたグループからの削除、および OPEN 状態のグループへの挿入として実装されます。  
  
## <a name="permissions"></a>アクセス許可  
 **VIEW SERVER STATE** アクセス許可が必要です。  
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>例: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] および [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の例の結合、 **sys.pdw_nodes_column_store_row_groups**特定のテーブルに関する情報を返すには、その他のシステム テーブル。 計算済みの `PercentFull` 列は、行グループの効率の推定値を示します。 1 つのテーブルの削除については、WHERE 句の前にあるコメント ハイフンを検索し、テーブル名を指定します。  
  
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

次[!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)]方法と、多くの行は、開く、終了、または圧縮行グループでは、クラスター化列ストアもについて、例がパーティションあたりの行数をカウントします。  

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
  
## <a name="see-also"></a>関連項目  
 [SQL Data Warehouse and Parallel Data Warehouse Catalog Views (SQL Data Warehouse および Parallel Data Warehouse のカタログ ビュー)](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [列ストア インデックスを作成&#40;TRANSACT-SQL&#41;](../../t-sql/statements/create-columnstore-index-transact-sql.md)   
 [sys.pdw_nodes_column_store_segments &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-segments-transact-sql.md)   
 [sys.pdw_nodes_column_store_dictionaries &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-dictionaries-transact-sql.md)  
  
  
