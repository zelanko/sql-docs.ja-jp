---
title: 構造に対してテストデータセットを指定する (基本的なデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 75cd508f-b126-418b-848d-3c4c3e6c303f
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 21eaa86fb1ff594e8b9d2b779b787276ee13ab4b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62720101"
---
# <a name="specifying-a-testing-data-set-for-the-structure-basic-data-mining-tutorial"></a>構造のテスト データ セットの指定 (基本的なデータ マイニング チュートリアル)
  データ マイニング ウィザードの最後の数画面では、データをテスト セットとトレーニング セットに分割します。 次に、構造に名前を付けて、モデルのドリルスルーを有効にします。  
  
## <a name="specifying-a-testing-set"></a>テスト セットの指定  
 マイニング構造を作成する際にデータをトレーニング セットとテスト セットに分割すると、後で作成するマイニング モデルの精度を簡単に評価できるようになります。 テストセットの詳細については、「[データセットのトレーニングとテスト](../../2014/analysis-services/data-mining/training-and-testing-data-sets.md)」を参照してください。  
  
#### <a name="to-specify-the-testing-set"></a>テスト セットを指定するには  
  
1.  [テスト**セットの作成**] ページで、**テスト用データの割合**を既定値のまま`30`にします。  
  
2.  **[テストデータセット内のケースの最大数**] `1000`に、「」と入力します。  
  
3.  **[次へ]** をクリックします。  
  
## <a name="specifying-drillthrough"></a>ドリルスルーの指定  
 ドリルスルーは、モデルおよび構造で有効にできます。 このダイアログ ボックスのチェック ボックスを使って、該当するモデルに対するドリルスルーを有効にします。 モデルの処理後は、モデルの作成に使用されたトレーニング データから、詳細情報を取得できます。  
  
 基になるマイニング構造もドリルスルーを許可するように構成されている場合は、モデル ケースとマイニング構造の両方から、詳細な情報 (マイニング モデルに含まれていなかった列など) を取得できます。 詳細については、「 [ドリルスルー クエリ (データ マイニング)](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)」をご覧ください。  
  
#### <a name="to-name-the-model-and-structure-and-specify-drillthrough"></a>モデルおよび構造に名前を付けてドリルスルーを指定するには  
  
1.  [**ウィザードの完了**] ページの [**マイニング構造名**] に`Targeted Mailing`「」と入力します。  
  
2.  [**マイニングモデル名**] に`TM_Decision_Tree`「」と入力します。  
  
3.  [ドリルスルーを**許可する**] チェックボックスをオンにします。  
  
4.  **プレビュー**ウィンドウを確認します。 [**キー**]、[**入力**]、または [**予測可能**] として選択した列のみが表示されます。 選択した他の列 (AddressLine1 など) は、モデルの作成には使用されませんが、基になる構造で使用することができ、モデルを処理および配置した後でクエリすることができます。  
  
5.  **[完了]** をクリックします。  
  
## <a name="previous-task-in-lesson"></a>このレッスンの前の作業  
 [データ型とコンテンツの種類の指定 &#40;基本的なデータマイニングチュートリアル&#41;](../../2014/tutorials/specifying-the-data-type-and-content-type-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a>次のレッスン  
 [レッスン 3: モデルの追加と処理](../../2014/tutorials/lesson-3-adding-and-processing-models.md)  
  
## <a name="see-also"></a>参照  
 [マイニングモデルのドリルスルーを有効にする](../../2014/analysis-services/data-mining/enable-drillthrough-for-a-mining-model.md)   
 [データマイニング &#40;のドリルスルークエリ&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)   
 [データマイニング &#40;トレーニングウィザードを指定し&#41;](../../2014/analysis-services/specify-the-training-data-data-mining-wizard.md)  
  
  
