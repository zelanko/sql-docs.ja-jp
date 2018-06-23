---
title: クラスタ リング モデル (基本的なデータ マイニング チュートリアル) の検証 |Microsoft ドキュメント
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ce8aa034-161b-473f-baec-9c29e0a8e5f5
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 0d731d16bdb19fdf600f050d580a8b018515fe8d
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/21/2018
ms.locfileid: "36313190"
---
# <a name="exploring-the-clustering-model-basic-data-mining-tutorial"></a>クラスター モデルの検証 (基本的なデータ マイニング チュートリアル)
  [!INCLUDE[msCoName](../includes/msconame-md.md)]クラスタ リング アルゴリズムは、類似した特性を持つクラスターにケースをグループ化します。 このグループ化は、データの探索、データの異常の特定、および予測の作成に役立ちます。  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] クラスター ビューアーには、クラスタリング マイニング モデルを調べるための次のタブがあります。  
  

  
##  <a name="ClusterDiagramTab"></a> クラスター ダイアグラム タブ  
 [クラスター ダイアグラム] タブには、マイニング モデル内のすべてのクラスターが表示されます。 クラスター間を結ぶ線は "緊密度" を表しており、緊密度が高いほど濃い線で表示されます。 各クラスター本体の色は、クラスター内の変数の頻度と状態を表します。  
  
#### <a name="to-explore-the-model-in-the-cluster-diagram-tab"></a>[クラスター ダイアグラム] タブでモデルを調査するには  
  
1.  使用して、**マイニング モデルの**一覧の上部にある、**マイニング モデル ビューアー**  タブに切り替えるには、`TM_Clustering`モデル。  
  
2.  **ビューアー**一覧で、 **Microsoft クラスター ビューアー**です。  
  
3.  **網掛け変数**ボックスで、 **Bike Buyer**です。  
  
     既定変数は**母集団**が、これを検出するクラスターが必要な属性を持つメンバーを含む、モデル内のすべての属性を変更することができます。  
  
4.  選択**1**で、**状態**自転車を購入したケースを調査するボックスです。  
  
     **密度**凡例には、網掛け変数と状態で選択した属性状態のペアの密度がについて説明します。 この例ではことがわかること clusterwith 色の濃いが自転車購入者の高い割合であります。  
  
5.  最も色の濃いクラスター上にマウス ポインターを置きます。  
  
     ツールヒントに、属性が `Bike Buyer = 1` であるケースの割合が表示されます。  
  
