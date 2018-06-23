---
title: グラフのトラブルシューティング (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a327ffa-3b69-40d6-8015-cc01cfae9161
caps.latest.revision: 7
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: b5369ef0fd3f96345e0fc7e0c688f1230bfe41c1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36164020"
---
# <a name="troubleshoot-charts-report-builder-and-ssrs"></a>グラフのトラブルシューティング (レポート ビルダーおよび SSRS)
  グラフを使用するときに役立つヒントを以下に示します。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="why-does-my-chart-count-not-sum-the-values-on-the-value-axis"></a>グラフの値軸で件数がカウントされ、値が合計されない  
 ほとんどの種類のグラフでは、正確に描画するために値軸 (通常は Y 軸) に数値が必要です。 値フィールドのデータ型が場合`String`フィールドに数字がある場合でも、グラフは、数値を表示できません。 その代わり、グラフには、そのフィールドに値が格納されている行の総数が表示されます。 この動作を回避するには、値系列に使用するフィールドに、書式設定された数値を格納した文字列ではなく、数値データ型を設定してください。  
  
## <a name="see-also"></a>参照  
 [グラフ&#40;レポート ビルダーおよび SSRS&#41;](charts-report-builder-and-ssrs.md)  
  
  