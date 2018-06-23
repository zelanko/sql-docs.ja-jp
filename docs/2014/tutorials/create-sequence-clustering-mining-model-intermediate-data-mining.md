---
title: シーケンス クラスター マイニング モデル構造 (中級者向けデータ マイニング チュートリアル) を作成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e9339227-6c2e-4c4b-8be2-8c1960bc4a8d
caps.latest.revision: 40
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 09aaac50873d6c4c63b46fdf37dd7ee854000886
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312700"
---
# <a name="creating-a-sequence-clustering-mining-model-structure-intermediate-data-mining-tutorial"></a>シーケンス クラスター マイニング モデル構造の作成 (中級者向けデータ マイニング チュートリアル)
  シーケンス クラスター マイニング モデルを作成する最初の手順では、データ マイニング ウィザードを使用して新しいマイニング構造を作成し、[!INCLUDE[msCoName](../includes/msconame-md.md)] シーケンス クラスター アルゴリズムに基づくマイニング モデルを作成します。  
  
 マーケット バスケット分析に使用したものと同じデータ ソース ビューを使用しますが、`sequence` ID を格納する列を追加します。 このシナリオでは、シーケンスは、顧客が品目を買い物かごに追加した順序を表します。  
  
 統計データによって顧客を分類するためにいずれかのモデルで使用する列も追加します。  
  
### <a name="to-create-a-sequence-clustering-structure-and-model"></a>シーケンス クラスターの構造とモデルを作成するには  
  
1.  ソリューション エクスプ ローラーで[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]を右クリックして**マイニング構造**選択**新しいマイニング構造**です。  
  
2.  **[データ マイニング ウィザードへようこそ]** ページで **[次へ]** をクリックします。  
  
3.  **定義方法の選択** ページであることを確認**既存のリレーショナル データベースまたはデータ ウェアハウスから**を選択して、をクリックして**次**です。  
  
4.  **データ マイニング構造の作成**ことを確認 ページで、オプション**マイニング モデルを含むマイニング構造の作成**が選択されています。 次に、オプションの場合、ドロップダウン リストをクリックして**を使用するデータ マイニング技法ですか?** を選択し、 **Microsoft シーケンス クラスター**です。 **[次へ]** をクリックします。  
  
     **データ ソース ビューの選択**ページが表示されます。 **使用可能なデータ ソース ビュー**`Orders`です。  
  
     Orders は、マーケット バスケット シナリオで使用したものと同じデータ ソース ビューです。 このデータ ソース ビューを作成していない場合は、次を参照してください。[入れ子になったテーブルを持つデータ ソース ビューの追加&#40;中級者向けデータ マイニング チュートリアル&#41;](../../2014/tutorials/adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial.md)です。  
  
5.  **[次へ]** をクリックします。  
  
6.  **テーブルの種類の指定** ページで、、**ケース** チェック ボックスの隣に、 **vAssocSeqOrders** 、テーブルを選択して、**入れ子になった** チェック ボックス次に、 **vAssocSeqLineItems**テーブル。 **[次へ]** をクリックします。  
  
    > [!NOTE]  
    >  選択したときにエラーが発生した場合、**ケース**または**入れ子になった** チェック ボックスがあります、データ ソース ビューの結合が正しくないことです。 入れ子になったテーブル、 **vAssocSeqLineItems**、ケース テーブルに接続されている必要があります**vAssocSeqOrders**多対一結合でします。 結合線を右クリックして結合の方向を逆向きにすることによって、リレーションシップを編集できます。 詳細については、次を参照してください。[リレーションシップの編集 ダイアログ ボックスの作成または&#40;Analysis Services - 多次元データ&#41;](../../2014/analysis-services/create-or-edit-relationship-dialog-box-analysis-services-multidimensional-data.md)です。  
  
7.  **トレーニング データの指定**ページで、次のように、チェック ボックスを選択して、モデルで使用する列を選択します。  
  
    -   **IncomeGroup**選択、**入力**チェック ボックスをオンします。  
  
         この列には、クラスタリングに使用できる、顧客に関する有用な情報が格納されます。 最初のモデルではこの情報を使用し、2 番目のモデルではこの情報を無視します。  
  
    -   **OrderNumber**選択、`Key`チェック ボックスをオンします。  
  
         このフィールドは、ケース テーブルの識別子、つまり `Key` として使用されます。 一般に、キーにはクラスタリングに適さない一意の値が格納されるので、ケース テーブルのキー フィールドは入力として使用しないでください。  
  
    -   **地域**選択、**入力**チェック ボックスをオンします。  
  
         この列には、クラスタリングに使用できる、顧客に関する有用な情報が格納されます。 最初のモデルではこの情報を使用し、2 番目のモデルではこの情報を無視します。  
  
    -   **LineNumber**選択、`Key`と**入力**のチェック ボックスです。  
  
         **LineNumber**フィールドは、入れ子になったテーブルの識別子として使用されますか`Sequence Key`です。 入れ子になったテーブルのキーは、常に入力に使用する必要があります。  
  
    -   **モデル**選択、**入力**と**Predictable**チェック ボックスです。  
  
     選択内容が正しいことを確認 をクリックし、**次**です。  
  
8.  **コンテンツおよびデータ型の列の指定の** ページで、グリッドには、列、コンテンツの種類、および次の表に示すようにデータ型が含まれていることを確認してをクリックして**次**です。  
  
    |テーブルまたは列|コンテンツの種類|データ型|  
    |---------------------|------------------|---------------|  
    |IncomeGroup|Discrete|Text|  
    |OrderNumber|Key|Text|  
    |Region|Discrete|Text|  
    |vAssocSeqLineItems|||  
    |Line Number|Key Sequence|Long|  
    |[モデル]|Discrete|Text|  
  
9. **テスト セットの作成** ページで、変更、**テスト用データの割合**20、およびクリックを**次へ**です。  
  
10. **ウィザードの完了** ページの**マイニング構造名**、型`Sequence Clustering with Region`です。  
  
11. **マイニング モデル名**、型`Sequence Clustering with Region`です。  
  
12. チェック、**ドリルスルーを許可する**ボックスをクリックして**完了**です。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [シーケンス クラスター モデルの処理](../../2014/tutorials/processing-the-sequence-clustering-model.md)  
  
## <a name="see-also"></a>参照  
 [データ マイニング デザイナー](../../2014/analysis-services/data-mining/data-mining-designer.md)   
 [Microsoft シーケンス クラスタリング アルゴリズム](../../2014/analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md)  
  
  