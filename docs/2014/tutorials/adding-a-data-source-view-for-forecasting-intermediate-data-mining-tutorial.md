---
title: 予測用のデータソースビューの追加 (中級者向けデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 2665040a-1291-4064-ba01-f458637dda57
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: f60ea2b2a642cf9435ed8366c42e43abb927e426
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62823132"
---
# <a name="adding-a-data-source-view-for-forecasting-intermediate-data-mining-tutorial"></a>予測用のデータ ソース ビューの追加 (中級者向けデータ マイニング チュートリアル)
  この作業では、予測シナリオに使用するデータ ソース ビューを追加します。 予測モデルでは、時系列内のステップを識別するための列がデータに含まれている必要があります。 複数の系列のデータを分析する場合は、すべての系列が終了する日付または時間ステップが同じである必要があります。  
  
### <a name="to-add-a-data-source-view"></a>データ ソース ビューを追加するには  
  
1.  ソリューションエクスプローラーで、[**データソースビュー**] を右クリックし、[**新しいデータソースビュー**] をクリックします。  
  
2.  **[データ ソース ビュー ウィザードへようこそ]** ページで **[次へ]** をクリックします。  
  
3.  [**データソースの選択**] ページの [**リレーショナルデータソース**] で、 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]データソースを選択します。 **[次へ]** をクリックします。  
  
    > [!NOTE]  
    >  このデータソースがない場合は、「[基本的なデータマイニングチュートリアル](../../2014/tutorials/basic-data-mining-tutorial.md)」で、データソースを作成する手順を確認できます。  
  
4.  [**テーブルとビューの選択**] ページで、[vTimeSeries (dbo)] テーブルを選択し、右矢印をクリックしてデータソースビューに追加します。  
  
5.  **[次へ]** をクリックします。  
  
6.  既定では、[**ウィザードの完了**] ページにはという名前[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]のデータソースビューがあります。 名前を**Salesbyregion**に変更し、[**完了**] をクリックします。  
  
     データソースビューデザイナーが開き、 **Salesbyregion**データソースビューが表示されます。  
  
## <a name="working-with-the-data-source-view"></a>データ ソース ビューの使用  
 データ ソース ビューを作成したら、次の方法でデータを検証できます。  
  
-   デザイナーで vTimeSeries テーブルを右クリックし、[データの**探索**] を選択して、選択したテーブルをグリッドで開きます。  
  
-   [**サンプリングオプション**] をクリックし、[**データ探索オプション**] ダイアログボックスを使用してサンプリング方法を変更します。 [**最新**の情報に更新] をクリックして、新しいオプション設定を使用してテーブルにデータを読み込みます。 たとえば、サンプルに出力する行の数を指定したり、上位 n 行を選択したりできます。  
  
-   テーブル vTimeSeries を右クリックし、[**プロパティ**] を選択してテーブルに新しい名前を割り当てます。 データ ソース ビューから個々の列を選択して、列のプロパティを変更することもできます。  
  
-   データ ソース ビューのデザイン領域の任意の場所をクリックして、新しいクエリの作成と名前の割り当て、テーブル間のリレーションシップの作成、デザイン領域のレイアウトの変更を行います。  
  
-   テーブルを右クリックし、[**新しい名前付き計算**] を選択して、集計を含む派生列を作成します。 また、このビューではデータ ソースから新しいテーブルやビューを追加することもできます。  
  
 次の作業では、時系列データについて学習し、時系列識別子として使用するのに最適な列を決定します。 時系列データのギャップを処理する方法についても学習します。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [タイムシリーズモデルの要件について &#40;中級者向けデータマイニングチュートリアル&#41;](../../2014/tutorials/time-series-model-requirements-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [Microsoft Time Series アルゴリズム](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)  
  
  
