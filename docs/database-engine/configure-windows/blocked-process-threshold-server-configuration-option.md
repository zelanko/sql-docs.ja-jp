---
title: blocked process threshold サーバー構成オプション | Microsoft Docs
description: blocked process threshold オプションを使用して、SQL Server がブロックされたプロセス レポートを生成してアラートを発行する間隔を指定する方法について説明します。
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- thresholds [SQL Server]
- blocked process threshold option
ms.assetid: 3d46d143-bc6a-4220-8b55-6baa37547c25
author: markingmyname
ms.author: maghan
ms.openlocfilehash: bdd5f7d01e7271609562fb7d42126746d6163de4
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85725244"
---
# <a name="blocked-process-threshold-server-configuration-option"></a>blocked process threshold サーバー構成オプション
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

 ブロックされたプロセスのレポートを生成するためのしきい値を秒単位で指定するには、 **blocked process threshold** オプションを使用します。 しきい値は 5 ～ 86,400 の範囲で設定できます。  ロック モニターは、5 秒ごとにスリープ状態を解除して、ブロック状態を検出します (デッドロックなどの他の条件も検索します)。 したがって、'blocked process threshold' の値を 1 に設定すると、1 秒間ブロックされているプロセスは検出されません。 ブロックされているプロセスを検出できる最小時間は 5 秒です。
 
 既定では、ブロックされているプロセスのレポートは生成されません。 システム タスクや、検出可能なデッドロックを生成しないリソースで待機しているタスクの場合、このイベントは生成されません。  
  
 このイベントが生成されたときに [警告](../../ssms/agent/alerts.md) が実行されるように定義できます。 たとえば、ブロック状態を処理する適切な操作を行うために、管理者を呼び出すように選択できます。  
  
 blocked process threshold オプションでは、デッドロック監視バックグラウンド スレッドを使用して、設定されたしきい値より長い間待機しているか、またはしきい値の数倍の時間待機しているタスクの一覧を調べます。 イベントは、ブロックされた各タスクの報告間隔ごとに 1 回生成されます。  
  
 ブロックされたプロセスのレポートは、ベスト エフォートの原則で行われます。 リアルタイムまたはリアルタイムに近い報告は保証されていません。  
  
 この設定は、サーバーを停止して再起動しなくてもすぐに有効になります。  
  
## <a name="examples"></a>例  
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
  
  
