---
title: sys.dm_exec_query_optimizer_memory_gateways (TRANSACT-SQL) |Microsoft Docs
description: 同時実行クエリの最適化を抑制するために使用するリソース セマフォの現在の状態を返します
ms.custom: ''
ms.date: 04/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: performance
ms.topic: language-reference
f1_keywords:
- dm_exec_query_optimizer_memory_gateways_TSQL
- dm_exec_query_optimizer_memory_gateways
- sys.dm_exec_query_optimizer_memory_gateways_TSQL
- sys.dm_exec_query_optimizer_memory_gateways
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_query_optimizer_memory_gateways dynamic management view
author: josack
ms.author: josack
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: cf134f630e4112f0cef87b7138b92fc83959e230
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68097670"
---
# <a name="sysdmexecqueryoptimizermemorygateways-transact-sql"></a>sys.dm_exec_query_optimizer_memory_gateways (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

同時実行クエリの最適化を抑制するために使用するリソース セマフォの現在の状態を返します。

|[列]|種類|説明|  
|----------|---------------|-----------------|  
|**pool_id**|**int**|リソース ガバナーの下のリソース プール ID|  
|**name**|**sysname**|ゲート名 (中規模ゲートウェイの場合は、小規模のゲートウェイ大規模ゲートウェイ) のコンパイルします。|
|**max_count**|**int**|最大同時コンパイルの数を構成します。|
|**active_count**|**int**|現在アクティブなこのゲートのコンパイル数|
|**waiter_count**|**int**|このゲートの待機処理の数|
|**threshold_factor**|**bigint**|クエリの最適化で使用されるメモリの最大部分を定義するしきい値の係数。  小規模のゲートウェイの threshold_factor では、小規模のゲートウェイにアクセスする必要があります前に 1 つのクエリのバイト単位で最大オプティマイザー メモリ使用量を示します。  中規模および大規模なゲートウェイの場合は、threshold_factor は、このゲートの使用できる合計サーバー メモリの一部を示しています。 ゲートのメモリ使用率のしきい値を計算するときに、除数として使用されます。|
|**threshold**|**bigint**|(バイト単位) [次へ] のしきい値のメモリ。  そのメモリ消費量がこのしきい値に達した場合、このゲートウェイへのアクセスを取得するクエリが必要です。  「-1」場合は、クエリは、このゲートウェイに、アクセスする必要はありません。|
|**is_active**|**bit**|かどうかを現在のゲートを渡すか、クエリが必要です。|


## <a name="permissions"></a>アクセス許可  
SQL Server では、サーバーに対する VIEW SERVER STATE 権限が必要です。

Azure SQL Database には、データベースで VIEW DATABASE STATE 権限が必要です。


## <a name="remarks"></a>コメント  
SQL Server では、ゲートウェイの階層型アプローチを使用して許可される同時コンパイルの数を調整します。  S、m など、大規模な 3 つのゲートウェイが使用されます。 ゲートウェイは、大規模なコンパイルのメモリが必要なコンシューマーによって全体的なメモリ リソースの枯渇を防ぐのに役立ちます。

遅延コンパイルでゲートウェイの結果を待機します。 スロットルされた要求はコンパイルが遅延、に加えて、待機の種類が蓄積される関連付けの RESOURCE_SEMAPHORE_QUERY_COMPILE があります。 クエリは、コンパイルの大量のメモリを使用していることと、そのメモリが不足している、またはまたは十分なメモリが全体的に見て、RESOURCE_SEMAPHORE_QUERY_COMPILE 待機の種類を示す場合がありますにある特定のただし使用可能なユニットゲートウェイが使用されています。 出力**sys.dm_exec_query_optimizer_memory_gateways**シナリオのトラブルシューティングに使用できますが、クエリ実行プランをコンパイルする十分なメモリ。  

## <a name="examples"></a>使用例  

### <a name="a-viewing-statistics-on-resource-semaphores"></a>A. リソース セマフォの統計情報の表示  
SQL Server のこのインスタンスの現在のオプティマイザー メモリ ゲートウェイの統計情報とは

```  
SELECT [pool_id], [name], [max_count], [active_count],
       [waiter_count], [threshold_factor], [threshold],
       [is_active]
FROM sys.dm_exec_query_optimizer_memory_gateways;   

```  

## <a name="see-also"></a>関連項目  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](./system-dynamic-management-views.md)   
 [実行関連の動的管理ビューおよび関数 &#40;Transact-SQL&#41;](./execution-related-dynamic-management-views-and-functions-transact-sql.md)  
[DBCC MEMORYSTATUS コマンドを使用して、SQL Server 2005 のメモリ使用量を監視する方法](https://support.microsoft.com/help/907877/how-to-use-the-dbcc-memorystatus-command-to-monitor-memory-usage-on-sql-server-2005)
[大きなクエリ コンパイルが SQL Server 2014 で RESOURCE_SEMAPHORE_QUERY_COMPILE で待機](https://support.microsoft.com/help/3024815/large-query-compilation-waits-on-resource-semaphore-query-compile-in-sql-server-2014)
