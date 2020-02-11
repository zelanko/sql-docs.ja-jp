---
title: '[ジョブの利用状況モニター] | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.ACTIVITYMON.F1
- sql12.ag.jobactivitymonitor.alljobs.f1
ms.assetid: 11f2182c-5f71-46f8-8d2b-74f0fc48f2d6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f34b06d90bfb8e028004beb03c3f4b9a87345c0d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68211379"
---
# <a name="job-activity-monitor"></a>[ジョブの利用状況モニター]
  このページでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブの現在の利用状況を参照できます。 
  **[フィルター]** をクリックすると、表示されるジョブが限定されます。 
  **[エージェント ジョブの利用状況]** グリッドは読み取り専用です。 列ヘッダーをクリックすると、グリッドが並べ替えられます。 ジョブを変更するには、ジョブをダブルクリックして **[ジョブのプロパティ]** ダイアログ ボックスを開きます。 グリッドでジョブを右クリックして表示されるメニューから、すべてのジョブ ステップの実行の開始、特定のジョブ ステップの実行、ジョブの無効化または有効化、ジョブの更新、ジョブの削除、ジョブの履歴の表示、ジョブのプロパティの表示ができます。 
  **[最新の情報に更新]** をクリックすると、グリッドが現在の情報で更新されます。  
  
## <a name="options"></a>オプション  
 **名前**  
 ジョブの名前。  
  
 **有効**  
 ジョブが有効 (**[はい]**) か無効 (**[いいえ]**) かを示します。  
  
 **状態** <sup>1</sup>  
 ジョブの現在の状態です。  
  
 **最終実行の結果**  
 最終実行時のジョブの状態です。  
  
 **前回の実行**  
 サーバーのローカル時刻に基づき、ジョブが最後に実行された日付と時刻を示します。  
  
 **次の実行** <sup>1</sup>  
 サーバーのローカル時刻に基づき、ジョブが次に実行される予定の日付と時刻を示します。  
  
 **カテゴリ**  
 ジョブに割り当てられているジョブ カテゴリです。  
  
 **可**  
 ジョブを実行できる場合は **[はい]** 。ジョブを実行できない場合は [**いいえ**。 ステップがないジョブおよびターゲット サーバーがないジョブは実行できません。  
  
 **予定**  
 ジョブがジョブスケジュールに割り当てられている場合は **[はい]** になります。ジョブにスケジュールがない場合は [**いいえ**。  
  
 <sup>1</sup>[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Sysadmin 固定サーバーロールおよび server administrators グループのメンバーだけが、この列の値を表示できます。 SQLAgentOperatorRole ロールのメンバーはこの列の値を表示できません。  
  
#### <a name="to-open-the-job-activity-monitor"></a>[ジョブの利用状況モニター] を開くには  
  
-   
  **オブジェクト エクスプローラー**で、サーバーを展開して **[SQL Server エージェント]** を展開し、 **[ジョブの利用状況モニター]** を右クリックした後、 **[ジョブの利用状況の表示]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [ジョブの利用状況の監視](monitor-job-activity.md)  
  
  
