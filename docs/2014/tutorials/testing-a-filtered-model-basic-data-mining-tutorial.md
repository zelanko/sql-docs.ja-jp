---
title: フィルター選択されたモデル (基本的なデータ マイニング チュートリアル) のテスト |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f0d74f8c-600d-4df5-a742-695e6947a071
caps.latest.revision: 28
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 0dfb4b3ae34b230c591071f02cdaa9b0984cf05e
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312550"
---
# <a name="testing-a-filtered-model-basic-data-mining-tutorial"></a>フィルター選択されたモデルのテスト (基本的なデータ マイニング チュートリアル)
  これであることを確認、`TM_Decision_Tree`モデルは、最も正確なでは、モデルのニーズに合わせて、カスタマイズ、[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]絞り込みメール配信キャンペーン。 具体的には、マーケティング部門では男性顧客と女性顧客に違いがあるかどうかを知りたいと考えています。 情報には、広告のために使用する雑誌を決定するためでしたダイレクト_メールで特集する製品とします。  
  
## <a name="using-filters"></a>フィルターの使用  
 フィルター選択を行うと、データのサブセットに基づくモデルを簡単に作成できます。 フィルターはモデルにのみ適用され、基になるデータ ソースは変更しません。  
  
 このレッスンでは、性別に基づいてフィルター処理を実行するモデルを作成し、男性と女性それぞれの購買行動に最も大きな影響を及ぼす特性を予測します。  
  
 最初のコピーを作成、`TM_Decision_Tree`モデル。  
  
#### <a name="to-copy-the-decision-tree-model"></a>デシジョン ツリー モデルをコピーするには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]、ソリューション エクスプ ローラーで、次のように選択します。 **BasicDataMining**です。  
  
2.  **[マイニング モデル]** タブをクリックします。  
  
3.  右クリックして、`TM_Decision_Tree`モデル、および選択**新しいマイニング モデルです。**  
  
4.  **モデル名**フィールドに「`TM_Decision_Tree_Male`です。  
  
5.  **[OK]** をクリックします。  
  
 次に、性別に基づいてモデルの顧客を選択するフィルターを作成します。  
  
#### <a name="to-create-a-case-filter-on-a-mining-model"></a>マイニング モデルに対してケース フィルターを作成するには  
  
1.  右クリックし、`TM_Decision_Tree_Male`マイニング モデルのショートカット メニューを開きます。  
  
     -- または --  
  
     モデルを選択します。 **[マイニング モデル]** メニューの **[モデル フィルターの設定]** をクリックします。  
  
2.  **[モデル フィルター]** ダイアログ ボックスで、 **[マイニング構造列]** ボックスのグリッドの先頭行をクリックします。  
  
     ドロップダウン リストに、そのテーブルの列の名前のみが表示されます。  
  
