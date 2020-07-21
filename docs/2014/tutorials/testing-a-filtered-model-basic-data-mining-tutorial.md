---
title: フィルター選択されたモデルのテスト (基本的なデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f0d74f8c-600d-4df5-a742-695e6947a071
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: baa4910b2849c4eb2dd04c6d0115c83683ee8bea
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63044097"
---
# <a name="testing-a-filtered-model-basic-data-mining-tutorial"></a>フィルター選択されたモデルのテスト (基本的なデータ マイニング チュートリアル)
  `TM_Decision_Tree`モデルが最も正確であると判断したので、 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]絞り込みメール配信キャンペーンのニーズに合わせてモデルをカスタマイズします。 具体的には、マーケティング部門では男性顧客と女性顧客に違いがあるかどうかを知りたいと考えています。 この情報は、広告媒体として使用する雑誌やダイレクト メールで特集する製品を決定する際に役立つ可能性があります。  
  
## <a name="using-filters"></a>フィルターの使用  
 フィルター選択を行うと、データのサブセットに基づくモデルを簡単に作成できます。 フィルターはモデルにのみ適用され、基になるデータ ソースは変更しません。  
  
 このレッスンでは、性別に基づいてフィルター処理を実行するモデルを作成し、男性と女性それぞれの購買行動に最も大きな影響を及ぼす特性を予測します。  
  
 まず、 `TM_Decision_Tree`モデルのコピーを作成します。  
  
#### <a name="to-copy-the-decision-tree-model"></a>デシジョン ツリー モデルをコピーするには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]の [ソリューションエクスプローラーで、[ **BasicDataMining**] を選択します。  
  
2.  **[マイニング モデル]** タブをクリックします。  
  
3.  `TM_Decision_Tree`モデルを右クリックし、[**新しいマイニングモデル**] をクリックします。  
  
4.  [**モデル名**] フィールドに「 `TM_Decision_Tree_Male`」と入力します。  
  
5.  **[OK]** をクリックします。  
  
 次に、性別に基づいてモデルの顧客を選択するフィルターを作成します。  
  
#### <a name="to-create-a-case-filter-on-a-mining-model"></a>マイニング モデルに対してケース フィルターを作成するには  
  
1.  `TM_Decision_Tree_Male`マイニングモデルを右クリックして、ショートカットメニューを開きます。  
  
     -- または --  
  
     モデルを選択します。 **[マイニング モデル]** メニューの **[モデル フィルターの設定]** をクリックします。  
  
2.  **[モデル フィルター]** ダイアログ ボックスで、 **[マイニング構造列]** ボックスのグリッドの先頭行をクリックします。  
  
     ドロップダウン リストに、そのテーブルの列の名前のみが表示されます。  
  
3.  [マイニング構造列] ボックスで、[**性別**] を選択します。  
  
     テキスト ボックスの左側のアイコンが変化して、選択されたアイテムがテーブルであるか列であるかが示されます。  
  
4.  [**演算子**] ボックスをクリックし、一覧から等号 (=) 演算子を選択します。  
  
5.  [**値**] テキストボックスをクリックし、「 **M**」と入力します。  
  
6.  グリッドの次の行をクリックします。  
  
7.  [ **OK]** をクリックして [**モデルフィルター** ] ダイアログボックスを閉じます。  
  
     フィルターが [**プロパティ**] ウィンドウに表示されます。 または、[**プロパティ**] ウィンドウから [**モデルフィルター** ] ダイアログを起動することもできます。  
  
8.  上記の手順を繰り返しますが、今度はモデル`TM_Decision_Tree_Female`の名前を指定し、[**値**] テキストボックスに「 **F** 」と入力します。  
  
