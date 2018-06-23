---
title: Naive Bayes モデル (基本的なデータ マイニング チュートリアル) の検証 |Microsoft ドキュメント
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b06708d5-4477-4a51-bf8d-0b1e3c1f9ebb
caps.latest.revision: 25
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ce01a9d352513e4b69bb4a9e735f30cc657a9c97
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/21/2018
ms.locfileid: "36311860"
---
# <a name="exploring-the-naive-bayes-model-basic-data-mining-tutorial"></a>Naive Bayes モデルの検証 (基本的なデータ マイニング チュートリアル)
  [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes アルゴリズムは、自転車の購入と入力属性の間の相互作用を表示するためのいくつかのメソッドを提供します。  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes ビューアーは、Naive Bayes マイニング モデルの検証で使用するため、次のタブを提供します。  
  
 
  
##  <a name="DependencyNetwork"></a> 依存関係ネットワーク  
 **依存関係ネットワーク** タブの動作と同じ方法で、**依存関係ネットワーク**タブに移動して、[!INCLUDE[msCoName](../includes/msconame-md.md)]ツリー ビューアー。 ビューアーの各ノードは属性を表し、ノード間を結ぶ線は関係を表します。 このビューアーでは、予測可能属性 Bike Buyer の状態に影響を与えるすべての属性を確認できます。  
  
#### <a name="to-explore-the-model-in-the-dependency-network-tab"></a>[依存関係ネットワーク] タブでモデルを調査するには  
  
1.  使用して、**マイニング モデルの**一覧の上部にある、**マイニング モデル ビューアー**  タブに切り替えるには、`TM_NaiveBayes`モデル。  
  
2.  使用して、**ビューアー**に切り替えるにはリスト**Microsoft Naive Bayes ビューアー**です。  
  
3.  クリックして、`Bike Buyer`ノードをその依存関係を識別します。  
  
     ピンクの網掛けは、すべての属性が自転車の購入に影響を与えることを表します。  
  
4.  スライダーを調整して、最も影響の大きい属性を特定します。  
  
     スライダーを下方向に動かすと、[Bike Buyer] 列に最も大きな影響を与える属性のみが表示されます。 スライダーを調整することにより、所有する車の台数、通勤距離、子供の数などが影響の大きい属性であることがわかります。  
 
  
##  <a name="AttributeProfiles"></a> 属性のプロファイル  
 **属性のプロファイル** タブには、入力属性は、予測可能な属性の結果に与える影響の別の方法の状態がについて説明します。  
  
#### <a name="to-explore-the-model-in-the-attribute-profiles-tab"></a>[属性のプロファイル] タブでモデルを調査するには  
  
1.  **Predictable**ボックスであることを確認`Bike Buyer`が選択されています。  
  
2.  場合、**マイニング凡例**の表示がブロックされて、**属性のプロファイル**の場所に移動します。  
  
3.  **ヒストグラム**バー ボックスで、 **5**です。  
  
     このモデルでは、1 つの変数に対する状態の最大数が 5 になります。  
  
     この予測可能属性の状態に影響を与える属性の一覧が表示されます。さらに、それぞれの入力属性について、各状態の値、および予測可能属性の各状態に対する影響分布も表示されます。  
  
4.  **属性**列で、検索**Number Cars Owned**です。  自転車の購入者 (1 のラベルが付けられた列) と非購入者 (0 のラベルが付けられた列) について、ヒストグラムで違いを確認できます。 車の台数が 0 または 1 の人は、自転車を購入する可能性が高くなります。  
  
5.  ダブルクリックして、 **Number Cars Owned**自転車購入者のセル (列 1 のラベル) 列。  
  
     **マイニング凡例**より詳細なビューが表示されます。  
  
  
##  <a name="AttributeCharacteristics"></a> 属性の特性  
 **属性の特性** タブで、属性と値を参照し、選択した値の場合に他の属性の値を表示するどのくらいの頻度を選択できます。  
  
#### <a name="to-explore-the-model-in-the-attribute-characteristics-tab"></a>[属性の特性] タブでモデルを調査するには  
  
1.  **属性**ボックスの一覧であることを確認`Bike Buyer`が選択されています。  
  
2.  設定、**値**に**1**です。  
  
     このビューアーで見ると、自転車を購入する可能性が高いのは、北米地域に在住し、子供と同居しておらず、通勤距離が短い顧客であることがわかります。  
  
  
##  <a name="AttributeDiscrimination"></a> 属性の識別  
 **属性の識別** タブで、自転車の購入の 2 つの不連続値とその他の属性値間のリレーションシップを調査することができます。 `TM_NaiveBayes`モデルには、2 つの状態では、1 と 0 の場合は、ビューアーを変更する必要はありません。  
  
 このビューアーでは、車を所有していない人が自転車を購入する傾向にあり、車を 2 台所有している人は自転車を購入しない傾向にあることがわかります。  
  
## <a name="related-tasks"></a>Related Tasks  
 他のマイニング モデルを探索するには、次のトピックを参照してください。  
  
-   [デシジョン ツリー モデルの検証&#40;基本的なデータ マイニングのチュートリアル&#41;](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
-   [クラスター モデルの検証&#40;基本的なデータ マイニングのチュートリアル&#41;](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a>次のレッスン  
 [レッスン 5: モデルのテスト&#40;基本的なデータ マイニングのチュートリアル&#41;](../../2014/tutorials/lesson-5-testing-models-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a>このレッスンの前の作業  
 [クラスター モデルの検証&#40;基本的なデータ マイニングのチュートリアル&#41;](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [Microsoft Naive Bayes ビューアーを使用してモデルを参照します。](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)   
 [属性の識別 タブ&#40;マイニング モデル ビューアー&#41;](../../2014/analysis-services/attribute-discrimination-tab-mining-model-viewer.md)   
 [属性のプロファイル タブ&#40;マイニング モデル ビューアー&#41;](../../2014/analysis-services/attribute-profiles-tab-mining-model-viewer.md)   
 [属性の特性 タブ&#40;マイニング モデル ビューアー&#41;](../../2014/analysis-services/attribute-characteristics-tab-mining-model-viewer.md)   
 [依存関係ネットワーク タブ&#40;マイニング モデル ビューアー&#41;](../../2014/analysis-services/dependency-network-tab-mining-model-viewer.md)  
  
  