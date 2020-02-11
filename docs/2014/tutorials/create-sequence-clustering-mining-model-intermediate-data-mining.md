---
title: シーケンスクラスターマイニングモデル構造の作成 (中級者向けデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e9339227-6c2e-4c4b-8be2-8c1960bc4a8d
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b7f4f543952fd86cf6c3c66f9f4b2c51019b1869
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63273479"
---
# <a name="creating-a-sequence-clustering-mining-model-structure-intermediate-data-mining-tutorial"></a>シーケンス クラスター マイニング モデル構造の作成 (中級者向けデータ マイニング チュートリアル)
  シーケンス クラスター マイニング モデルを作成する最初の手順では、データ マイニング ウィザードを使用して新しいマイニング構造を作成し、[!INCLUDE[msCoName](../includes/msconame-md.md)] シーケンス クラスター アルゴリズムに基づくマイニング モデルを作成します。  
  
 マーケット バスケット分析に使用したものと同じデータ ソース ビューを使用しますが、`sequence` ID を格納する列を追加します。 このシナリオでは、シーケンスは、顧客が品目を買い物かごに追加した順序を表します。  
  
 統計データによって顧客を分類するためにいずれかのモデルで使用する列も追加します。  
  
### <a name="to-create-a-sequence-clustering-structure-and-model"></a>シーケンス クラスターの構造とモデルを作成するには  
  
1.  のソリューションエクスプローラーで[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]、[**マイニング構造**] を右クリックし、[**新しいマイニング構造**] をクリックします。  
  
2.  
  **[データ マイニング ウィザードへようこそ]** ページで **[次へ]** をクリックします。  
  
3.  [**定義方法の選択**] ページで、[**既存のリレーショナルデータベースまたはデータウェアハウスから**] が選択されていることを確認し、[**次へ**] をクリックします。  
  
4.  [**データマイニング構造の作成**] ページで、[**マイニングモデルを含むマイニング構造を作成**する] オプションが選択されていることを確認します。 次に、オプションのドロップダウンリストをクリックして、**使用するデータマイニング技法**を選択し、[ **Microsoft シーケンスクラスター**] を選択します。 **[次へ]** をクリックします。  
  
     **[データソースビューの選択**] ページが表示されます。 [**使用できるデータソースビュー**] `Orders`で、[] を選択します。  
  
     Orders は、マーケット バスケット シナリオで使用したものと同じデータ ソース ビューです。 このデータソースビューを作成していない場合は、「[入れ子になったテーブルを含むデータソースビューの追加 &#40;中級者向けデータマイニングチュートリアル」&#41;](../../2014/tutorials/adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial.md)を参照してください。  
  
5.  **[次へ]** をクリックします。  
  
6.  [**テーブルの種類の指定**] ページで、 **vAssocSeqOrders**テーブルの横にある [**ケース**] チェックボックスをオンにし、 **VAssocSeqLineItems**テーブルの横にある [**入れ子になっ**た] チェックボックスをオンにします。 **[次へ]** をクリックします。  
  
    > [!NOTE]  
    >  **ケース**または**入れ子になっ**たチェックボックスをオンにしたときにエラーが発生した場合、データソースビューの結合が正しくない可能性があります。 入れ子になったテーブル**vAssocSeqLineItems**は、多対一の結合によってケーステーブル**vAssocSeqOrders**に接続されている必要があります。 結合線を右クリックして結合の方向を逆向きにすることによって、リレーションシップを編集できます。 詳細については、「[[リレーションシップの作成] または [リレーションシップの編集] ダイアログボックス &#40;Analysis Services-多次元データ&#41;](../../2014/analysis-services/create-or-edit-relationship-dialog-box-analysis-services-multidimensional-data.md)」を参照してください。  
  
7.  [**トレーニングデータの指定**] ページで、次のようにチェックボックスをオンにして、モデルで使用する列を選択します。  
  
    -   **IncomeGroup**[**入力**] チェックボックスをオンにします。  
  
         この列には、クラスタリングに使用できる、顧客に関する有用な情報が格納されます。 最初のモデルではこの情報を使用し、2 番目のモデルではこの情報を無視します。  
  
    -   **Ordernumber**チェックボックス`Key`をオンにします。  
  
         このフィールドは、ケース テーブルの識別子、つまり `Key` として使用されます。 一般に、キーにはクラスタリングに適さない一意の値が格納されるので、ケース テーブルのキー フィールドは入力として使用しないでください。  
  
    -   **リージョン**[**入力**] チェックボックスをオンにします。  
  
         この列には、クラスタリングに使用できる、顧客に関する有用な情報が格納されます。 最初のモデルではこの情報を使用し、2 番目のモデルではこの情報を無視します。  
  
    -   **LineNumber**[] `Key`および [**入力**] チェックボックスをオンにします。  
  
         **LineNumber**フィールドは、入れ子になったテーブルの識別子として、 `Sequence Key`またはとして使用されます。 入れ子になったテーブルのキーは、常に入力に使用する必要があります。  
  
    -   **モデル**[**入力**] チェックボックスと [**予測可能**] チェックボックスをオンにします。  
  
     選択内容が正しいことを確認し、[**次へ**] をクリックします。  
  
8.  [**列のコンテンツおよびデータ型の指定**] ページで、次の表に示す列、コンテンツの種類、およびデータ型がグリッドに表示されていることを確認し、[**次へ**] をクリックします。  
  
    |テーブルまたは列|コンテンツの種類|データ型|  
    |---------------------|------------------|---------------|  
    |IncomeGroup|Discrete|Text|  
    |OrderNumber|キー|Text|  
    |リージョン|Discrete|Text|  
    |vAssocSeqLineItems|||  
    |Line Number|Key Sequence|Long|  
    |モデル|Discrete|Text|  
  
9. [**テストセットの作成**] ページで、**テスト用データの割合**を20に変更し、[**次へ**] をクリックします。  
  
10. [**ウィザードの完了**] ページで、[**マイニング構造名**] に`Sequence Clustering with Region`「」と入力します。  
  
11. [**マイニングモデル名**] に「 `Sequence Clustering with Region`」と入力します。  
  
12. [ドリルスルーを**許可する**] チェックボックスをオンにし、[**完了**] をクリックします。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [シーケンス クラスター モデルの処理](../../2014/tutorials/processing-the-sequence-clustering-model.md)  
  
## <a name="see-also"></a>参照  
 [データマイニングデザイナー](../../2014/analysis-services/data-mining/data-mining-designer.md)   
 [「Microsoft シーケンス クラスター アルゴリズム」](../../2014/analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md)  
  
  
