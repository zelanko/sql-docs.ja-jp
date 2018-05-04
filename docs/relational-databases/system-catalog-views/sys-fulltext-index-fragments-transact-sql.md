---
title: sys.fulltext_index_fragments (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- fulltext_index_fragments
- sys.fulltext_index_fragments_TSQL
- fulltext_index_fragments_TSQL
- sys.fulltext_index_fragments
dev_langs:
- TSQL
helpviewer_keywords:
- full-text indexes [SQL Server], fragments
- full-text indexes [SQL Server], metadata
- troubleshooting [SQL Server], full-text search
- sys.fulltext_index_fragments catalog view
ms.assetid: a82e5018-5d88-45c0-9a47-c251e17a6cdb
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 965fb4acf4c203c0a6f2a579b4c14801e082ef7e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysfulltextindexfragments-transact-sql"></a>sys.fulltext_index_fragments (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  フルテキスト インデックスと呼ばれる内部テーブルを使用して*、フルテキスト インデックス フラグメント*逆インデックスのデータを格納します。 このビューを使用すると、これらのフラグメントに関するメタデータをクエリできます。 このビューは、フルテキスト インデックスが含まれているすべてのテーブルのフルテキスト インデックス フラグメントごとに 1 行のデータを格納しています。  
 
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|table_id|**int**|フルテキスト インデックス フラグメントが含まれているテーブルのオブジェクト ID。|  
|fragment_object_id|**int**|フラグメントに関連付けられている内部テーブルのオブジェクト ID。|  
|fragment_id|**int**|フルテキスト インデックス フラグメントの論理 ID。 テーブルのすべてのフラグメントで一意です。|  
|timestamp|**timestamp**|フラグメントの作成に関連付けられているタイムスタンプ。 新しいフラグメントほどタイムスタンプの値が大きくなります。|  
|data_size|**int**|フラグメントの論理サイズ (バイト単位)。|  
|row_count|**int**|フラグメント内の個々の行の数。|  
|ステータス|**int**|フラグメントの状態。有効値は次のとおりです。<br /><br /> 0 = 新たに作成され、まだ使用されていません。<br /><br /> 1 = フルテキスト インデックスの作成またはマージの際の挿入のために使用されています。<br /><br /> 4 = 閉じています。 クエリを実行できます。<br /><br /> 6 = マージ入力のために使用されています。クエリを実行できます。<br /><br /> 8 = 削除の対象としてマークされています。 クエリやマージ ソースには使用されません。<br /><br /> 4 または 6 の意味、フラグメントは論理フルテキスト インデックスの一部であるし、クエリを実行できます; の状態つまり、これは、*クエリ可能な*フラグメント。|  
  
## <a name="remarks"></a>解説  
 sys.fulltext_index_fragments カタログ ビューを使用すると、フルテキスト インデックスを構成するフラグメントの数を照会できます。 フルテキスト クエリのパフォーマンスに問題がある場合は、次のように、sys.fulltext_index_fragments を使用してフルテキスト インデックス内のクエリ可能なフラグメント (状態が 4 または 6 のフラグメント) の数を照会します。  
  
```  
SELECT table_id, status FROM sys.fulltext_index_fragments  
   WHERE status=4 OR status=6;  
```  
  
 クエリ可能なフラグメントが多数存在する場合は、そのフルテキスト インデックスを含むフルテキスト カタログを再構成してフラグメントをマージすることをお勧めします。 再編成する、フルテキスト カタログの使用[ALTER FULLTEXT CATALOG](../../t-sql/statements/alter-fulltext-catalog-transact-sql.md)*catalog_name*再編成します。 たとえば、という名前のフルテキスト カタログを再構成する`ftCatalog`で、`AdventureWorks2012`データベースを入力します。  
  
```  
USE AdventureWorks2012;  
GO  
ALTER FULLTEXT CATALOG ftCatalog REORGANIZE;  
GO  
```  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [フルテキスト インデックスの作成](../../relational-databases/search/populate-full-text-indexes.md)  
  
  
