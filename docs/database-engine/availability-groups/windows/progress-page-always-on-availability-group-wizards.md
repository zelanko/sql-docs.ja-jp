---
title: "[進行状況] ページ (AlwaysOn 可用性グループ ウィザード) | Microsoft Docs"
ms.custom: 
ms.date: 05/17/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.failoverwizard.progress.f1
- sql13.swb.adddatabasewizard.progress.f1
- sql13.swb.addreplicawizard.progress.f1
- sql13.swb.newagwizard.progress.f1
ms.assetid: bd3b0306-8384-4120-a1c9-03825f0ae26a
caps.latest.revision: 13
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 78fd0315e1f58eef1dbc5d8c41f6254817879d8c
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="progress-page-always-on-availability-group-wizards"></a>[進行状況] ページ (AlwaysOn 可用性グループ ウィザード)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  このダイアログ ボックスを使用すると、 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] で実行中の [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]ウィザードの進行状況を表示できます。 進行状況バーには、ウィザードが実行している手順の相対的な進行状況が示されます。  
  
## <a name="uielement-list"></a>UI 要素の一覧  
 **[詳細]**  
 下矢印をクリックすると、完了した手順を順に示す一覧と現在進行中の操作が進行状況グリッドに表示されます。 このグリッドには次の列が含まれています。  
  
 **名前**  
 各手順についての説明が表示されます。  
  
 **[状態]**  
 完了した手順の結果と、現在の手順の完了の割合を次のように示します。  
  
|結果|説明|  
|------------|-----------------|  
|**[エラー]**|この手順の操作がエラーになったことを示します。 リンクをクリックすると、エラーを説明するメッセージ ダイアログ ボックスが表示されます。|  
|**[実行中 (** *完了の割合* **)]**|操作が現在実行中であることを示し、この手順の進行状況をパーセンテージで示します。|  
|**Success**|この手順の操作が正常に完了したことを示します。|  
  
 **[詳細の非表示]**  
 進行状況グリッドを非表示にします。  
  
 **キャンセル**  
 残りのすべての操作をスキップして、ウィザードを終了します。  
  
##  <a name="RelatedTasks"></a> 関連タスク  
  
-   [[新しい可用性グループ] ダイアログ ボックスの使用 &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [可用性グループへのレプリカ追加ウィザードの使用 &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
-   [可用性グループへのデータベース追加ウィザードの使用 &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/availability-group-add-database-to-group-wizard.md)  
  
-   [可用性グループのフェールオーバー ウィザードの使用 &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-fail-over-availability-group-wizard-sql-server-management-studio.md)  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループの概要 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)  
  
  

