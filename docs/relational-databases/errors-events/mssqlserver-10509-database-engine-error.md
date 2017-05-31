---
title: MSSQLSERVER_10509 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 10509 (Database Engine error)
ms.assetid: e9dd5357-ee3d-420a-9a89-d12ab5404e73
caps.latest.revision: 9
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f4a15b91d34353e7bf7206b1367620e2de00ff9d
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

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
|メッセージ テキスト|プラン ガイド '%.\*ls' を作成できません。**@stmt** または **@statement_start_offset** で指定したステートメントが構文エラーを含んでいるか、またはプラン ガイドでの使用に適していません。 有効な [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを 1 つだけ指定するか、またはバッチ内のステートメントの有効な開始位置を指定します。 有効な開始位置を取得するには、動的管理関数 sys.dm_exec_query_stats の statement_start_offset 列のクエリを実行します。|  
  
## <a name="explanation"></a>説明  
**@stmt** または **@statement_start_offset** で指定したステートメントが構文エラーを含んでいるか、またはプラン ガイドでの使用に適していません。  
  
## <a name="user-action"></a>ユーザーの操作  
有効な [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを 1 つだけ指定するか、またはバッチ内のステートメントの有効な開始位置を指定します。 有効な開始位置を取得するには、動的管理関数 sys.dm_exec_query_stats の statement_start_offset 列のクエリを実行します。  
  
## <a name="see-also"></a>参照  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[プラン ガイド](~/relational-databases/performance/plan-guides.md)  
[sys.dm_exec_query_stats &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  

