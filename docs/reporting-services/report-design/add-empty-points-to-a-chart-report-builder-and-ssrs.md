---
title: 空のポイントのグラフへの追加 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-design
ms.suite: pro-bi
ms.topic: conceptual
ms.assetid: 2b056119-439f-494f-83cf-ee0c05dc6487
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: eb8d9c7b946847406a7ad09aa0fd56501fec119e
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/30/2018
ms.locfileid: "43279769"
---
# <a name="add-empty-points-to-a-chart-report-builder-and-ssrs"></a>空のポイントのグラフへの追加 (レポート ビルダーおよび SSRS)
NULL 値は、系列内のデータ ポイント間の空白 (すきま) としてグラフに表示されます。 改ページ調整された [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポートの空のポイントとは、NULL 値によって作成された空白に挿入できるデータ ポイントのことです。  
  
 既定では、空のポイントは、値が含まれている前のデータ ポイントと次のデータ ポイントの平均値を求めることによって計算されます。 この既定の動作を変更して、すべての空のポイントが値ゼロのデータ ポイントとして挿入されるようにすることもできます。  
  
 詳細については、「[グラフ内の空のデータ ポイントおよび NULL データ ポイント &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/empty-and-null-data-points-in-charts-report-builder-and-ssrs.md)」を参照してください。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-specify-empty-points-on-a-chart"></a>空のポイントをグラフ上で指定するには  
  
1.  プロパティ ペインを開きます。  
  
2.  デザイン画面で、NULL 値が含まれている系列を右クリックします。 系列のプロパティが [プロパティ] ペインに表示されます。  
  
3.  **[EmptyPoint]** ノードを展開します。  
  
4.  Color プロパティの色の値を選択します。  
  
5.  **[EmptyPoint]** ノードで [Marker] ノードを展開します。  
  
6.  MarkerType プロパティのマーカーの種類を選択します。  
  
    > [!NOTE]  
    >  空のポイントを横棒グラフ、縦棒グラフ、または散布図に追加するには、マーカーの種類を選択する必要があります。 ただし、面グラフ、折れ線グラフ、およびレーダー グラフの場合は、マーカーを指定しなくても空白 (すきま) が自動的に塗りつぶされるので、マーカーの種類の選択は省略可能です。  
  
7.  空のポイントの値を設定します。  
  
    1.  プロパティ ペインで、 **[CustomAttributes]** ノードを展開します。  
  
    2.  EmptyPointValue プロパティを設定します。 前のデータ ポイントと次のデータ ポイントの平均値で空のポイントを挿入するには、 **[Average]** を選択します。 値ゼロのデータ ポイントとして空のポイントを挿入するには、 **[Zero]** を選択します。  
  
## <a name="see-also"></a>参照  
 [データセット フィルター、データ領域フィルター、およびグループ フィルターの追加 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/add-dataset-filters-data-region-filters-and-group-filters.md)   
 [グラフの種類 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/chart-types-report-builder-and-ssrs.md)   
 [グラフへのスケール区切りの追加 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/add-scale-breaks-to-a-chart-report-builder-and-ssrs.md)   
 [グラフ &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)  
  
  
