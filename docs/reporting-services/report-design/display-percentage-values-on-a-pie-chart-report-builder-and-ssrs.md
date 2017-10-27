---
title: "円グラフ (レポート ビルダーおよび SSRS) にパーセンテージの表示 |Microsoft ドキュメント"
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
ms.assetid: eb905fc1-5235-4773-a27e-b07be9318be5
caps.latest.revision: 9
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: Active
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 6c0fdf9d1b694f2f6d49389e913d1c156ba77838
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="display-percentage-values-on-a-pie-chart-report-builder-and-ssrs"></a>円グラフへのパーセンテージの表示 (レポート ビルダーおよび SSRS)
[!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)]改ページ調整されたレポートは、既定の凡例でカテゴリが表示されます。 凡例または自体円グラフのスライスにパーセンテージをすることもできます。   

![report-builder-pie-chart-preview-percents](../../reporting-services/media/report-builder-pie-chart-preview-percents.png)

 [チュートリアル: レポート (レポート ビルダー) に円グラフを追加](Tutorial:%20Add%20a%20Pie%20Chart%20to%20Your%20Report%20\(Report%20Builder\).md)最初にこのサンプル データを使用したい場合、円グラフのスライスにパーセンテージを追加する手順について説明します。
 
  
## <a name="to-display-percentage-values-as-labels-on-a-pie-chart"></a>円グラフにパーセンテージをラベルとして表示するには  
  
1.  レポートに円グラフを追加します。 詳細については、「[レポートへのグラフの追加 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/add-a-chart-to-a-report-report-builder-and-ssrs.md)」を参照してください。  
  
2.  デザイン画面で、円グラフを右クリックし、**[データ ラベルの表示]** をクリックします。 円グラフの各スライス内にデータ ラベルが表示されます。  
  
3.  デザイン画面で、ラベルを右クリックし、 **[系列ラベルのプロパティ]**をクリックします。 **[系列ラベルのプロパティ]** ダイアログ ボックスが表示されます。  
  
4.  **[ラベル データ]** オプションに **#PERCENT** と入力します。  
  
5.  (省略可能)ラベルに表示する数の小数点以下桁数を指定する入力"#PERCENT {P*n*}"、  *n* を表示する小数点以下桁数の数です。 たとえば、小数点以下を表示しない場合は「#PERCENT{P0}」と入力します。  
  
## <a name="to-display-percentage-values-in-the-legend-of-a-pie-chart"></a>円グラフの凡例にパーセンテージを表示するには  
  
1.  デザイン画面で、円グラフを右クリックし、 **[系列のプロパティ]**をクリックします。 **[系列のプロパティ]** ダイアログ ボックスが表示されます。  
  
2.  **[凡例]**の **[凡例のユーザー定義テキスト]** プロパティに **#PERCENT** と入力します。  
  
## <a name="see-also"></a>参照  
* [チュートリアル: レポート (レポート ビルダー) への円グラフの追加します。](Tutorial:%20Add%20a%20Pie%20Chart%20to%20Your%20Report%20\(Report%20Builder\).md)
*  [円グラフ &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/pie-charts-report-builder-and-ssrs.md)   
*  [グラフの凡例の書式設定 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/chart-legend-formatting-report-builder.md)   
*  [円グラフの外側へのデータ ポイント ラベルの表示 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md)   
 
  

