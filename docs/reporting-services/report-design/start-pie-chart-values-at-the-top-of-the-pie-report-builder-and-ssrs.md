---
title: 円グラフの値の開始位置を円の最上部にする (レポート ビルダー) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: d0e6fb59-ca4e-4d70-97cb-0ad183da21d3
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3f23163da5fc4b23a364646be607167e663187fd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "77080902"
---
# <a name="start-pie-chart-values-at-the-top-of-the-pie-report-builder-and-ssrs"></a>円グラフの値の開始位置を円の最上部にする (レポート ビルダーおよび SSRS)
[!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] の改ページ調整されたレポートの円グラフでは、既定でデータセットの最初の値が円の最上部から 90 度の位置から開始されます。 

![report-builder-pie-chart-start-at-90](../../reporting-services/media/report-builder-pie-chart-start-at-90.png)

*円グラフの値は 90 度の位置から開始されます。*

開始位置を円の最上部にすることもできます。 

![report-builder-pie-chart-start-at-top](../../reporting-services/media/report-builder-pie-chart-start-at-top.png)

*円グラフの値は円の最上部から開始されます。*
  
## <a name="to-start-the-pie-chart-at-the-top-of-the-pie"></a>円グラフの開始位置を円の最上部にするには  
  
1.  円グラフをクリックします。  
  
2.  **プロパティ** ペインが開いていない場合は、 **[表示]** タブの **[プロパティ]** をクリックします。  
  
3.  **プロパティ** ペインの **[カスタム属性]** で、 **[PieStartAngle]** を **0** から **270**に変更します。  
  
4.  **[実行]** をクリックして、レポートをプレビューします。  
  
 最初の値の開始位置が円グラフの最上部になります。  
  
## <a name="see-also"></a>参照  
 [グラフの書式設定 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)   
 [円グラフ &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/pie-charts-report-builder-and-ssrs.md)  
  
  
