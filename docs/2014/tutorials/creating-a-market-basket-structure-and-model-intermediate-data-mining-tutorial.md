---
title: マーケットバスケットの構造とモデルの作成 (中級者向けデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 659b7a4e-f687-44d9-a60a-86490ccbf90f
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 207d82f740b7b5ff174e220e647d67d5bac7f9ea
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63190830"
---
# <a name="creating-a-market-basket-structure-and-model-intermediate-data-mining-tutorial"></a>Market Basket 構造およびモデルの作成 (中級者向けデータ マイニング チュートリアル)
  前の作業では、データ ソース ビューを作成しました。次の作業では、データ マイニング ウィザードを使用して、新しいマイニング構造を作成します。 この作業では、[!INCLUDE[msCoName](../includes/msconame-md.md)] アソシエーション アルゴリズムに基づくマイニング構造とマイニング モデルを作成します。  
  
> [!NOTE]  
>  vAssocSeqLineItems テーブルを入れ子にできないことを示すエラーが表示された場合は、レッスンの前の作業に戻り、多対一の結合を確実に作成してください。この結合を作成するには、vAssocSeqLineItems テーブル ("多" の側) から vAssocSeqOrders テーブル ("一" の側) にドラッグします。 結合線を右クリックして、テーブル間のリレーションシップを編集することもできます。  
  
### <a name="to-create-an-association-mining-structure"></a>アソシエーション マイニング構造を作成するには  
  
1.  のソリューションエクスプローラーで[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]、[**マイニング構造**] を右クリックし、[**新しいマイニング構造**] をクリックして、データマイニングウィザードを開きます。  
  
2.  **[データ マイニング ウィザードへようこそ]** ページで **[次へ]** をクリックします。  
  
3.  [**定義方法の選択**] ページで、[**既存のリレーショナルデータベースまたはデータウェアハウスから**] が選択されていることを確認し、[**次へ**] をクリックします。  
  
4.  [**データマイニング構造の作成**] ページの [**使用するデータマイニング技法を指定**してください] で、一覧から [ **Microsoft アソシエーションルール**] を選択し、[**次へ**] をクリックします。 **[データソースビューの選択**] ページが表示されます。  
  
5.  [**使用できるデータソースビュー**] で [**注文**] を選択し、[**次へ**] をクリックします。  
  
6.  [**テーブルの種類の指定**] ページで、vAssocSeqLineItems テーブルの行の [**入れ子**] チェックボックスをオンにし、入れ子になったテーブル vAssocSeqOrders の行で [**ケース**] チェックボックスをオンにします。 **[次へ]** をクリックします。  
  
7.  [**トレーニングデータの指定**] ページで、チェックボックスをオフにします。 [OrderNumber] の横にある [**キー** ] チェックボックスをオンにして、ケーステーブル vAssocSeqOrders のキーを設定します。  
  
     マーケットバスケット分析の目的は、1つのトランザクションに含まれる製品を特定することであるため、[**顧客キー** ] フィールドを使用する必要はありません。  
  
8.  [モデル] の横にある [**キー** ] チェックボックスをオンにして、入れ子になったテーブル vAssocSeqLineItems のキーを設定します。 この操作を行うと、[**入力**] チェックボックスも自動的に選択されます。 [**予測可能**] チェックボックス`Model`もオンにします。  
  
     マーケットバスケットモデルでは、買い物かごに含まれる一連の製品を気にする必要はないため、入れ子になったテーブルのキーとして**LineNumber**を含めることはできません。 **LineNumber**は、シーケンスが重要なモデル内でのみキーとして使用します。 レッスン 4 では、[!INCLUDE[msCoName](../includes/msconame-md.md)] シーケンス クラスター アルゴリズムを使用するモデルを作成します。  
  
9. [IncomeGroup] および [Region] の左側にあるチェック ボックスをオンにします。ただし、それ以外のチェック ボックスはオンにしないでください。 左端の列のチェック ボックスをオンにすると、これらの列が構造に追加され、後で参照できるようになります。ただし、これらの列はモデルでは使用されません。 選択内容は以下のようになります。  
  
     ![ダイアログ ボックスの状態](../../2014/tutorials/media/tutorial-configassocmodel.gif "ダイアログ ボックスの状態")  
  
10. **[次へ]** をクリックします。  
  
11. [**列のコンテンツおよびデータ型の指定**] ページで、選択内容 (次の表を参照) を確認し、[**次へ**] をクリックします。  
  
    |[列]|コンテンツの種類|データ型|  
    |-------------|------------------|---------------|  
    |IncomeGroup|Discrete|テキスト|  
    |Order Number|Key|テキスト|  
    |リージョン|Discrete|テキスト|  
    |vAssocSeqLineItems|||  
    |モデル|Key|テキスト|  
  
12. [**テストセットの作成**] ページの [**テスト用データの割合**] オプションの既定値は30% です。 これを**0**に変更します。 **[次へ]** をクリックします。  
  
    > [!NOTE]  
    >  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] には、モデルの精度を測定するための別のチャートが用意されています。 ただし、リフト チャートや相互検証レポートなど、一部の種類の精度チャートは、分類および推定用に設計されています。 結合型の予測には使用できません。  
  
13. [**ウィザードの完了**] ページの [**マイニング構造名**] に`Association`「」と入力します。  
  
14. [**マイニングモデル名**] に`Association`「」と入力します。  
  
15. [ドリルスルーを**許可する**] オプションを選択し、[**完了**] をクリックします。  
  
     データマイニングデザイナーが開き、作成`Association`したマイニング構造が表示されます。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [「中級者向けデータマイニングチュートリアル &#40;のマーケットバスケットモデルの変更と処理&#41;](../../2014/tutorials/modify-process-market-basket-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [Microsoft アソシエーションアルゴリズム](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md)   
 [コンテンツの種類 (データ マイニング)](../../2014/analysis-services/data-mining/content-types-data-mining.md)  
  
  
