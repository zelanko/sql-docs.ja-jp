---
title: R と SQL のデータ型とオブジェクト (SQL Server Machine Learning) に関するクイック スタート |Microsoft Docs
description: このクイック スタートでは、データ型と R と SQL Server でのデータ オブジェクトを操作する方法について説明します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/15/2018
ms.topic: quickstart
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 6eeb2c71e821c9ccf5a89129a862b3d01a1d64bf
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39085504"
---
# <a name="quickstart-handle-data-types-and-objects-using-r-in-sql-server"></a>クイック スタート: データ型と SQL Server で R を使用するオブジェクトを処理します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

このクイック スタートでは、R と SQL Server の間でデータを移動するときに発生する一般的な問題に対する実践的な概要を取得します。 この演習でできるように、エクスペリエンスは、独自のスクリプトでデータを扱うときに、重要な背景知識を提供します。

前もって把握する一般的な問題は次のとおりです。

+ データ型が一致しない場合がある
+ 暗黙的な変換を実行する場合があります。
+ キャスト操作と変換操作が必要な場合がある
+ R と SQL が異なるデータ オブジェクトを使用する

## <a name="prerequisites"></a>前提条件

前のクイック スタート[の Hello World R と SQL を](rtsql-using-r-code-in-transact-sql-quickstart.md)情報を提供し、このクイック スタートに必要な R 環境を設定するためにリンクします。

## <a name="always-return-a-data-frame"></a>常にデータ フレームを返す

スクリプトが R から SQL Server に結果を返す場合は、データを **data.frame** として返す必要があります。 スクリプトで生成する他の型のオブジェクト (リスト、因子、ベクトル、バイナリ データ) をストアド プロシージャの結果の一部として出力する場合は、そのオブジェクトをデータ フレームに変換する必要があります。 他のオブジェクトをデータ フレームに変更する処理をサポートする R 関数は複数あります。 バイナリ モデルをシリアル化して、データ フレームに返すこともできます。この処理については、このチュートリアルで後述します。

最初に、一部 R の基本的な R オブジェクトで実験してみましょう-ベクトル、マトリックス、および一覧- と SQL Server に渡される出力の変換をデータ フレームの変化を確認します。

これら 2 つの"Hello World"スクリプトを R での比較します。スクリプトにほとんど同じようになりますが、2 つ目は、3 つの列を 1 つの値の各を返しますが、最初に 3 つの値の 1 つの列が返されます。

**例 1**

```sql
EXECUTE sp_execute_external_script
       @language = N'R'
     , @script = N' mytextvariable <- c("hello", " ", "world");
       OutputDataSet <- as.data.frame(mytextvariable);'
     , @input_data_1 = N' ';
```

**例 2**

```sql
EXECUTE sp_execute_external_script
        @language = N'R'
      , @script = N' OutputDataSet<- data.frame(c("hello"), " ", c("world"));'
      , @input_data_1 = N'  ';
```

## <a name="identify-schema-and-data-types"></a>スキーマとデータ型を識別します。

結果が異なる理由は何でしょうか。 

通常、その答えは、R の `str()` コマンドを使用するとわかります。 R スクリプトのいずれかの場所に関数 `str(object_name)` を追加し、指定された R オブジェクトのデータ スキーマを情報メッセージとして返します。 メッセージを確認するには、Visual Studio Code の **[メッセージ]** ウィンドウまたは SSMS の **[メッセージ]** タブを参照してください。

例 1 と例 2 の結果が異なる理由を理解するには、次に示すように、各ステートメントの _@script_ 変数定義の末尾に `str(OutputDataSet)` という行を挿入します。

**追加 str 関数を使用した例 1**

```sql
EXECUTE sp_execute_external_script
        @language = N'R'
      , @script = N' mytextvariable <- c("hello", " ", "world");
      OutputDataSet <- as.data.frame(mytextvariable);
      str(OutputDataSet);'
      , @input_data_1 = N'  '
;
```

**追加 str 関数を使用した例 2**

```sql
EXECUTE sp_execute_external_script
  @language = N'R', 
  @script = N' OutputDataSet <- data.frame(c("hello"), " ", c("world"));
    str(OutputDataSet);' , 
  @input_data_1 = N'  ';
```

これで、**[メッセージ]** のテキストを確認すると、出力が異なる理由がわかります。

**結果 - 例 1**

```
STDOUT message(s) from external script:
'data.frame':   3 obs. of  1 variable:
$ mytextvariable: Factor w/ 3 levels " ","hello","world": 2 1 3
```

**結果 - 例 2**

```
STDOUT message(s) from external script:
'data.frame':   1 obs. of  3 variables:
$ c..hello..: Factor w/ 1 level "hello": 1
$ X...      : Factor w/ 1 level " ": 1
$ c..world..: Factor w/ 1 level "world": 1
```

