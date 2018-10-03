---
title: グラフの種類 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10423"
ms.assetid: 57b00017-69ae-4e71-8d78-44744e208ac7
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 8da6fab7797154cdb59ee83993499607f515550a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48098862"
---
# <a name="chart-types-report-builder-and-ssrs"></a>グラフの種類 (レポート ビルダーおよび SSRS)
  表示するデータの種類に対して適切な種類のグラフを選択することが重要です。 これにより、データをグラフ形式にした場合にどの程度わかりやすくなるかが決まります。 たとえば、グラフのサイズに対して多数のデータ ポイントがデータセットに含まれている場合は、面グラフ、折れ線グラフ、または散布図を使用して表示するのが適しています。 選択したグラフの種類に応じてデータを準備する方法の詳細については、次を参照してください。[グラフ&#40;レポート ビルダーおよび SSRS&#41;](charts-report-builder-and-ssrs.md)します。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="choosing-a-chart-type"></a>グラフの種類の選択  
 それぞれのグラフの種類には、データセットの視覚化に役立つ固有の特性があります。 どのグラフの種類を使用してもデータを表示できますが、レポートに表示する内容に基づいて、データに適したグラフの種類を使用すると、データは読み取りやすくなります。 次の表に、特定のデータセットに対するグラフの適性に影響する、グラフの機能を示します。  
  
 グラフの種類は、作成後に変更できます。 詳細については、「[グラフの種類の変更 &#40;レポート ビルダーおよび SSRS&#41;](change-a-chart-type-report-builder-and-ssrs.md)」を参照してください。  
  
 これらの種類のグラフについては、サンプル レポートに多くの例が含まれています。 サンプル レポートをダウンロードする方法の詳細については、「 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][レポート ビルダーおよびレポート デザイナーのサンプル レポート](http://go.microsoft.com/fwlink/?LinkId=198283)」を参照してください。  
  
|グラフの種類|比率データの表示|株価データの表示|線形データの表示|複数値データの表示|  
|----------------|------------------------|------------------------|-------------------------|-------------------------------|  
|[面グラフ&#40;レポート ビルダーおよび SSRS&#41;](area-charts-report-builder-and-ssrs.md)|||![使用可能](../media/greencheck.gif "使用可能")||  
|[横棒グラフ&#40;レポート ビルダーおよび SSRS&#41;](bar-charts-report-builder-and-ssrs.md)|||![使用可能](../media/greencheck.gif "使用可能")||  
|[データ バー](sparklines-and-data-bars-report-builder-and-ssrs.md)|||![使用可能](../media/greencheck.gif "使用可能")||  
|[縦棒グラフ&#40;レポート ビルダーおよび SSRS&#41;](column-charts-report-builder-and-ssrs.md)|||![使用可能](../media/greencheck.gif "使用可能")||  
|[折れ線グラフ&#40;レポート ビルダーおよび SSRS&#41;](line-charts-report-builder-and-ssrs.md)|||![使用可能](../media/greencheck.gif "使用可能")||  
|[円グラフ&#40;レポート ビルダーおよび SSRS&#41;](pie-charts-report-builder-and-ssrs.md)|![使用可能](../media/greencheck.gif "使用可能")||||  
|[極座標グラフ&#40;レポート ビルダーおよび SSRS&#41;](polar-charts-report-builder-and-ssrs.md)|![使用可能](../media/greencheck.gif "使用可能")||||  
|[範囲グラフ&#40;レポート ビルダーおよび SSRS&#41;](range-charts-report-builder-and-ssrs.md)|||![使用可能](../media/greencheck.gif "使用可能")|![使用可能](../media/greencheck.gif "使用可能")|  
|[散布図&#40;レポート ビルダーおよび SSRS&#41;](scatter-charts-report-builder-and-ssrs.md)|![使用可能](../media/greencheck.gif "使用可能")||![使用可能](../media/greencheck.gif "使用可能")||  
|[図形グラフ&#40;レポート ビルダーおよび SSRS&#41;](shape-charts-report-builder-and-ssrs.md)|![使用可能](../media/greencheck.gif "使用可能")||||  
|[スパーク ライン](sparklines-and-data-bars-report-builder-and-ssrs.md)|![使用可能](../media/greencheck.gif "使用可能")|![使用可能](../media/greencheck.gif "使用可能")|![使用可能](../media/greencheck.gif "使用可能")|![使用可能](../media/greencheck.gif "使用可能")|  
|[株価チャート&#40;レポート ビルダーおよび SSRS&#41;](stock-charts-report-builder-and-ssrs.md)||![使用可能](../media/greencheck.gif "使用可能")||![使用可能](../media/greencheck.gif "使用可能")|  
  
## <a name="see-also"></a>参照  
 [グラフ &#40;レポート ビルダーおよび SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [グラフ内の空のデータ ポイントおよび NULL データ ポイント (レポート ビルダーおよび SSRS)](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md)   
 [レポートにグラフを追加&#40;レポート ビルダーおよび SSRS&#41;](add-a-chart-to-a-report-report-builder-and-ssrs.md)  
  
  
