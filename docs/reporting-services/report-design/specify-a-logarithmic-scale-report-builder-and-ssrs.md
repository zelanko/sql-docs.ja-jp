---
title: 対数スケールの指定 (レポート ビルダー) | Microsoft Docs
description: ページ分割されたレポートのグラフで対数スケールを利用し、データを管理しやすくすることで、グラフの外観を改善します。
ms.date: 03/03/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: f3092c1c-b128-433d-9a95-983508b2a8d4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 9525e71bf388b6a9265be3a101c03db65c622084
ms.sourcegitcommit: 5b7457c9d5302f84cc3baeaedeb515e8e69a8616
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2020
ms.locfileid: "83688833"
---
# <a name="specify-a-logarithmic-scale-report-builder-and-ssrs"></a>対数スケールの指定 (レポート ビルダーおよび SSRS)
  対数比例するデータがある場合は、 [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] のページ分割されたレポートのグラフ上での対数スケールの使用を検討します。 これにより、データの管理が容易になり、グラフの外観が向上します。 ほとんどの対数スケールでは、底に 10 を使用します。  
  
 この機能は値軸でのみ使用できます。 通常、値軸は縦軸 (Y 軸) です。 ただし、横棒グラフの値軸は横軸 (X 軸) です。  
  
 軸が対数の場合、その軸に関連するその他すべてのプロパティは、対数スケールで示されます。 たとえば、10 を底とする対数スケールを軸で指定した場合、軸の間隔を 2 に設定すると、10 の 2 乗 (つまり 100) の増分率で間隔が生成されます。 つまり、軸の値は既定の 1、10、100、1000、10000 ではなく、1、100、10000 という値を取ります。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-specify-a-logarithmic-scale"></a>対数スケールを指定するには  
  
1.  グラフの Y 軸を右クリックし、 **[縦軸のプロパティ]** をクリックします。 **[縦軸のプロパティ]** ダイアログ ボックスが表示されます。  
  
2.  **[軸のオプション]** で、 **[対数スケールを使用する]** を選択します。  
  
3.  **[対数の底]** ボックスに、対数の底を正の値で入力します。 値を指定しなかった場合、対数の底は既定値の 10 に設定されます。  
  
## <a name="see-also"></a>参照  
 [グラフの軸ラベルの書式設定 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)   
 [グラフの書式設定 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)   
 [日付または通貨として軸ラベルを書式設定する &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md)   
 [グラフ &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)  
  
  
