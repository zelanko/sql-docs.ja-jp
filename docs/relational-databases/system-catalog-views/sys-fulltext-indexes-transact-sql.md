---
title: sys.fulltext_indexes (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- fulltext_indexes
- fulltext_indexes_TSQL
- sys.fulltext_indexes_TSQL
- sys.fulltext_indexes
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fulltext_indexes catalog view
- full-text indexes [SQL Server], properties
ms.assetid: 7fc10fdc-370f-4927-bba0-b76108a7508e
caps.latest.revision: 40
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: cf388a8850b78a6dc46efe43411c4d7c0482c289
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43092381"
---
# <a name="sysfulltextindexes-transact-sql"></a>sys.fulltext_indexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  表形式オブジェクトのフルテキスト インデックスごとに 1 行のデータを保持します。  

|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|このフルテキスト インデックスが属するオブジェクトの ID です。|  
|**unique_index_id**|**int**|対応するフルテキスト以外の一意なインデックスの ID です。このインデックスは、フルテキスト インデックスを行に関連付けるために使用されます。|  
|**fulltext_catalog_id**|**int**|フルテキスト インデックスが存在するフルテキスト カタログの ID です。|  
|**is_enabled**|**bit**|1 = フルテキスト インデックスが現在有効です。|  
|**change_tracking_state**|**char(1)**|変更の追跡の状態です。<br /><br /> M = 手動<br /><br /> A = 自動<br /><br /> O = オフ|  
|**change_tracking_state_desc**|**nvarchar(60)**|変更の追跡の状態に関する説明です。<br /><br /> MANUAL<br /><br /> AUTO<br /><br /> OFF|  
|**has_crawl_completed**|**bit**|フルテキスト インデックスが完了した最新のクロール (作成) です。|  
|**crawl_type**|**char(1)**|現在または最新のクロールの種類です。<br /><br /> F = フル クロール<br /><br /> I = タイムスタンプに基づく増分クロール<br /><br /> U = 通知に基づく更新クロール<br /><br /> P = フル クロールが一時停止された状態|  
|**crawl_type_desc**|**nvarchar(60)**|現在または最新のクロールの種類に関する説明です。<br /><br /> FULL_CRAWL<br /><br /> INCREMENTAL_CRAWL<br /><br /> UPDATE_CRAWL<br /><br /> PAUSED_FULL_CRAWL|  
|**crawl_start_date**|**datetime**|現在または最新のクロールの開始日付です。<br /><br /> NULL = なし|  
|**crawl_end_date**|**datetime**|現在または最新のクロールの終了日付です。<br /><br /> NULL = なし|  
|**incremental_timestamp**|**binary(8)**|次回の増分クロールに使用するタイムスタンプ値です。<br /><br /> NULL = なし|  
|**stoplist_id**|**int**|ID、[ストップ リスト](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)このフルテキスト インデックスに関連付けられています。|  
|**data_space_id**|**int**|このフルテキスト インデックスが存在するファイル グループです。|  
|**property_list_id**|**int**|このフルテキスト インデックスに関連付けられている検索プロパティ リストの ID です。 NULL は、フルテキスト インデックスに関連付けられている検索プロパティ リストがないことを示します。 詳細については、この検索プロパティ リストを取得する、 [sys.registered_search_property_lists &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md)カタログ ビューです。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="examples"></a>使用例  
 次の例では、`HumanResources.JobCandidate` サンプル データベースの `AdventureWorks2012` テーブルのフルテキスト インデックスを使用します。 この例では、テーブルのオブジェクト ID、検索プロパティ リストの ID、およびフルテキスト インデックスで使用されるストップリストのストップリスト ID が返されます。  
  
> [!NOTE]  
>  このフルテキスト インデックスを作成するコード例は、の「例」セクションを参照してください。 [CREATE FULLTEXT INDEX &#40;TRANSACT-SQL&#41;](../../t-sql/statements/create-fulltext-index-transact-sql.md)します。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT object_id, property_list_id, stoplist_id FROM sys.fulltext_indexes  
    where object_id = object_id('HumanResources.JobCandidate');   
GO  
```  
  
## <a name="see-also"></a>参照  
 [sys.fulltext_index_fragments &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-index-fragments-transact-sql.md)   
 [sys.fulltext_index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql.md)   
 [sys.fulltext_index_catalog_usages &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-index-catalog-usages-transact-sql.md)   
 [オブジェクト カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [フルテキスト インデックスの作成と管理](../../relational-databases/search/create-and-manage-full-text-indexes.md)   
 [DROP FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/drop-fulltext-index-transact-sql.md)   
 [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-index-transact-sql.md)   
 [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-index-transact-sql.md)  
  
  
