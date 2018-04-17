---
title: R と SQL データ型とデータ オブジェクト (SQL のクイック スタートで R) |Microsoft ドキュメント
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: eeed977c3b942f0c23e4036f514018f54b966b70
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="r-and-sql-data-types-and-data-objects-r-in-sql-quickstart"></a>R と SQL データ型とデータ オブジェクト (SQL のクイック スタートで R)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この手順では、R と SQL Server の間でデータを移動するときに発生する一般的な問題について学習します。

+ データ型が一致しない場合がある
+ 暗黙的な変換を実行する可能性があります。
+ キャスト操作と変換操作が必要な場合がある
+ R と SQL が異なるデータ オブジェクトを使用する

## <a name="always-return-r-data-as-a-data-frame"></a>常にデータ フレームとして R データを返す

スクリプトが R から SQL Server に結果を返す場合は、データを **data.frame** として返す必要があります。 スクリプトで生成する他の型のオブジェクト (リスト、因子、ベクトル、バイナリ データ) をストアド プロシージャの結果の一部として出力する場合は、そのオブジェクトをデータ フレームに変換する必要があります。 他のオブジェクトをデータ フレームに変更する処理をサポートする R 関数は複数あります。 バイナリ モデルをシリアル化して、データ フレームに返すこともできます。この処理については、このチュートリアルで後述します。

最初に、R 基本的な R オブジェクトの一部に試してみましょう — ベクター、マトリックス、および一覧- し、データ フレームへの変換が SQL Server に渡される出力をどのように変化するかを参照してください。

R. でこれら 2 つの"Hello World"スクリプトを比較します。スクリプトがほとんど同じに見えますが、2 つ目は、それぞれ 3 つの列を 1 つの値を返しますが、最初に 3 つの値の 1 つの列が返されます。

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

## <a name="identifying-the-schema-and-data-types-of-r-data"></a>R データのスキーマとデータ型の識別

結果が異なる理由は何でしょうか。

通常、その答えは、R の `str()` コマンドを使用するとわかります。 R スクリプトのいずれかの場所に関数 `str(object_name)` を追加し、指定された R オブジェクトのデータ スキーマを情報メッセージとして返します。 メッセージを確認するには、Visual Studio Code の **[メッセージ]** ウィンドウまたは SSMS の **[メッセージ]** タブを参照してください。

例 1 と例 2 の結果が異なる理由を理解するには、次に示すように、各ステートメントの _@script_ 変数定義の末尾に `str(OutputDataSet)` という行を挿入します。

**例 1 str 関数を追加**

```sql
EXECUTE sp_execute_external_script
        @language = N'R'
      , @script = N' mytextvariable <- c("hello", " ", "world");
      OutputDataSet <- as.data.frame(mytextvariable);
      str(OutputDataSet);'
      , @input_data_1 = N'  '
;
```

**追加 str 関数で、例 2**

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

