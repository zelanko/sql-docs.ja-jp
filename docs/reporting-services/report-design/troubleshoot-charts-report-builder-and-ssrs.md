---
title: "グラフ (レポート ビルダーおよび SSRS) のトラブルシューティング |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a327ffa-3b69-40d6-8015-cc01cfae9161
caps.latest.revision: 7
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: Inactive
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: a84dbd7d608d2de7ced66e66b49288fbf8fe1682
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="troubleshoot-charts-report-builder-and-ssrs"></a>グラフのトラブルシューティング (レポート ビルダーおよび SSRS)
  グラフを使用するときに役立つヒントを以下に示します。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="why-does-my-chart-count-not-sum-the-values-on-the-value-axis"></a>グラフの値軸で件数がカウントされ、値が合計されない  
 ほとんどの種類のグラフでは、正確に描画するために値軸 (通常は Y 軸) に数値が必要です。 値フィールドのデータ型が **String**の場合、フィールドに数字が入っていても、グラフでは数値を表示できません。 その代わり、グラフには、そのフィールドに値が格納されている行の総数が表示されます。 この動作を回避するには、値系列に使用するフィールドに、書式設定された数値を格納した文字列ではなく、数値データ型を設定してください。  
  
## <a name="see-also"></a>参照  
 [グラフ (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)  
  
  

