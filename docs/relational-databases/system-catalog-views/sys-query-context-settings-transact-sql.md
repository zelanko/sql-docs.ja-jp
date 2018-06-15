---
title: sys.query_context_settings (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/22/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- QUERY_CONTEXT_SETTINGS_TSQL
- SYS.QUERY_CONTEXT_SETTINGS_TSQL
- SYS.QUERY_CONTEXT_SETTINGS
- QUERY_CONTEXT_SETTINGS
dev_langs:
- TSQL
helpviewer_keywords:
- sys.query_context_settings catalog view
ms.assetid: 3c1887df-6bd8-491e-82fc-d25ad9589faf
caps.latest.revision: 16
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 448727aa29d55e0cd41b0859f620ad393b738e09
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33182098"
---
# <a name="sysquerycontextsettings-transact-sql"></a>sys.query_context_settings (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  クエリに関連付けられているコンテキストの設定に影響するセマンティクスについてを説明します。 いくつかのコンテキストの設定で使用できる[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を (クエリの正しい結果を定義する) クエリのセマンティクスに影響します。 さまざまな設定でコンパイルされたクエリ テキストと同じでは、(基になるデータでは) によって異なる結果を生成可能性があります。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**context_settings_id**|**bigint**|主キー。 この値は、クエリのプラン表示の XML で公開されます。|  
|**set_options**|**varbinary(8)**|いくつかの SET オプションの状態を反映するビット マスクです。 詳細については、次を参照してください。 [sys.dm_exec_plan_attributes &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-plan-attributes-transact-sql.md)です。|  
|**language_id**|**smallint**|言語の id です。 詳細については、次を参照してください。 [sys.syslanguages &#40;TRANSACT-SQL&#41;](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md)です。|  
|**date_format**|**smallint**|日付形式です。 詳しくは、「[SET DATEFORMAT &#40;Transact-SQL&#41;](../../t-sql/statements/set-dateformat-transact-sql.md)」をご覧ください。|  
|**date_first**|**tinyint**|最初の日付の値。 詳しくは、「[SET DATEFIRST &#40;Transact-SQL&#41;](../../t-sql/statements/set-datefirst-transact-sql.md)」をご覧ください。|  
|**ステータス**|**varbinary(2)**|クエリまたはクエリの実行に使用されるコンテキストの型を示すビットマスク フィールドです。 <br />列の値は、複数のフラグ (16 進数で表される) の組み合わせであることができます。<br /><br /> 0x0-標準のクエリ (固有のフラグがありません)<br /><br /> 0x1 -、カーソル Api が格納されている手順のいずれかで実行されたクエリ<br /><br /> 0x2-クエリ通知<br /><br /> 0x4 – 内部クエリ<br /><br /> 0x8-universal パラメーター化せず、自動パラメーター化クエリ<br /><br /> 0x10 – カーソル フェッチがクエリを更新します。<br /><br /> 0x20 - カーソルの更新の要求で使用されているクエリ<br /><br /> 0x40 - カーソルを開いたときに最初の結果セットが返されます (カーソル自動のフェッチ)<br /><br /> 0x80 – 暗号化されたクエリ<br /><br /> 0x100: 行レベルのセキュリティ述語のコンテキストでのクエリ|  
|**required_cursor_options**|**int**|カーソルの種類など、ユーザーによって指定されたカーソル オプションです。|  
|**acceptable_cursor_options**|**int**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がステートメントの実行をサポートするために暗黙的に変換できるカーソル オプションです。|  
|**merge_action_type**|**smallint**|結果として使用するトリガーの実行プランの種類、**マージ**ステートメントです。<br /><br /> 0 は、非トリガー プランの結果として実行されないトリガー プランを示す、**マージ**ステートメント、またはの結果として実行されるトリガー プラン、**マージ**ステートメントでのみ、を指定した**削除**アクション。<br /><br /> 1 は、**挿入**の結果として実行されるトリガー プラン、**マージ**ステートメントです。<br /><br /> 2 を示します、**更新**の結果として実行されるトリガー プラン、**マージ**ステートメントです。<br /><br /> 3 に示す、**削除**の結果として実行されるトリガー プラン、**マージ**、対応するを含むステートメント**挿入**または**更新**アクション。<br /><br /> <br /><br /> 入れ子になったトリガーが実行の連鎖動作によって、この値のアクション、**マージ**連鎖を原因となったステートメントです。|  
|**default_schema_id**|**int**|完全修飾されている名前解決に使用される既定のスキーマの ID です。|  
|**is_replication_specific**|**bit**|レプリケーションに使用されます。|  
|**is_contained**|**varbinary(1)**|1 では、包含データベースを示します。|  
  
## <a name="permissions"></a>権限  
 必要があります、 **VIEW DATABASE STATE**権限です。  
  
## <a name="see-also"></a>参照  
 [sys.database_query_store_options &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [sys.query_store_plan &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)   
 [sys.query_store_query &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-transact-sql.md)   
 [sys.query_store_query_text &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)   
 [sys.query_store_runtime_stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-transact-sql.md)   
 [sys.query_store_wait_stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-wait-stats-transact-sql.md)   
 [sys.query_store_runtime_stats_interval &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md)   
 [関連するビュー、関数、プロシージャ](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [クエリ ストアのストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)   
 [sys.fn_stmt_sql_handle_from_sql_stmt &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-stmt-sql-handle-from-sql-stmt-transact-sql.md)  
  
  
