---
title: Analysis Services テーブルモデルの計算グループ |Microsoft Docs
ms.date: 07/24/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: af63f41555a021fc720c7d1e15778265fe7de500
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419528"
---
# <a name="calculation-groups-preview"></a>計算グループ (プレビュー)
 
[!INCLUDE[ssas-appliesto-sql2019-aas](../../includes/ssas-appliesto-sql2019-aas.md)]

計算グループを使用すると、共通メジャー式を*計算項目*としてグループ化することで、冗長なメジャーの数を大幅に削減できます。 計算グループは、1470以上の[互換性レベル](compatibility-level-for-tabular-models-in-analysis-services.md)で Azure Analysis Services および SQL Server Analysis Services 2019 の表形式モデルでサポートされています。 互換性レベルが1470のモデルは、現在**プレビュー**の段階にあります。  

この記事では、以下について説明します。 

> [!div class="checklist"]
> * 利点 
> * 計算グループのしくみ
> * 動的書式指定文字列
> * 順番
> * 優先順位
> * ツール
> * 制限事項



## <a name="benefits"></a>利点

計算グループは、同じ計算 (タイムインテリジェンス計算で最も一般的) を使用して冗長なメジャーが急増する可能性がある複雑なモデルの問題に対処します。 たとえば、販売アナリストは、月別 (MTD)、四半期累計 (QTD)、年度累計 (YTD)、前年の年度累計 (.PY) などの売上合計と注文を表示しようとしています。これについても同様です。 データモデルでは、計算ごとに個別のメジャーを作成する必要があります。これにより、多数のメジャーが発生する可能性があります。 ユーザーにとって、これは、メジャーをいくつでも並べ替え、個別にレポートに適用する必要があることを意味します。 

まず、Power BI などのレポートツールで計算グループがユーザーにどのように表示されるかを見てみましょう。 次に、計算グループの構成と、モデルでの作成方法について説明します。

計算グループは、レポート クライアントでは 1 つの列を含むテーブルとして示されます。 列は一般的な列またはディメンションとは同じではなく、再利用可能な1つ以上の計算、または視覚化の値フィルターに既に追加されているメジャーに適用できる*計算項目*を表します。

次のアニメーションでは、ユーザーが2012年と2013年の売上データを分析しています。 計算グループを適用する前に、共通の基本メジャー **sales**によって、毎月の総売上の合計が計算されます。 次に、タイムインテリジェンス計算を適用して、月累計、四半期累計、年累計などの売上合計を取得します。 計算グループがない場合、ユーザーは個々のタイムインテリジェンスメジャーを選択する必要があります。

計算グループの場合、この例では、**タイムインテリジェンス**という名前の例では、ユーザーが**時間の計算**項目を **[列]** フィルター領域にドラッグすると、各計算項目が個別の列として表示されます。 各行の値は、基本メジャー **Sales**から計算されます。  

![Power BI に適用される計算グループ](media/calculation-groups/calc-groups-pbi.gif)


計算グループは、**明示的**な DAX メジャーと連携します。 この例では、 **Sales**はモデルに既に作成されている明示的なメジャーです。 計算グループは、暗黙的な DAX メジャーでは機能しません。 たとえば Power BI では、明示的なメジャーを作成せずに、ユーザーがビジュアルに列をドラッグして集計値を表示すると、暗黙的なメジャーが作成されます。 現時点では、Power BI は、インライン DAX 計算として記述された暗黙的なメジャーに対して DAX を生成します。つまり、暗黙的なメジャーは計算グループでは使用できません。 表形式オブジェクトモデル (TOM) に表示される新しいモデルプロパティは、 **DiscourageImplicitMeasures**に導入されました。 現在、計算グループを作成するには、このプロパティを**true**に設定する必要があります。 True に設定すると、Live Connect モードの Power BI Desktop により、暗黙的なメジャーの作成が無効になります。

## <a name="how-they-work"></a>しくみ

これで、計算グループがユーザーにどのように役立つかを確認できました。次は、示されているタイムインテリジェンス計算グループの例の作成方法を見てみましょう。

