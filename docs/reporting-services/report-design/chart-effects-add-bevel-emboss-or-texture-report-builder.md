---
title: グラフへの傾斜、エンボス、テクスチャのスタイルの追加 (レポート ビルダー) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 737cfc80-b39e-497c-817b-b46693deb58f
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 9bbb097362d2569bcea8a16d451d33d931b82b35
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "77078750"
---
# <a name="chart-effects---add-bevel-emboss-or-texture-report-builder"></a>グラフの効果 - ベベル、エンボス、またはテクスチャの追加(レポート ビルダー)
  特定のグラフの種類を使用する場合、グラフの視覚的な効果を高めるために、描画効果を指定できます。 このような描画効果を適用できるのは、グラフの系列だけです。 その他のグラフ要素には影響しません。  
  
 円グラフまたはドーナツ グラフの一種を使用する場合、画像に適用できる傾斜やエンボスの効果と同様、ぼかしや凹状の描画スタイルを指定できます。  
  
 横棒グラフまたは縦棒グラフの一種を使用する場合、円柱、くさび形、グラデーションなどのテクスチャのスタイルを、個々の横棒および縦棒に適用できます。  
  
 多くのグラフ要素では、これらの描画スタイルに加え、罫線および影を追加することで、奥行を持たせることができます。 その他のグラフの書式設定方法の詳細については、「 [グラフの書式設定 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)」を参照してください。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-bevel-or-emboss-styles-to-a-pie-or-doughnut-chart"></a>円グラフまたはドーナツ グラフに傾斜またはエンボスのスタイルを追加するには  
  
1.  **[表示]** タブで、 **[プロパティ]** を選択してプロパティ ペインを開きます。  
  
2.  強調する円グラフまたはドーナツ グラフを選択します。 グラフ全体ではなく、グラフのデータ フィールドを選択します。  
  
3.  プロパティ ペインで、 **[CustomAttributes]** ノードを展開します。  
  
4.  PieDrawingStyle で、ドロップダウン リストからスタイルを選択します。  
  
> [!NOTE]  
>  3D と、傾斜またはエンボスのスタイルを同じグラフに含めることはできません。 グラフで 3D を有効にした場合は、PieDrawingStyle プロパティが表示されません。  
  
 ![凹型描画スタイルの円グラフ](../../reporting-services/report-design/media/rs-piedrawingeffects-concave.gif "凹型描画スタイルの円グラフ")  
  
### <a name="to-add-texture-styles-to-a-bar-or-column-chart"></a>横棒グラフまたは縦棒グラフにテクスチャのスタイルを追加するには  
  
1.  強調する横棒グラフまたは縦棒グラフを選択します。 グラフ全体ではなく、グラフのデータ フィールドを選択します。  
  
2.  プロパティ ペインを開きます。  
  
3.  **[CustomAttributes]** ノードを展開します。  
  
4.  DrawingStyle で、ドロップダウン リストからスタイルを選択します。  
  
> [!NOTE]  
>  3D と、傾斜またはエンボスのスタイルを同じグラフに含めることはできません。 グラフで 3D を有効にした場合は、PieDrawingStyle プロパティが表示されません。  
  
 ![LightToDark 描画効果付きの横棒グラフ](../../reporting-services/report-design/media/rs-bardrawingeffects-lighttodark.gif "LightToDark 描画効果付きの横棒グラフ")  
  
## <a name="see-also"></a>参照  
 [横棒グラフ (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/bar-charts-report-builder-and-ssrs.md)   
 [縦棒グラフ &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/column-charts-report-builder-and-ssrs.md)   
 [円グラフ &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/pie-charts-report-builder-and-ssrs.md)   
 [グラフの書式設定 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)  
  
  
