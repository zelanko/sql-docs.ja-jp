---
title: "blocked process threshold サーバー構成オプション | Microsoft Docs"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- thresholds [SQL Server]
- blocked process threshold option
ms.assetid: 3d46d143-bc6a-4220-8b55-6baa37547c25
caps.latest.revision: "20"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 18905f1c5eb69d95f51767a50ceb7846e26582f3
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="blocked-process-threshold-server-configuration-option"></a>blocked process threshold サーバー構成オプション
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ブロックされたプロセスのレポートを生成するためのしきい値を秒単位で指定するには、 **blocked process threshold** オプションを使用します。 しきい値は 0 ～ 86,400 の範囲で設定できます。 既定では、ブロックされているプロセスのレポートは生成されません。 システム タスクや、検出可能なデッドロックを生成しないリソースで待機しているタスクの場合、このイベントは生成されません。  
  
 このイベントが生成されたときに [警告](http://msdn.microsoft.com/library/3f57d0f0-4781-46ec-82cd-b751dc5affef) が実行されるように定義できます。 たとえば、ブロック状態を処理する適切な操作を行うために、管理者を呼び出すように選択できます。  
  
 blocked process threshold オプションでは、デッドロック監視バックグラウンド スレッドを使用して、設定されたしきい値より長い間待機しているか、またはしきい値の数倍の時間待機しているタスクの一覧を調べます。 イベントは、ブロックされた各タスクの報告間隔ごとに 1 回生成されます。  
  
 ブロックされたプロセスのレポートは、ベスト エフォートの原則で行われます。 リアルタイムまたはリアルタイムに近い報告は保証されていません。  
  
 この設定は、サーバーを停止して再起動しなくてもすぐに有効になります。  
  
## <a name="examples"></a>使用例  
 次の例では、 `blocked process threshold` を `20` 秒に設定して、ブロックされたタスクごとに、ブロックされたプロセスのレポートを生成します。  
  
```  
sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE ;  
GO  
sp_configure 'blocked process threshold', 20 ;  
GO  
RECONFIGURE ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [Blocked Process Report イベント クラス](../../relational-databases/event-classes/blocked-process-report-event-class.md)  
  
  