3.  マイニング構造列] ボックスで、[**性別**です。  
  
     テキスト ボックスの左側のアイコンが変化して、選択されたアイテムがテーブルであるか列であるかが示されます。  
  
4.  クリックして、**演算子**テキスト ボックスと、一覧から等号 (=) 演算子を選択します。  
  
5.  クリックして、**値**テキスト ボックス、および種類**M**です。  
  
6.  グリッドの次の行をクリックします。  
  
7.  をクリックして**OK**を閉じる、**モデル フィルター**  ダイアログ ボックス。  
  
     フィルターが表示されます、**プロパティ**ウィンドウです。 またはを実行して、**モデル フィルター**からダイアログ ボックス、**プロパティ**ウィンドウです。  
  
8.  上記の手順では、今度はモデルの名前を繰り返して`TM_Decision_Tree_Female`および種類**F**で、**値**テキスト ボックス。  
  
## <a name="process-the-filtered-models"></a>フィルター選択されたモデルの処理  
 モデルを使用するには、事前にそのモデルを配置して処理する必要があります。 モデルの処理の詳細については、次を参照してください。[メーリング対象となる構造の処理モデル&#40;Basic Data Mining Tutorial&#41;](../../2014/tutorials/processing-models-in-the-targeted-mailing-structure-basic-data-mining-tutorial.md)です。  
  
#### <a name="to-process-the-filtered-model"></a>フィルター選択されたモデルを処理するには  
  
1.  右クリックし、`TM_Decision_Tree_Male`モデルし、選択**および全モデルのマイニング構造の処理**s  
  
2.  をクリックして**実行**を新しいモデルを処理します。  
  
3.  処理が完了したらをクリックして**閉じる**両方の処理ウィンドウにします。  
  
     今すぐに表示される 2 つの新しいモデルがある、**マイニング モデル**タブです。  
  
## <a name="evaluate-the-results"></a>結果の評価  
 結果を表示してフィルター選択されたモデルの精度を評価する方法は、前の 3 つのモデルの場合とほぼ同じです。 詳細については、以下をご覧ください。  
  
 [デシジョン ツリー モデルの検証&#40;基本的なデータ マイニングのチュートリアル&#41;](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
 [リフト チャートを使用した精度テスト&#40;基本的なデータ マイニングのチュートリアル&#41;](../../2014/tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
#### <a name="to-explore-the-filtered-models"></a>フィルター選択されたモデルを調査するには  
  
1.  選択、**マイニング モデル ビューアー** ] タブの [**データ マイニング デザイナー**です。  
  
2.  マイニング モデル ボックスで選択`TM_Decision_Tree_Male`です。  
  
3.  スライド**レベルを表示する**に`3`です。  
  
4.  変更、**背景**値を`1`です。  
  
5.  ラベルの付いたノードの上にカーソルを置きます**すべて**自転車を購入する自転車非購入者との比較の数を表示します。  
  
6.  手順 1. ~ 5. を繰り返します`TM_Decision_Tree_Female`です。  
  
7.  結果を検証、`TM_Decision_Tree`性別に基づいてフィルター選択された、モデルとします。 すべての自転車購入者と比較すると、男性の自転車購入者および女性の自転車購入者には、フィルター選択されていない自転車購入者と同じ特性もいくつかありますが、この 3 者には興味深い相違点もあります。 これは、有用な情報を[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]を使用してマーケティング キャンペーンを開発します。  
  
#### <a name="to-test-the-lift-of-the-filtered-models"></a>フィルター選択されたモデルのリフトをテストするには  
  
1.  切り替えて、**マイニング精度チャート** タブで、データ マイニング デザイナーで[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]を選択し、**入力の選択**タブです。  
  
2.  **精度チャートに使用するデータセットの選択**グループ ボックスで、**マイニング構造のテスト_ケースを使用して**です。  
  
3.  **入力の選択**データ マイニング デザイナーのタブで、**リフト チャートに表示する予測可能なマイニング モデル列の選択**、チェック ボックスをオン**予測可能列の同期と値**です。  
  
4.  **予測可能列名**列、いることを確認**Bike Buyer**モデルごとに選択します。  
  
5.  **表示**列で、各モデルのです。  
  
6.  **予測値**列をオン`1`です。  
  
7.  選択、**リフト チャート**リフト チャートを表示するタブです。  
  
     3 つすべてのデシジョン ツリー モデルでランダム推測モデルよりも大幅なリフトが見られ、クラスター モデルや Naive Bayes モデルより高精度であることがわかります。  
  
## <a name="related-tasks"></a>Related Tasks  
 フィルターの詳細については、次を参照してください。[マイニング モデル フィルターの&#40;Analysis Services - データ マイニング&#41;](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)です。  
  
 入れ子になったテーブルにフィルターを適用する方法の例は、次を参照してください。[中級者向けデータ マイニング チュートリアル&#40;Analysis Services - データ マイニング&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)です。  
  
## <a name="previous-task-in-lesson"></a>このレッスンの前の作業  
 [リフト チャートを使用した精度テスト&#40;基本的なデータ マイニングのチュートリアル&#41;](../../2014/tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a>次のレッスン  
 [レッスン 6: の作成と操作の予測&#40;基本的なデータ マイニングのチュートリアル&#41;](../../2014/tutorials/lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [データ マイニング チュートリアルを中間&#40;Analysis Services - データ マイニング&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)   
 [マイニング モデル タスクと操作方法](../../2014/analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [マイニング モデルからフィルターを削除します。](../../2014/analysis-services/data-mining/delete-a-filter-from-a-mining-model.md)   
 [マイニング モデル フィルターの&#40;Analysis Services - データ マイニング&#41;](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)  
  
  