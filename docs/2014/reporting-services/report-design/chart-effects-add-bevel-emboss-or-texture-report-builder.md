---
title: グラフへの傾斜、エンボス、およびテクスチャのスタイルの追加 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 737cfc80-b39e-497c-817b-b46693deb58f
caps.latest.revision: 6
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: f9fac39f0b11bdc2bbf14b054bfe8947bf767906
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37309292"
---
# <a name="add-bevel-emboss-and-texture-styles-to-a-chart-report-builder-and-ssrs"></a>グラフへの傾斜、エンボス、およびテクスチャのスタイルの追加 (レポート ビルダーおよび SSRS)
  特定のグラフの種類を使用する場合、グラフの視覚的な効果を高めるために、描画効果を指定できます。 このような描画効果を適用できるのは、グラフの系列だけです。 その他のグラフ要素には影響しません。  
  
 円グラフまたはドーナツ グラフの一種を使用する場合、画像に適用できる傾斜やエンボスの効果と同様、ぼかしや凹状の描画スタイルを指定できます。  
  
 横棒グラフまたは縦棒グラフの一種を使用する場合、円柱、くさび形、グラデーションなどのテクスチャのスタイルを、個々の横棒および縦棒に適用できます。  
  
 多くのグラフ要素では、これらの描画スタイルに加え、罫線および影を追加することで、奥行を持たせることができます。 グラフの書式設定するには、他の方法の詳細については、次を参照してください。[グラフの書式設定&#40;レポート ビルダーおよび SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md)します。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-bevel-or-emboss-styles-to-a-pie-or-doughnut-chart"></a>円グラフまたはドーナツ グラフに傾斜またはエンボスのスタイルを追加するには  
  
1.  **[表示]** タブで、 **[プロパティ]** を選択してプロパティ ペインを開きます。  
  
2.  強調する円グラフまたはドーナツ グラフを選択します。 グラフ全体ではなく、グラフのデータ フィールドを選択します。  
  
3.  プロパティ ペインで、 **[CustomAttributes]** ノードを展開します。  
  
4.  PieDrawingStyle で、ドロップダウン リストからスタイルを選択します。  
  
> [!NOTE]  
>  3D と、傾斜またはエンボスのスタイルを同じグラフに含めることはできません。 グラフで 3D を有効にした場合は、PieDrawingStyle プロパティが表示されません。  
  
 ![凹型描画スタイルの円グラフ](../media/rs-piedrawingeffects-concave.gif "凹型描画スタイルの円グラフ")  
  
### <a name="to-add-texture-styles-to-a-bar-or-column-chart"></a>横棒グラフまたは縦棒グラフにテクスチャのスタイルを追加するには  
  
1.  強調する横棒グラフまたは縦棒グラフを選択します。 グラフ全体ではなく、グラフのデータ フィールドを選択します。  
  
2.  プロパティ ペインを開きます。  
  
3.  **[CustomAttributes]** ノードを展開します。  
  
4.  DrawingStyle で、ドロップダウン リストからスタイルを選択します。  
  
> [!NOTE]  
>  3D と、傾斜またはエンボスのスタイルを同じグラフに含めることはできません。 グラフで 3D を有効にした場合は、PieDrawingStyle プロパティが表示されません。  
  
 ![LightToDark 描画効果付きの横棒グラフ](../media/rs-bardrawingeffects-lighttodark.gif "LightToDark 描画効果付きの横棒グラフ")  
  
## <a name="see-also"></a>参照  
 [横棒グラフ&#40;レポート ビルダーおよび SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [縦棒グラフ &#40;レポート ビルダーおよび SSRS&#41;](column-charts-report-builder-and-ssrs.md)   
 [円グラフ&#40;レポート ビルダーおよび SSRS&#41;](pie-charts-report-builder-and-ssrs.md)   
 [グラフの書式設定&#40;レポート ビルダーおよび SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md)  
  
  
