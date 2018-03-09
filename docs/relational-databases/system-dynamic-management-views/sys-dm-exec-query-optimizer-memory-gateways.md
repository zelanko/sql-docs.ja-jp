---
title: "sys.dm_exec_query_optimizer_memory_gateways (TRANSACT-SQL) |Microsoft ドキュメント"
description: "同時実行クエリの最適化を抑制するために使用するリソース セマフォの現在の状態を返します"
ms.custom: 
ms.date: 04/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b65e22d1cd2f403e2ed3aa1bd1dc14faa90079b9
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmexecqueryoptimizermemorygateways-transact-sql"></a>sys.dm_exec_query_optimizer_memory_gateways (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

同時実行クエリの最適化を抑制するために使用するリソース セマフォの現在の状態を返します。

|列|型|Description|  
|----------|---------------|-----------------|  
|**pool_id**|**int**|リソース ガバナー リソース プール ID|  
|**name**|**sysname**|ゲート名 (小さなゲートウェイ、中規模ゲートウェイの場合は、大規模ゲートウェイ) のコンパイルします。|
|**max_count**|**int**|最大同時実行モードでのコンパイルの数を構成します。|
|**active_count**|**int**|現在アクティブなこのゲートのコンパイル数|
|**waiter_count**|**int**|このゲートの待機中の数|
|**threshold_factor**|**bigint**|クエリの最適化によって使用されるメモリの最大の部分を定義するしきい値の係数。  Small のゲートウェイの threshold_factor では、小規模のゲートウェイにアクセスする必要が前にクエリが 1 つのバイト単位で最大オプティマイザー メモリ使用量を示します。  中規模および大規模なゲートウェイの場合は、threshold_factor は、このゲートの使用できる合計サーバー メモリの一部を示しています。 ゲートのメモリ使用率のしきい値を計算するときに、除数として使用されます。|
|**threshold**|**bigint**|[次へ] のしきい値メモリのバイト。  アクセスするために、このゲートウェイに、メモリの消費がこのしきい値に達すると、クエリが必要です。  「-1」場合は、クエリは、このゲートウェイにアクセスする必要はありません。|
|**is_active**|**bit**|かどうかを現在のゲートを渡すか、クエリが必要です。|


## <a name="permissions"></a>権限  
SQL Server では、サーバーに対する VIEW SERVER STATE 権限が必要です。

Azure SQL Database には、データベース内の VIEW DATABASE STATE 権限が必要です。


## <a name="remarks"></a>解説  
SQL Server では、ゲートウェイの階層型アプローチを使用して許可される同時実行のコンパイルの数を調整します。  Small、medium など、大規模な 3 つのゲートウェイが使用されます。 ゲートウェイは、コンパイルのより大きなメモリ要求のコンシューマーによって全体的なメモリ リソースの枯渇を防ぐのに役立ちます。

コンパイルの遅延ゲートウェイ検索結果を待機します。 コンパイルの遅延、だけでなく、調整された要求は待機の種類が蓄積される関連付けの RESOURCE_SEMAPHORE_QUERY_COMPILE があります。 クエリは、コンパイルの大量のメモリを使用していることとそのメモリが不足しているか、または十分なメモリが全体的に見て、RESOURCE_SEMAPHORE_QUERY_COMPILE 待機の種類がある可能性がありますただし使用可能な特定のユニットゲートウェイがなくなりました。 出力**sys.dm_exec_query_optimizer_memory_gateways**場合のトラブルシューティングに使用できますがメモリ不足のため、クエリ実行プランをコンパイルします。  

## <a name="examples"></a>使用例  

### <a name="a-viewing-statistics-on-resource-semaphores"></a>A. リソース セマフォの統計情報の表示  
SQL Server のこのインスタンスの現在のオプティマイザー メモリ ゲートウェイの統計情報とは

```  
SELECT [pool_id], [name], [max_count], [active_count],
       [waiter_count], [threshold_factor], [threshold],
       [is_active]
FROM sys.dm_exec_query_optimizer_memory_gateways;   

```  

## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](./system-dynamic-management-views.md)   
 [実行関連の動的管理ビューおよび関数 &#40;TRANSACT-SQL と #41 です。](./execution-related-dynamic-management-views-and-functions-transact-sql.md)  
[DBCC MEMORYSTATUS コマンドを使用して、SQL Server 2005 のメモリ使用量を監視する方法](https://support.microsoft.com/help/907877/how-to-use-the-dbcc-memorystatus-command-to-monitor-memory-usage-on-sql-server-2005)
[大規模なクエリのコンパイルを SQL Server 2014 で RESOURCE_SEMAPHORE_QUERY_COMPILE 待機](https://support.microsoft.com/help/3024815/large-query-compilation-waits-on-resource-semaphore-query-compile-in-sql-server-2014)