6.  クラスターを右クリックし、選択は、最も高い密度の高いクラスターを選択して**クラスターの名前を変更**および種類**自転車購入者率高**の後で識別します。 [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  最も色の薄い (最も密度の低い) クラスターを見つけます。 クラスターを右クリックし、選択**クラスターの名前を変更**および種類**自転車購入者率低**です。 [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  クリックして、**自転車購入者率高**クラスターし、他のクラスターとの接続を明確に表示するためのウィンドウの領域にドラッグします。  
  
     クラスターを選択すると、そのクラスターと別のクラスターをつなぐ線が強調表示され、このクラスターに対するすべての関係を簡単に確認できます。 クラスターが選択されていないときは、ダイアグラム内にあるすべてのクラスター間の相互関係の度合いを、線の濃さによって確認できます。 網掛けが薄いか存在しない場合は、クラスターがあまり似ていません。  
  
9. ネットワークの左側にあるスライダーを使用して、緊密度の低いリンクを非表示にし、緊密な関係にあるクラスターだけを表示します。 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] のマーケティング部門は、絞り込みメール配信に最適な方法を決定する際に、類似するクラスターをまとめることができます。  
  

  
##  <a name="ClusterProfilesTab"></a> クラスターのプロファイル タブ  
 **クラスターのプロファイル** タブの全体的なビューを提供する、`TM_Clustering`モデル。 **クラスターのプロファイル** タブには、各クラスター モデル内の列が含まれています。 一番左側の列には、少なくとも 1 つのクラスターに関連付けられているすべての属性が表示されます。 その他の部分には、それぞれのクラスターについて、各属性の状態の分布状況が表示されます。 離散変数の分布に表示されるバーの数が最大で色分けされたバーとして表示、**ヒストグラム バー**  ボックスの一覧です。 連続属性はダイヤモンド グラフで示されます。このグラフでは、各クラスターの平均と標準偏差を確認できます。  
  
#### <a name="to-explore-the-model-in-the-cluster-profiles-tab"></a>[クラスターのプロファイル] タブでモデルを調査するには  
  
1.  設定**ヒストグラム**バーに**5**です。  
  
     このモデルでは、1 つの変数に対する状態の最大数が 5 になります。  
  
2.  場合、**マイニング凡例**ブロックの表示、**属性のプロファイル**の場所に移動します。  
  
3.  選択、**自転車購入者率高**列の右側にドラッグし、**母集団**列です。  
  
4.  選択、**自転車購入者率低**列の右側にドラッグし、**自転車購入者率高**列です。  
  
5.  クリックして、**自転車購入者率高**列です。  
  
     **変数**列がそのクラスターの重要度順に並べ替えられます。 列をスクロールし、[自転車購入者率高] クラスターの特性を確認します。 たとえば、多くの場合、このクラスターに属する人は通勤距離が短い傾向にあります。  
  
6.  ダブルクリックして、 **Age**セル、**自転車購入者率高**列です。  
  
     **マイニング凡例**より詳細な表示を確認しては、平均年齢と同様にこれらの顧客の年齢を確認できます。  
  
7.  右クリックし、**自転車購入者率低**列と select**列の非表示**です。  
  

  
##  <a name="ClusterCharacteristicsTab"></a> クラスターの特性 タブ  
 **クラスターの特性** タブで、ことを確認するさらに詳しくクラスターを構成する特性です。 ([クラスターのプロファイル] タブのように) すべてのクラスターの特性を比較するのではなく、一度に 1 つのクラスターを検証することができます。 例では、選択した場合の**自転車購入者率高**から、**クラスター**一覧は、このクラスターの顧客の特性を確認することができます。 [クラスターのプロファイル] ビューアーとは表示が異なりますが、結果は同じです。  
  
> [!NOTE]  
>  初期値を設定する場合を除き、 **holdoutseed**結果は、モデルを処理するたびに異なります。 詳細については、次を参照してください[HoldoutSeed 要素。](../analysis-services/scripting/properties/holdoutseed-element.md)  
  

  
##  <a name="ClusterDiscriminationTab"></a> クラスターの識別 タブ  
 **クラスターの識別** タブで、別の 1 つのクラスターを識別する特性を調べることができます。 2 つのクラスターから 1 つを選択した後、**クラスター 1**リスト、およびから 1 つ、**クラスター 2**ビューアー ボックスの一覧は、クラスター間の相違点を計算し、属性の一覧を表示します。ほとんどのクラスターを区別してください。  
  
#### <a name="to-explore-the-model-in-the-cluster-discrimination-tab"></a>[クラスターの識別] タブでモデルを調査するには  
  
1.  **クラスター 1**ボックスで、**自転車購入者率高**です。  
  
2.  **クラスター 2**ボックスで、**自転車購入者率低**です。  
  
3.  をクリックして**変数**アルファベット順に並べ替えます。  
  
     お客様の間での重要な違いの一部、**自転車購入者率低**と**自転車購入者率高**クラスターには、年齢、車の所有、子供、および地域の番号が含まれています。  
  
## <a name="related-tasks"></a>Related Tasks  
 他のマイニング モデルを探索するには、次のトピックを参照してください。  
  
-   [デシジョン ツリー モデルの検証&#40;基本的なデータ マイニングのチュートリアル&#41;](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
-   [Naive Bayes モデルの検証&#40;基本的なデータ マイニングのチュートリアル&#41;](../../2014/tutorials/exploring-the-naive-bayes-model-basic-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [Naive Bayes モデルの検証&#40;基本的なデータ マイニングのチュートリアル&#41;](../../2014/tutorials/exploring-the-naive-bayes-model-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a>このレッスンの前の作業  
 [デシジョン ツリー モデルの検証&#40;基本的なデータ マイニングのチュートリアル&#41;](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [Microsoft クラスター ビューアーを使用してモデルを参照します。](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)   
 [クラスターの識別 タブ&#40;マイニング モデル ビューアー&#41;](../../2014/analysis-services/cluster-discrimination-tab-mining-model-viewer.md)   
 [クラスターのプロファイル タブ&#40;マイニング モデル ビューアー&#41;](../../2014/analysis-services/cluster-profiles-tab-mining-model-viewer.md)   
 [クラスターの特性 タブ&#40;マイニング モデル ビューアー&#41;](../../2014/analysis-services/cluster-characteristics-tab-mining-model-viewer.md)   
 [クラスター ダイアグラム タブ&#40;マイニング モデル ビューアー&#41;](../../2014/analysis-services/cluster-diagram-tab-mining-model-viewer.md)  
  
  