---
title: タイム シリーズの要件について (中級者向けデータ マイニング チュートリアル) をモデル化 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 1ce2b3e3-108a-4f7e-985f-a20b816d0da7
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 5b3438e832f28329cb0fec764d3a4846bae18ede
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63043115"
---
# <a name="understanding-the-requirements-for-a-time-series-model-intermediate-data-mining-tutorial"></a>時系列モデルの要件について (中級者向けデータ マイニング チュートリアル)
  予測モデルで使用するデータを準備する際に、時系列内のステップの識別に使用できる列がデータに含まれていることを確認する必要があります。 その列が `Key Time` 列として指定されて キーになるため、この列には一意の数値が含まれている必要があります。  
  
 `Key Time` 列の右の単位の選択は、分析を行う上で重要な要素になります。 たとえば、売上データを 1 分ごとに更新するとします。 このとき、必ずしも時系列の単位として分を使用する必要はなく、売上データを日、週、または月ごとにロール アップする方が重要です。 どの時間単位を使用すればよいかわからない場合は、各集計のための新しいデータ ソース ビューを作成し、関連モデルを構築することで、集計の各レベルで異なる傾向があるかどうかを確認できます。  
  
 このチュートリアルでは、売上データについてはトランザクション売上データベースで毎日収集しますが、データ マイニングのデータについては、事前にビューを使用して月単位で集計します。  
  
 分析を行うときは、データのギャップをできるだけ少なくすることも重要です。 複数の系列のデータを分析する場合は、すべての系列の開始日と終了日をできるだけ同じにするようにしてください。 データにギャップがある場合でも、系列の開始時点と終了時点以外のものであれば、MISSING_VALUE_SUBSTITUTION パラメーターを使用して系列を埋めることができます。 また、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] には、不足データを平均や定数などの値で置き換えるためのオプションもいくつか用意されています。  
  
> [!WARNING]  
>  以前のバージョンのデータ ソース ビュー デザイナーに付属していたピボットグラフおよびピボットテーブルのツールは廃止されました。 時系列データのギャップを事前に特定するときは、[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] に付属の Data Profiler などのツールを使用することをお勧めします。  
  
### <a name="to-identify-the-time-key-for-the-forecasting-model"></a>予測モデルの時間キーを特定するには  
  
1.  ウィンドウで、 **SalesByRegion.dsv [Design]**、vTimeSeries テーブルを右クリックし、**データの探索**します。  
  
     新しいタブが開き、「 **vTimeSeries テーブルの探索**します。  
  
2.  **テーブル**タブで、TimeIndex と Reporting Date 列で使用されているデータを確認します。  
  
     どちらの列も一意の値を持つシーケンスであり、時系列キーとして使用できますが、列によってデータ型が異なります。 Microsoft タイム シリーズ アルゴリズムでは、`datetime` データ型は必要なく、値が一意であり、順序付けられていることのみが必要とされます。 したがって、どちらの列も予測モデルの時間キーとして使用できます。  
  
3.  データ ソース ビュー デザイン画面で、Reporting Date] 列を選択し、[**プロパティ**します。 次に、TimeIndex 列をクリックし、選択**プロパティ**します。  
  
     TimeIndex フィールドは、Reporting Date フィールドでは、System.DateTime の入力データは、System.Int32 データ型を持ちます。 多くのデータ ウェアハウスでは、インデックス作成のパフォーマンスを高めるために、日付/時刻の値が整数に変換され、その整数列がキーとして使用されます。 ただし、この列を使用した場合、Microsoft タイム シリーズ アルゴリズムでは、201014、201014 などの将来の値を使用して予測が行われます。 売上データの予測をカレンダー日付を表現するため、Reporting Date 列は一意の系列 id として使用します。  
  
### <a name="to-set-the-key-in-the-data-source-view"></a>データ ソース ビューのキーを設定するには  
  
1.  ウィンドウで**SalesByRegion.dsv**、vTimeSeries テーブルを選択します。  
  
2.  レポートの Date 列を右クリックして**論理主キーの設定**します。  
  
## <a name="handling-missing-data-optional"></a>不足データの処理 (オプション)  
 系列に不足データがあると、モデルを処理しようとする際にエラーが表示されます。 不足データには、複数の方法で対処することができます。  
  
-   Analysis Services で、平均を計算するか、前の値を使用して、不足した値を埋めることができます。 この操作を行うには、マイニング モデルに MISSING_VALUE_SUBSTITUTION パラメーターを設定します。 このパラメーターの詳細については、次を参照してください。 [Microsoft タイム シリーズ アルゴリズム テクニカル リファレンス](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)します。 既存のマイニング モデルのパラメーターを変更する方法については、次を参照してください。[アルゴリズム パラメーターの変更の表示または](../../2014/analysis-services/data-mining/view-or-change-algorithm-parameters.md)します。  
  
-   データ ソースを変更するか、基になるビューをフィルター処理することで、不規則な系列を除外するか、値を置き換えることができます。 この操作はリレーショナル データ ソースで行うことができます。または、カスタムの名前付きクエリまたは名前付き計算を作成することでデータ ソース ビューを変更できます。 詳細については、 [「多次元モデルのデータ ソース ビュー」](../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)を参照してください。 このレッスンの後半の作業で、名前付きクエリとカスタム計算の両方を作成する例を示します。  
  
 このシナリオでは、ある系列の開始時点でデータの一部が不足しています。具体的には、T1000 製品ラインの 2007 年 7 月までのデータがありません。 その点を除けば、すべての系列は同じ日に終了し、不足値はありません。  
  
 Microsoft タイム シリーズ アルゴリズムの要件は、1 つのモデルに含めることのすべての系列が存在するように同じ**終了**ポイントします。 T1000 モデルの自転車は 2007 年に売り出されたため、この系列のデータは他のモデルの自転車よりも開始時点が後になりますが、系列の終了日が同じことにより、データは使用できます。  
  
#### <a name="to-close-the-data-source-view-designer"></a>データ ソース ビュー デザイナーを閉じるには  
  
-   タブを右クリックして**vTimeSeries テーブルの探索**、選択と**閉じる**します。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [Forecasting 構造およびモデルの作成&#40;中級者向けデータ マイニング チュートリアル&#41;](../../2014/tutorials/creating-a-forecasting-structure-and-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [Microsoft タイム シリーズ アルゴリズム](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)  
  
  