詳細に進む前に、計算グループ専用の新しい DAX 関数をいくつか紹介します。 

[Selectedmeasure](https://docs.microsoft.com/dax/selectedmeasure-function-dax) -現在コンテキスト内にあるメジャーを参照するために、計算項目の式によって使用されます。 この例では、Sales メジャーです。

[SELECTEDMEASURENAME](https://docs.microsoft.com/dax/selectedmeasurename-function-dax) -名前によってコンテキスト内のメジャーを決定するために、計算項目の式によって使用されます。

[Isselectedmeasure](https://docs.microsoft.com/dax/isselectedmeasure-function-dax) -メジャーの一覧でコンテキスト内のメジャーが指定されているかどうかを判断するために、計算項目の式によって使用されます。

[Selectedmeasureformatstring](https://docs.microsoft.com/dax/selectedmeasureformatstring-function-dax) -コンテキスト内のメジャーの書式文字列を取得するために、計算項目の式によって使用されます。

### <a name="time-intelligence-example"></a>タイムインテリジェンスの例

テーブル名-**タイムインテリジェンス**   
列名-**時間の計算**   
優先順位- **20**   

#### <a name="time-intelligence-calculation-items"></a>タイムインテリジェンス計算項目

**現在**

```dax
SELECTEDMEASURE()
```

**MTD**

```dax
CALCULATE(SELECTEDMEASURE(), DATESMTD(DimDate[Date]))
```

**QTD**

```dax
CALCULATE(SELECTEDMEASURE(), DATESQTD(DimDate[Date]))
```

**今日**

```dax
CALCULATE(SELECTEDMEASURE(), DATESYTD(DimDate[Date]))
```

**.PY**

```dax
CALCULATE(SELECTEDMEASURE(), SAMEPERIODLASTYEAR(DimDate[Date]))
```

**.PY MTD**

```dax
CALCULATE(
    SELECTEDMEASURE(),
    SAMEPERIODLASTYEAR(DimDate[Date]),
    'Time Intelligence'[Time Calculation] = "MTD"
)
```

**.PY QTD**

```dax
CALCULATE(
    SELECTEDMEASURE(),
    SAMEPERIODLASTYEAR(DimDate[Date]),
    'Time Intelligence'[Time Calculation] = "QTD"
)
```

**.PY YTD**

```dax
CALCULATE(
    SELECTEDMEASURE(),
    SAMEPERIODLASTYEAR(DimDate[Date]),
    'Time Intelligence'[Time Calculation] = "YTD"
)
```

**前年比**

```dax
SELECTEDMEASURE() –
CALCULATE(
    SELECTEDMEASURE(),
    'Time Intelligence'[Time Calculation] = "PY"
)
```

**前年比**

```dax
DIVIDE(
    CALCULATE(
        SELECTEDMEASURE(),
        'Time Intelligence'[Time Calculation]="YOY"
    ),
    CALCULATE(
        SELECTEDMEASURE(),
        'Time Intelligence'[Time Calculation]="PY"
    ),
)
```

この計算グループをテストするには、SSMS またはオープンソースの[Dax Studio](http://daxstudio.org/)で dax クエリを実行します。 このクエリの例では、"ヨーク y%" は省略されています。

#### <a name="time-intelligence-query"></a>タイムインテリジェンスクエリ

```dax
EVALUATE
CALCULATETABLE (
    SUMMARIZECOLUMNS (
        DimDate[CalendarYear],
        DimDate[EnglishMonthName],
        "Current", CALCULATE ( [Sales], 'Time Intelligence'[Time Calculation] = "Current" ),
        "QTD",     CALCULATE ( [Sales], 'Time Intelligence'[Time Calculation] = "QTD" ),
        "YTD",     CALCULATE ( [Sales], 'Time Intelligence'[Time Calculation] = "YTD" ),
        "PY",      CALCULATE ( [Sales], 'Time Intelligence'[Time Calculation] = "PY" ),
        "PY QTD",  CALCULATE ( [Sales], 'Time Intelligence'[Time Calculation] = "PY QTD" ),
        "PY YTD",  CALCULATE ( [Sales], 'Time Intelligence'[Time Calculation] = "PY YTD" )
    ),
    DimDate[CalendarYear] IN { 2012, 2013 }
)
```

#### <a name="time-intelligence-query-return"></a>タイムインテリジェンスクエリの戻り値

返されるテーブルには、適用された各計算項目の計算が表示されます。 たとえば、2012年3月の QTD が、2012年1月、2月、および3月の合計であることがわかります。

![クエリの戻り値](media/calculation-groups/calc-groups-query-return.png)


## <a name="dynamic-format-strings"></a>動的書式指定文字列

計算グループを含む*動的書式指定文字列*を使用すると、書式指定文字列の条件付きアプリケーションで、文字列を返すことなく、メジャーを使用できます。

表形式モデルでは、DAX の[FORMAT](https://docs.microsoft.com/dax/format-function-dax)関数を使用したメジャーの動的な書式設定がサポートされています。 ただし、FORMAT 関数には文字列を返すという欠点があり、それ以外の場合は数値になるようなメジャーを強制的に文字列として返すことができます。 これにはいくつかの制限があります。たとえば、グラフのように数値に応じてほとんどの Power BI ビジュアルを使用しない場合などです。

### <a name="dynamic-format-strings-for-time-intelligence"></a>タイムインテリジェンスの動的書式指定文字列

上に示したタイムインテリジェンスの例を見ると、すべての計算項目 (末尾の**y%** を除く) は、現在のメジャーの形式をコンテキスト内で使用する必要があります。 たとえば、売上ベースメジャーで計算された**YTD**は currency である必要があります。 これが Orders ベースメジャーのような計算グループである場合、形式は数値になります。 ただし、基本メジャーの形式に関係なく、"_ **y%** " はパーセントである必要があります。

この**場合、書式**文字列式プロパティを**0.00%;-0.00%; 0.00%** に設定することにより、書式設定文字列をオーバーライドできます。 書式文字列式のプロパティの詳細については、「 [MDX セルプロパティ-書式指定文字列の内容](../multidimensional-models/mdx/mdx-cell-properties-format-string-contents.md#numeric-values)」を参照してください。

Power BI のこのマトリックスビジュアルでは、**現在の売上高** と 現在の注文 の**順**に表示されます。各基本メジャーの書式指定文字列は保持されます。 一方、 **Sales**と**Orders y%** は、書式設定文字列をオーバーライドして*パーセンテージ*形式を使用します。

![マトリックスビジュアルのタイムインテリジェンス](media/calculation-groups/calc-groups-dynamicstring-timeintel.png)

### <a name="dynamic-format-strings-for-currency-conversion"></a>通貨換算用の動的書式指定文字列

動的書式指定文字列を使用すると、簡単に通貨を変換できます。 次の Adventure Works データモデルについて考えてみましょう。 このモデルは、[変換型](../currency-conversions-analysis-services.md#conversion-types)によって定義された*1 対多*の通貨換算用にモデル化されています。

![表形式モデルでの通貨レート](media/calculation-groups/calc-groups-currency-conversion.png)

**FormatString**列が**DimCurrency**テーブルに追加され、それぞれの通貨の書式文字列が設定されます。

![書式指定文字列の列](media/calculation-groups/calc-groups-formatstringcolumn.png)

この例では、次の計算グループがとして定義されます。

### <a name="currency-conversion-example"></a>通貨換算の例

テーブル名-**通貨換算**   
列名-**変換の計算**   
優先順位- **5**   

#### <a name="calculation-items-for-currency-conversion"></a>通貨換算の計算項目

**変換なし**

```dax
SELECTEDMEASURE()
```

**換算された通貨**

```dax
IF(
    //Check one currency in context & not US Dollar, which is the pivot currency:
    SELECTEDVALUE( DimCurrency[CurrencyName], "US Dollar" ) = "US Dollar",
    SELECTEDMEASURE(),
    SUMX(
        VALUES(DimDate[Date]),
        CALCULATE( DIVIDE( SELECTEDMEASURE(), MAX(FactCurrencyRate[EndOfDayRate]) ) )
    )
)
```

書式文字列式

```dax
SELECTEDVALUE(
    DimCurrency[FormatString],
    SELECTEDMEASUREFORMATSTRING()
)
```
書式指定文字列式は、スカラー文字列を返す必要があります。 フィルターコンテキストに複数の通貨がある場合は、新しい[Selectedmeasureformatstring](https://docs.microsoft.com/dax/selectedmeasureformatstring-function-dax)関数を使用してベースメジャー形式の文字列に戻ります。

次のアニメーションは、レポートの**Sales**メジャーの動的形式通貨換算を示しています。

![適用される通貨変換の動的書式指定文字列](media/calculation-groups/calc-groups-dynamic-format-string.gif)

## <a name="precedence"></a>優先順位

優先順位は、計算グループに対して定義されたプロパティです。 複数の計算グループがある場合の評価の順序を指定します。 数値が大きいほど優先順位が高くなります。つまり、優先順位の低い計算グループの前に評価されます。

この例では、上のタイムインテリジェンスの例と同じモデルを使用しますが、**平均**計算グループも追加します。 平均計算グループには、日付フィルターコンテキストを変更しないという点で、従来のタイムインテリジェンスに依存しない平均計算が含まれています。これにより、平均計算が適用されます。

この例では、1日あたりの平均計算が定義されています。 石油およびガスのアプリケーションでは、1日あたりの平均樽のような計算が一般的です。 その他の一般的なビジネス例としては、小売店での店舗売上平均などがあります。

このような計算は、タイムインテリジェンス計算とは無関係に計算されますが、それらを結合する必要がある場合もあります。 たとえば、年の最初から現在の日付までの1日の石油率を表示するために、1日の石油の樽のバレルを表示することができます。 このシナリオでは、計算項目に優先順位を設定する必要があります。

### <a name="averages-example"></a>平均の例

テーブル名は**平均**です。   
列名は**平均計算**です。   
優先順位は**10**です。   

#### <a name="calculation-items-for-averages"></a>平均の計算項目

**平均なし**

```dax
SELECTEDMEASURE()
```

**1日あたりの平均**

```dax
DIVIDE(SELECTEDMEASURE(), COUNTROWS(DimDate))
```

DAX クエリと返されるテーブルの例を次に示します。

#### <a name="averages-query"></a>平均クエリ

```dax
EVALUATE
    CALCULATETABLE (
        SUMMARIZECOLUMNS (
        DimDate[CalendarYear],
        DimDate[EnglishMonthName],
        "Sales", CALCULATE (
            [Sales],
            'Time Intelligence'[Time Calculation] = "Current",
            'Averages'[Average Calculation] = "No Average"
        ),
        "YTD", CALCULATE (
            [Sales],
            'Time Intelligence'[Time Calculation] = "YTD",
            'Averages'[Average Calculation] = "No Average"
        ),
        "Daily Average", CALCULATE (
            [Sales],
            'Time Intelligence'[Time Calculation] = "Current",
            'Averages'[Average Calculation] = "Daily Average"
        ),
        "YTD Daily Average", CALCULATE (
            [Sales],
            'Time Intelligence'[Time Calculation] = "YTD",
            'Averages'[Average Calculation] = "Daily Average"
        )
    ),
    DimDate[CalendarYear] = 2012
)
```

#### <a name="averages-query-return"></a>平均クエリの戻り値

![クエリの戻り値](media/calculation-groups/calc-groups-ytd-daily-avg.png)

次の表は、2012年3月の値がどのように計算されるかを示しています。


|列名  |計算 |
|---------|---------|
|YTD     |    1月、2月、3月2012の売上の合計<br />= 495364 + 506994 + 373483     |
|1日あたりの平均    |     3月の日数で割った3月2012の売上<br />= 373483/31       |
|YTD 日次平均     | 1月、2月、3月の日数で割った2012年3月の YTD<br />= 1375841/(31 + 29 + 31)       |

次に、YTD 計算項目の定義を示します。これは、優先順位が**20**の場合に適用されます。

```dax
CALCULATE(SELECTEDMEASURE(), DATESYTD(DimDate[Date]))
```

1日あたりの平均は**10**の優先順位で適用されます。

```dax
DIVIDE(SELECTEDMEASURE(), COUNTROWS(DimDate))
```

タイムインテリジェンス計算グループの優先順位は平均計算グループよりも高いため、可能な限り広く適用されます。 YTD の1日あたりの平均計算では、1日の平均計算の分子と分母 (日数の数) の両方に YTD が適用されます。

これは、次の式と同じです。

```dax
CALCULATE(DIVIDE(SELECTEDMEASURE(), COUNTROWS(DimDate)), DATESYTD(DimDate[Date]))
```

次の式ではない:

```dax
DIVIDE(CALCULATE(SELECTEDMEASURE(), DATESYTD(DimDate[Date])), COUNTROWS(DimDate)))
```

## <a name="sideways-recursion"></a>横向きの再帰

上のタイムインテリジェンスの例では、一部の計算項目は同じ計算グループ内の他の項目を参照しています。 これは、*横向きの再帰*と呼ばれます。 たとえば、**ヨーク y%** は、.py**の両方**を参照します。

```dax
DIVIDE(
    CALCULATE(
        SELECTEDMEASURE(),
        'Time Intelligence'[Time Calculation]="YOY"
    ),
    CALCULATE(
        SELECTEDMEASURE(),
        'Time Intelligence'[Time Calculation]="PY"
    ),
)
```

この場合、両方の式は異なる calculate ステートメントを使用しているため、個別に評価されます。 その他の種類の再帰はサポートされていません。

## <a name="single-calculation-item-in-filter-context"></a>フィルターコンテキストの単一の計算項目

タイムインテリジェンスの例では、 **.PY YTD**計算項目に1つの calculate 式があります。

```dax
CALCULATE(
    SELECTEDMEASURE(),
    SAMEPERIODLASTYEAR(DimDate[Date]),
    'Time Intelligence'[Time Calculation] = "YTD"
)
```

CALCULATE () 関数の YTD 引数は、YTD 計算項目で既に定義されているロジックを再利用するために、フィルターコンテキストを上書きします。 .PY と YTD の両方を1回の評価で適用することはできません。 計算グループは、計算グループの1つの計算項目がフィルターコンテキスト内にある場合に*のみ適用*されます。

## <a name="mdx-support"></a>MDX のサポート

計算グループは、多次元データ式 (MDX) クエリをサポートします。 つまり、MDX を使用して表形式のデータモデルにクエリを実行する Microsoft Excel ユーザーは、ワークシートのピボットテーブルとグラフの計算グループを最大限に活用できます。

## <a name="tools"></a>ツール

SQL Server Data Tools、Visual Studio で Analysis Services 拡張機能を使用した計算グループはまだサポートされていません。 ただし、計算グループは、表形式モデルのスクリプト言語 (TMSL) またはオープンソースの[表形式エディター](https://github.com/otykier/TabularEditor)を使用して作成できます。

## <a name="limitations"></a>制限事項

[オブジェクトレベルのセキュリティ](object-level-security.md)(XE) 計算グループテーブルで定義されているはサポートされていません。 ただし、同じモデル内の他のテーブルに XE を定義することもできます。 計算項目が XE で保護されたオブジェクトを参照する場合は、一般的なエラーが返されます。

[行レベルのセキュリティ](roles-ssas-tabular.md#bkmk_rowfliters)(RLS) はサポートされていません。 同じモデルのテーブルに RLS を定義することはできますが、計算グループ自体 (直接または間接的) には定義できません。

## <a name="see-also"></a>関連項目  

[テーブルモデルでの DAX](understanding-dax-in-tabular-models-ssas-tabular.md)   
[DAX リファレンス](https://docs.microsoft.com/dax/data-analysis-expressions-dax-reference)  
