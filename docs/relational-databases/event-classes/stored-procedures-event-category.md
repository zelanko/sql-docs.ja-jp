---
title: Stored Procedures イベント カテゴリ | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Stored Procedures event category [SQL Server]
- SQL Server event classes, Stored Procedures event category
- event classes [SQL Server], Stored Procedures event category
ms.assetid: 71bebaa3-a05a-4695-b349-078cecd0949a
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 766ea798faa2df28520fa93c852add32e6778c80
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85790968"
---
# <a name="stored-procedures-event-category"></a>Stored Procedures イベント カテゴリ
[!INCLUDE [SQL Server - ASDB](../../includes/applies-to-version/sql-asdb.md)]
  **Stored Procedures** イベント カテゴリには、一般的なストアド プロシージャ イベントが含まれています。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|説明|  
|-----------|-----------------|  
|[RPC:Completed イベント クラス](../../relational-databases/event-classes/rpc-completed-event-class.md)|リモート プロシージャ コール (RPC) が完了したことを示します。|  
|[PreConnect:Completed イベント クラス](../../relational-databases/event-classes/preconnect-completed-event-class.md)|リソース ガバナー分類子関数の実行が終了したことを示します。|  
|[PreConnect:Starting イベント クラス](../../relational-databases/event-classes/preconnect-starting-event-class.md)|リソース ガバナー分類子関数の実行が開始されたことを示します。|  
|[RPC Output Parameter イベント クラス](../../relational-databases/event-classes/rpc-output-parameter-event-class.md)|リモート プロシージャ コールの実行後に、その出力パラメーターの値をトレースします。|  
|[RPC:Starting イベント クラス](../../relational-databases/event-classes/rpc-starting-event-class.md)|リモート プロシージャ コールが開始されたことを示します。|  
|[SP:CacheHit イベント クラス](../../relational-databases/event-classes/sp-cachehit-event-class.md)|ストアド プロシージャがキャッシュに存在することを示します。|  
|[SP:CacheInsert イベント クラス](../../relational-databases/event-classes/sp-cacheinsert-event-class.md)|ストアド プロシージャがキャッシュに挿入されたことを示します。|  
|[SP:CacheMiss イベント クラス](../../relational-databases/event-classes/sp-cachemiss-event-class.md)|ストアド プロシージャがキャッシュで見つからなかったことを示します。|  
|[SP:CacheRemove イベント クラス](../../relational-databases/event-classes/sp-cacheremove-event-class.md)|ストアド プロシージャがキャッシュから削除されていることを示します。|  
|[SP:Completed イベント クラス](../../relational-databases/event-classes/sp-completed-event-class.md)|ストアド プロシージャの実行が完了したことを示します。|  
|[SP:Recompile イベント クラス](../../relational-databases/event-classes/sp-recompile-event-class.md)|ストアド プロシージャが再コンパイルされたことを示します。|  
|[SP:Starting イベント クラス](../../relational-databases/event-classes/sp-starting-event-class.md)|ストアド プロシージャの実行が開始されたことを示します。|  
|[SP:StmtCompleted イベント クラス](../../relational-databases/event-classes/sp-stmtcompleted-event-class.md)|ストアド プロシージャ内の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントが完了したことを示します。|  
|[SP:StmtStarting イベント クラス](../../relational-databases/event-classes/sp-stmtstarting-event-class.md)|ストアド プロシージャ内の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントが開始されたことを示します。|  
  
## <a name="see-also"></a>参照  
 [拡張イベント](../../relational-databases/extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  