## <a name="process-the-filtered-models"></a>フィルター選択されたモデルの処理  
 モデルを使用するには、事前にそのモデルを配置して処理する必要があります。 モデルの処理の詳細については、「 [&#40;基本的なデータマイニングチュートリアル&#41;](../../2014/tutorials/processing-models-in-the-targeted-mailing-structure-basic-data-mining-tutorial.md)」を参照してください。  
  
#### <a name="to-process-the-filtered-model"></a>フィルター選択されたモデルを処理するには  
  
1.  モデルを右クリック`TM_Decision_Tree_Male`し、[**マイニング構造の処理] と [すべてのモデル**] を選択します。  
  
2.  [**実行**] をクリックして、新しいモデルを処理します。  
  
3.  処理が完了したら、両方の処理ウィンドウで [**閉じる**] をクリックします。  
  
     [**マイニングモデル**] タブに2つの新しいモデルが表示されるようになりました。  
  
## <a name="evaluate-the-results"></a>結果の評価  
 結果を表示してフィルター選択されたモデルの精度を評価する方法は、前の 3 つのモデルの場合とほぼ同じです。 詳細については次を参照してください:  
  
 [デシジョンツリーモデルの調査 &#40;基本的なデータマイニングチュートリアル&#41;](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
 [リフト チャートを使用した精度テスト (基本的なデータ マイニング チュートリアル)](../../2014/tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
#### <a name="to-explore-the-filtered-models"></a>フィルター選択されたモデルを調査するには  
  
1.  **データマイニングデザイナー**で [**マイニングモデルビューアー** ] タブを選択します。  
  
2.  [マイニングモデル] ボックスで、 `TM_Decision_Tree_Male`を選択します。  
  
3.  スライド**ショーレベル**を`3`にスライドします。  
  
4.  [**背景**値をに`1`変更します。  
  
5.  "**すべて**" というラベルが付いたノードの上にカーソルを置き、自転車購入者と非自転車購入者の数を確認します。  
  
6.  に対して手順`TM_Decision_Tree_Female`1-5 を繰り返します。  
  
7.  `TM_Decision_Tree`および性別に対してフィルター処理されたモデルの結果を調べます。 すべての自転車購入者と比較すると、男性の自転車購入者および女性の自転車購入者には、フィルター選択されていない自転車購入者と同じ特性もいくつかありますが、この 3 者には興味深い相違点もあります。 これは、マーケティングキャンペーン[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]の開発に使用できる有用な情報です。  
  
#### <a name="to-test-the-lift-of-the-filtered-models"></a>フィルター選択されたモデルのリフトをテストするには  
  
1.  の[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]データマイニングデザイナーの [**マイニング精度チャート**] タブに切り替えて、[**入力の選択**] タブを選択します。  
  
2.  [**精度チャートに使用するデータセットの選択**] グループボックスで、[**マイニング構造のテストケースを使用**する] を選択します。  
  
3.  データマイニングデザイナーの [**入力の選択**] タブの [**リフトチャートに表示する予測可能なマイニングモデル列の選択**] で、[**予測列と値の同期**] のチェックボックスをオンにします。  
  
4.  [**予測可能列の名前**] 列で、各モデルに対して [**自転車購入**者] が選択されていることを確認します。  
  
5.  [**表示]** 列で、各モデルを選択します。  
  
6.  [**予測値**] 列でを`1`選択します。  
  
7.  [**リフトチャート**] タブを選択すると、リフトチャートが表示されます。  
  
     3 つすべてのデシジョン ツリー モデルでランダム推測モデルよりも大幅なリフトが見られ、クラスター モデルや Naive Bayes モデルより高精度であることがわかります。  
  
## <a name="related-tasks"></a>Related Tasks  
 フィルターの詳細については、「 [Analysis Services データマイニング&#41;&#40;マイニングモデルのフィルター ](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)」を参照してください。  
  
 入れ子になったテーブルにフィルターを適用する方法の例については、「中級者向け[データマイニングチュートリアル &#40;Analysis Services データマイニング&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)」を参照してください。  
  
## <a name="previous-task-in-lesson"></a>このレッスンの前の作業  
 [リフト チャートを使用した精度テスト (基本的なデータ マイニング チュートリアル)](../../2014/tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a>次のレッスン  
 [レッスン 6: 予測の作成と操作 &#40;基本的なデータ マイニング チュートリアル&#41;](../../2014/tutorials/lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [中級者向けデータマイニングチュートリアル &#40;Analysis Services データマイニング&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)   
 [マイニングモデルタスクと操作方法](../../2014/analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [マイニングモデルからのフィルターの削除](../../2014/analysis-services/data-mining/delete-a-filter-from-a-mining-model.md)   
 [マイニング モデルのフィルター &#40;Analysis Services - データ マイニング&#41;](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)  
  
  
