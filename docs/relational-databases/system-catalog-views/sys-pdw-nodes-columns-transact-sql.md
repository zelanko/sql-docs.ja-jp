---
title: sys.pdw_nodes_columns (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/03/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 268c77b7-1d71-4197-a2ed-5e2b2b8fc260
caps.latest.revision: 7
author: barbkess
ms.author: barbkess
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: cd82f69a33e973eb911e70fa295188a838aed3e6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="syspdwnodescolumns-transact-sql"></a>sys.pdw_nodes_columns (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  ユーザー定義テーブルとユーザー定義のビューの列が表示されます。  
  
|列名|データ型|Description|範囲|  
|-----------------|---------------|-----------------|-----------|  
|object_id|**int**|この列が属するオブジェクトの ID です。||  
|name|**sysname**|列の名前です。 オブジェクト内で一意です。||  
|column_id|**int**|列の ID です。 オブジェクト内で一意です。||  
|system_type_id|**tinyint**|列のシステム型の ID。||  
|user_type_id|**int**|ユーザーが定義した列の型の ID です。||  
|max_length|**smallint**|列の最大長 (バイト単位) です。|場合は-1 (無効) サポートされていない列の型が含まれています。|  
|有効桁数 (precision)|**tinyint**|数値ベースの場合は、列の有効桁数です。それ以外の場合は、0 です。||  
|scale|**tinyint**|数値ベース以外の場合は列の小数点以下桁数それ以外の場合、0 を返します。||  
|collation_name|**sysname**|文字ベースの場合は、列の照合順序の名前です。それ以外の場合は、NULL です。||  
|is_nullable|**bit**|1 = 列で NULL 値を使用できます。||  
|is_ansi_padded|**bit**|1 = 文字、バイナリ、またはバリアントの場合、列で ANSI_PADDING ON 動作を使用します。|常に 0 です。|  
|is_rowguidcol|**bit**|1 = 列は宣言された ROWGUIDCOL です。|常に 0 です。|  
|is_identity|**bit**|1 = 列は ID 値を保持しています。|常に 0 です。|  
|is_computed|**bit**|1 = 列は計算列です。|常に 0 です。|  
|is_filestream|**bit**|1 = 列は FILESTREAM 列です。|常に 0 です。|  
|is_replicated|**bit**|1 = 列はレプリケートされています。|常に 0 です。|  
|is_non_sql_subscribed|**bit**|1 = 列には、SQL 以外のサブスクライバー。|常に 0 です。|  
|is_merge_published|**bit**|1 = 列はマージ パブリッシュされています。|常に 0 です。|  
|is_dts_replicated|**bit**|1 = 列は、SSIS を使用してレプリケートされます。|常に 0 です。|  
|is_xml_document|**bit**|1 = 内容が完全な XML ドキュメントです。|常に 0 です。|  
|xml_collection_id|**int**|0 = いいえの XML スキーマ コレクションです。|常に 0 です。|  
|default_object_id|**int**|既定のオブジェクトの ID0 = 既定値はありません。|常に 0 です。|  
|rule_object_id|**int**|列にバインドするスタンドアロン ルールの ID です。 <br />0 = スタンドアロン ルールはありません。|常に 0 です。|  
|is_sparse|**bit**|1 = 列はスパース列です。|常に 0 です。|  
|is_column_set|**bit**|1 = 列は列セットです。|常に 0 です。|  
|pdw_node_id|**int**|一意の識別子、[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]ノード。|NOT NULL|  
  
## <a name="permissions"></a>権限  
 CONTROL SERVER 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と並列データ ウェアハウスのカタログ ビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [sys.all_columns &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)  
  
  
