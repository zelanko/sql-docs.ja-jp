---
title: MSSQLSERVER_10509 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 10509 (Database Engine error)
ms.assetid: e9dd5357-ee3d-420a-9a89-d12ab5404e73
caps.latest.revision: 10
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: fb203b703df342107384cf0c082917aea18c5f20
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36076877"
---
# <a name="mssqlserver10509"></a>MSSQLSERVER_10509
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|10509|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|PG_INVALID_STMT|  
|メッセージ テキスト|プラン ガイドを作成することはできません ' % です。\*%1! によって指定されたステートメント`@stmt`または`@statement_start_offset`構文エラーを含む、またはプラン ガイドで使用する条件を満たしません。 有効な [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを 1 つだけ指定するか、またはバッチ内のステートメントの有効な開始位置を指定します。 有効な開始位置を取得するには、動的管理関数 sys.dm_exec_query_stats の statement_start_offset 列のクエリを実行します。|  
  
## <a name="explanation"></a>説明  
 `@stmt` または `@statement_start_offset` で指定したステートメントが構文エラーを含んでいるか、またはプラン ガイドでの使用に適していません。  
  
## <a name="user-action"></a>ユーザーの操作  
 有効な [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを 1 つだけ指定するか、またはバッチ内のステートメントの有効な開始位置を指定します。 有効な開始位置を取得するには、動的管理関数 sys.dm_exec_query_stats の statement_start_offset 列のクエリを実行します。  
  
## <a name="see-also"></a>参照  
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [プラン ガイド](../performance/plan-guides.md)   
 [sys.dm_exec_query_stats &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
