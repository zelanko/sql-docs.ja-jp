---
title: Market Basket 構造およびモデル (中級者向けデータ マイニング チュートリアル) の作成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 659b7a4e-f687-44d9-a60a-86490ccbf90f
caps.latest.revision: 48
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 957a55114e5a4fb756c63b63779eed3fbfb5f95b
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312600"
---
# <a name="creating-a-market-basket-structure-and-model-intermediate-data-mining-tutorial"></a>Market Basket 構造およびモデルの作成 (中級者向けデータ マイニング チュートリアル)
  前の作業では、データ ソース ビューを作成しました。次の作業では、データ マイニング ウィザードを使用して、新しいマイニング構造を作成します。 この作業では、[!INCLUDE[msCoName](../includes/msconame-md.md)] アソシエーション アルゴリズムに基づくマイニング構造とマイニング モデルを作成します。  
  
> [!NOTE]  
>  vAssocSeqLineItems テーブルを入れ子にできないことを示すエラーが表示された場合は、レッスンの前の作業に戻り、多対一の結合を確実に作成してください。この結合を作成するには、vAssocSeqLineItems テーブル ("多" の側) から vAssocSeqOrders テーブル ("一" の側) にドラッグします。 結合線を右クリックして、テーブル間のリレーションシップを編集することもできます。  
  
### <a name="to-create-an-association-mining-structure"></a>アソシエーション マイニング構造を作成するには  
  
1.  ソリューション エクスプ ローラーで[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]を右クリックして**マイニング構造**選択と**新しいマイニング構造**データ マイニング ウィザードを開きます。  
  
2.  **[データ マイニング ウィザードへようこそ]** ページで **[次へ]** をクリックします。  
  
3.  **定義方法の選択** ページであることを確認**既存のリレーショナル データベースまたはデータ ウェアハウスから**を選択して、をクリックして**次**です。  
  
4.  **データ マイニング構造の作成**] ページの [**を使用するデータ マイニング技法ですか?****[Microsoft アソシエーション ルール]** をクリックし、一覧から**次**です。 **データ ソース ビューの選択**ページが表示されます。  
  
5.  選択**Orders****使用可能なデータ ソース ビュー**、順にクリック**次へ**です。  
  
6.  **テーブルの種類の指定**ページで、vAssocSeqLineItems テーブルの行で、選択、**入れ子になった**チェック ボックスをオンし、入れ子になったテーブル vAssocSeqOrders の行をクリックし、**ケース**チェック ボックスをオンします。 **[次へ]** をクリックします。  
  
7.  **トレーニング データの指定** ページで、オンになっている任意のボックスをオフにします。 選択、ケース テーブル vAssocSeqOrders のキーを設定、**キー** OrderNumber 横のチェック ボックスです。  
  
     マーケット バスケット分析の目的は、どの製品が 1 つのトランザクションに含まれるを決定するが、ためには使用する必要はありません、 **CustomerKey**フィールドです。  
  
8.  選択、入れ子になったテーブル vAssocSeqLineItems のキーを設定、**キー**モデルの横にあるチェック ボックスです。 **入力** チェック ボックスは、これを行うときにも自動的に選択します。 選択、 **Predictable**のチェック ボックスを`Model`もします。  
  
     マーケット バスケット モデルでを気にせず、買い物かごに商品のシーケンスとそのため、含めることはできません**LineNumber**入れ子になったテーブル キーとして。 使用する**LineNumber**モデルでのみ、順序が重要なキーとして。 レッスン 4 では、[!INCLUDE[msCoName](../includes/msconame-md.md)] シーケンス クラスター アルゴリズムを使用するモデルを作成します。  
  
9. [IncomeGroup] および [Region] の左側にあるチェック ボックスをオンにします。ただし、それ以外のチェック ボックスはオンにしないでください。 左端の列のチェック ボックスをオンにすると、これらの列が構造に追加され、後で参照できるようになります。ただし、これらの列はモデルでは使用されません。 選択内容は以下のようになります。  
  
     ![ダイアログ ボックスの外観](../../2014/tutorials/media/tutorial-configassocmodel.gif " ダイアログ ボックスの外観")  
  
10. **[次へ]** をクリックします。  
  
11. **コンテンツおよびデータ型の列の指定の** ページで、次の表に示すようをクリックする必要がありますが、選択内容を確認**次**です。  
  
    |[列]|コンテンツの種類|データ型|  
    |-------------|------------------|---------------|  
    |IncomeGroup|Discrete|Text|  
    |Order Number|Key|Text|  
    |Region|Discrete|Text|  
    |vAssocSeqLineItems|||  
    |[モデル]|Key|Text|  
  
12. **テストの設定を作成** ページで、オプションの既定値**テスト用データの割合**が 30% です。 これを変更**0**します。 **[次へ]** をクリックします。  
  
    > [!NOTE]  
    >  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] には、モデルの精度を測定するための別のチャートが用意されています。 ただし、リフト チャートや相互検証レポートなど、一部の種類の精度チャートは、分類および推定用に設計されています。 結合型の予測には使用できません。  
  
13. **ウィザードの完了**] ページの [**マイニング構造名**、型`Association`です。  
  
14. **マイニング モデル名**、型`Association`です。  
  
15. オプションを選択**ドリルスルーを許可する**、クリックして**完了**です。  
  
     データ マイニング デザイナーで開いて、表示、`Association`先ほど作成したマイニング構造です。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [マーケット バスケット モデルの処理の変更と&#40;中級レベルのデータ マイニング チュートリアル&#41;](../../2014/tutorials/modify-process-market-basket-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [Microsoft アソシエーション アルゴリズム](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md)   
 [コンテンツの種類&#40;データ マイニング&#41;](../../2014/analysis-services/data-mining/content-types-data-mining.md)  
  
  