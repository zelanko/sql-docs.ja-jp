---
title: "サーバーのポーリング | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- target servers [SQL Server], polling interval
- polling master servers [SQL Server]
- server polling [SQL Server]
- master servers [SQL Server], polling
- polling interval [SQL Server]
ms.assetid: 96f5fd43-3edd-4418-9dd0-4d34e618890e
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d45f50c0ac7a211f00fbdb1b0b08245c474bebf1
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="poll-servers"></a>サーバーのポーリング
マルチサーバー管理を実装している場合、対象サーバーからマスター サーバーに定期的にアクセスし、既に実行したジョブの情報をアップロードして新しいジョブをダウンロードします。 マスター サーバーにアクセスする処理は *サーバー ポーリング* と呼ばれ、定期的な *ポーリング間隔*で行われます。  
  
## <a name="polling-intervals"></a>ポーリング間隔  
対象サーバーからマスター サーバーに接続し、命令をダウンロードしてジョブの実行結果をアップロードする頻度をポーリング間隔 (既定値は 1 分) で制御します。  
  
対象サーバーからマスター サーバーにポーリングするとき、対象サーバーに割り当てられる操作を **msdb** データベースの **sysdownloadlist** テーブルから読み取ります。 読み取った操作により、マルチサーバー ジョブや対象サーバーのさまざまな動作を制御します。 操作の例には、ジョブの削除、ジョブの挿入、ジョブの開始、対象サーバーのポーリング間隔の更新などがあります。  
  
操作は次のいずれかの方法で **sysdownloadlist** テーブルに書き込まれます。  
  
-   **sp_post_msx_operation** ストアド プロシージャを使用して明示的に行います。  
  
-   他のジョブ ストアド プロシージャを使用して暗黙的に行います。  
  
ジョブ ストアド プロシージャを使用してマルチサーバー ジョブ スケジュールやジョブ ステップを変更する場合、または SQL-DMO (SQL 分散管理オブジェクト) を使用してマルチサーバー ジョブを制御する場合、マルチサーバー ジョブのステップやスケジュールを変更してから次のコマンドを実行します。  
  
```  
EXECUTE msdb.dbo.sp_post_msx_operation 'INSERT', 'JOB', '<job id>'  
```  
  
このコマンドを実行すると、現在のジョブ定義が対象サーバーと同期されます。  
  
次の場合、操作を明示的に書き込む必要はありません。  
  
-   Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] を使用してマルチサーバー ジョブを制御する場合。  
  
-   ジョブ スケジュールまたはジョブ ステップを変更しないジョブ ストアド プロシージャの場合。  
  
**対象サーバーからマスター サーバーにポーリングさせるには**  
  
-   [SQL Server Management Studio](../../ssms/agent/force-a-target-server-to-poll-the-master-server.md)  
  
-   [Transact-SQL](http://msdn.microsoft.com/en-us/085deef8-2709-4da9-bb97-9ab32effdacf)  
  
## <a name="see-also"></a>参照  
[イベントの管理](../../ssms/agent/manage-events.md)  
  
