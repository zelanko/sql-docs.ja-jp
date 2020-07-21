---
title: クラスターモデルの調査 (基本的なデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ce8aa034-161b-473f-baec-9c29e0a8e5f5
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 9bb2c6457122a5ea49824ca178b6950d88f75563
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63280432"
---
# <a name="exploring-the-clustering-model-basic-data-mining-tutorial"></a>クラスター モデルの検証 (基本的なデータ マイニング チュートリアル)
  クラスタリング[!INCLUDE[msCoName](../includes/msconame-md.md)]アルゴリズムでは、類似した特性を含むクラスターにケースがグループ化されます。 このグループ化は、データの探索、データの異常の特定、および予測の作成に役立ちます。  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] クラスター ビューアーには、クラスタリング マイニング モデルを調べるための次のタブがあります。  
  

  
##  <a name="cluster-diagram-tab"></a><a name="ClusterDiagramTab"></a>[クラスターダイアグラム] タブ  
 [クラスター ダイアグラム] タブには、マイニング モデル内のすべてのクラスターが表示されます。 クラスター間を結ぶ線は "緊密度" を表しており、緊密度が高いほど濃い線で表示されます。 各クラスター本体の色は、クラスター内の変数の頻度と状態を表します。  
  
#### <a name="to-explore-the-model-in-the-cluster-diagram-tab"></a>[クラスター ダイアグラム] タブでモデルを調査するには  
  
1.  [**マイニングモデルビューアー** ] タブの上部にある [**マイニングモデル**] ボックスの一覧を`TM_Clustering`使用すると、モデルに切り替えることができます。  
  
2.  [**ビューアー** ] ボックスの一覧で、[ **Microsoft クラスタービューアー**] を選択します。  
  
3.  [**シェーディング変数**] ボックスで、[**自転車購入**者] を選択します。  
  
     既定の変数は**母集団**ですが、モデル内の任意の属性に変更して、必要な属性を持つメンバーを含むクラスターを検出することができます。  
  
4.  [**状態**] ボックスで [ **1** ] を選択すると、自転車が購入されたケースを調べることができます。  
  
     [**密度**] 凡例には、[シェーディング変数] と [状態] で選択した属性の状態の組み合わせの密度が示されます。 この例では、最も暗い網掛けのある clusterwith 自転車購入者の割合の最高値を示しています。  
  
5.  最も色の濃いクラスター上にマウス ポインターを置きます。  
  
     ツールヒントに、属性が `Bike Buyer = 1` であるケースの割合が表示されます。  
  
