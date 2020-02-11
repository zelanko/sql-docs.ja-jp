---
title: Naive Bayes モデルの調査 (基本的なデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b06708d5-4477-4a51-bf8d-0b1e3c1f9ebb
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: eb35c829b798335a27a37629711acf299ac2c7c9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62472886"
---
# <a name="exploring-the-naive-bayes-model-basic-data-mining-tutorial"></a>Naive Bayes モデルの検証 (基本的なデータ マイニング チュートリアル)
  Naive [!INCLUDE[msCoName](../includes/msconame-md.md)] Bayes アルゴリズムには、自転車の購入と入力属性の間の相互作用を表示するためのいくつかの方法が用意されています。  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes ビューアーには、Naive Bayes マイニングモデルの調査に使用できる次のタブが用意されています。  
  
 
  
##  <a name="DependencyNetwork"></a>依存関係ネットワーク  
 [**依存関係ネットワーク**] タブは、 [!INCLUDE[msCoName](../includes/msconame-md.md)]ツリービューアーの [**依存関係ネットワーク**] タブと同じように動作します。 ビューアーの各ノードは属性を表し、ノード間を結ぶ線は関係を表します。 このビューアーでは、予測可能属性 Bike Buyer の状態に影響を与えるすべての属性を確認できます。  
  
#### <a name="to-explore-the-model-in-the-dependency-network-tab"></a>[依存関係ネットワーク] タブでモデルを調査するには  
  
1.  [**マイニングモデルビューアー** ] タブの上部にある [**マイニングモデル**] ボックスの一覧を`TM_NaiveBayes`使用すると、モデルに切り替えることができます。  
  
2.  [**ビューアー** ] ボックスの一覧を使用して、 **Microsoft Naive Bayes Viewer**に切り替えます。  
  
3.  `Bike Buyer`ノードをクリックすると、その依存関係が識別されます。  
  
     ピンクの網掛けは、すべての属性が自転車の購入に影響を与えることを表します。  
  
4.  スライダーを調整して、最も影響の大きい属性を特定します。  
  
     スライダーを下方向に動かすと、[Bike Buyer] 列に最も大きな影響を与える属性のみが表示されます。 スライダーを調整することにより、所有する車の台数、通勤距離、子供の数などが影響の大きい属性であることがわかります。  
 
  
##  <a name="AttributeProfiles"></a>属性のプロファイル  
 [**属性のプロファイル**] タブでは、入力属性のさまざまな状態が予測可能な属性の結果にどのように影響するかを説明します。  
  
#### <a name="to-explore-the-model-in-the-attribute-profiles-tab"></a>[属性のプロファイル] タブでモデルを調査するには  
  
1.  [**予測可能**] ボックスで、 `Bike Buyer`が選択されていることを確認します。  
  
2.  [**マイニング凡例**] が**属性プロファイル**の表示をブロックしている場合は、そのまま移動します。  
  
3.  [**ヒストグラム**バー] ボックスで、[ **5**] を選択します。  
  
     このモデルでは、1 つの変数に対する状態の最大数が 5 になります。  
  
     この予測可能属性の状態に影響を与える属性の一覧が表示されます。さらに、それぞれの入力属性について、各状態の値、および予測可能属性の各状態に対する影響分布も表示されます。  
  
4.  [**属性**] 列で、**車が所有**している数値を検索します。  自転車の購入者 (1 のラベルが付けられた列) と非購入者 (0 のラベルが付けられた列) について、ヒストグラムで違いを確認できます。 車の台数が 0 または 1 の人は、自転車を購入する可能性が高くなります。  
  
5.  自転車の購入者 (列ラベルが 1) のセル**番号**をダブルクリックします。  
  
     [**マイニング凡例**] には、より詳細なビューが表示されます。  
  
  
##  <a name="AttributeCharacteristics"></a>属性の特性  
 [**属性の特性**] タブでは、属性と値を選択して、選択した値のケースで他の属性の値がどの程度の頻度で表示されるかを確認できます。  
  
#### <a name="to-explore-the-model-in-the-attribute-characteristics-tab"></a>[属性の特性] タブでモデルを調査するには  
  
1.  [**属性**] ボックスの一覧で`Bike Buyer` 、が選択されていることを確認します。  
  
2.  **値**を**1**に設定します。  
  
     このビューアーで見ると、自転車を購入する可能性が高いのは、北米地域に在住し、子供と同居しておらず、通勤距離が短い顧客であることがわかります。  
  
  
##  <a name="AttributeDiscrimination"></a>属性の識別  
 [**属性の識別**] タブでは、自転車の購入とその他の属性値の2つの不連続値の関係を調べることができます。 `TM_NaiveBayes`モデルには1と0の2つの状態しかないため、ビューアーを変更する必要はありません。  
  
 このビューアーでは、車を所有していない人が自転車を購入する傾向にあり、車を 2 台所有している人は自転車を購入しない傾向にあることがわかります。  
  
## <a name="related-tasks"></a>Related Tasks  
 他のマイニング モデルを探索するには、次のトピックを参照してください。  
  
-   [デシジョンツリーモデルの調査 &#40;基本的なデータマイニングチュートリアル&#41;](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
-   [「基本的なデータマイニングチュートリアル」 &#40;クラスターモデルの調査&#41;](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a>次のレッスン  
 [レッスン 5: モデルのテスト &#40;基本的なデータマイニングチュートリアル&#41;](../../2014/tutorials/lesson-5-testing-models-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a>このレッスンの前の作業  
 [「基本的なデータマイニングチュートリアル」 &#40;クラスターモデルの調査&#41;](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [Microsoft Naive Bayes ビューアーを使用したモデルの参照](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)   
 [[属性の識別] タブ &#40;マイニングモデルビューアー&#41;](../../2014/analysis-services/attribute-discrimination-tab-mining-model-viewer.md)   
 [[属性のプロファイル] タブ &#40;マイニングモデルビューアー&#41;](../../2014/analysis-services/attribute-profiles-tab-mining-model-viewer.md)   
 [[属性の特性] タブ &#40;マイニングモデルビューアー&#41;](../../2014/analysis-services/attribute-characteristics-tab-mining-model-viewer.md)   
 [[依存関係ネットワーク] タブ &#40;マイニングモデルビューアー&#41;](../../2014/analysis-services/dependency-network-tab-mining-model-viewer.md)  
  
  
