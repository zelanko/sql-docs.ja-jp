---
title: sys.dm_exec_query_optimizer_info (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_exec_query_optimizer_info_TSQL
- dm_exec_query_optimizer_info
- sys.dm_exec_query_optimizer_info_TSQL
- sys.dm_exec_query_optimizer_info
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_query_optimizer_info dynamic management view
ms.assetid: 1d72cef1-22d8-4ae0-91db-6694fe918c9e
caps.latest.revision: 30
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: cf54ff13623d2ca2e523fd8db3afde8bb2be3367
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmexecqueryoptimizerinfo-transact-sql"></a>sys.dm_exec_query_optimizer_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クエリ オプティマイザーの操作に関する詳細な統計を返します。 このビューは、ワークロードをチューニングしてクエリの最適化の問題や改善点を特定する際に使用できます。 たとえば、最適化の合計数、所要時間、および最終的なコストを使用して、現在のワークロードのクエリの最適化と、チューニング処理中に確認された変更を比較できます。 一部のカウンターでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の内部診断で使用するためだけに適用されるデータを提供します。 このようなカウンターには、"内部使用のみ" と記載してあります。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して**sys.dm_pdw_nodes_exec_query_optimizer_info**です。  
  
|名前|データ型|Description|  
|----------|---------------|-----------------|  
|**counter**|**nvarchar (4000)**|オプティマイザーの統計イベントの名前。|  
|**occurrence**|**bigint**|このカウンターに関する最適化イベントの発生回数。|  
|**value**|**float**|1 回のイベント発生あたりの平均プロパティ値。|  
|**pdw_node_id**|**int**|**適用されます**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この分布はでは、ノードの識別子。|  
  
## <a name="permissions"></a>権限  

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]が必要です`VIEW SERVER STATE`権限です。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限です。   
    
## <a name="remarks"></a>解説  
 **sys.dm_exec_query_optimizer_info**次のプロパティ (カウンター) が含まれています。 すべての発生回数の値は累積され、システムの再起動時に 0 に設定されます。 値フィールドのすべての値は、システムの再起動時に NULL に設定されます。 平均を示す列のすべての値では、平均計算の分母として、同一行を基にした発生回数の値が使用されます。 すべてのクエリの最適化のときに測定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]への変更を判断**dm_exec_query_optimizer_info**、両方のユーザーとシステムによって生成されたクエリを含むです。 既にキャッシュされている計画の実行がの値を変更していない**dm_exec_query_optimizer_info**、大幅な最適化のみです。  
  
