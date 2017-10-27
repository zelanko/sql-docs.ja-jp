---
title: "グラフ (レポート ビルダーおよび SSRS) にラベルを配置 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5db74e0b-8be8-4b47-b386-faab56dffa9b
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 53f0d4b0c6aed30746af82de7d5f1caf5e42721c
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="position-labels-in-a-chart-report-builder-and-ssrs"></a>グラフへのラベルの配置 (レポート ビルダーおよび SSRS)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の改ページ調整されたレポートのグラフはその種類によって形状が異なるので、グラフが見やすい位置にデータ ポイント ラベルを配置する必要があります。 ラベルの既定の位置は、グラフの種類によって異なります。  
  
-   積み上げグラフでは、ラベルは系列内にのみ配置できます。  
  
-   じょうごグラフまたはピラミッド グラフでは、ラベルがグラフの外側に縦一列に配置されます。  
  
-   円グラフでは、ラベルはグラフ上の個々のスライスの内側に配置されます。  
  
-   横棒グラフでは、ラベルは、データ ポイントを表すバーの外側に配置されます。  
  
-   極座標グラフでは、データ ポイントを表す円形領域の外側にラベルが配置されます。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-change-the-position-of-point-labels-in-a-pie-chart"></a>円グラフ内のポイント ラベルの場所を変更するには  
  
1.  円グラフを作成します。  
  
2.  デザイン画面で、グラフを右クリックし、 **[データ ラベルの表示]**をクリックします。  
  
3.  プロパティ ペインを開きます。 **[表示]** タブの **[プロパティ]**をクリックします。  
  
4.  デザイン画面で、グラフをクリックします。 グラフのプロパティが [プロパティ] ペインに表示されます。  
  
5.  **[全般]** セクションで、 **[CustomAttributes]** ノードを展開します。 円グラフの属性の一覧が表示されます。  
  
6.  PieLabelStyle プロパティの値を選択します。  
  
## <a name="to-change-the-position-of-point-labels-in-a-funnel-or-pyramid-chart"></a>じょうごグラフまたはピラミッド グラフ内のポイント ラベルの場所を変更するには  
  
1.  じょうごグラフまたはピラミッド グラフを作成します。  
  
2.  デザイン画面で、グラフを右クリックし、 **[データ ラベルの表示]**をクリックします。  
  
3.  プロパティ ペインを開きます。 **[表示]** タブの **[プロパティ]**をクリックします。  
  
4.  デザイン画面で、グラフをクリックします。 グラフのプロパティが [プロパティ] ペインに表示されます。  
  
5.  **[全般]** セクションで、 **[CustomAttributes]** ノードを展開します。 じょうごグラフの属性の一覧が表示されます。  
  
6.  じょうごグラフの場合は、FunnelLabelStyle プロパティの値を選択します。 ピラミッド グラフの場合は、PyramidLabelStyle プロパティの値を選択します。  
  
    > [!NOTE]  
    >  このプロパティを **OutsideInColumn**に設定した場合、ラベルは縦一列に描画されます。 列の位置を変更することはできません。  
  
## <a name="to-change-the-position-of-point-labels-in-a-bar-chart"></a>横棒グラフ内のポイント ラベルの場所を変更するには  
  
1.  横棒グラフを作成します。  
  
2.  デザイン画面で、グラフを右クリックし、 **[データ ラベルの表示]**をクリックします。  
  
3.  プロパティ ペインを開きます。 **[表示]** タブの **[プロパティ]**をクリックします。  
  
4.  デザイン画面で、グラフをクリックします。 グラフのプロパティが [プロパティ] ペインに表示されます。  
  
5.  **[全般]** セクションで、 **[CustomAttributes]** ノードを展開します。 横棒グラフの属性の一覧が表示されます。  
  
6.  BarLabelStyle プロパティの値を選択します。  
  
 バーのラベル スタイルが **Outside**に設定されている場合、ラベルがグラフ領域内に収まる範囲内でバーの外側に配置されます。 ラベルをバーの外側に置くことで、グラフ領域からはみ出る場合は、ラベルがバーの内側の終端部分に近接する位置に配置されます。  
  
## <a name="to-change-the-position-of-point-labels-in-an-area-column-line-or-scatter-chart"></a>面グラフ、縦棒グラフ、折れ線グラフ、または散布図内のポイント ラベルの場所を変更するには  
  
1.  面グラフ、縦棒グラフ、折れ線グラフ、または散布図を作成します。  
  
2.  デザイン画面で、グラフを右クリックし、 **[データ ラベルの表示]**をクリックします。  
  
3.  プロパティ ペインを開きます。 **[表示]** タブの **[プロパティ]**をクリックします。  
  
4.  デザイン画面で、系列をクリックします。 系列のプロパティが [プロパティ] ペインに表示されます。  
  
5.  **[データ]** セクションで、 **[DataPoint]** ノードを展開し、 **[Label]**ノードを展開します。  
  
6.  Position プロパティの値を選択します。  
  
## <a name="see-also"></a>参照  
 [円グラフと #40 です。レポート ビルダーおよび SSRS &#41;](../../reporting-services/report-design/pie-charts-report-builder-and-ssrs.md)   
 [横棒グラフと #40 です。レポート ビルダーおよび SSRS &#41;](../../reporting-services/report-design/bar-charts-report-builder-and-ssrs.md)   
 [グラフの軸ラベルの書式設定 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)   
 [日付または通貨として軸ラベルを書式設定する &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md)   
 [円グラフ &#40; 外部のデータ ポイント ラベルの表示します。レポート ビルダーおよび SSRS &#41;](../../reporting-services/report-design/display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md)   
 [グラフ &#40; 上のデータ ポイントの書式設定レポート ビルダーおよび SSRS &#41;](../../reporting-services/report-design/formatting-data-points-on-a-chart-report-builder-and-ssrs.md)  
  
  

