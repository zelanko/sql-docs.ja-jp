---
title: "(レポート ビルダーおよび SSRS) のグラフの凡例項目を非表示に |Microsoft ドキュメント"
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
ms.assetid: 92256240-0cd5-4be4-8904-d1e3b93cb6b3
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 06f1cf8cde2eb9a9c9aa261188e64aa2fc7afe4b
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="chart-legend---hide-items-report-builder"></a>グラフの凡例の非表示アイテム (レポート ビルダー)
既定では、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のページ分割されたレポートで図形グラフ以外のグラフに追加した系列は、凡例の項目として使用されます。 円グラフ、ドーナツ グラフ、じょうごグラフ、およびピラミッド グラフでは、グラフに系列を追加すると、凡例に個々のデータ ポイントが追加されます。  
  
 凡例の任意の項目を非表示にすることができます。 凡例の項目を非表示にした場合も、グラフには表示されます。 これは、グラフに追加した系列の詳細な情報を表示したくないときに便利です。 たとえば、移動平均のような計算系列をグラフに追加した場合、凡例のこのエントリを非表示にし、元の系列の詳細な情報のみを表示できます。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-hide-an-item-from-display-in-the-legend"></a>凡例の項目を非表示にするには  
  
1.  非表示にする系列を右クリックし、 **[系列のプロパティ]**をクリックします。  
  
2.  **[凡例]**をクリックします。 **[凡例内の次の系列を非表示にする]** オプションを選択します。  
  
    > [!NOTE]  
    >  あるグループの系列を非表示にし、他のグループの系列を表示することはできません。 **[系列グループ]** 領域にフィールドを追加している場合、このグループに属するすべての系列は非表示になります。  
  
## <a name="see-also"></a>参照  
 [グラフの凡例の書式設定 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/chart-legend-formatting-report-builder.md)   
 [グラフでのデータ ポイントの書式設定 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/formatting-data-points-on-a-chart-report-builder-and-ssrs.md)   
 [凡例アイテムのテキストの変更 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/chart-legend-change-item-text-report-builder.md)   
 [グラフへの移動平均の追加 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/add-a-moving-average-to-a-chart-report-builder-and-ssrs.md)   
 [[全般] ([凡例のプロパティ] ダイアログ ボックス) &#40;レポート ビルダーおよび SSRS&#41;](http://msdn.microsoft.com/library/db718f8f-f185-422f-871c-96f0749e5893)  
  
  