|カウンター|個数|値|  
|-------------|----------------|-----------|  
|optimizations|最適化の合計数。|適用なし|  
|elapsed time|最適化の合計数。|個別のステートメント (クエリ) の最適化ごとの平均経過時間 (秒単位)。|  
|final cost|最適化の合計数。|内部コスト単位での、最適化プランに対する推定コストの平均。|  
|trivial plan|内部使用のみ|内部使用のみ|  
|tasks|内部使用のみ|内部使用のみ|  
|no plan|内部使用のみ|内部使用のみ|  
|0 を検索します。|内部使用のみ|内部使用のみ|  
|search 0 time|内部使用のみ|内部使用のみ|  
|search 0 tasks|内部使用のみ|内部使用のみ|  
|1 を検索します。|内部使用のみ|内部使用のみ|  
|search 1 time|内部使用のみ|内部使用のみ|  
|search 1 tasks|内部使用のみ|内部使用のみ|  
|search 2|内部使用のみ|内部使用のみ|  
|search 2 time|内部使用のみ|内部使用のみ|  
|search 2 tasks|内部使用のみ|内部使用のみ|  
|gain stage 0 to stage 1|内部使用のみ|内部使用のみ|  
|gain stage 1 to stage 2|内部使用のみ|内部使用のみ|  
|timeout|内部使用のみ|内部使用のみ|  
|memory limit exceeded|内部使用のみ|内部使用のみ|  
|insert stmt|INSERT ステートメントに対する最適化の数。|適用なし|  
|delete stmt|DELETE ステートメントに対する最適化の数。|適用なし|  
|update stmt|UPDATE ステートメントに対する最適化の数。|適用なし|  
|contains subquery|最低 1 つのサブクエリを含むクエリに対する最適化の数。|適用なし|  
|unnest failed|内部使用のみ|内部使用のみ|  
|表|最適化の合計数。|最適化された 1 つのクエリあたりの、参照テーブルの平均数。|  
|hints|ヒントが指定された回数。 カウントされるヒントには、JOIN、GROUP、UNION、および FORCE ORDER クエリ ヒント、FORCE PLAN 設定オプション、および結合ヒントが含まれます。|適用なし|  
|order hint|FORCE ORDER ヒントが指定された回数。|適用なし|  
|join hint|結合ヒントによって結合アルゴリズムが強制された回数。|適用なし|  
|view reference|ビューがクエリで参照された回数。|適用なし|  
|remote query|4 つの要素で構成される名前を持つテーブルまたは OPENROWSET の結果など、少なくとも 1 つのリモート データ ソースをクエリが参照した場合の最適化の数。|適用なし|  
|maximum DOP|最適化の合計数。|最適化プランに有効な MAXDOP の平均値。 既定では、有効な MAXDOP はによって決まります、**並列処理の次数の最大**サーバー構成オプションし、MAXDOP クエリ ヒントの値によって、特定のクエリをオーバーライドする可能性があります。|  
|maximum recursion level|クエリ ヒントで 0 より大きい MAXRECURSION レベルが指定された最適化の数。|クエリ ヒントで最大再帰レベルが指定された、最適化における MAXRECURSION レベルの平均。|  
|indexed views loaded|内部使用のみ|内部使用のみ|  
|indexed views matched|1 つ以上のインデックス付きビューが一致した、最適化の数。|一致したビューの平均数。|  
|indexed views used|出力プラン内で照合された後に 1 つ以上のインデックス付きビューが使用されている、最適化の数。|使用されたビューの平均数。|  
|indexed views updated|1 つ以上のインデックス付きビューを管理するプランを作成する DML ステートメントの最適化の数。|管理されるビューの平均数。|  
|dynamic cursor request|動的カーソルの要求が指定された最適化の数。|適用なし|  
|fast forward cursor request|高速順方向カーソルの要求が指定された最適化の数。|適用なし|  
|merge stmt|MERGE ステートメントに対する最適化の数。|適用なし|  
  
## <a name="examples"></a>使用例  
  
### <a name="a-viewing-statistics-on-optimizer-execution"></a>A. オプティマイザー実行における統計を表示する  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに対する、現在のオプティマイザー実行の統計を表示します。  
  
```  
SELECT * FROM sys.dm_exec_query_optimizer_info;  
```  
  
### <a name="b-viewing-the-total-number-of-optimizations"></a>B. 最適化の合計数を表示する  
 実行される最適化の数を表示します。  
  
```  
SELECT occurrence AS Optimizations FROM sys.dm_exec_query_optimizer_info  
WHERE counter = 'optimizations';  
```  
  
### <a name="c-average-elapsed-time-per-optimization"></a>C. 最適化ごとの平均経過時間を表示する  
 最適化ごとの平均経過時間を表示します。  
  
```  
SELECT ISNULL(value,0.0) AS ElapsedTimePerOptimization  
FROM sys.dm_exec_query_optimizer_info WHERE counter = 'elapsed time';  
```  
  
### <a name="d-fraction-of-optimizations-that-involve-subqueries"></a>D. サブクエリを含む最適化の割合を表示する  
 サブクエリを含む最適化されたクエリの割合を表示します。  
  
```  
SELECT (SELECT CAST (occurrence AS float) FROM sys.dm_exec_query_optimizer_info WHERE counter = 'contains subquery') /  
       (SELECT CAST (occurrence AS float)   
        FROM sys.dm_exec_query_optimizer_info WHERE counter = 'optimizations')  
        AS ContainsSubqueryFraction;  
```  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [実行関連の動的管理ビューおよび関数&#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  


