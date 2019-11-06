---
title: sys.indexes (Transact SQL) |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 06/26/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.indexes
- indexes
- sys.indexes_TSQL
- indexes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.indexes catalog view
ms.assetid: 066bd9ac-6554-4297-88fe-d740de1f94a8
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0008599ad16db3c7200c824458f0bbae82580750
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68103411"
---
# <a name="sysindexes-transact-sql"></a>sys.indexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  テーブル、ビュー、テーブル値関数など、テーブル オブジェクトのインデックスまたはヒープごとに 1 行のデータを格納します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|インデックスが属しているオブジェクトの ID。|  
|**name**|**sysname**|インデックスの名前です。 **名前**オブジェクト内でのみ一意です。<br /><br /> NULL = ヒープ|  
|**index_id**|**int**|インデックスの ID。 **index_id**オブジェクト内でのみ一意です。<br /><br /> 0 = ヒープ<br /><br /> 1 = クラスター化インデックス<br /><br /> > 1 = 非クラスター化インデックス|  
|**type**|**tinyint**|インデックスの種類です。<br /><br /> 0 = ヒープ<br /><br /> 1 = クラスター化<br /><br /> 2 = 非クラスター化<br /><br /> 3 = XML<br /><br /> 4 = 空間<br /><br /> 5 = columnstore インデックスをクラスター化します。 **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 6 = columnstore の非クラスター化インデックスです。 **適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 7 = ハッシュの非クラスター化インデックスです。 **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**type_desc**|**nvarchar(60)**|インデックスの種類の説明。<br /><br /> HEAP<br /><br /> CLUSTERED<br /><br /> NONCLUSTERED<br /><br /> XML<br /><br /> SPATIAL<br /><br /> クラスター化された COLUMNSTORE ・**に適用される**:[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]を[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。<br /><br /> 非クラスター化の COLUMNSTORE -**に適用される**:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]を[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。<br /><br /> 非クラスター化ハッシュ:非クラスター化ハッシュ インデックスは、メモリ最適化テーブルでのみサポートされます。 sys.hash_indexes ビューでは、現在のハッシュ インデックスとハッシュ プロパティが表示されます。 詳細については、次を参照してください。 [sys.hash_indexes &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-hash-indexes-transact-sql.md)します。 **適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**is_unique**|**bit**|1 = インデックスは一意です。<br /><br /> 0 = インデックスは一意ではありません。<br /><br /> クラスター化列ストア インデックスの場合、常に 0 です。|  
|**data_space_id**|**int**|インデックスのデータ領域の ID。 データ領域は、ファイル グループまたはパーティション構成です。<br /><br /> 0 = **object_id**はテーブル値関数またはメモリ内インデックスです。|  
|**ignore_dup_key**|**bit**|1 = IGNORE_DUP_KEY はオンです。<br /><br /> 0 = IGNORE_DUP_KEY はオフです。|  
|**is_primary_key**|**bit**|1 = インデックスは PRIMARY KEY 制約の一部です。<br /><br /> クラスター化列ストア インデックスの場合、常に 0 です。|  
|**is_unique_constraint**|**bit**|1 = インデックスは UNIQUE 制約の一部です。<br /><br /> クラスター化列ストア インデックスの場合、常に 0 です。|  
|**fill_factor**|**tinyint**|> 0 = インデックスが作成または再構築された場合に使用される FILLFACTOR のパーセンテージです。<br /><br /> 0 = 既定値<br /><br /> クラスター化列ストア インデックスの場合、常に 0 です。|  
|**is_padded**|**bit**|1 = PADINDEX がオンです。<br /><br /> 0 = PADINDEX がオフです。<br /><br /> クラスター化列ストア インデックスの場合、常に 0 です。|  
|**is_disabled**|**bit**|1 = インデックスは無効です。<br /><br /> 0 = インデックスは無効ではありません。|  
|**is_hypothetical**|**bit**|1 = インデックスは仮想的であり、データへのアクセス パスとして直接使用することはできません。 仮想インデックスは、列レベルの統計を保持しています。<br /><br /> 0 = インデックスは仮想的ではありません。|  
|**allow_row_locks**|**bit**|1 = インデックスは行ロックを許可します。<br /><br /> 0 = インデックスは行ロックを許可しません。<br /><br /> クラスター化列ストア インデックスの場合、常に 0 です。|  
|**allow_page_locks**|**bit**|1 = インデックスはページ ロックを許可します。<br /><br /> 0 = インデックスはページ ロックを許可しません。<br /><br /> クラスター化列ストア インデックスの場合、常に 0 です。|  
|**has_filter**|**bit**|1 = インデックスにフィルターがあり、フィルター定義を満たす行だけが含まれます。<br /><br /> 0 = インデックスにフィルターはありません。|  
|**filter_definition**|**nvarchar(max)**|フィルター選択されたインデックスに含まれる行のサブセットの式。<br /><br /> ヒープまたはフィルター選択されたインデックス以外のインデックスの場合は、NULL です。|  
|**auto_created**|**bit**|1 = 自動チューニングによってインデックスが作成されました。<br /><br />0 = ユーザーによってインデックスが作成されました。
|**optimize_for_sequential_key**|**bit**|1 = インデックスが最後のページの挿入の最適化を有効にします。<br><br>0 = 既定値。 インデックスでは、無効になっている最後のページの挿入の最適化があります。|

  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="examples"></a>使用例  
 次の例は、テーブルのすべてのインデックスを返します`Production.Product`で、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。  
  
```  
  
SELECT i.name AS index_name  
    ,i.type_desc  
    ,is_unique  
    ,ds.type_desc AS filegroup_or_partition_scheme  
    ,ds.name AS filegroup_or_partition_scheme_name  
    ,ignore_dup_key  
    ,is_primary_key  
    ,is_unique_constraint  
    ,fill_factor  
    ,is_padded  
    ,is_disabled  
    ,allow_row_locks  
    ,allow_page_locks  
FROM sys.indexes AS i  
INNER JOIN sys.data_spaces AS ds ON i.data_space_id = ds.data_space_id  
WHERE is_hypothetical = 0 AND i.index_id <> 0   
AND i.object_id = OBJECT_ID('Production.Product');  
GO  
  
```  
  
## <a name="see-also"></a>関連項目  
 [オブジェクト カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)   
 [sys.xml_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-xml-indexes-transact-sql.md)   
 [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.key_constraints &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-key-constraints-transact-sql.md)   
 [sys.filegroups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [sys.partition_schemes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-partition-schemes-transact-sql.md)   
 [SQL Server のシステム カタログよく寄せられる質問のクエリを実行します。](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [インメモリ OLTP &#40;インメモリ最適化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
