---
title: "トレース (SQL Server Profiler) の再生に関する注意事項 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- traces [SQL Server], replaying
- replaying traces
ms.assetid: 73fa339f-b71a-4be4-97ca-d4ae84c8b90b
caps.latest.revision: 21
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 77934826a2ba364c4ec8b4e6a5295699d8469257
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="considerations-for-replaying-traces-sql-server-profiler"></a>トレースの再生に関する注意点 (SQL Server Profiler)
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]次の種類のトレースを再生できません。  
  
-   トランザクション レプリケーションや他のトランザクションのログ利用状況を含むトレース。 このようなイベントはスキップされます。 他の種類のレプリケーションではトランザクション ログが記録されないので、そのようなレプリケーションは影響を受けません。  
  
-   グローバル一意識別子 (GUID) を必要とする操作を含むトレース。 このようなイベントはスキップされます。  
  
-   **bcp**ユーティリティ、BULK INSERT、READTEXT、WRITETEXT、UPDATETEXT ステートメントを必要とする **text**列、 **ntext** 列、および **image** 列での操作やフルテキスト操作を含むトレース。 このようなイベントはスキップされます。  
  
-   セッションをバインドする **sp_getbindtoken** および **sp_bindsession** システム ストアド プロシージャを含むトレース。 このようなイベントはスキップされます。  
  
> [!NOTE]  
>  あらかじめ構成された再生テンプレート (**TSQL_Replay**) を使用せず、必要なすべてのデータをキャプチャしていないトレースは、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] では再生されません。 詳細については、「 [再生を実行するための必要条件](../../tools/sql-server-profiler/replay-requirements.md)」を参照してください。  
  
 トレースの再生に必要な権限の詳細については、「 [SQL Server Profiler の実行に必要な権限](../../tools/sql-server-profiler/permissions-required-to-run-sql-server-profiler.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [bcp ユーティリティ](../../tools/bcp-utility.md)   
 [SQL Server イベント クラスのリファレンス](../../relational-databases/event-classes/sql-server-event-class-reference.md)   
 [sp_getbindtoken & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-getbindtoken-transact-sql.md)   
 [sp_bindsession & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-bindsession-transact-sql.md)   
 [一括挿入 &#40; です。Transact SQL と &#41; です。](../../t-sql/statements/bulk-insert-transact-sql.md)   
 [READTEXT & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/readtext-transact-sql.md)   
 [WRITETEXT と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/writetext-transact-sql.md)   
 [UPDATETEXT & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/updatetext-transact-sql.md)  
  
  
