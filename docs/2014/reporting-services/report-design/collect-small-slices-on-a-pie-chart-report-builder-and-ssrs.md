---
title: 円グラフの小さいスライスをまとめる (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 21c2b8cb-b9ca-4bc0-bf49-50ba432562f6
caps.latest.revision: 8
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: af1a270524d91621cdeb15b56ace7c07ad4a4df7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36074758"
---
# <a name="collect-small-slices-on-a-pie-chart-report-builder-and-ssrs"></a>円グラフの小さいスライスをまとめる (レポート ビルダーおよび SSRS)
  円グラフに表示されるデータ ポイントが多すぎると、円グラフの外観が煩雑になります。 この問題を解決するため、特定の値を下回るすべてのデータを、円グラフ上の 1 つのスライスとして表示できます。  
  
 小さいスライスを 1 つのスライスにまとめるには、まず小さいスライスを収集するためのしきい値を円グラフに対する比率と固定値のどちらで表すかを決定します。 次に、[CollectedThreshold] と [CollectedThresholdUsePercent] プロパティを設定します。[CollectedThreshold] プロパティを、収集する値が必ず下回るグラフのパーセンテージ、またはコレクションの実際のしきい値データの値のいずれかに設定します。 CollectedThresholdUsePercent プロパティを設定`True`パーセンテージを使用するまたは`False`実際の値を使用します。  
  
 小さいスライスは、1 つ目の円グラフでまとめられたスライスから切り離し、2 つ目の円グラフにまとめることもできます。 2 つ目の円グラフは元の円グラフの右側に描画されます。  
  
 じょうごグラフまたはピラミッド グラフのスライスを 1 つのスライスに結合することはできません。  
  
 このグラフについては、サンプル レポートに例が含まれています。 このサンプル レポートおよびその他のサンプル レポートをダウンロードする方法の詳細については、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の[レポート ビルダーおよびレポート デザイナーのサンプル レポート](http://go.microsoft.com/fwlink/?LinkId=198283)に関するページを参照してください。  
  
### <a name="to-collect-small-slices-into-a-single-slice-on-a-pie-chart"></a>円グラフの小さいスライスを 1 つのスライスにまとめるには  
  
1.  プロパティ ペインを開きます。  
  
2.  デザイン画面で、円グラフの任意のスライスをクリックします。 系列のプロパティが [プロパティ] ペインに表示されます。  
  
3.  **[全般]** セクションで、 **[CustomAttributes]** ノードを展開します。  
  
4.  [CollectedStyle] プロパティを **[SingleSlice]** に設定します。  
  
5.  収集されるしきい値としきい値の種類を設定します。 次の例は、収集されるしきい値を設定する一般的な方法です。  
  
    -   **比率で設定します。** たとえば、円グラフ上の 10% 未満の小さいスライスを 1 つのスライスにまとめるには、次の手順を実行します。  
  
         CollectedThresholdUsePercent プロパティを設定`True`です。  
  
         [CollectedThreshold] プロパティを **10**に設定します。  
  
        > [!NOTE]  
        >  CollectedStyle を設定した場合**SingleSlice**より大きい値に CollectedThreshold **100**、CollectedThresholdUsePercent は`True`、グラフできないため、例外がスローされますパーセンテージを計算します。 この問題を解決するには、[CollectedThreshold] を **100** 未満の値に設定します。  
  
    -   **データ値で設定します。** たとえば、円グラフ上の 5,000 未満の小さいスライスを 1 つのスライスにまとめるには、次の手順を実行します。  
  
         CollectedThresholdUsePercent プロパティを設定`False`です。  
  
         [CollectedThreshold] プロパティを **5000**に設定します。  
  
6.  [CollectedLabel] プロパティを、収集されたスライスに表示されるテキスト ラベルを表す文字列に設定します。  
  
7.  (省略可) CollectedSliceExploded、CollectedColor、CollectedLegendText および CollectedToolTip の各プロパティを設定します。 これらのプロパティでは、1 つのスライスの外観、色、ラベルのテキスト、凡例のテキスト、およびツールヒントを変更します。  
  
### <a name="to-collect-small-slices-into-a-secondary-callout-pie-chart"></a>小さいスライスをまとめた 2 つ目の円グラフにするには  
  
1.  上記の手順 1. ～ 3. を実行します。  
  
2.  [CollectedStyle] プロパティを **[CollectedPie]** に設定します。  
  
3.  [CollectedThreshold] プロパティを、小さいスライスを 1 つのスライスにまとめる基準となるしきい値を表す値に設定します。 CollectedStyle プロパティに設定するときに**CollectedPie**、CollectedThresholdUsePercentproperty が always に設定されている`True`、され、収集されるしきい値は常に比率でします。  
  
4.  (省略可) CollectedColor、CollectedLabel、CollectedLegendText および CollectedToolTip の各プロパティを設定します。 "Collected" という名前を持つその他すべてのプロパティは、まとめられた円に適用されません。  
  
> [!NOTE]  
>  2 つ目の円グラフは、データの中の小さいスライスに基づいて計算され、プレビューのみに表示されます。 この円グラフはデザイン画面には表示されません。  
  
> [!NOTE]  
>  2 つ目の円グラフの書式は設定できません。 このため、円スライスを収集する際は最初の方法を使用することを強くお勧めします。  
  
## <a name="see-also"></a>参照  
 [円グラフ&#40;レポート ビルダーおよび SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [グラフのデータ ポイントの書式設定&#40;レポート ビルダーおよび SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)   
 [データ ポイント ラベルを表示する円グラフの外側&#40;レポート ビルダーおよび SSRS&#41;](display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md)   
 [円グラフへのパーセンテージの表示 &#40;レポート ビルダーおよび SSRS&#41;](display-percentage-values-on-a-pie-chart-report-builder-and-ssrs.md)   
 [グラフへの 3D 効果の追加 &#40;レポート ビルダーおよび SSRS&#41;](chart-effects-add-3d-effects-report-builder.md)  
  
  