6.  密度が最も高いクラスターを選択し、クラスターを右クリックして、[**クラスター名の変更**] を選択し、後で識別できるように「**自転車購入者高**」と入力します。 [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  最も色の薄い (最も密度の低い) クラスターを見つけます。 クラスターを右クリックし、[**クラスター名の変更**] を選択して、「**自転車購入者低**」と入力します。 [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  [**自転車購入**者率高] クラスターをクリックして、他のクラスターへの接続を明確に表示するペインの領域にドラッグします。  
  
     クラスターを選択すると、そのクラスターと別のクラスターをつなぐ線が強調表示され、このクラスターに対するすべての関係を簡単に確認できます。 クラスターが選択されていないときは、ダイアグラム内にあるすべてのクラスター間の相互関係の度合いを、線の濃さによって確認できます。 網掛けが薄いか存在しない場合は、クラスターがあまり似ていません。  
  
9. ネットワークの左側にあるスライダーを使用して、緊密度の低いリンクを非表示にし、緊密な関係にあるクラスターだけを表示します。 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] のマーケティング部門は、絞り込みメール配信に最適な方法を決定する際に、類似するクラスターをまとめることができます。  
  

  
##  <a name="cluster-profiles-tab"></a><a name="ClusterProfilesTab"></a>[クラスターのプロファイル] タブ  
 [**クラスターのプロファイル**] タブには、 `TM_Clustering`モデルの全体的なビューが表示されます。 [**クラスターのプロファイル**] タブには、モデル内の各クラスターの列が表示されます。 一番左側の列には、少なくとも 1 つのクラスターに関連付けられているすべての属性が表示されます。 その他の部分には、それぞれのクラスターについて、各属性の状態の分布状況が表示されます。 離散変数の分布は色分けされたバーとして表示され、最大数のバーが [**ヒストグラム] バー**の一覧に表示されます。 連続属性はダイヤモンド グラフで示されます。このグラフでは、各クラスターの平均と標準偏差を確認できます。  
  
#### <a name="to-explore-the-model-in-the-cluster-profiles-tab"></a>[クラスターのプロファイル] タブでモデルを調査するには  
  
1.  **ヒストグラム**バーを**5**に設定します。  
  
     このモデルでは、1 つの変数に対する状態の最大数が 5 になります。  
  
2.  [**マイニング凡例**] で**属性プロファイル**の表示がブロックされている場合は、そのまま移動します。  
  
3.  [**自転車購入**者率高] 列を選択し、[**母集団**] 列の右側にドラッグします。  
  
4.  [**自転車購入**者率低] 列を選択し、[**自転車購入**者率高] 列の右側にドラッグします。  
  
5.  [**自転車購入**者率高] 列をクリックします。  
  
     [**変数**列は、そのクラスターの重要度順に並べ替えられます。 列をスクロールし、[自転車購入者率高] クラスターの特性を確認します。 たとえば、多くの場合、このクラスターに属する人は通勤距離が短い傾向にあります。  
  
6.  [**自転車購入**者率高] 列の [ **Age** ] セルをダブルクリックします。  
  
     [**マイニング凡例**] には、より詳細なビューが表示されます。また、これらの顧客の年齢範囲と平均年齢も表示できます。  
  
7.  [**自転車購入**者率低] 列を右クリックし、[**列の非表示**] を選択します。  
  

  
##  <a name="cluster-characteristics-tab"></a><a name="ClusterCharacteristicsTab"></a>[クラスターの特性] タブ  
 [**クラスターの特性**] タブでは、クラスターを構成する特性の詳細を確認できます。 ([クラスターのプロファイル] タブのように) すべてのクラスターの特性を比較するのではなく、一度に 1 つのクラスターを検証することができます。 たとえば、[**クラスター** ] ボックスの一覧から [**自転車購入**者率高] を選択した場合、このクラスターの顧客の特性を確認できます。 [クラスターのプロファイル] ビューアーとは表示が異なりますが、結果は同じです。  
  
> [!NOTE]  
>  **Holdoutseed**の初期値を設定しない限り、結果はモデルを処理するたびに変わります。 詳細については、「 [HoldoutSeed 要素](https://docs.microsoft.com/bi-reference/assl/properties/holdoutseed-element)」を参照してください。  
  

  
##  <a name="cluster-discrimination-tab"></a><a name="ClusterDiscriminationTab"></a>[クラスターの識別] タブ  
 [**クラスターの識別**] タブでは、あるクラスターと別のクラスターを区別する特性を調べることができます。 **クラスター 1**の一覧から2つのクラスターを選択し、クラスター **2**の一覧からクラスターを選択すると、ビューアーによってクラスター間の相違が計算され、クラスターを最もよく区別する属性の一覧が表示されます。  
  
#### <a name="to-explore-the-model-in-the-cluster-discrimination-tab"></a>[クラスターの識別] タブでモデルを調査するには  
  
1.  [**クラスター 1** ] ボックスで、[**自転車購入**者率高] を選択します。  
  
2.  [**クラスター 2** ] ボックスで、[**自転車購入者低**] を選択します。  
  
3.  [**変数**] をクリックしてアルファベット順に並べ替えます。  
  
     **自転車購入者低**および**自転車購入**者の高いクラスターでは、年齢、車の所有権、子供の数、地域など、より大きな違いがあります。  
  
## <a name="related-tasks"></a>Related Tasks  
 他のマイニング モデルを探索するには、次のトピックを参照してください。  
  
-   [デシジョンツリーモデルの調査 &#40;基本的なデータマイニングチュートリアル&#41;](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
-   [Naive Bayes Model &#40;基本的なデータマイニングチュートリアル&#41;](../../2014/tutorials/exploring-the-naive-bayes-model-basic-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [Naive Bayes Model &#40;基本的なデータマイニングチュートリアル&#41;](../../2014/tutorials/exploring-the-naive-bayes-model-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a>このレッスンの前の作業  
 [デシジョンツリーモデルの調査 &#40;基本的なデータマイニングチュートリアル&#41;](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [Microsoft クラスタービューアーを使用したモデルの参照](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)   
 [[クラスターの識別] タブ &#40;マイニングモデルビューアー&#41;](../../2014/analysis-services/cluster-discrimination-tab-mining-model-viewer.md)   
 [[クラスターのプロファイル] タブ &#40;マイニングモデルビューアー&#41;](../../2014/analysis-services/cluster-profiles-tab-mining-model-viewer.md)   
 [[クラスターの特性] タブ &#40;マイニングモデルビューアー&#41;](../../2014/analysis-services/cluster-characteristics-tab-mining-model-viewer.md)   
 [[クラスターダイアグラム] タブ &#40;マイニングモデルビューアー&#41;](../../2014/analysis-services/cluster-diagram-tab-mining-model-viewer.md)  
  
  
