---
title: 予測 (中級者向けデータ マイニング チュートリアル) のソース ビューのデータを追加する |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2665040a-1291-4064-ba01-f458637dda57
caps.latest.revision: 25
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 3c355f9755e4dfd2ddd1fcc3f65e1b34857709ca
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312220"
---
# <a name="adding-a-data-source-view-for-forecasting-intermediate-data-mining-tutorial"></a>予測用のデータ ソース ビューの追加 (中級者向けデータ マイニング チュートリアル)
  この作業では、予測シナリオに使用するデータ ソース ビューを追加します。 予測モデルでは、時系列内のステップを識別するための列がデータに含まれている必要があります。 複数の系列のデータを分析する場合は、すべての系列が終了する日付または時間ステップが同じである必要があります。  
  
### <a name="to-add-a-data-source-view"></a>データ ソース ビューを追加するには  
  
1.  ソリューション エクスプ ローラーで右クリック**データ ソース ビュー**、し、**新しいデータ ソース ビュー**です。  
  
2.  **[データ ソース ビュー ウィザードへようこそ]** ページで **[次へ]** をクリックします。  
  
3.  **データ ソースの選択**] ページの [**リレーショナル データ ソース**、select、[!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]データ ソース。 **[次へ]** をクリックします。  
  
    > [!NOTE]  
    >  このデータ ソースがあるない場合は、内のデータ ソースを作成する手順を検索できます、 [Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md)です。  
  
4.  **[テーブルおよびビュー** ] ページで vTimeSeries (dbo) テーブルを選択して、データ ソース ビューに追加する右矢印をクリックします。  
  
5.  **[次へ]** をクリックします。  
  
6.  **ウィザードの完了** ページで、既定では、データ ソース ビューの名前は[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]します。 名前を変更**SalesByRegion**、順にクリック**完了**です。  
  
     データ ソース ビュー デザイナーが開き、 **SalesByRegion**データ ソース ビューが表示されます。  
  
## <a name="working-with-the-data-source-view"></a>データ ソース ビューの使用  
 データ ソース ビューを作成したら、次の方法でデータを検証できます。  
  
-   デザイナーで vTimeSeries テーブルを右クリックし **データの探索**をグリッドで選択したテーブルを開きます。  
  
-   をクリックして**サンプリング オプション**しを使用して、**データ探索オプション** ダイアログ ボックスをサンプリング メソッドを変更します。 をクリックして**更新**新しいオプション設定を使用してテーブルにデータを読み込みます。 たとえば、サンプルでは、出力または上位 n 行を選択する行の数を指定する可能性があります。  
  
-   VTimeSeries テーブルを右クリックし **プロパティ**テーブルに新しい名前を付けます。 データ ソース ビューから個々の列を選択して、列のプロパティを変更することもできます。  
  
-   データ ソース ビューのデザイン領域の任意の場所をクリックして、新しいクエリの作成と名前の割り当て、テーブル間のリレーションシップの作成、デザイン領域のレイアウトの変更を行います。  
  
-   テーブルを右クリックし **新しい名前付き計算**集計を含む派生の列を作成します。 また、このビューではデータ ソースから新しいテーブルやビューを追加することもできます。  
  
 次の作業では、時系列データについて学習し、時系列識別子として使用するのに最適な列を決定します。 時系列データのギャップを処理する方法についても学習します。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [タイム シリーズの要件についてモデル&#40;中級レベルのデータ マイニング チュートリアル&#41;](../../2014/tutorials/time-series-model-requirements-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [Microsoft タイム シリーズ アルゴリズム](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)  
  
  