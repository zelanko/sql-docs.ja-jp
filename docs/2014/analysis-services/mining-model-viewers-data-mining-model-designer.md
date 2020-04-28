---
title: マイニングモデルビューアー (データマイニングモデルデザイナー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.viewers.f1
ms.assetid: 4ba391d5-c97b-4848-ba7c-7d096fa4b7dd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9458f2c1fb3d170bf1b4a2887acae94b55ed877e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "78175807"
---
# <a name="mining-model-viewers-data-mining-model-designer"></a>マイニング モデル ビューアー (データ マイニング モデル デザイナー)
  **[マイニング モデル ビューアー]** タブでは、マイニング構造に含まれているマイニング モデルを調べることができます。

 最初にマイニング モデルを選択してから、ビューアーを選択します。 各モデルでは、常に、複数のタブを表示できるカスタム ビューアーと汎用ビューアーの 2 種類のビューアーを使用できます。

 各ビューアーの使用方法に関するチュートリアルについては、「 [データ マイニング モデル ビューアー](data-mining/data-mining-model-viewers.md)」を参照してください。

## <a name="common-options"></a>共通オプション
 **[ビューアーのコンテンツを最新状態に更新]** ビューアーにマイニング モデルを再読み込みします。

 **マイニングモデル**現在のマイニング構造に含まれている、表示するマイニングモデルを選択します。 まず、関連付けられているカスタム ビューアーが開き、マイニング モデルが表示されます。

 **[ビューアー]** 選択したマイニング モデルを調べるために使用するビューアーを選択します。 この一覧には、各[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]マイニングモデル、 [!INCLUDE[msCoName](../includes/msconame-md.md)]マイニングコンテンツビューアー、およびすべてのプラグインビューアーに用意されているビューアーが含まれています。

 次の図は、同じモデルに対するカスタム ビューアーと汎用ビューアーを示しています。

-   上の図では、Microsoft Time Series アルゴリズムに基づくマイニング モデルのビューアーを示しています。 この特定のカスタム ビューアーによってタイム シリーズのグラフが自動的に作成され、5 つの予測が提供されます。

-   下の図では、 **Microsoft 汎用コンテンツ ツリー ビューアー**を使用して表示される同じモデルを示しています。 このビューアーは、標準スキーマに従ってマイニング モデルのコンテンツを表示します。 詳細については、「[Microsoft 汎用コンテンツ ツリー ビューアー (データ マイニング)](microsoft-generic-content-tree-viewer-data-mining.md)」を参照してください。

 ![マイニング モデル デザイナーの概要](media/generic-mining-model-tab1.gif "マイニング モデル デザイナーの概要")

## <a name="viewers-and-their-components"></a>ビューアーとそのコンポーネント
 選択されたデータ マイニング モデルの作成に使用したアルゴリズムに合わせて調整されるため、選択したモデルに応じて表示されるカスタム ビューアーは異なります。 各カスタム ビューアーには、モデルの統計とパターンの調査に役立つさまざまなツールやダイアログ ボックスがあります。

 カスタム ビューアーの各部分の説明を次に示します。

### <a name="microsoft-association-rules-algorithm"></a>Microsoft アソシエーション ルール アルゴリズム

-   [Microsoft アソシエーション ルール ビューアーを使用したモデルの参照](data-mining/browse-a-model-using-the-microsoft-association-rules-viewer.md)

    -   [[アイテムセット] タブ &#40;マイニングモデルビューアー&#41;](itemsets-tab-mining-model-viewer.md)

    -   [[ルール] タブ &#40;マイニングモデルビューアー&#41;](rules-tab-mining-model-viewer.md)

    -   [[依存関係ネットワーク] タブ &#40;マイニングモデルビューアー&#41;](dependency-network-tab-mining-model-viewer.md)

### <a name="microsoft-clustering-algorithm"></a>Microsoft クラスタリング アルゴリズム

-   [「Microsoft クラスター ビューアーを使用したモデルの参照」](data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)

    -   [[クラスターダイアグラム] タブ &#40;マイニングモデルビューアー&#41;](cluster-diagram-tab-mining-model-viewer.md)

    -   [[クラスターのプロファイル] タブ &#40;マイニングモデルビューアー&#41;](cluster-profiles-tab-mining-model-viewer.md)

    -   [[クラスターの特性] タブ &#40;マイニングモデルビューアー&#41;](cluster-characteristics-tab-mining-model-viewer.md)

    -   [[クラスターの識別] タブ &#40;マイニングモデルビューアー&#41;](cluster-discrimination-tab-mining-model-viewer.md)

    -   [[マイニング凡例] ダイアログボックス &#40;マイニングモデルビューアー&#41;](mining-legend-dialog-box-mining-model-viewer.md)

### <a name="microsoft-decision-tree-algorithm"></a>Microsoft デシジョン ツリー アルゴリズム

-   [Microsoft ツリー ビューアーを使用したモデルの参照](data-mining/browse-a-model-using-the-microsoft-tree-viewer.md)

    -   [[デシジョンツリー] タブ &#40;マイニングモデルビューアー&#41;](decision-tree-tab-mining-model-viewer.md)

    -   [[依存関係ネットワーク] タブ &#40;マイニングモデルビューアー&#41;](dependency-network-tab-mining-model-viewer.md)

    -   [[マイニング凡例] ダイアログボックス &#40;マイニングモデルビューアー&#41;](mining-legend-dialog-box-mining-model-viewer.md)

### <a name="microsoft-linear-regression-algorithm"></a>Microsoft 線形回帰アルゴリズム

-   [Microsoft ニューラル ネットワーク ビューアーを使用したモデルの参照](data-mining/browse-a-model-using-the-microsoft-neural-network-viewer.md)

    -   [[デシジョンツリー] タブ &#40;マイニングモデルビューアー&#41;](decision-tree-tab-mining-model-viewer.md)

    -   [[依存関係ネットワーク] タブ &#40;マイニングモデルビューアー&#41;](dependency-network-tab-mining-model-viewer.md)

    -   [[マイニング凡例] ダイアログボックス &#40;マイニングモデルビューアー&#41;](mining-legend-dialog-box-mining-model-viewer.md)

### <a name="microsoft-logistic-regression-algorithm"></a>Microsoft ロジスティック回帰アルゴリズム

-   [Microsoft ニューラル ネットワーク ビューアーを使用したモデルの参照](data-mining/browse-a-model-using-the-microsoft-neural-network-viewer.md)

### <a name="microsoft-nave-bayes-algorithm"></a>Microsoft Na&#239;</ph>ve Bayes アルゴリズム

-   [Microsoft Naive Bayes ビューアーを使用したモデルの参照](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)

    -   [[依存関係ネットワーク] タブ &#40;マイニングモデルビューアー&#41;](dependency-network-tab-mining-model-viewer.md)

    -   [[属性のプロファイル] タブ &#40;マイニングモデルビューアー&#41;](attribute-profiles-tab-mining-model-viewer.md)

    -   [[属性の特性] タブ &#40;マイニングモデルビューアー&#41;](attribute-characteristics-tab-mining-model-viewer.md)

    -   [[属性の識別] タブ &#40;マイニングモデルビューアー&#41;](attribute-discrimination-tab-mining-model-viewer.md)

### <a name="microsoft-neural-network-algorithm"></a>Microsoft Neural Network Algorithm

-   [Microsoft ニューラル ネットワーク ビューアーを使用したモデルの参照](data-mining/browse-a-model-using-the-microsoft-neural-network-viewer.md)

    -   [[依存関係ネットワーク] タブ &#40;マイニングモデルビューアー&#41;](dependency-network-tab-mining-model-viewer.md)

    -   [ニューラルネットワーク &#40;マイニングモデルビューアー&#41;](neural-network-mining-model-viewer.md)

    -   [[ノードの検索] ダイアログボックス &#40;マイニングモデルビューアー&#41;](find-node-dialog-box-mining-model-viewer.md)

### <a name="microsoft-sequence-clustering-algorithm"></a>「Microsoft シーケンス クラスター アルゴリズム」

-   [Microsoft シーケンス クラスター ビューアーを使用したモデルの参照](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)

    -   [シーケンスクラスターの [クラスターダイアグラム] タブ &#40;マイニングモデルビューアー](sequence-clustering-cluster-diagram-tab-mining-model-viewer.md)

    -   [マイニングモデルビューアー &#40;シーケンスクラスターの [クラスターのプロファイル] タブ](sequence-clustering-cluster-profiles-tab-mining-model-viewer.md)

    -   [マイニングモデルビューアー &#40;のシーケンスクラスターの [クラスターの特性] タブ&#41;](sequence-clustering-cluster-characteristics-tab-mining-model-viewer.md)

    -   [マイニングモデルビューアー &#40;のシーケンスクラスターの [クラスターの識別] タブ&#41;](sequence-clustering-cluster-discrimination-tab-mining-model-viewer.md)

    -   [マイニングモデルビューアー &#40;のシーケンスクラスターの [遷移] タブ&#41;](sequence-clustering-cluster-transition-tab-mining-model-viewer.md)

### <a name="microsoft-time-series-algorithm"></a>Microsoft Time Series アルゴリズム

-   [Microsoft タイム シリーズ ビューアーを使用したモデルの参照](data-mining/browse-a-model-using-the-microsoft-time-series-viewer.md)

    -   [[モデル] タブ &#40;マイニングモデルビューアー&#41;](model-tab-mining-model-viewers.md)

    -   [[グラフ] タブ &#40;マイニングモデルビューアー&#41;](chart-tab-mining-model-viewers.md)

    -   [[マイニング凡例] ダイアログボックス &#40;マイニングモデルビューアー&#41;](mining-legend-dialog-box-mining-model-viewer.md)

## <a name="see-also"></a>参照
 マイニング[モデルビュー &#40;データマイニングモデルデザイナー&#41;](mining-models-view-data-mining-model-designer.md) [マイニング構造ビュー &#40;データマイニングモデルデザイナー&#41;](mining-structure-view-data-mining-model-designer.md) [マイニング精度チャートデザイナー &#40;データマイニング&#41;](mining-accuracy-chart-designer-data-mining.md) [予測クエリビルダー &#40;データマイニング](prediction-query-builder-data-mining.md)&#41;