R 構文のわずかな変更が結果のスキーマに大きな影響をもたらしていることがわかります。 触れません理由で R のデータ型の違いの説明は Hadley Wickham によってこの記事の内容より徹底的なので: [R のデータ構造体](http://adv-r.had.co.nz/Data-structures.html)です。

ここでは、R オブジェクトをデータ フレームに変換する際に予想される結果を確認する必要があることに留意してください。

> [!TIP]
> 
> などの id の R 関数を使用することもできます。 `is.matrix`、 `is.vector`, などです。

## <a name="implicit-conversion-of-data-objects"></a>データ オブジェクトの暗黙的な変換

R の各データ オブジェクトには、2 つのデータ オブジェクトの次元数が同じ場合や、いずれかのデータ オブジェクトに異種データ型が格納されている場合に他のデータ オブジェクトと結合する際の値の処理方法に関する固有のルールがあります。

たとえば、次のステートメントを実行し、R を使用して行列の乗算を行うとします。3 つの値を持つ 1 列の行列に 4 つの値を持つ配列を掛けると、結果として 4x3 行列が想定されます。

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

ただし、配列のサイズを変更するときに起こる`y`です。

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

なぜでしょうか。 ここでは、同じ長さのベクトルとしては、2 つの引数を処理することができますので、R は、行列として内部積を返します。  これは、線形代数のルールに従った想定どおりの動作です。ただし、ダウンストリーム アプリケーションで出力スキーマが変更されないと想定されている場合に問題が発生する可能性があります。

> [!TIP]
> 
> エラーが発生しますか。 これらの例は、テーブルを必要と**RTestData**です。 テスト データ テーブルを作成していない場合このトピックに戻ります。[入力と出力の操作](../tutorials/rtsql-working-with-inputs-and-outputs.md)です。
> 
> テーブルを作成したエラーが発生した場合とではなく、テーブルを含むデータベースのコンテキストでストアド プロシージャを実行していることを確認してください**マスター**または別のデータベースです。
> 
> また、これらの例の一時テーブルを使用しないことをお勧めします。 一部の R クライアントには、一時テーブルを削除すると、バッチの間で接続が終了します。

## <a name="merge-or-multiply-columns-of-different-length"></a>異なる長さの列の結合または乗算

R は、異なるサイズのベクターを操作するため、これらの列のような構造をデータ フレームに結合するための優れた柔軟性を提供します。 ベクトルのリストはテーブルのような外見ですが、データベース テーブルを管理するすべてのルールに従うわけではありません。

たとえば、次のスクリプトでは、長さが 6 の数値配列を定義し、R 変数 `df1` に格納します。 数値の配列が、新しいデータ フレームを作成する 3 つの値を格納する RTestData テーブルの整数と組み合わせて、`df2`です。

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

- SQL Server では、スタート パッド サービスによって管理される R プロセスに、クエリからデータをプッシュし、効率の内部表現に変換します。
- R ランタイムはデータを data.frame 変数に読み込み、データに対する操作を実行します。
- データベース エンジンは、セキュリティで保護された内部接続を使用する SQL Server にデータを返し、SQL Server のデータ型の観点からデータを提供します。
- データを取得するには、SQL クエリを発行して表形式データ セットを処理できるクライアントまたはネットワーク ライブラリを使用して SQL Server に接続します。 このクライアント アプリケーションは、他の方法でデータに影響を及ぼす可能性があります。

変換のしくみを確認するには、AdventureWorksDW データ ウェアハウスで次のようなクエリを実行します。 このビューは、予測の作成に使用する売上データを返します。

```sql
SELECT ReportingDate
         , CAST(ModelRegion as varchar(50)) as ProductSeries
         , Amount
           FROM [AdventureWorksDW2014].[dbo].[vTimeSeries]
           WHERE [ModelRegion] = 'M200 Europe'
           ORDER BY ReportingDate ASC
```

> [!NOTE]
> 
> AdventureWorks の任意のバージョンを使用するか、独自のデータベースを使用して別のクエリを作成します。 ポイントでは、テキスト、日付時刻と数値の値を含む一部のデータを処理しようとしています。

ここで、ストアド プロシージャへの入力として次のクエリを貼り付けることを再試行してください。

```sql
EXECUTE sp_execute_external_script
       @language = N'R'
      , @script = N' str(InputDataSet);
      OutputDataSet <- InputDataSet;'
      , @input_data_1 = N'
           SELECT ReportingDate
         , CAST(ModelRegion as varchar(50)) as ProductSeries
         , Amount
           FROM [AdventureWorksDW2014].[dbo].[vTimeSeries]
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
+ "ProductSeries"として識別された text 列、**係数**、カテゴリ変数を意味します。 文字列値は、既定では因子として処理されます。 R に渡した文字列は、内部で使用するために整数に変換され、出力時に再度文字列にマップされます。

### <a name="summary"></a>[概要]

でもこれらの簡単な例をからは、SQL を渡す入力としてクエリを実行するときに、データ変換の効果を確認する必要性を確認できます。 一部の SQL Server データ型が R でサポートされていないために、次のエラーを回避する方法を考慮してください。

+ データを事前にテストして、列または R コードに渡されるときに問題の可能性がある、スキーマ内の値を確認してください。
+ `SELECT *` を使用するのではなく、入力データ ソースに列を個別に指定し、各列の処理方法を把握します。
+ 予期しない動作を回避するために、入力データを準備する際に、必要に応じて明示的なキャストを実行します。
+ エラーが発生し、モデリングの役に立たない (GUID や rowguids) などのデータの受け渡し列を避けます。

サポートされており、サポートされていないデータ型の詳細については、次を参照してください。 [R ライブラリとデータ型](../r/r-libraries-and-data-types.md)です。

数値の要因に文字列の実行時の変換のパフォーマンスに与える影響については、次を参照してください。 [SQL Server R Services のパフォーマンス チューニング](../r/sql-server-r-services-performance-tuning.md)です。

## <a name="next-lesson"></a>次のレッスン

次の手順では、R 関数を SQL Server データに適用する方法について説明します。

[SQL Server データでの R 関数の使用](../../advanced-analytics/tutorials/rtsql-using-r-functions-with-sql-server-data.md)
