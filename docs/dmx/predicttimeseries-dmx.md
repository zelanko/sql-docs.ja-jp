---
title: "PredictTimeSeries (DMX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: PredictTimeSeries
dev_langs: DMX
helpviewer_keywords:
- time series algorithms [Analysis Services]
- time series [Analysis Services]
- EXTEND_MODEL_CASES parameter
- REPLACE_MODEL_CASES parameter
- PredictTimeSeries function
ms.assetid: 85c596be-a7f4-499b-8d36-7e67c2647b6c
caps.latest.revision: "56"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: eba719cb9cc1463b83e6e8aeda8b489d05fba53a
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="predicttimeseries-dmx"></a>PredictTimeSeries (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  予測される時系列データの将来値を返します。 時系列データは連続的なデータで、入れ子になったテーブルまたはケース テーブルに格納できます。 **PredictTimeSeries**関数が常に入れ子になったテーブルを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
PredictTimeSeries(<table column reference>)  
PredictTimeSeries(<table column reference>, n)  
PredictTimeSeries(<table column reference>, n-start, n-end)  
PredictTimeSeries(<scalar column reference>)  
PredictTimeSeries(<scalar column reference>, n)  
PredictTimeSeries(<scalar column reference>, n-start, n-end)  
PredictTimeSeries(<table column reference>, n, REPLACE_MODEL_CASES | EXTEND_MODEL_CASES) PREDICTION JOIN <source query>  
PredictTimeSeries(<table column reference>, n-start, n-end, REPLACE_MODEL_CASES | EXTEND_MODEL_CASES) PREDICTION JOIN <source query>  
PredictTimeSeries(<scalar column reference>, n, REPLACE_MODEL_CASES | EXTEND_MODEL_CASES) PREDICTION JOIN <source query>  
PredictTimeSeries(<scalar column reference>, n-start, n-end, REPLACE_MODEL_CASES | EXTEND_MODEL_CASES) PREDICTION JOIN <source query>  
```  
  
## <a name="arguments"></a>引数  
 *\<テーブルの列参照 >*、 *\<スカラー列以下のリファレンス情報 >*  
 予測する列の名前を指定します。 列にはスカラー データまたは表形式データを格納できます。  
  
 *n*  
 予測する次のステップの数を指定します。 値が指定されていない場合 *n* 、既定値は 1 です。  
  
 *n*0 にすることはできません。 1 つ以上の予測を作成しないと、関数はエラーを返します。  
  
 *開始 n、n エンド*  
 時系列ステップの範囲を指定します。  
  
 *n 開始*整数でなければなりませんおよび 0 にすることはできません。  
  
 *n エンド*よりも大きい整数である必要があります*n 開始*です。  
  
 *\<ソース クエリ >*  
 予測の作成に使用される外部データを定義します。  
  
 REPLACE_MODEL_CASES | EXTEND_MODEL_CASES  
 新しいデータの処理方法を指定します。  
  
 REPLACE_MODEL_CASES を指定すると、モデルのデータ ポイントが新しいデータに置き換えられます。 ただし、予測は既存のマイニング モデル内のパターンに基づきます。  
  
 EXTEND_MODEL_CASES を指定すると、新しいデータが元のトレーニング データセットに追加されます。 将来の予測は、新しいデータを使い果たした後にのみ複合データセットに基づいて作成されます。  
  
 これらの引数は、PREDICTION JOIN ステートメントを使用して新しいデータを追加する場合にのみ使用できます。 PREDICTION JOIN クエリで引数を指定しない場合の既定値は EXTEND_MODEL_CASES です。  
  
## <a name="return-type"></a>戻り値の型  
 A \<*テーブル式*>。  
  
## <a name="remarks"></a>解説  
 [!INCLUDE[msCoName](../includes/msconame-md.md)]ユーザーは、PREDICTION JOIN ステートメントを使用して新しいデータを追加する場合は、タイム シリーズ アルゴリズムには履歴予測はサポートされません。  
  
 PREDICTION JOIN では、予測処理は常に、元のトレーニング シリーズが終了した直後の時間ステップから開始されます。 これは、新しいデータを追加する場合にも当てはまります。 したがって、  *n* パラメーターと*n 開始*パラメーター値は 0 より大きい整数である必要があります。  
  
> [!NOTE]  
>  新しいデータの長さは、予測の開始位置には影響しません。 そのため、新しいデータを追加して新しい予測を作成する場合は、予測の開始位置を新しいデータの長さより大きい値に設定するか、予測の終了位置を新しいデータの長さだけ拡張するようにします。  
  
## <a name="examples"></a>使用例  
 次の例は、既存の時系列モデルに対する予測の作成方法を示しています。  
  
-   最初の例では、現在のモデルに基づいた予測を指定した数だけ作成する方法を示します。  
  
-   2 番目の例では、REPLACE_MODEL_CASES パラメーターを使用して、指定したモデル内のパターンを新しいデータセットに適用する方法を示します。  
  
-   3 番目の例では、EXTEND_MODEL_CASES パラメーターを使用して、マイニング モデルを新しいデータで更新する方法を示します。  
  
 タイム シリーズ モデルの操作に関する詳細については、データ マイニング チュートリアル」を参照してください。[レッスン 2: a Forecasting Scenario &#40;中級者向けデータ マイニング チュートリアル&#41; の構築](http://msdn.microsoft.com/library/9a988156-c900-4c22-97fa-f6b0c1aea9e2)と[時系列予測の DMX のチュートリアル](http://msdn.microsoft.com/library/38ea7c03-4754-4e71-896a-f68cc2c98ce2)です。  
  
> [!NOTE]  
>  モデルの結果は異なる場合があります。次の例の結果は、結果の形式を説明することのみを目的としています。  
  
### <a name="example-1-predicting-a-number-of-time-slices"></a>例 1: 特定の数のタイム スライスを予測する  
 次の例では、 **PredictTimeSeries**関数を予測を返し、次の 3 ステップし、結果をヨーロッパ、太平洋地域の M200 シリーズに制限します。 この特定のモデルでは、予測可能な属性が Quantity で使用する必要がありますので`[Quantity]`PredictTimeSeries 関数は、1 番目の引数として。  
  
```  
SELECT FLATTENED  
    [Forecasting].[Model Region],  
    PredictTimeSeries([Forecasting].[Quantity],3)AS t   
FROM  
    [Forecasting]  
WHERE [Model Region] = 'M200 Europe'  
OR [Model Region] = 'M200 Pacific'  
```  
  
 期待される結果:  
  
|Model Region|t.$TIME|t.Quantity|  
|------------------|-------------|----------------|  
|M200 Europe|7/25/2008 12:00:00 AM|121|  
|M200 Europe|8/25/2008 12:00:00 AM|142|  
|M200 Europe|9/25/2008 12:00:00 AM|152|  
|M200 Pacific|7/25/2008 12:00:00 AM|46|  
|M200 Pacific|8/25/2008 12:00:00 AM|44|  
|M200 Pacific|9/25/2008 12:00:00 AM|42|  
  
 この例では、結果を読みやすくするために FLATTENED キーワードが使用されています。  FLATTENED キーワードを使用せずに、階層的な行セットを返す場合、このクエリでは 2 つの列が返されます。 1 つ目の列には [ModelRegion] の値、2 つ目の列には入れ子になったテーブルが含まれます。入れ子になったテーブルには、予測されているタイム スライスを示す $TIME と予測された値を含む Quantity という 2 つの列が含まれています。  
  
### <a name="example-2-adding-new-data-and-using-replacemodelcases"></a>例 2: 新しいデータを追加して REPLACE_MODEL_CASES を使用する  
 特定の地域のデータが正しくないことが判明したので、モデル内のパターンを使用しながら新しいデータに合わせて予測を調整するとします。 または、別の地域の傾向の方が信頼性が高いことが判明したので、最も信頼性が高いモデルを異なる地域のデータに適用するとします。  
  
 このようなシナリオでは、REPLACE_MODEL_CASES パラメーターを使用して、履歴データとして使用する新しいデータセットを指定できます。 これにより、予測は指定したモデル内のパターンに基づくが、新しいデータ ポイントの末尾からスムーズに継続するようになります。 このシナリオの完全なチュートリアルについては、次を参照してください。[高度な時系列予測 &#40;中級者向けデータ マイニング チュートリアル&#41;](http://msdn.microsoft.com/library/b614ebdb-07ca-44af-a0ff-893364bd4b71)です。  
  
 次の PREDICTION JOIN クエリでは、データを置き換えて新しい予測を作成する構文を示します。 この例では、置き換え後のデータとして、Amount 列と Quantity 列の値を取得してそれぞれの値に 2 を乗算します。  
  
```  
SELECT [Forecasting].[Model Region],  
    PredictTimeSeries([Forecasting].[Quantity], 3, REPLACE_MODEL_CASES)   
FROM  
    [Forecasting]  
PREDICTION JOIN  
  OPENQUERY([Adventure Works DW Multidimensional 2012],  
    'SELECT [ModelRegion],   
    ([Quantity] * 2) as Quantity,  
    ([Amount] * 2) as Amount,  
      [ReportingDate]  
    FROM [dbo].vTimeSeries  
    WHERE ModelRegion = N''M200 Pacific''  
    ') AS t  
ON  
  [Forecasting].[Model Region] = t.[ Model Region] AND  
[Forecasting].[Reporting Date] = t.[ReportingDate] AND  
[Forecasting].[Quantity] = t.[Quantity] AND  
[Forecasting].[Amount] = t.[Amount]  
```  
  
 次の表は、予測の結果を比較します。  
  
 元の予測。  
  
||||  
|-|-|-|  
|M200 Pacific|7/25/2008 12:00:00 AM|46|  
|M200 Pacific|8/25/2008 12:00:00 AM|44|  
|M200 Pacific|9/25/2008 12:00:00 AM|42|  
  
 更新された予測は:  
  
||||  
|-|-|-|  
|M200 Pacific|7/25/2008 12:00:00 AM|91|  
|M200 Pacific|8/25/2008 12:00:00 AM|89|  
|M200 Pacific|9/25/2008 12:00:00 AM|84|  
  
### <a name="example-3-adding-new-data-and-using-extendmodelcases"></a>例 3: 新しいデータを追加して EXTEND_MODEL_CASES を使用する  
 使用例 3 を*EXTEND_MODEL_CASES* 、既存のデータ系列の末尾に追加された新しいデータを提供するオプションです。 既存のデータ ポイントを置き換えるのではなく、新しいデータをモデルに追加します。  
  
 次の例では、NATURAL PREDICTION JOIN の後の SELECT ステートメントで新しいデータを指定します。 この構文では複数行の新しい入力を指定できますが、それぞれの新しい入力行のタイムスタンプが一意である必要があります。  
  
```  
SELECT [Model Region],  
    PredictTimeSeries([Forecasting].[Quantity], 5, EXTEND_MODEL_CASES)   
FROM  
    [Forecasting]  
NATURAL PREDICTION JOIN  
    (SELECT  
        1 as [Reporting Date],  
        10 as [Quantity],  
        'M200 Europe' AS [Model Region]  
    UNION SELECT   
        2 as [Reporting Date],  
        15 as [Quantity],  
        'M200 Europe' AS [Model Region]  
) AS T  
WHERE ([Model Region] = 'M200 Europe'  
 OR [Model Region] = 'M200 Pacific')  
```  
  
 クエリを使用しているため、 *EXTEND_MODEL_CASES*オプション、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]は、予測のための次の操作を実行します。  
  
-   2 か月分の新しいデータをモデルに追加して、トレーニング ケースの合計サイズを大きくします。  
  
-   前のケース データの末尾から予測を開始します。 したがって、最初の 2 つの予測は、モデルに追加した実際の新しい売上データを表します。  
  
-   新しく拡張されたモデルに基づく残りの 3 つのタイム スライスの新しい予測を返します。  
  
 次の表は、例 2 のクエリの結果を示しています。 最初に返された M200 Europe の 2 つの値は、指定した新しい値とまったく同じです。 この動作は仕様であり、新しいデータの末尾から予測を開始するには、開始時刻と終了時刻のステップを指定する必要があります。 これを行う方法の例は、次を参照してください。[レッスン 5: 時系列モデルを拡張する](http://msdn.microsoft.com/library/7aad4946-c903-4e25-88b9-b087c20cb67d)です。  
  
 また、太平洋地域については、新しいデータを指定していません。 したがって、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] は、5 つすべてのタイム スライスの新しい予測を返します。  
  
 数量: M200 Europe です。 EXTEND_MODEL_CASES:  
  
|$TIME|Quantity|  
|-----------|--------------|  
|7/25/2008 0:00|10|  
|8/25/2008 0:00|15|  
|9/25/2008 0:00|72|  
|10/25/2008 0:00|69|  
|11/25/2008 0:00|68|  
  
 数量: M200 Pacific です。 EXTEND_MODEL_CASES:  
  
|$TIME|Quantity|  
|-----------|--------------|  
|7/25/2008 0:00|46|  
|8/25/2008 0:00|44|  
|9/25/2008 0:00|42|  
|10/25/2008 0:00|42|  
|11/25/2008 0:00|38|  
  
## <a name="example-4-returning-statistics-in-a-time-series-prediction"></a>例 4: 時系列予測の統計を返す  
 **PredictTimeSeries**関数がサポートされていません*INCLUDE_STATISTICS*をパラメーターとして。 ただし、次のクエリを使用して、時系列のクエリに対する予測の統計を返すことができます。 この方法は、テーブル列を入れ子にしているモデルにも使用できます。  
  
 この特定のモデルでは、予測可能な属性が Quantity で使用する必要がありますので`[Quantity]`PredictTimeSeries 関数は、1 番目の引数として。 モデルで別の予測可能な属性を使用する場合は、別の列名に置き換えることができます。  
  
```  
SELECT FLATTENED [Model Region],  
(SELECT   
     $Time,  
     [Quantity] as [PREDICTION],   
     PredictVariance([Quantity]) AS [VARIANCE],  
     PredictStdev([Quantity]) AS [STDEV]  
FROM  
      PredictTimeSeries([Quantity], 3) AS t  
) AS t  
FROM Forecasting  
WHERE [Model Region] = 'M200 Europe'  
OR [Model Region] = 'M200 North America'  
```  
  
 サンプルの結果 :  
  
|Model Region|t.$TIME|t.PREDICTION|t.VARIANCE|t.STDEV|  
|------------------|-------------|------------------|----------------|-------------|  
|M200 Europe|7/25/2008 12:00:00 AM|121|11.6050581415597|3.40661975300439|  
|M200 Europe|8/25/2008 12:00:00 AM|142|10.678201866621|3.26775180615374|  
|M200 Europe|9/25/2008 12:00:00 AM|152|9.86897842568614|3.14149302493037|  
|M200 North America|7/25/2008 12:00:00 AM|163|1.20434529288162|1.20434529288162|  
|M200 North America|8/25/2008 12:00:00 AM|178|1.65031343900634|1.65031343900634|  
|M200 North America|9/25/2008 12:00:00 AM|156|1.68969399185442|1.68969399185442|  
  
> [!NOTE]  
>  この例では、FLATTENED キーワードを使用して、結果を表形式でわかりやすくしました。ただし、プロバイダーで階層的な行セットがサポートされている場合は、FLATTENED キーワードを省略できます。 FLATTENED キーワードを省略した場合、クエリを返します 2 つの列を識別する値を含む最初の列、`[Model Region]`データ系列、および統計の入れ子になったテーブルを含む 2 番目の列です。  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能 &#40;DMX&#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [タイム シリーズ モデルのクエリ例](../analysis-services/data-mining/time-series-model-query-examples.md)   
 [予測 (& a) # #40; DMX &#41;](../dmx/predict-dmx.md)  
  
  
