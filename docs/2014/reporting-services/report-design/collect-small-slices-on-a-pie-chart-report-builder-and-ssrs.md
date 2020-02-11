---
title: 円グラフの小さいスライスをまとめる (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 21c2b8cb-b9ca-4bc0-bf49-50ba432562f6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 517f5c5dddd809ee71037a95d04109a005968132
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66106220"
---
# <a name="collect-small-slices-on-a-pie-chart-report-builder-and-ssrs"></a>円グラフの小さいスライスをまとめる (レポート ビルダーおよび SSRS)
  円グラフに表示されるデータ ポイントが多すぎると、円グラフの外観が煩雑になります。 この問題を解決するため、特定の値を下回るすべてのデータを、円グラフ上の 1 つのスライスとして表示できます。  
  
 小さいスライスを 1 つのスライスにまとめるには、まず小さいスライスを収集するためのしきい値を円グラフに対する比率と固定値のどちらで表すかを決定します。 次に、[CollectedThreshold] と [CollectedThresholdUsePercent] プロパティを設定します。[CollectedThreshold] プロパティを、収集する値が必ず下回るグラフのパーセンテージ、またはコレクションの実際のしきい値データの値のいずれかに設定します。 パーセントを使用するか`True` 、実際の値を`False`使用するには、collectedthresholdusepercent] プロパティをに設定します。  
  
 小さいスライスは、1 つ目の円グラフでまとめられたスライスから切り離し、2 つ目の円グラフにまとめることもできます。 2 つ目の円グラフは元の円グラフの右側に描画されます。  
  
 じょうごグラフまたはピラミッド グラフのスライスを 1 つのスライスに結合することはできません。  
  
 このグラフについては、サンプル レポートに例が含まれています。 このサンプルレポートのダウンロードの詳細については、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]「[サンプルレポートのレポートビルダーとレポートデザイナー](https://go.microsoft.com/fwlink/?LinkId=198283)」を参照してください。  
  
### <a name="to-collect-small-slices-into-a-single-slice-on-a-pie-chart"></a>円グラフの小さいスライスを 1 つのスライスにまとめるには  
  
1.  プロパティ ペインを開きます。  
  
2.  デザイン画面で、円グラフの任意のスライスをクリックします。 系列のプロパティが [プロパティ] ペインに表示されます。  
  
3.  **[全般]** セクションで、 **[CustomAttributes]** ノードを展開します。  
  
4.  [CollectedStyle] プロパティを **[SingleSlice]** に設定します。  
  
5.  収集されるしきい値としきい値の種類を設定します。 次の例は、収集されるしきい値を設定する一般的な方法です。  
  
    -   **比率で設定します。** たとえば、円グラフ上の 10% 未満の小さいスライスを 1 つのスライスにまとめるには、次の手順を実行します。  
  
         Collectedthresholdusepercent] プロパティをに`True`設定します。  
  
         [CollectedThreshold] プロパティを **10**に設定します。  
  
        > [!NOTE]  
        >  [Collectedstyle] を **[singleslice]** に設定し、CollectedThreshold を**100**より大きい値に設定し、collectedthresholdusepercent] `True`がである場合、グラフではパーセンテージを計算できないため、例外がスローされます。 この問題を解決するには、[CollectedThreshold] を **100** 未満の値に設定します。  
  
    -   **データ値で設定します。** たとえば、円グラフ上の 5,000 未満の小さいスライスを 1 つのスライスにまとめるには、次の手順を実行します。  
  
         Collectedthresholdusepercent] プロパティをに`False`設定します。  
  
         [CollectedThreshold] プロパティを **5000**に設定します。  
  
6.  [CollectedLabel] プロパティを、収集されたスライスに表示されるテキスト ラベルを表す文字列に設定します。  
  
7.  (省略可) CollectedSliceExploded、CollectedColor、CollectedLegendText および CollectedToolTip の各プロパティを設定します。 これらのプロパティでは、1 つのスライスの外観、色、ラベルのテキスト、凡例のテキスト、およびツールヒントを変更します。  
  
### <a name="to-collect-small-slices-into-a-secondary-callout-pie-chart"></a>小さいスライスをまとめた 2 つ目の円グラフにするには  
  
1.  上記の手順 1. ～ 3. を実行します。  
  
2.  [CollectedStyle] プロパティを **[CollectedPie]** に設定します。  
  
3.  [CollectedThreshold] プロパティを、小さいスライスを 1 つのスライスにまとめる基準となるしきい値を表す値に設定します。 [Collectedstyle] プロパティが**CollectedPie**に設定されている場合、CollectedThresholdUsePercentproperty は常`True`にに設定され、収集されるしきい値は常に比率で計測されます。  
  
4.  (省略可) CollectedColor、CollectedLabel、CollectedLegendText および CollectedToolTip の各プロパティを設定します。 "Collected" という名前を持つその他すべてのプロパティは、まとめられた円に適用されません。  
  
> [!NOTE]  
>  2 つ目の円グラフは、データの中の小さいスライスに基づいて計算され、プレビューのみに表示されます。 この円グラフはデザイン画面には表示されません。  
  
> [!NOTE]  
>  2 つ目の円グラフの書式は設定できません。 このため、円スライスを収集する際は最初の方法を使用することを強くお勧めします。  
  
## <a name="see-also"></a>参照  
 [円グラフ &#40;レポート ビルダーおよび SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [グラフでのデータ ポイントの書式設定 (レポート ビルダーおよび SSRS)](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)   
 [レポートビルダーおよび SSRS&#41;&#40;円グラフの外側にデータポイントラベルを表示する](display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md)   
 [レポートビルダーおよび SSRS&#41;&#40;円グラフにパーセンテージ値を表示する](display-percentage-values-on-a-pie-chart-report-builder-and-ssrs.md)   
 [グラフへの 3D 効果の追加 &#40;レポート ビルダーおよび SSRS&#41;](chart-effects-add-3d-effects-report-builder.md)  
  
  
