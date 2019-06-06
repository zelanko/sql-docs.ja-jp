---
title: Analysis Services 表形式モデルで計算グループ |Microsoft Docs
ms.date: 06/05/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 58e845965bb9cd4eeba46ad30193c79b436da569
ms.sourcegitcommit: fc341b2e08937fdd07ea5f4d74a90677fcdac354
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "66719865"
---
# <a name="calculation-groups-preview"></a>計算グループ (プレビュー)
 
[!INCLUDE[ssas-appliesto-sql2019](../../includes/ssas-appliesto-sql2019.md)]

として一般的なメジャーの式をグループ化して冗長なメジャーの数を大幅に短縮できます計算グループ*計算アイテム*します。 1470 以降の SQL Server Analysis Services 2019 表形式モデルで計算グループがサポートされている[互換性レベル](compatibility-level-for-tabular-models-in-analysis-services.md)します。 1470 の互換性レベル モデルでは、現在では**プレビュー**します。  

この記事では、以下について説明します。 

> [!div class="checklist"]
> * 利点 
> * 計算グループのしくみ
> * 動的な書式指定文字列
> * 優先順位
> * ツール
> * 制限事項



## <a name="benefits"></a>利点

計算グループがある複雑なモデルで、問題に対処する同じ計算でタイム インテリジェンス計算の最も一般的なを使用してメジャーを冗長化の数が増加します。 たとえば、セールス アナリストが売上合計を表示して、月累計 (MTD) 四半期-日付 (QTD) での注文年の日付 (YTD) と前の年 (PY)、今年を並べ替えます。 データ モデラーは、数十個のメジャーにつながることが、各計算のための個別のメジャーを作成するがします。 、ユーザーのこのを並べ替えるだけ多くのメジャーであることを意味し、そのレポートを個別に適用されます。 

計算グループが Power BI などのレポート作成ツールでユーザーを表示する方法を見てまずみましょう。 計算グループの構成し、モデルで作成する方法を見て、ご説明しましょう。

計算グループは、レポート クライアントでは 1 つの列を含むテーブルとして示されます。 列が、一般的な列またはディメンションと、代わりに、1 つまたは複数の再利用可能な計算を表しますまたは*計算アイテム*値フィルターの視覚エフェクトに既に追加されて、測定値に適用できます。

次のアニメーションでは、ユーザーが 2012 と 2013 年の売上データを分析します。 共通のベース メジャー、計算グループを適用する前に**販売**1 か月あたりの合計売上の合計を計算します。 ユーザーは、しを日付の年の日付の四半期累計の日付の月の売上合計を取得するタイム インテリジェンス計算を適用するがします。 計算グループのないユーザーを個別のタイム インテリジェンス メジャーを選択する必要があります。

という名前のこの例では、計算グループと**タイム インテリジェンス**、ユーザーがドラッグしたとき、**時間の計算**項目を**列**領域で、計算の各項目をフィルター処理別の列として表示されます。 各行の値は、ベース メジャーから計算される**Sales**します。  

![Power BI で適用されている計算グループ](media/calculation-groups/calc-groups-pbi.gif)


計算グループ操作**明示的な**DAX メジャーです。 この例で**Sales**は、モデルで既に作成された明示的なメジャーです。 計算グループは、暗黙的なメジャーの DAX では動作しません。 たとえば、Power BI で暗黙的なメジャーが作成されます、ユーザーが明示的なメジャーを作成せずに、集計された値を表示するビジュアルに列をドラッグするとき。 この時点では、Power BI は、DAX を暗黙的なメジャーの DAX 計算 - つまり、暗黙的なメジャーが計算グループを操作できませんをインラインとして記述を生成します。 表形式オブジェクト モデル (TOM) で表示される新しいモデル プロパティが導入されました**DiscourageImplicitMeasures**します。 現時点では、このプロパティの計算グループを作成するためにする必要がありますに設定する**true**します。 True の場合、Live Connect での Power BI Desktop モードには、暗黙的なメジャーの作成が無効にします。

## <a name="how-they-work"></a>そのしくみ

計算グループのユーザーに役立つ方法を確認したら、タイム インテリジェンス計算のグループの例に示すを作成する方法を見てをみましょう。

