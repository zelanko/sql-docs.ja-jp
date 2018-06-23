---
title: 時系列予測 (中級者向けデータ マイニング チュートリアル) の作成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb22cffa-ac99-4d34-ac4a-9c93068e33e8
caps.latest.revision: 28
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 999dcdec7c6a30617c9c9e04512da26ddebfdcc3
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312950"
---
# <a name="creating-time-series-predictions-intermediate-data-mining-tutorial"></a>時系列予測の作成 (中級者向けデータ マイニング チュートリアル)
  このレッスンの前の作業では、時系列モデルを作成し、結果を検証しました。 既定では、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] によって常に時系列モデルの 5 つの予測のセットが作成され、予測された値が予測グラフの一部として表示されます。 ただし、データ マイニング拡張機能 (DMX) の予測クエリを作成することによって、予測を作成することもできます。  
  
 この作業では、ビューアーに表示された予測と同じ予測を生成する予測クエリを作成します。 「基本的なデータ マイニング チュートリアル」のレッスンが完了し、予測クエリ ビルダーの使用方法について理解していることを前提とします。 ここでは、時系列モデルに固有のクエリを作成する方法を学習します。  
  
## <a name="creating-time-series-predictions"></a>時系列予測の作成  
 通常、予測クエリを作成するには、まず、マイニング モデルと入力テーブルを選択します。 ただし、時系列モデルでは、通常の予測では必要な追加の入力が必要ありません。 したがって、モデルにデータを追加したり、データを置き換えたりする場合以外は、予測を行うときに新しいデータ ソースを指定する必要はありません。  
  
 このレッスンでは、予測期間の値を指定する必要があります。 系列名を指定して、製品と地域の特定の組み合わせに対する予測を取得できます。  
  
#### <a name="to-select-a-model-and-input-table"></a>モデルと入力テーブルを選択するには  
  
1.  **マイニング モデル予測**、データ マイニング デザイナーのタブで、**マイニング モデルの**ボックスで、クリックして**モデルの選択**です。  
  
2.  **マイニング モデルの選択** ダイアログ ボックスで、Forecasting 構造を展開し、選択、 **Forecasting**クリックして、一覧からモデル**OK**です。  
  
3.  無視する、**入力テーブルの選択**ボックス。  
  
    > [!NOTE]  
    >  時系列モデルでは、クロス予測を実行する場合以外は、個別の入力を指定する必要はありません。  
  
4.  **ソース**上のグリッド内の列、**マイニング モデル予測** タブで、最初の空白行のセルをクリックしを選択し、 **Forecasting マイニング モデル**です。  
  
5.  **フィールド**列をオン**Model Region**です。  
  
     この操作により、予測クエリに系列の識別子が追加され、予測が適用されるモデルと地域の組み合わせが指定されます。  
  
6.  次の空白行をクリックして、**ソース**列、および選択**予測関数**です。  
  
7.  **フィールド**列をオン**PredictTimeSeries**です。  
  
    > [!NOTE]  
    >  使用することも、`Predict`タイム シリーズ モデルで機能します。 ただし、既定では、Predict 関数を使用すると、系列ごとに 1 つしか予測が作成されません。 したがって、複数の予測期間を指定する必要がありますを使用する、 **PredictTimeSeries**関数。  
  
8.  **マイニング モデル** ウィンドウで、マイニング モデル列を選択して**量。** 金額をドラッグして、**条件と引数**のボックス、 **PredictTimeSeries**前に追加する関数。  
  
9. クリックして、**条件と引数**ボックス、および、コンマを続けて入力**5**フィールド名の後です。  
  
     内のテキスト、**条件と引数**ボックスは、次が表示されます。  
  
     `[Forecasting].[Amount],5`  
  
10. **エイリアス**列に「`PredictAmount`です。  
  
11. 次の空白行をクリックして、**ソース**列、および選択**予測関数**もう一度です。  
  
12. **フィールド**列をオン**PredictTimeSeries**です。  
  
13. **マイニング モデルの** ウィンドウでは、数量、列を選択しにドラッグ、**条件と引数**、2 番目のボックス**PredictTimeSeries**関数。  
  
14. クリックして、**条件と引数**ボックス、および、コンマを続けて入力**5**フィールド名の後です。  
  
     内のテキスト、**条件と引数**ボックスは、次が表示されます。  
  
     `[Forecasting].[ Quantity],5`  
  
15. **エイリアス**列に「`PredictQuantity`です。  
  
16. をクリックして**クエリ結果ビューに切り替える**です。  
  
     クエリの結果が表形式で表示されます。  
  
 クエリ ビルダーで 3 種類の異なる結果を作成したことに注意してください。列の値を使用した結果が 1 つと、予測関数から予測値を取得した結果が 2 つです。 したがって、クエリの結果には 3 つの異なる列が含まれます。 最初の列には、製品と地域の組み合わせの一覧が格納されます。 2 番目と 3 番目の列には、それぞれ、予測結果の入れ子になったテーブルが格納されます。 入れ子になった各テーブルには、次の表のような時間ステップと予測された値が含まれます。  
  
 例の結果 (金額は小数点以下 2 桁に切り捨てられます):  
  
 **M200 Europe PredictAmount**  
  
