---
title: column_store_dictionaries (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.column_store_dictionaries_TSQL
- column_store_dictionaries
- column_store_dictionaries_TSQL
- sys.column_store_dictionaries
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_store_dictionaries catalog view
ms.assetid: 56efd563-2f72-4caf-94e3-8a182385c173
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3d69a2355f18a162f3e7a6b76b07bbb7cd6a597a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "75656619"
---
# <a name="syscolumn_store_dictionaries-transact-sql"></a>sys.column_store_dictionaries (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  XVelocity メモリ最適化列ストアインデックスで使用されるディクショナリごとに1行の値を格納します。 ディクショナリは、一部のデータ型ではなく一部のデータ型をエンコードするために使用されます。したがって、列ストアインデックスのすべての列がディクショナリを持つわけではありません。 ディクショナリは、プライマリディクショナリ (すべてのセグメント) として存在することができ、場合によっては、列のセグメントのサブセットに使用される他のセカンダリディクショナリとして存在することもあります。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**hobt_id**|**bigint**|この列ストアインデックスを持つテーブルのヒープまたは B ツリーインデックス (HoBT) の ID。|  
|**column_id**|**int**|1から始まる列ストア列の ID。 最初の列の ID が1、2番目の列の ID が2、など。|  
|**dictionary_id**|**int**|列セグメントに関連付けられている辞書には、グローバルとローカルの2種類があります。 Dictionary_id 0 は、その列のすべての列セグメント (行グループごとに1つ) 間で共有されるグローバルディクショナリを表します。|  
|**バージョン**|**int**|辞書形式のバージョン。|  
|**type**|**int**|辞書の種類:<br /><br /> 1- **int**値を含むハッシュディクショナリ<br /><br /> 2-使用されていません<br /><br /> 3-文字列値を含むハッシュディクショナリ<br /><br /> 4- **float**値を含むハッシュディクショナリ<br /><br /> ディクショナリの詳細については、「[列ストアインデックスガイド](~/relational-databases/indexes/columnstore-indexes-overview.md)」を参照してください。|  
|**last_id**|**int**|ディクショナリ内の最後のデータ ID。|  
|**entry_count**|**bigint**|ディクショナリ内のエントリの数。|  
|**on_disk_size**|**bigint**|ディクショナリのサイズ (バイト単位)。|  
|**partition_id**|**bigint**|パーティション ID を示します。 データベース内で一意です。|  
  
## <a name="permissions"></a>アクセス許可  
テーブル`VIEW DEFINITION`に対する権限が必要です。 次の列は、ユーザーがアクセス許可を`SELECT`持っていない場合は null を返します last_id、entry_count、data_ptr です。  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]詳細については、「[メタデータ表示の構成](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [オブジェクトカタログビュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [SQL Server システムカタログに対するクエリについてよく寄せられる質問](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [&#40;Transact-sql&#41;の列](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [all_columns &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [computed_columns &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-computed-columns-transact-sql.md)   
 [列ストアインデックスガイド](~/relational-databases/indexes/columnstore-indexes-overview.md)   
 [列ストアインデックスガイド](~/relational-databases/indexes/columnstore-indexes-overview.md)   
 [column_store_segments &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-column-store-segments-transact-sql.md)  
  
  