詳細に進む前に計算グループ向けのいくつかの新しい DAX 関数を紹介します。 

[SELECTEDMEASURE](https://docs.microsoft.com/dax/selectedmeasure-function-dax) - 現在のコンテキスト内にあるメジャーを参照する計算アイテムの式で使用されます。 この例では、売上を測定します。

[SELECTEDMEASURENAME](https://docs.microsoft.com/dax/selectedmeasurename-function-dax) - 計算アイテムの名前でコンテキスト内にあるメジャーの決定を式で使用されます。

[ISSELECTEDMEASURE](https://docs.microsoft.com/dax/isselectedmeasure-function-dax) - コンテキスト内にあるメジャーはメジャーの一覧で指定されたかを決定する計算アイテムの式で使用されます。

[SELECTEDMEASUREFORMATSTRING](https://docs.microsoft.com/dax/selectedmeasurefromatstring-function-dax) - コンテキスト内にあるメジャーの書式指定文字列を取得する項目を計算の式で使用されます。

### <a name="time-intelligence-example"></a>タイム インテリジェンスの使用例

テーブル名 -**タイム インテリジェンス**   
列名 -**時間の計算**   
優先順位 - **20**   

#### <a name="time-intelligence-calculation-items"></a>タイム インテリジェンス計算の項目

**Current**

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

**YTD**

```dax
CALCULATE(SELECTEDMEASURE(), DATESYTD(DimDate[Date]))
```

**PY**

```dax
CALCULATE(SELECTEDMEASURE(), SAMEPERIODLASTYEAR(DimDate[Date]))
```

**PY MTD**

```dax
CALCULATE(
    SELECTEDMEASURE(),
    SAMEPERIODLASTYEAR(DimDate[Date]),
    'Time Intelligence'[Time Calculation] = "MTD"
)
```

**PY QTD**

```dax
CALCULATE(
    SELECTEDMEASURE(),
    SAMEPERIODLASTYEAR(DimDate[Date]),
    'Time Intelligence'[Time Calculation] = "QTD"
)
```

**PY YTD**

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

**前年比 %**

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

この計算グループをテストするには、SSMS またはオープン ソースで DAX クエリを実行できる[DAX Studio](http://daxstudio.org/)します。 前年比と前年比 % は、次のクエリ例から省略されます。

#### <a name="time-intelligence-query"></a>タイム インテリジェンスのクエリ

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

#### <a name="time-intelligence-query-return"></a>タイム インテリジェンスのクエリを返す

返されるテーブルは、項目に適用される各計算の計算を示しています。 たとえば、2012 年 3 月の QTD が年 1 月、年 2 月および 2012 年 3 月の合計を確認できます。

![クエリの戻り値](media/calculation-groups/calc-groups-query-return.png)


## <a name="dynamic-format-strings"></a>動的な書式指定文字列

*動的な書式指定文字列*グループ計算で文字列を返すことを強制することがなくメジャーに書式指定文字列の条件付きのアプリケーションを使用します。

表形式モデルの DAX を使用して動的なメジャーの書式をサポートする[形式](https://docs.microsoft.com/dax/format-function-dax)関数。 ただし、FORMAT 関数には、それ以外の場合も、文字列として返される数値はメジャーの強制、文字列を返すことの欠点があります。 これにより、グラフなどの数値の値によって、ほとんどの Power BI ビジュアルを使用していないなど、いくつかの制限があります。

### <a name="dynamic-format-strings-for-time-intelligence"></a>タイム インテリジェンスの動的な書式指定文字列

除くすべての計算が項目上に示した例では、タイム インテリジェンスを見る場合**の前年比 %** コンテキストで現在のメジャーの形式を使用する必要があります。 たとえば、 **YTD** Sales ベース メジャーの計算は currency である必要があります。 これが注文のベース メジャーの計算グループの場合、数値書式になります。 **前年比 %** 、ただしの形式に関係なく、ベース メジャーの割合をする必要があります。

**の前年比 %** 、形式の文字列式のプロパティを設定して、書式指定文字列を無効にできます**0.00;-0.00; 0.00%** します。 書式設定文字列式のプロパティの詳細については、次を参照してください。 [MDX セル プロパティ - 文字列の内容を形式](../multidimensional-models/mdx/mdx-cell-properties-format-string-contents.md#numeric-values)します。

このマトリックス ビジュアルを Power BI で確認**現在/前年比の売上**と**注文現在/前年比**それぞれのベース メジャーの書式指定文字列を保持します。 **販売の前年比 %** と**注文の前年比 %** 、ただし、使用する書式指定文字列を上書き*割合*形式。

![マトリックス ビジュアルでタイム インテリジェンス](media/calculation-groups/calc-groups-dynamicstring-timeintel.png)

### <a name="dynamic-format-strings-for-currency-conversion"></a>通貨換算用の動的な書式指定文字列

動的な書式指定文字列は、簡単な通貨換算を提供します。 次の Adventure Works データ モデルを検討してください。 モデルの作成には、*一対多*で定義されている通貨換算[型変換](../currency-conversions-analysis-services.md#conversion-types)します。

![表形式モデルの通貨レート](media/calculation-groups/calc-groups-currency-conversion.png)

A **FormatString**に列が追加、 **DimCurrency**テーブルし、それぞれの通貨の書式指定文字列が設定されます。

![書式文字列の列](media/calculation-groups/calc-groups-formatstringcolumn.png)

この例では、次の計算グループとして定義し。

### <a name="currency-conversion-example"></a>通貨変換の例

テーブル名 -**通貨換算**   
列名 -**変換の計算**   
優先順位 - **5**   

#### <a name="calculation-items-for-currency-conversion"></a>通貨換算の計算アイテム

**変換なし**

```dax
SELECTEDMEASURE()
```

**変換後の通貨**

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

書式指定文字列式

```dax
SELECTEDVALUE(
    DimCurrency[FormatString],
    SELECTEDMEASUREFORMATSTRING()
)
```
形式の文字列式では、スカラーの文字列を返す必要があります。 これは、新しい[SELECTEDMEASUREFORMATSTRING](https://docs.microsoft.com/dax/selectedmeasurefromatstring-function-dax)フィルターのコンテキストで複数の通貨がある場合は、ベース メジャーの書式指定文字列に戻す関数。

次のアニメーションの動的形式の通貨換算を示しています、 **Sales**レポート内のメジャー。

![適用された通貨変換の動的な書式文字列](media/calculation-groups/calc-groups-dynamic-format-string.gif)

## <a name="precedence"></a>優先順位

優先順位は、計算グループに対して定義されているプロパティです。 1 つ以上の計算グループがある場合に、評価の順序を指定します。 大きい数値は、つまりで優先順位の低い計算グループの前に評価される、優先順位の高いをことを示します。

この例で説明します、タイム インテリジェンス上記の例と、同じモデルを使用してがここも追加、**平均**計算グループ。 平均計算のグループには、従来のタイム インテリジェンスの独立したは、日付フィルター コンテキストを変更しない - 平均の計算を単に適用される点で平均の計算が含まれています。

この例では、1 日の平均の計算を定義します。 石油 1 日あたりの平均バレルなどの計算は、石油とガスのアプリケーションで共通です。 その他の一般的なビジネスの例にはの小売店舗売上の平均が含まれます。

このような計算の計算でタイム インテリジェンス計算とは無関係には、ある可能性がありますもそれらを結合するための要件。 たとえば、ユーザーは 1 日を現在の日付の年の最初から 1 日の石油率を表示する YTD 石油のバレルを参照してくださいする可能性があります。 このシナリオで計算アイテムの優先順位を設定する必要があります。

### <a name="averages-example"></a>平均値の例

テーブル名は**平均**します。   
列名が**平均の計算**します。   
優先順位が**10**します。   

#### <a name="calculation-items-for-averages"></a>平均の計算アイテム

**平均なし**

```dax
SELECTEDMEASURE()
```

**1 日あたり平均**

```dax
DIVIDE(SELECTEDMEASURE(), COUNTROWS(DimDate))
```

DAX クエリを戻り値のテーブルの例を次に示します。

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

#### <a name="averages-query-return"></a>戻り値の平均クエリ

![クエリの戻り値](media/calculation-groups/calc-groups-ytd-daily-avg.png)

次の表では、2012 年 3 月の値の計算方法を示します。


|列名  |計算 |
|---------|---------|
|YTD     |    1 月、年 2 月、年 2012年 3 月売上の合計<br />= 495,364 + 506,994 + 373,483     |
|1 日あたり平均    |     Mar の 2012 年 3 月の日数で割った値の売上<br />= 373,483 / 31       |
|YTD 1 日あたりの平均     | YTD 年 3 月の 2012 年 1 月、年 2 月、および 3 月の日数で割った値<br />=  1,375,841 / (31 + 29 + 31)       |

優先順位で適用される、YTD 計算アイテムの定義を示します。 **20**します。

```dax
CALCULATE(SELECTEDMEASURE(), DATESYTD(DimDate[Date]))
```

ここでは 1 日平均値、適用の優先順位を持つ**10**します。

```dax
DIVIDE(SELECTEDMEASURE(), COUNTROWS(DimDate))
```

タイム インテリジェンス計算グループの優先順位は平均の計算グループよりも上位であるために、できるだけ広くとして適用されます。 YTD 日次平均を計算には、分子と分母 (日の数) の日次平均を計算の両方に YTD が適用されます。

これは、次の式と等価です。

```dax
CALCULATE(DIVIDE(SELECTEDMEASURE(), COUNTROWS(DimDate)), DATESYTD(DimDate[Date]))
```

この式されません。

```dax
DIVIDE(CALCULATE(SELECTEDMEASURE(), DATESYTD(DimDate[Date])), COUNTROWS(DimDate)))
```

## <a name="sideways-recursion"></a>横向きの再帰

上記タイム インテリジェンスの例で計算アイテムの一部を参照してください他のユーザーで同じ計算グループ。 これは呼び出されます*横向き再帰*します。 たとえば、**の前年比 %** 両方を参照**前年比**と**PY**します。

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

両方の式が個別に評価されるこの場合は、さまざまな使用しているため、ステートメントを計算します。 その他の種類の再帰呼び出しはサポートされていません。

## <a name="single-calculation-item-in-filter-context"></a>フィルターのコンテキストで項目を 1 つの計算

このタイム インテリジェンスの例では、 **PY YTD**計算アイテムが 1 つの式を計算します。

```dax
CALCULATE(
    SELECTEDMEASURE(),
    SAMEPERIODLASTYEAR(DimDate[Date]),
    'Time Intelligence'[Time Calculation] = "YTD"
)
```

YTD CALCULATE() 関数の引数は、YTD の計算アイテムで既に定義されているロジックを再利用するフィルター コンテキストをオーバーライドします。 1 つの評価で、PY、YTD の両方を適用することはできません。 計算グループは*のみに適用される*計算グループから 1 つの計算アイテムがフィルター コンテキストの場合。

## <a name="mdx-support"></a>MDX のサポート

計算グループは、多次元データ式 (MDX) クエリをサポートします。 つまり、どのクエリの表形式データ モデルで MDX を使用してフル活用できますワークシート ピボット テーブルで計算グループとグラフの Microsoft Excel ユーザー。

## <a name="tools"></a>ツール

計算グループは SQL Server Data Tools、Analysis Services の拡張機能を使用した Visual Studio でまだサポートされていません。 ただし、Tabular Model Scripting Language (TMSL) またはオープン ソースを使用して計算グループを作成できます[表形式エディター](https://github.com/otykier/TabularEditor)します。

## <a name="limitations"></a>制限事項

[オブジェクト レベル セキュリティ](object-level-security.md)(OLS) は、計算で定義されているグループのテーブルがサポートされていません。 ただし、ツールは、同じモデル内の他のテーブルで定義できます。 OLS セキュリティで保護されたオブジェクトの計算アイテムを参照して、一般的なエラーが返されます。

[行レベルのセキュリティ](roles-ssas-tabular.md#bkmk_rowfliters)(RLS) はサポートされていません。 (直接または間接的に)、計算グループ自体ではなく、同じモデル内のテーブルで RLS を定義することができます。

[行の式について詳しく説明](../tutorial-tabular-1400/as-supplemental-lesson-detail-rows.md)計算グループではサポートされません。

## <a name="see-also"></a>関連項目  

[テーブル モデルにおける DAX](understanding-dax-in-tabular-models-ssas-tabular.md)   
[DAX リファレンス](https://docs.microsoft.com/dax/data-analysis-expressions-dax-reference)  
