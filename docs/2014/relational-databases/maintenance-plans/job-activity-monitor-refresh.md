---
title: ジョブの利用状況モニターの更新 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql13.swb.jobactivitymon.refresh.f1
ms.assetid: 413a368e-fd2b-4e1f-b370-002cdbc85bab
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 44490a19763f69a4ed88d15aacdfba853db8c040
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62856477"
---
# <a name="job-activity-monitor-refresh"></a>ジョブの利用状況モニターの更新
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  **[更新の設定]** ダイアログ ボックスを使用すると、ジョブの利用状況モニターでサーバーの利用状況に関する新しい情報を取得する頻度を構成できます。 ジョブの利用状況モニターは、監視対象のサーバーに対してクエリを実行して、[ジョブの利用状況モニター] グリッドの情報を取得する必要があります。 自動更新の間隔を 30 秒未満に設定すると、これらのクエリを実行する時間がサーバーのパフォーマンスに影響を与える可能性があります。  
  
 このダイアログを開くには、ジョブの利用状況モニターの **[状態]** セクションの **[更新の設定を表示します]** をクリックします。  
  
## <a name="options"></a>および  
 **[次の間隔で自動更新する]**  
 オンにすると、ジョブの利用状況モニターの情報の自動更新が有効になります。 既定では、このオプションはオフになっています。  
  
 **seconds**  
 自動更新の間隔 (秒数) です。 既定値は 60 秒です。 5 秒以下に設定した場合は、5 秒ごとに情報が更新されます。  
  
## <a name="see-also"></a>参照  
 [ジョブの利用状況の監視](../../ssms/agent/monitor-job-activity.md)  
  
  