|$TIME|Amount|  
|-----------|------------|  
|2008 年 7 月 25 日|99978.00|  
|8/25/2008|145575.07|  
|9/25/2008|116835.19|  
|10/25/2008|116537.38|  
|2008 11 月 25 日|107760.55|  
  
 **M200 Europe PredictQuantity**  
  
|$TIME|Quantity|  
|-----------|--------------|  
|2008 年 7 月 25 日|52|  
|8/25/2008|67|  
|9/25/2008|58|  
|10/25/2008|57|  
|2008 11 月 25 日|54|  
  
 **M200 North America - PredictAmount**  
  
|$TIME|Amount|  
|-----------|------------|  
|2008 年 7 月 25 日|348533.93|  
|8/25/2008|340097.98|  
|9/25/2008|257986.19|  
|10/25/2008|374658.24|  
|2008 11 月 25 日|379241.44|  
  
 **M200 North America - PredictQuantity**  
  
|$TIME|Quantity|  
|-----------|--------------|  
|2008 年 7 月 25 日|272|  
|8/25/2008|152|  
|9/25/2008|250|  
|10/25/2008|181|  
|2008 11 月 25 日|290|  
  
> [!WARNING]  
>  サンプル データベースで使用されている日付は、このリリース用に更新されています。 以前のバージョンのサンプル データを使用している場合は、異なる結果が表示されることがあります。  
  
## <a name="saving-the-prediction-results"></a>予測結果の保存  
 いくつかの方法で予測結果を使用することができます。 結果をフラット化し、結果ビューのデータをコピーして、Excel ワークシートなどのファイルに貼り付けることができます。  
  
 結果を保存するプロセスを簡単にするため、データ マイニング デザイナーではデータをデータ ソース ビューに保存する機能も提供されています。 結果をデータ ソース ビューに保存する機能は、[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] だけで使用できます。 結果はフラット化された形式でのみ格納できます。  
  
#### <a name="to-flatten-the-results-in-the-results-pane"></a>結果ペインで結果をフラット化するには  
  
1.  予測クエリ ビルダーで、をクリックして**クエリ デザイン ビューに切り替えます**です。  
  
     ビューが切り替わり、DMX クエリ テキストを手動で編集できるようになります。  
  
2.  `FLATTENED` キーワードの後に、`SELECT` キーワードを入力します。 最終的なクエリ テキストは次のようになります。  
  
    ```  
    SELECT FLATTENED  
      [Forecasting].[Model Region],  
      (PredictTimeSeries([Forecasting].[Amount],5)) as [PredictAmount],  
      (PredictTimeSeries([Forecasting].[Quantity],5)) as [PredictQuantity]  
    FROM  
      [Forecasting]  
    ```  
  
3.  必要に応じて、次の例のように、結果を制限するための句を入力できます。  
  
    ```  
    SELECT FLATTENED  
      [Forecasting].[Model Region],  
      (PredictTimeSeries([Forecasting].[Amount],5)) as [PredictAmount],  
      (PredictTimeSeries([Forecasting].[Quantity],5)) as [PredictQuantity]  
    FROM  
      [Forecasting]  
    WHERE [Forecasting].[Model Region] = 'M200 North America'   
    OR [Forecasting].[Model Region] = 'M200 Europe'  
  
    ```  
  
4.  をクリックして**クエリ結果ビューに切り替える**です。  
  
#### <a name="to-export-prediction-query-results"></a>予測クエリの結果をエクスポートするには  
  
1.  をクリックして**クエリ結果の保存**です。  
  
2.  **保存のデータ マイニング クエリの結果**] ダイアログ ボックスの**データ ソース**[[!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]です。 データを別のリレーショナル データベースに保存する場合は、データ ソースを作成することもできます。  
  
3.  **テーブル名**列に「などの新しい一時的なテーブル名、 **Test Predictions**です。  
  
4.  **[保存]** をクリックします。  
  
    > [!NOTE]  
    >  作成したテーブルを表示するには、データを保存したインスタンスのデータベース エンジンに対する接続を作成し、クエリを作成します。  
  
## <a name="conclusion"></a>まとめ  
 基本的な時系列モデルを作成し、予測を解釈し、予測を作成する方法について学習しました。  
  
 このチュートリアルの残りのタスクは省略可能であり、高度な時系列予測について説明します。 さらにチュートリアルを続けると、モデルに新しいデータを追加し、拡張系列で予測を作成する方法について学習できます。 また、モデルの傾向を使用し、データを新しい系列に置き換えることで、クロス予測を実行する方法についても学習します。  
  
## <a name="next-lesson"></a>次のレッスン  
 [時系列予測での高度な&#40;中級レベルのデータ マイニング チュートリアル&#41;](../../2014/tutorials/advanced-time-series-predictions-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [タイム シリーズ モデルのクエリ例](../../2014/analysis-services/data-mining/time-series-model-query-examples.md)  
  
  