R 構文のわずかな変更が結果のスキーマに大きな影響をもたらしていることがわかります。 R データ型の違いの説明は Hadley Wickham によるこの記事ではより詳細なので、理由に移動されません。 [R データ構造](http://adv-r.had.co.nz/Data-structures.html)します。

ここでは、R オブジェクトをデータ フレームに変換する際に予想される結果を確認する必要があることに留意してください。

> [!TIP]
> 
> など、R の恒等関数を使用することもできます。 `is.matrix`、 `is.vector`、内部データ構造に関する情報を返します。

## <a name="implicit-conversion-of-data-objects"></a>データ オブジェクトの暗黙的な変換

R の各データ オブジェクトには、2 つのデータ オブジェクトの次元数が同じ場合や、いずれかのデータ オブジェクトに異種データ型が格納されている場合に他のデータ オブジェクトと結合する際の値の処理方法に関する固有のルールがあります。

たとえば、R を使用する行列乗算を実行する次のステートメントを実行します。4 つの値を含む配列で、次の 3 つの値を持つ 1 列の行列を乗算し、その結果として 4 x 3 行列を期待します。

```sql
EXECUTE sp_execute_external_script
    @language = N'R'
    , @script = N'
        x <- as.matrix(InputDataSet);
        y <- array(12:15);
    OutputDataSet <- as.data.frame(x %*% y);'
    , @input_data_1 = N' SELECT [Col1]  from RTestData;'
    WITH RESULT SETS (([Col1] int, [Col2] int, [Col3] int, Col4 int));
```

この場合、3 つの値で構成される列が 1 列の行列に変換されます。 R では行列は特殊なケースの配列であるため、2 つの引数が一致するように、配列 `y` が暗黙的に 1 列の行列に変換されます。

**結果**

|Col1|Col2|Col3|Col4|
|---|---|---|---|
|12|13|14|15|
|120|130|140|150|
|1200|1300|1400|1500|

ただし、配列のサイズを変更するときに起こる`y`します。

```sql
execute sp_execute_external_script
   @language = N'R'
   , @script = N'
        x <- as.matrix(InputDataSet);
        y <- array(12:14);
   OutputDataSet <- as.data.frame(y %*% x);'
   , @input_data_1 = N' SELECT [Col1]  from RTestData;'
   WITH RESULT SETS (([Col1] int ));
```

これで、R は結果として 1 つの値を返します。

**結果**
    
|Col1|
|---|
|1542|

なぜでしょうか。 この場合、同じ長さのベクトルとしては、2 つの引数を処理することができますので、R は行列として内積を返します。  これは、線形代数のルールに従った想定どおりの動作です。ただし、ダウンストリーム アプリケーションで出力スキーマが変更されないと想定されている場合に問題が発生する可能性があります。

> [!TIP]
> 
> エラーが発生しますか。 これらの例は、テーブルを必要と**RTestData**します。 テスト データのテーブルを作成していない場合、テーブルを作成するには、このトピックに戻り:[入力と出力を処理](../tutorials/rtsql-working-with-inputs-and-outputs.md)します。
> 
> テーブルが作成されましたが、エラーが発生する場合ではなく、テーブルを含むデータベースのコンテキストでストアド プロシージャを実行していること確認**マスター**または別のデータベース。
> 
> また、これらの例の一時テーブルを使用しないことをお勧めします。 一部の R クライアントでは、一時テーブルを削除するバッチ間の接続を終了します。

## <a name="merge-or-multiply-columns-of-different-length"></a>異なる長さの列の結合または乗算

R は、操作、さまざまなサイズのベクターを使用するため、これらの列のような構造をデータ フレームに結合するための柔軟性を提供します。 ベクトルのリストはテーブルのような外見ですが、データベース テーブルを管理するすべてのルールに従うわけではありません。

たとえば、次のスクリプトでは、長さが 6 の数値配列を定義し、R 変数 `df1` に格納します。 数値配列合わされ、新しいデータ フレームに 3 つの値を含む RTestData テーブルの整数と結合されて`df2`します。

```sql
EXECUTE sp_execute_external_script
    @language = N'R'
    , @script = N'
               df1 <- as.data.frame( array(1:6) );
               df2 <- as.data.frame( c( InputDataSet , df1 ));
               OutputDataSet <- df2'
    , @input_data_1 = N' SELECT [Col1]  from RTestData;'
    WITH RESULT SETS (( [Col2] int not null, [Col3] int not null ));
```

データ フレームに入力するために、R は RTestData から取得した要素を必要な数だけ繰り返し、配列 `df1` 内の要素の数と一致させます。

**結果**
    
|*Col2*|*Col3*|
|----|----|
|1|1|
|10|2|
|100|3|
|1|4|
|10|5|
|100|6|

データ フレームはテーブルのような外見ですが、実際はベクトルのリストであることを思い出してください。

## <a name="cast-or-convert-sql-server-data"></a>SQL Server データのキャストまたは変換

R と SQL Server は同じデータ型を使用しないため、データを取得して R ランタイムに渡すためのクエリを SQL Server で実行する際は、通常何らかの暗黙的な変換を行います。 R から SQL Server にデータを返す場合は、別の変換を行います。

- SQL Server では、スタート パッド サービスによって管理される R プロセスに、クエリからのデータをプッシュし、効率が向上内部表現に変換します。
- R ランタイムはデータを data.frame 変数に読み込み、データに対する操作を実行します。
- データベース エンジンは、セキュリティで保護された内部接続を使用する SQL Server にデータを返し、SQL Server のデータ型の観点からデータを提供します。
- データを取得するには、SQL クエリを発行して表形式データ セットを処理できるクライアントまたはネットワーク ライブラリを使用して SQL Server に接続します。 このクライアント アプリケーションは、他の方法でデータに影響を及ぼす可能性があります。

この動作を確認するには、ようなクエリを実行、 [AdventureWorksDW](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)データ ウェアハウス。 このビューは、予測の作成に使用する売上データを返します。

```sql
USE AdventureWorksDW
GO

SELECT ReportingDate
         , CAST(ModelRegion as varchar(50)) as ProductSeries
         , Amount
           FROM [AdventureWorksDW].[dbo].[vTimeSeries]
           WHERE [ModelRegion] = 'M200 Europe'
           ORDER BY ReportingDate ASC
```

> [!NOTE]
> 
> 任意のバージョンの AdventureWorks を使用するか、独自のデータベースを使用して、別のクエリを作成します。 ポイントは、テキスト、datetime、および数値の値を含む一部のデータを処理することです。

ストアド プロシージャへの入力としてこのクエリを貼り付けてください。

```sql
EXECUTE sp_execute_external_script
       @language = N'R'
      , @script = N' str(InputDataSet);
      OutputDataSet <- InputDataSet;'
      , @input_data_1 = N'
           SELECT ReportingDate
         , CAST(ModelRegion as varchar(50)) as ProductSeries
         , Amount
           FROM [AdventureWorksDW].[dbo].[vTimeSeries]
           WHERE [ModelRegion] = ''M200 Europe''
           ORDER BY ReportingDate ASC ;'
WITH RESULT SETS undefined;
```

エラーが発生した場合は、クエリ テキストの一部を編集しなければならない可能性があります。 たとえば、WHERE 句に predicate という文字列を含める場合、単一引用符で囲む必要があります。

クエリを動作させたら、`str` 関数の結果を確認し、R で入力データがどのように処理されるかを把握します。

**結果**

```
STDOUT message(s) from external script: 'data.frame':    37 obs. of  3 variables:
STDOUT message(s) from external script: $ ReportingDate: POSIXct, format: "2010-12-24 23:00:00" "2010-12-24 23:00:00"
STDOUT message(s) from external script: $ ProductSeries: Factor w/ 1 levels "M200 Europe",..: 1 1 1 1 1 1 1 1 1 1
STDOUT message(s) from external script: $ Amount       : num  3400 16925 20350 16950 16950
```

+ 日時列は R データ型 **POSIXct** を使用して処理されました。
+ "ProductSeries"として識別された text 列、**要素**、カテゴリ変数を意味します。 文字列値は、既定では因子として処理されます。 R に渡した文字列は、内部で使用するために整数に変換され、出力時に再度文字列にマップされます。

### <a name="summary"></a>まとめ

こうした短い例についてからには、SQL に渡す入力としてクエリを実行するときに、データ変換の効果を確認する必要を確認できます。 一部の SQL Server データ型が R でサポートされていないために、次のエラーを回避する方法を検討してください。

+ データを事前にテストし、列または R コードに渡されるときに問題があるなスキーマ内の値を確認します。
+ `SELECT *` を使用するのではなく、入力データ ソースに列を個別に指定し、各列の処理方法を把握します。
+ 予期しない動作を回避するために、入力データを準備する際に、必要に応じて明示的なキャストを実行します。
+ エラーが発生して、モデリングの役に立たない (GUID や rowguids) などのデータの列を渡すことを回避します。

サポートされているとサポートされていないデータ型の詳細については、次を参照してください。 [R ライブラリとデータ型](../r/r-libraries-and-data-types.md)します。

文字列数値因子からの実行時の変換のパフォーマンスに与える影響については、次を参照してください。 [SQL Server R Services のパフォーマンス チューニング](../r/sql-server-r-services-performance-tuning.md)します。

## <a name="next-step"></a>次の手順

次のクイック スタートでは、SQL Server のデータを R 関数を適用する方法を学習します。

> [!div class="nextstepaction"]
> [SQL Server のデータのクイック スタート: R を使用して関数](rtsql-using-r-functions-with-sql-server-data.md)
