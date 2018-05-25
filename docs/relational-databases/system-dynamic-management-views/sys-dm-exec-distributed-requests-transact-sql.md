---
title: sys.dm_exec_distributed_requests (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DM_EXEC_DISTRIBUTED_REQUESTS
- DM_EXEC_DISTRIBUTED_REQUESTS_TSQL
- SYS.DM_EXEC_DISTRIBUTED_REQUESTS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- PolyBase,views
- sys.dm_exec_distributed_sql_requests management view
- PolyBase
- dm_exec_distributed_sql_requests management view
ms.assetid: c041d416-d8c6-435e-a563-6a310abd33e3
caps.latest.revision: 8
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 7d61b26c1af6a588140cdf47308ee8f69ecd42b2
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmexecdistributedrequests-transact-sql"></a>sys.dm_exec_distributed_requests (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  現在または最近アクティブになっている PolyBase クエリのすべての要求に関する情報を保持します。 これには、要求/クエリごとに 1 行が一覧表示します。  
  
 セッションに基づいており、要求 ID、ユーザーことができますし、取得、実際の分散要求を実行する – sys.dm_exec_distributed_requests を使用して生成されました。 たとえば、正規 SQL および SQL テーブルの外部に関連するクエリに分解し、さまざまなステートメントおよび要求のさまざまなコンピューティング ノード間で実行します。 すべてのコンピューティング ノード間で分散の手順を追跡するために、'global' の実行 ID のそれぞれの 1 つの特定の要求と演算子に関連付けられている計算ノード上のすべての操作を追跡するために使用できるについて紹介します。  
  
|列名|データ型|Description|範囲|  
|-----------------|---------------|-----------------|-----------|  
|sql_handle|**varbinary(64)**|このビューのキーです。 要求に関連付けられている一意の数値 id です。|システム内のすべての要求間で一意です。|  
|execution_id|**nvarchar(32**|このクエリの実行に使用されたセッションに関連付けられた一意の数値 id です。||  
|ステータス|**nvarchar(32**|要求の現在の状態。|'Pending' 'を承認する'、'AcquireSystemResources'、'初期化'、'プラン'、'解析'、'AquireResources'、'を実行している'、'キャンセルする'、'包括的な」は ' Failed'、「取り消し済み」です。|  
|error_id|**nvarchar(36)**|存在する場合は、要求に関連付けられているエラーの一意の id。|エラーが発生していない場合は、NULL に設定します。|  
|start_time|**datetime**|要求の実行が開始された時刻。|キューに置かれた要求の場合は 0それ以外の場合、有効な datetime 以下に、現在の時刻。|  
|end_time|**datetime**|エンジンが、要求のコンパイルを完了した時刻。|キューに置かれた、またはアクティブな要求の場合は nullそれ以外の場合、現在の時刻に以下の有効な datetime です。|  
|total_elapsed_time|**int**|(ミリ秒単位)、要求を開始してから、実行の経過時間です。|0 ～ start_time と end_time の違いです。Total_elapsed_time では、整数の最大値を超えると、total_elapsed_time 引き続き、最大値になります。 この状態が「、最大値を超過しました」警告を生成します。 最大値をミリ秒単位は 24.8 日に相当します。|  
  
## <a name="see-also"></a>参照  
 [PolyBase 動的管理ビューでのトラブルシューティング](http://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [データベース関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
