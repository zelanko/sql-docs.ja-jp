---
title: sys.internal_partitions (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/26/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 0262df2b-5ba7-4715-b17b-3d9ce470a38e
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 5795ec9feaef483dd3ee9b5f3e31dbb619a89331
ms.sourcegitcommit: ce5770d8b91c18ba5ad031e1a96a657bde4cae55
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2019
ms.locfileid: "67388338"
---
# <a name="sysinternalpartitions-transact-sql"></a>sys.internal_partitions (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  ディスク ベース テーブルで列ストア インデックスの内部データを追跡する各の行セットの 1 つの行を返します。 これらの行セットは列ストア インデックスに内部し、トラックが削除された行、行グループのマッピング、およびデルタ行グループを格納します。 各テーブル パーティションのそれぞれのデータを追跡します。すべてのテーブルでは、少なくとも 1 つのパーティションがあります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 再、行セットを列ストア インデックスを再構築するたびに作成されます。   
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|partition_id|**bigint**|このパーティションのパーティションの ID。 データベース内で一意です。|  
|object_id|**int**|パーティションを含むテーブルのオブジェクト ID。|  
|index_id|**int**|テーブルで定義された列ストア インデックスのインデックス ID。<br /><br /> 1 = クラスター化列ストア インデックス<br /><br /> 2 = 非クラスター化列ストア インデックス|  
|partition_number|**int**|パーティションの数です。<br /><br /> 1 = パーティション分割されたテーブルの最初のパーティションまたは非パーティション テーブルの 1 つのパーティション。<br /><br /> 2 番目のパーティションし、などです。|  
|internal_object_type|**tinyint**|列ストア インデックスの内部データを追跡するための行セット オブジェクト。<br /><br /> 2 = COLUMN_STORE_DELETE_BITMAP<br /><br /> 3 = COLUMN_STORE_DELTA_STORE<br /><br /> 4 = COLUMN_STORE_DELETE_BUFFER<br /><br /> 5 = COLUMN_STORE_MAPPING_INDEX|  
|internal_object_type_desc|**nvarchar(60)**|COLUMN_STORE_DELETE_BITMAP - このビットマップのインデックスは、列ストアから削除済みとしてマークされている行を追跡します。 パーティションは、複数の行グループ内の行を持つことができますので、ビットマップはすべての行グループは。 行は、列ストアにも物理的に存在する領域を占有してをあります。<br /><br /> COLUMN_STORE_DELTA_STORE - 行のグループをストアには、カラム型ストレージに圧縮されていないを行グループと呼ばれます。 各テーブル パーティションには、0 個以上のデルタストア行グループを持つことができます。<br /><br /> COLUMN_STORE_DELETE_BUFFER - 更新可能な非クラスター化列ストア インデックスの削除を維持するためです。 クエリでは、基になる行ストア テーブルから行を削除、削除バッファーは、列ストアから削除を追跡します。 削除された行の数が 1048576 を超えた場合にバック グラウンド スレッドの組ムーバーによって、または明示的な再編成コマンドによって、削除のビットマップにマージされます。  特定の時点で、削除のビットマップと削除バッファーの和集合がすべて削除された行を表します。<br /><br /> COLUMN_STORE_MAPPING_INDEX - クラスター化列ストア インデックスがセカンダリ非クラスター化インデックスを持つ場合にのみ使用します。 これにより、非クラスター化インデックス キーが、適切な行グループと列ストア行 ID にマップされます。 別の行グループに移動する行のキーを格納するだけこれは、デルタ行グループは、列ストアに圧縮するときに、マージ操作で、2 つの異なる行をグループから行をマージするときに発生します。|  
|Row_group_id|**int**|デルタストア行グループの ID。 各テーブル パーティションには、0 個以上のデルタストア行グループを持つことができます。|  
|hobt_id で|**bigint**|内部行セット オブジェクトの ID。 これは、内部の行セットの物理的な特性についての詳細を取得するには、その他の Dmv を使用したに参加するための適切なキーです。|  
|rows|**bigint**|このパーティション内の行の概数です。|  
|data_compression|**tinyint**|行セットの圧縮の状態。<br /><br /> 0 = NONE<br /><br /> 1 行を =<br /><br /> 2 ページを =|  
|data_compression_desc|**nvarchar(60)**|各パーティションの圧縮の状態。 行ストア テーブルに指定できる値は、NONE、ROW、および PAGE です。 列ストア テーブルに指定できる値は COLUMNSTORE および COLUMNSTORE_ARCHIVE です。|  
|optimize_for_sequential_key|**bit**|1 = パーティションが最後のページの挿入の最適化を有効にします。<br><br>0 = 既定値。 パーティションは、最後のページの挿入の最適化を無効になっているのです。|
  
## <a name="permissions"></a>アクセス許可  
 ロール **public** のメンバーシップが必要です。 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="general-remarks"></a>全般的な解説  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 再作成または列ストア インデックスを再構築は、毎回の新しい列ストア内部のインデックスを作成します。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-view-all-of-the-internal-rowsets-for-a-table"></a>A. すべてのテーブルの内部の行セットの表示します。  
 この例では、すべてのテーブルの内部列ストア行セットを返します。 詳細については、特定の行セットに hobt_id でを使用することもできます。  
  
```  
SELECT i.object_id, i.index_id, i.name, p.hobt_id, p.internal_object_type_id, p.internal_object_type_desc  
FROM sys.internal_partitions AS p  
JOIN sys.indexes AS i  
on i.object_id = p.object_id  
WHERE p.object_id = OBJECT_ID ( '<table name' ) ;  
```  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [SQL Server システム カタログに対するクエリに関してよくあるご質問](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
