---
title: "ジョブの利用状況モニターの更新 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.jobactivitymon.refresh.f1"
ms.assetid: 413a368e-fd2b-4e1f-b370-002cdbc85bab
caps.latest.revision: 11
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 11
---
# ジョブの利用状況モニターの更新
  **[更新の設定]** ダイアログ ボックスを使用すると、ジョブの利用状況モニターでサーバーの利用状況に関する新しい情報を取得する頻度を構成できます。 ジョブの利用状況モニターは、監視対象のサーバーに対してクエリを実行して、[ジョブの利用状況モニター] グリッドの情報を取得する必要があります。 自動更新の間隔を 30 秒未満に設定すると、これらのクエリを実行する時間がサーバーのパフォーマンスに影響を与える可能性があります。  
  
 このダイアログを開くには、ジョブの利用状況モニターの **[状態]**セクションの **[更新の設定を表示します]** をクリックします。  
  
## オプション  
 **[次の間隔で自動更新する]**  
 オンにすると、ジョブの利用状況モニターの情報の自動更新が有効になります。 既定では、このオプションはオフになっています。  
  
 **seconds**  
 自動更新の間隔 (秒数) です。 既定値は 60 秒です。 5 秒以下に設定した場合は、5 秒ごとに情報が更新されます。  
  
## 参照  
 [ジョブの利用状況の監視](../../ssms/agent/monitor-job-activity.md)  
  
  