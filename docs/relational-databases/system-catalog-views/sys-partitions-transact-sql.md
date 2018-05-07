---
title: sys.partitions (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- partitions
- partitions_TSQL
- sys.partitions_TSQL
- sys.partitions
dev_langs:
- TSQL
helpviewer_keywords:
- sys.partitions catalog view
ms.assetid: 1c19e1b1-c925-4dad-a652-581692f4ab5e
caps.latest.revision: 60
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 4902bca55295c2e6e870e2f3488cc178c0f771fa
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="syspartitions-transact-sql"></a>sys.partitions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  データベース内のすべてのテーブルとほとんどの種類のインデックスのパーティションごとに 1 行のデータを保持します。 フルテキスト、空間、XML などの特殊な種類のインデックスは、このビューには含まれません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のテーブルとインデックスは、明示的にパーティション分割されているかどうかに関係なく、1 つ以上のパーティションが保持されているものと見なされます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|partition_id|**bigint**|パーティション ID を示します。 データベース内で一意です。|  
|object_id|**int**|このパーティションが所属するオブジェクトの ID を示します。 すべてのテーブルまたはビューは 1 つ以上のパーティションで構成されます。|  
|index_id|**int**|このパーティションが所属するオブジェクト内のインデックスの ID を示します。<br /><br /> 0 = ヒープ<br />1 = クラスター化インデックス<br />2 以上 = 非クラスター化インデックス|  
|partition_number|**int**|所有しているインデックスまたはヒープ内で 1 から始まるパーティション番号です。 パーティション分割されていないテーブルおよびインデックスの場合、この列の値は 1 になります。|  
|hobt_id|**bigint**|このパーティションの行を保持するデータ ヒープまたは B ツリーの ID を示します。|  
|rows|**bigint**|このパーティション内の行の概数を示します。|  
|filestream_filegroup_id|**smallint**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> このパーティションに格納された FILESTREAM ファイル グループの ID を示します。|  
|data_compression|**tinyint**|各パーティションの圧縮の状態を示します。<br /><br /> 0 = NONE <br />1 = ROW <br />2 = PAGE <br />3 = 列ストア:**対象**:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]経由 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />4 = COLUMNSTORE_ARCHIVE:**対象**:[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]経由 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> **注:** の任意のエディションでフルテキスト インデックスが圧縮される[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。|  
|data_compression_desc|**nvarchar(60)**|各パーティションの圧縮状態を示します。 行ストア テーブルに指定できる値は、NONE、ROW、および PAGE です。 列ストア テーブルに指定できる値は COLUMNSTORE および COLUMNSTORE_ARCHIVE です。|  
  
## <a name="permissions"></a>権限  
 ロール **public** のメンバーシップが必要です。 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [SQL Server システム カタログに対するクエリに関してよくあるご質問](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
