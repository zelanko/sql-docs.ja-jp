---
title: "sys.column_store_dictionaries (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4e540f8bea10bb627554ebee15254112e3e4d71c
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="syscolumnstoredictionaries-transact-sql"></a>sys.column_store_dictionaries (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  XVelocity メモリ最適化列ストア インデックスで使用される各ディクショナリの行が含まれています。 ディクショナリは、すべてのデータ型ではなく一部のデータ型のエンコードに使用されるため、列ストア インデックスのすべての列にディクショナリがあるわけではありません。 ディクショナリは、プライマリ ディクショナリ (すべてのセグメント用) として、および列のセグメントのサブセットに対して使用される別のセカンダリ ディクショナリ用として存在する可能性があります。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**hobt_id で**|**bigint**|この列ストア インデックスを保持するテーブルのヒープまたは B ツリー インデックス (hobt) の ID。|  
|**column_id**|**int**|1 から始まる列ストア列の ID。 最初の列が ID = 1、2 番目の列が ID = 2, などです。|  
|**dictionary_id**|**int**|グローバルとローカルの列セグメントに関連付けられた辞書の 2 種類があります。 0 の dictionary_id では、すべての列セグメント (行グループごとに 1 つ) その列の間で共有されるグローバルの辞書を表します。|  
|**version**|**int**|ディクショナリの形式のバージョン。|  
|**型**|**int**|ディクショナリの種類:<br /><br /> 1 – 含むハッシュ ディクショナリ**int**値<br /><br /> 2 – 使用されていません<br /><br /> 3 - 文字列値を含むハッシュ ディクショナリ<br /><br /> 4 – 含むハッシュ ディクショナリ**float**値<br /><br /> ディクショナリの詳細については、次を参照してください。[列ストア インデックス ガイド](~/relational-databases/indexes/columnstore-indexes-overview.md)です。|  
|**持っていない場合**|**int**|ディクショナリ内の最後のデータ ID。|  
|**entry_count**|**bigint**|ディクショナリ内のエントリの数。|  
|**on_disc_size**|**bigint**|ディクショナリのサイズ (バイト単位)。|  
|**partition_id**|**bigint**|パーティション ID を示します。 データベース内で一意です。|  
  
## <a name="permissions"></a>Permissions  
 すべての列で、少なくともテーブルに対する VIEW DEFINITION 権限が必要です。 ユーザーがあるない限り列は null を返します**選択**権限: 持っていない場合、entry_count、data_ptr の各します。  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [SQL Server のシステム カタログよく寄せられる質問のクエリを実行します。](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.all_columns &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys.computed_columns &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-computed-columns-transact-sql.md)   
 [列ストア インデックス ガイド](~/relational-databases/indexes/columnstore-indexes-overview.md)   
 [列ストア インデックス ガイド](~/relational-databases/indexes/columnstore-indexes-overview.md)   
 [sys.column_store_segments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-segments-transact-sql.md)  
  
  

