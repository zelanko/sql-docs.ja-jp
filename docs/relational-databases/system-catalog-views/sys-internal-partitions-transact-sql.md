---
title: sys.internal_partitions (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
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
ms.openlocfilehash: 82b3e432321260a5efa1d25537202d351b89a380
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47603430"
---
# <a name="sysinternalpartitions-transact-sql"></a>sys.internal_partitions (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  ディスク ベース テーブルで列ストア インデックスの内部データを追跡するそれぞれの行セットの 1 つの行を返します。 これらの行セットでは、列ストア インデックスに内部し、トラックが削除された行、行グループのマッピング、およびデルタは、行グループを格納します。 データを追跡ごとに各テーブル パーティション。すべてのテーブルには、少なくとも 1 つのパーティションがあります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 再、行セットを列ストア インデックスを再構築するたびに作成されます。   
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|partition_id|**bigint**|このパーティションのパーティションの ID です。 データベース内で一意です。|  
|object_id|**int**|パーティションを含むテーブルのオブジェクト ID。|  
|index_id|**int**|テーブルで定義された列ストア インデックスのインデックスの ID。<br /><br /> 1 = クラスター化列ストア インデックス<br /><br /> 2 = 非クラスター化列ストア インデックス|  
|partition_number|**int**|パーティションの数です。<br /><br /> 1 = パーティション分割されたテーブルの最初のパーティションまたは非パーティション テーブルの 1 つのパーティションです。<br /><br /> 2 = 2 番目のパーティションとなどです。|  
|internal_object_type|**tinyint**|列ストア インデックスの内部データを追跡するための行セット オブジェクトです。<br /><br /> 2 = COLUMN_STORE_DELETE_BITMAP<br /><br /> 3 = COLUMN_STORE_DELTA_STORE<br /><br /> 4 = COLUMN_STORE_DELETE_BUFFER<br /><br /> 5 = COLUMN_STORE_MAPPING_INDEX|  
|internal_object_type_desc|**nvarchar(60)**|COLUMN_STORE_DELETE_BITMAP – このビットマップのインデックスでは、列ストアから削除済みとしてマークされている行を追跡します。 ビットマップは、パーティションは、複数の行グループ内の行を持つことができますので、すべての行グループは。 行は、列ストアにも物理的に存在し、領域を占有にあります。<br /><br /> COLUMN_STORE_DELTA_STORE – ストアの複数の行では、列指向の記憶域に圧縮されていないを行グループと呼ばれます。 各テーブル パーティションでは、0 個以上のデルタストアの行グループを持つことができます。<br /><br /> COLUMN_STORE_DELETE_BUFFER – をクリックし、更新可能なの非クラスター化列ストア インデックスの削除を維持するためです。 クエリを基になる行ストア テーブルから行を削除すると、削除のバッファーは、列ストアから、削除を追跡します。 削除された行の数が 1048576 を超えた場合にバック グラウンド スレッドの組ムーバーによって、または明示的な再編成コマンドによって、削除のビットマップにマージされます。  任意の特定の時点では、delete ビットマップ、および削除のバッファーの和集合は、すべて削除された行を表します。<br /><br /> COLUMN_STORE_MAPPING_INDEX – では、クラスター化列ストア インデックスがセカンダリの非クラスター化インデックスを持つ場合にのみを使用します。 これは、非クラスター化インデックスのキーは、適切な行グループと列ストア行 ID にマップします。 のみを格納します。 別の行グループに移動する行のキーこれは、マージ操作で、次の 2 つの異なる行をグループからの行をマージして、デルタ行グループは、列ストアに圧縮されたときに発生します。|  
|Row_group_id|**int**|デルタストアの行グループの ID。 各テーブル パーティションでは、0 個以上のデルタストアの行グループを持つことができます。|  
|hobt_id|**bigint**|内部行セット オブジェクトの ID。 これは、適切なキーの詳細については、内部の行セットの物理的な特性を取得するには、その他の Dmv を使用したに参加するためです。|  
|rows|**bigint**|このパーティション内の行の概数です。|  
|data_compression|**tinyint**|行セットの圧縮の状態。<br /><br /> 0 = NONE<br /><br /> 1 = ROW<br /><br /> 2 = PAGE|  
|data_compression_desc|**nvarchar(60)**|各パーティションの圧縮の状態。 行ストア テーブルに指定できる値は、NONE、ROW、および PAGE です。 列ストア テーブルに指定できる値は COLUMNSTORE および COLUMNSTORE_ARCHIVE です。|  
  
## <a name="permissions"></a>アクセス許可  
 ロール **public** のメンバーシップが必要です。 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="general-remarks"></a>全般的な解説  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 再作成または列ストア インデックスを再構築は、毎回の新しい列ストア内部のインデックスを作成します。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-view-all-of-the-internal-rowsets-for-a-table"></a>A. すべてのテーブルの内部の行セットの表示します。  
 この例では、すべてのテーブルの内部列ストア行セットを返します。 詳細については、特定の行セットを検索するのに hobt_id でを使用することもできます。  
  
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
  
  
