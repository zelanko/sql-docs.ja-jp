---
title: "R Services の結果とリソースのパフォーマンス |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/09/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e902312-ad9c-480d-b82f-b871cd1052d9
caps.latest.revision: "8"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 65e3ca0b62da2a8412b92485316074a5f52fa080
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="performance-for-r-services-results-and-resources"></a>R Services のパフォーマンス: 結果とリソース

この記事では、4 番目と R Services のパフォーマンスの最適化を説明するシリーズで最終版です。 この記事では、メソッド、調査、およびさまざまな最適化の方法をテストした 2 つのケース スタディの結論をまとめたものです。

2 つのケース スタディでは、さまざまな目標がありました。

+ 最初のケース スタディ、R Services の開発チームが探索される特定の最適化の手法の影響を測定するには
+ 2 番目のケース スタディ、データ科学者のチームでいろいろ試して、特定の大量のスコア付けシナリオに最適な最適化を判断する方法を複数です。

このトピックでは、最初のケース スタディの詳細な結果を示します。 2 番目のケース スタディの概要には、全体的な結果がについて説明します。 このトピックの最後に、すべてのスクリプトとサンプル データ、および元の作成者によって使用されているリソースへのリンクです。

## <a name="performance-case-study-airline-dataset"></a>パフォーマンスのケース スタディ: 航空券 dataset

SQL Server R Services の開発チームによっては、このケース スタディでは、さまざまな最適化の効果をテストします。 1 つ rxLogit モデルが作成されたおよび航空会社のデータ セット上で実行スコア付けします。 最適化は、トレーニング セットとスコアリングを個々 の影響を評価するプロセス中に適用されました。

- Github:[サンプル データおよびスクリプト](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/PerfTuning)SQL Server の最適化の調査

### <a name="test-methods"></a>テスト メソッド

1. 航空券 dataset には、10 分の行の 1 つのテーブルで構成されます。 ダウンロードされ、SQL Server に一括が読み込まれます。
2. テーブルの 6 つのコピーが行われました。
3. さまざまな変更は、ページの圧縮、インデックス、列指向データ ストアなど、行の圧縮などの SQL Server 機能をテストする、テーブルのコピーに適用されました。
4. 前に、と各最適化が適用された後、パフォーマンスが測定されました。

| テーブル名| Description|
|------|------|
| *airline* | `rxDataStep` を使用して元の xdf ファイルから変換されたデータ。|                          |
| *airlineWithIntCol*   | *DayOfWeek* が文字列ではなく整数に変換されています。 また、*rowNum* 列が追加されています。|
| *airlineWithIndex*    | *airlineWithIntCol* テーブルと同じデータですが、*rowNum* 列を使用する 1 つのクラスター化インデックスが含まれます。|
| *airlineWithPageComp* | *airlineWithIndex* テーブルと同じデータですが、ページ圧縮が有効になっています。 また、*CRSDepTime* と *ArrDelay* から計算された、*CRSDepHour* と *Late* の 2 つの列が追加されています。 |
| *airlineWithRowComp*  | *airlineWithIndex* テーブルと同じデータですが、行圧縮が有効になっています。 また、*CRSDepTime* と *ArrDelay* から計算された、*CRSDepHour* と *Late* の 2 つの列が追加されています。 |
| *airlineColumnar*     | 1 つのクラスター化インデックスを含む単票形式ストア。 このテーブルには、クリーンアップされた csv ファイルのデータが含まれます。|

各テストは、次の手順のとおりです。

1. R ガベージ コレクションは各テストの前に発生します。
2. ロジスティック回帰モデルは、テーブルのデータに基づいて作成されました。 各テストの *rowsPerRead* の値は 500000 に設定されます。
3. スコアは、トレーニング済みモデルを使用して生成されました。
4. 各テストの実行で 6 倍されます。 最初の実行 (「コールド実行」) の時間が削除されました。 不定期の外れ値では、許可するように、**最大**残り 5 回の実行時間のも削除します。 それ以外の 4 回の実行の平均値から、各テストの平均実行時間を計算します。
5. 使用して、テストの実行、 *reportProgress*パラメーターに値 3 (タイミングをレポートと進行状況を =)。 各出力ファイルには、IO、移行時間、およびコンピューティングの時間にかかった時間に関する情報が含まれています。 これらの時間はトラブルシューティングと診断に役立ちます。
6. コンソール出力は、出力ディレクトリ内のファイルにも指示されました。
7. テスト スクリプトは、これらのファイルの実行に時間の平均を計算する時刻を処理します。

たとえば、次の結果も、1 つのテスト。 関心がある主な時間は、**合計読み取り時間** (IO 時間) と **遷移時間** (計算のプロセスを設定するオーバーヘッド) です。

**サンプルのタイミング**

```
Running IntCol Test. Using airlineWithIntCol table.
run 1 took 3.66 seconds
run 2 took 3.44 seconds
run 3 took 3.44 seconds
run 4 took 3.44 seconds
run 5 took 3.45 seconds
run 6 took 3.75 seconds
  
Average Time: 3.4425
metric time pct
1 Total time 3.4425 100.00
2 Overall compute time 2.8512 82.82
3 Total read time 2.5378 73.72
4 Transition time 0.5913 17.18
5 Total non IO time 0.3134 9.10
```

ダウンロードして、R Services のまたは RevoScaleR 関数での問題のトラブルシューティングに役立つテスト スクリプトを変更することをお勧めします。

### <a name="test-results-all"></a>テスト結果 (すべて)

このセクションでは、各テストの前に、と後の結果を比較します。

#### <a name="data-size-with-compression-and-a-columnar-table-store"></a>圧縮と単票形式のテーブル ストアとデータのサイズ

最初のテストでは、圧縮とデータのサイズを縮小する単票形式のテーブルの使用と比較されます。

| テーブル名            | [行]     | 予約済み。   | data       | index_size | 未使用  | 節約率 (予約済み) |
|-----------------------|----------|------------|------------|------------|---------|---------------------|
| *airlineWithIndex*    | 10000000 | 2978816 KB | 2972160 KB | 6128 KB    | 528 KB  | 0                   |
| *airlineWithPageComp* | 10000000 | 625784 KB  | 623744 KB  | 1352 KB    | 688 KB  | 79%                 |
| *airlineWithRowComp*  | 10000000 | 1262520 KB | 1258880 KB | 2552 KB    | 1088 KB | 58%                 |
| *airlineColumnar*     | 9999999  | 201992 KB  | 201624 KB  | n/a        | 368 KB  | 93%                 |

**結論**

ページの圧縮後に、列ストア インデックスを適用することで、最大データ サイズの削減が実現されました。

#### <a name="effects-of-compression"></a>圧縮の影響

このテストでは、行の圧縮、ページの圧縮と圧縮はなしの利点と比較されます。 使用して、モデルのトレーニングが`rxLinMod`3 つの異なるデータ テーブルからのデータにします。 すべてのテーブルで同じ式とクエリが使用されました。

| テーブル名            | テスト名       | numTasks | 平均時間 |
|-----------------------|-----------------|----------|--------------|
| *airlineWithIndex*    | NoCompression   | @shouldalert        | 5.6775       |
|                       | NoCompression - 並列| 4        | 5.1775       |
| *airlineWithPageComp* | PageCompression | @shouldalert        | 6.7875       |
|                       | PageCompression - 並列 | 4        | 5.3225       |
| *airlineWithRowComp*  | RowCompression  | @shouldalert        | 6.1325       |
|                       | RowCompression - 並列  | 4        | 5.2375       |

**結論**

圧縮だけでは、ヘルプにしません。 この例では、圧縮処理に CPU の増加は、IO 時間の低下を補正します。

ただし、*numTasks* を 4 に設定してテストを並列実行すると、平均時間が短縮されます。

データ セットの量が増えると、圧縮の効果はさらに顕著になる可能性があります。 圧縮はデータ セットと値によって変わるため、自らのデータ セットに圧縮が与える効果を判別するには実験することをお勧めします。

### <a name="effect-of-windows-power-plan-options"></a>Windows の電源プランのオプションの効果

この実験では、`rxLinMod` が *airlineWithIntCol* テーブルで使用されました。 Windows の電源プランがいずれかに設定**バランス**または**高パフォーマンス**です。 すべてのテストで *numTasks* は 1 に設定されました。 テストは 6 回が実行され、結果のばらつきを調査するために両方の電源オプションで 2 回実行されました。

**高パフォーマンス**電源オプション。

| テスト名 | 実行します。\# | 経過時間 | 平均時間 |
|-----------|--------|--------------|--------------|
| IntCol    | @shouldalert      | 3.57 秒 |              |
|           | 2      | 3.45 秒 |              |
|           | 3      | 3.45 秒 |              |
|           | 4      | 3.55 秒 |              |
|           | 5      | 3.55 秒 |              |
|           | 6      | 3.45 秒 |              |
|           |        |              | 3.475        |
|           | @shouldalert      | 3.45 秒 |              |
|           | 2      | 3.53 秒 |              |
|           | 3      | 3.63 秒 |              |
|           | 4      | 3.49 秒 |              |
|           | 5      | 3.54 秒 |              |
|           | 6      | 3.47 秒 |              |
|           |        |              | 3.5075       |

**[バランス]** 電源オプション:

| テスト名 | 実行します。\# | 経過時間 | 平均時間 |
|-----------|--------|--------------|--------------|
| IntCol    | @shouldalert      | 3.89 秒 |              |
|           | 2      | 4.15 秒 |              |
|           | 3      | 3.77 秒 |              |
|           | 4      | 5 秒    |              |
|           | 5      | 3.92 秒 |              |
|           | 6      | 3.8 秒  |              |
|           |        |              | 3.91         |
|           | @shouldalert      | 3.82 秒 |              |
|           | 2      | 3.84 秒 |              |
|           | 3      | 3.86 秒 |              |
|           | 4      | 4.07 秒 |              |
|           | 5      | 4.86 秒 |              |
|           | 6      | 3.75 秒 |              |
|           |        |              | 3.88         |

**結論**

Windows を使用する場合、実行時間はより一貫して高速**高パフォーマンス**電源プラン。

#### <a name="using-integer-vs-strings-in-formulas"></a>数式での文字列と整数を使用します。

このテストでは、文字列の要素の一般的な問題を回避する R コードを変更した場合の影響を評価します。 具体的には、モデルのトレーニングが使用して`rxLinMod`2 つのテーブルを使用して: 文字列として、最初の要素が格納されている以外の整数値として 2 番目のテーブル内の要素が格納されています。

+ *Airline*テーブルでは、[DayOfWeek] 列に文字列が含まれています。 _ColInfo_要素レベル (月曜日、火曜日、...) を指定するパラメーターが使用されました

+  *AirlineWithIndex*テーブル、[DayOfWeek] は整数です。 _ColInfo_パラメーターが指定されていません。

+ どちらの場合も、同じ式 `ArrDelay ~ CRSDepTime + DayOfWeek` が使用されました。

| テーブル名          | テスト名   | 平均時間 |
|---------------------|-------------|--------------|
| *Airline*           | *FactorCol* | 10.72        |
| *airlineWithIntCol* | *IntCol*    | 3.4475       |

**結論**

明確な利点がある要因を文字列ではなく、整数を使用する場合。

### <a name="avoiding-transformation-functions"></a>変換関数の回避

使用してこのテストでは、モデルのトレーニングが`rxLinMod`が、2 つの実行、コードを変更します。

+ 最初の実行では、変換関数はモデルのビルドの一部として適用されました。 
+ 2 回目の実行、特徴の値が事前計算済みおよび使用可能な変換関数は必要ありませんようにしました。

| テスト名             | 平均時間 |
|-----------------------|--------------|
| WithTransformation    | 5.1675       |
| WithoutTransformation | 4.7          |

**結論**

短い場合にトレーニングの時間が**いない**変換関数を使用します。 つまり、モデルのトレーニングが高速事前計算され、テーブルに保存されている列を使用する場合。

サイズ削減量が大きいと想定される複数変換の多くがあったし、データ セットが大きい場合 (\> 100 M)。

### <a name="using-columnar-store"></a>列ストアを使用します。

このテストでは、列指向データ ストアとインデックスを使用するパフォーマンス上の利点を評価します。 使用して、同じモデルのトレーニングが`rxLinMod`とデータ変換はありません。

+ 最初の実行では、データ テーブルは、標準的な行ストアを使用します。
+ 2 つ目の実行では、列ストアが使用されました。

| テーブル名         | テスト名 | 平均時間 |
|--------------------|-----------|--------------|
| *airlineWithIndex* | RowStore  | 4.67         |
| *airlineColumnar*  | ColStore  | 4.555        |

**結論**

標準的な行ストアよりも単票形式ストアとパフォーマンスお勧めします。 大きなデータ セットのパフォーマンスに大きな違いを想定することができます (\> 100 M)。

### <a name="effect-of-using-the-cube-parameter"></a>キューブ パラメーターを使用しての影響

このテストの目的が決定されたかどうか RevoScaleR でオプションを使用して、事前計算済みの**キューブ**パラメーターは、パフォーマンスを向上させることができます。 使用して、モデルのトレーニングが`rxLinMod`、この数式を使用します。

```R
ArrDelay ~ Origin:DayOfWeek + Month + DayofMonth + CRSDepTime
```

要素の表に*DayOfWeek*文字列として格納されます。

| テスト名     | Cube パラメーター | numTasks | 平均時間 | 単一行の予測 (ArrDelay_Pred) |
|---------------|----------------|----------|--------------|---------------------------------|
| CubeArgEffect | `cube = F`     | @shouldalert        | 91.0725      | 9.959204                        |
|               |                | 4        | 44.09        | 9.959204                        |
|               | `cube = T`     | @shouldalert        | 21.1125      | 9.959204                        |
|               |                | 4        | 8.08         | 9.959204                        |

**結論**

キューブ パラメーター引数を使用するには、明確にパフォーマンスが向上します。

### <a name="effect-of-changing-maxdepth-for-rxdtree-models"></a>RxDTree モデルの maxDepth を変更した場合の効果

この実験で、`rxDTree`でモデルの作成に使用されたアルゴリズム、 *airlineColumnar*テーブル。 このテストでは *numTasks* は 4 に設定されました。 いくつかの値が異なる*maxDepth*ツリーの深さを変更すると、実行時にどのように影響する方法を示すために使用されました。

| テスト名       | maxDepth | 平均時間 |
|-----------------|----------|--------------|
| TreeDepthEffect | @shouldalert        | 10.1975      |
|                 | 2        | 13.2575      |
|                 | 4        | 19.27        |
|                 | 8        | 45.5775      |
|                 | 16       | 339.54       |

**結論**

ツリーの深さが多いほど、ノードの合計数が指数関数的に増加します。 モデルを作成するための経過時間も大幅に向上します。

### <a name="prediction-on-a-stored-model"></a>保存されたモデルの予測

このテストの目的は、現在実行中のコードの一部として生成ではなく、SQL Server テーブルに保存されると、トレーニング済みモデルをスコア付けのパフォーマンスに与える影響を判断します。 スコア付け、保存されたモデルがデータベースから読み込まれ、メモリ (ローカル コンピューティング コンテキスト) で 1 行のデータ フレームを使用して予測を作成します。

テスト結果は、モデルを保存するとき、モデルを読み込むし、予測にかかった時間を表示します。

| テーブル名 | テスト名 | 平均時間 (モデルのトレーニング) | モデルの保存/読み込みの時間|
|------------|------------|------------|------------|
| airline    | SaveModel| 21.59| 2.08|
| airline    | LoadModelAndPredict | | 2.09 (予測する時間を含む) |

**結論**

テーブルからトレーニング済みモデルの読み込みは、明確に、予測を行う高速な方法です。 モデルを作成して、同じスクリプトですべてのスコアを実行しないことをお勧めします。

## <a name="case-study-optimization-for-the-resume-matching-task"></a>ケース スタディ: 再開-一致するタスクの最適化

Resume-一致するモデルは科学者がスケーラブルな作成するためのヘルプ データを行うとデータ科学者の Microsoft SQL Server での R コードのパフォーマンスをテストする Ke Huang によって開発されたエンタープライズ レベルのソリューションです。

### <a name="methods"></a>メソッド

RevoScaleR と MicrosoftML の両方のパッケージは、大規模なデータセットを含む複雑な R ソリューションで予測モデルのトレーニングに使用されました。 SQL クエリと R コードは、すべてのテストで同じでした。 インストールされる SQL server の 1 つの Azure VM でのテストを実行しました。 作成者では、スコア付けの回および SQL Server によって提供される次の最適化を使用せずに、比較。

- インメモリ テーブル
- ssNoVersion
- [リソース ガバナー]

R スクリプトの実行にソフト NUMA の影響を評価するためは、データ サイエンス チームは、Azure の仮想マシンを物理コア数を 20 にソリューションをテストします。 これらの物理コアの 4 つのソフト NUMA ノードは各ノードには、5 つのコアが含まれているように、自動的に作成されました。

CPU の結合は、シナリオでは、再開の一致、R ジョブへの影響の評価に適用されました。 4 つ**SQL のリソース プール**と 4 つ**外部リソース プール**作成されたと Cpu の同じセットの各ノードで使用することを確認してくださいに CPU 関係を指定しました。

各リソース プールは、ハードウェア使用率を最適化するために別のワークロード グループに割り当てられました。 その理由は、ソフト NUMA、CPU 関係は、物理 NUMA ノードの物理メモリを分けることはできません。そのため、定義で、同じ物理 NUMA ノードに基づくすべてのソフト NUMA ノード必要がありますメモリ使用 OS のメモリ ブロックは同じにします。 つまり、メモリ、プロセッサのアフィニティはありません。

次のプロセスが使用すると、この構成を作成します。

1. 既定では SQL Server に割り当てられたメモリの量を削減します。

2. R ジョブを並列で実行するための 4 つの新しいプールを作成します。

3. 各ワークロード グループはリソース プールに関連付けられているように、4 つのワークロード グループを作成します。

4. 新しいワークロード グループの割り当てとリソース ガバナーを再起動します。

5. ユーザー定義の分類子関数 (UDF) を割り当てる別のワークロード グループでさまざまなタスクを作成します。

6. 関数を使用して、適切なワークロード グループのリソース ガバナーの構成を更新します。

### <a name="results"></a>[結果]

調査再開照合に最適なパフォーマンスのある構成は、とおりでした。

-   次の 4 つの内部リソース プール (for SQL Server)

-   4 つの外部リソース プール (の外部スクリプトのジョブ)

-   各リソース プールが特定のワークロード グループに関連付けられています。

-   各リソース プールが別の Cpu に割り当てられています。

-   (SQL Server) の最大の内部メモリ使用率 = 30%

-   R セッションで使用するための最大メモリ 70% を =

、Resume-一致するモデルの外部スクリプトの使用が高いとなかったその他のデータベース エンジン サービスが実行されています。 そのため、外部スクリプトに割り当てられたリソースは、スクリプトのパフォーマンスを最適な構成であること、70% に増加しました。

この構成は、試してみることで別の値に到着しました。 別のハードウェアまたは別のソリューションを使用する場合は、最適な構成が異なる可能性があります。 常に、このケースの最適な構成を検索する実験!

ソリューションでは、最適化された、(100 機能) を使用してデータの 1.1 100万行 20 core コンピューターに 8.5 秒以内にスコアによってます。 最適化では、スコア付けの時間の観点からパフォーマンスが大幅に向上します。

結果も推奨されること、**機能の数**スコア付けの時間に大きな影響が出ています。 多くの機能は、予測モデルで使用されたときに、改善は、さらに顕著でした。

このブログ記事および詳細については、付随するチュートリアルを読むことをお勧めします。

-   [SQL Server での機械学習の最適化ヒントとテクニック](https://azure.microsoft.com/blog/optimization-tips-and-tricks-on-azure-sql-server-for-machine-learning-services/)

多くのユーザーがある小規模の一時停止が最初に、R (または Python) ランタイムが読み込まれるとメモします。 このため、これらのテスト」の説明に従って初回実行時は多くの場合、測定しますが、後で破棄されます。 後続のキャッシングと、最初の重要なパフォーマンスの違いになる可能性があり、次に実行します。 オーバーヘッドが発生 SQL Server と外部のランタイムの間でデータを移動したときに SQL Server から直接読み込まれるのではなく、ネットワーク経由でデータが渡された場合に特にです。

これらのすべての理由から、ソリューションはありません単一この初期読み込み時間を緩和するためのタスクによってはパフォーマンスに与える影響が大幅に変化します。 たとえば、キャッシュが実行される単一行のバッチのスコアリングそのため、連続したスコア付けの操作がはるかに高速とモデルでも、R ランタイムを再読み込みします。 使用することも[ネイティブ スコアリング](../sql-native-scoring.md)R ランタイムを完全に読み込まれないようにします。

大規模なモデルのトレーニングまたは大きなバッチでスコアリング、オーバーヘッドは、データ移動を回避またはストリーミングと並列処理の向上と比較すると最小限に抑えられます可能性があります。 これらの最近のブログと追加のパフォーマンス ガイダンス用のサンプルを参照してください。

+ [SQL Server 2016 の R Services を使用してローン分類](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2016/09/27/loan-classification-using-sql-server-2016-r-services/)
+ [初期のユーザーが R Services を操作します。](https://blogs.msdn.microsoft.com/sqlcat/2016/06/16/early-customer-experiences-with-sql-server-r-services/)
+ [R を使用して、100万秒あたりのトランザクションで不正行為の検出](http://blog.revolutionanalytics.com/2016/09/fraud-detection.html/)

## <a name="resources"></a>リソース

情報、ツール、およびこれらのテストの開発に使用するスクリプトへのリンクを次に示します。

+ パフォーマンスのテスト スクリプトとデータへのリンク:[データと SQL Server の最適化の学習用のスクリプトのサンプル](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/PerfTuning)

+ Resume-一致するソリューションを説明する記事:[最適化ヒントとテクニックについては、SQL Server R Services](https://azure.microsoft.com/blog/optimization-tips-and-tricks-on-azure-sql-server-for-machine-learning-services/)

+ Resume-一致するソリューションの SQL の最適化に使用されるスクリプト: [GitHub リポジトリ](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/SQLOptimizationTips)

### <a name="learn-about-windows-server-management"></a>Windows server の管理についてください。

+ [64 ビット版 Windows 用の適切なページ ファイルのサイズを確認する方法](https://support.microsoft.com/kb/2860880)

+ [NUMA を理解します。](https://technet.microsoft.com/library/ms178144.aspx)

+ [SQL Server で NUMA をサポートする方法](https://technet.microsoft.com/library/ms180954.aspx)

+ [ソフト NUMA](https://docs.microsoft.com/sql/database-engine/configure-windows/soft-numa-sql-server)

### <a name="learn-about-sql-server-optimizations"></a>SQL Server の最適化についてください。

+ [インデックスの再編成と再構築](../../relational-databases\indexes\reorganize-and-rebuild-indexes.md)

+ [メモリ最適化テーブルの概要](https://docs.microsoft.com/sql/relational-databases/in-memory-oltp/introduction-to-memory-optimized-tables)

+ [実証: インメモリ OLTP でのパフォーマンス向上](https://docs.microsoft.com/sql/relational-databases/in-memory-oltp/demonstration-performance-improvement-of-in-memory-oltp)

+ [データの圧縮](../../relational-databases/data-compression/data-compression.md)

+ [テーブルまたはインデックスの圧縮の有効化](../../relational-databases/data-compression/enable-compression-on-a-table-or-index.md)

+ [テーブルまたはインデックスの圧縮の無効化](../../relational-databases/data-compression/disable-compression-on-a-table-or-index.md)

### <a name="learn-about-managing-sql-server"></a>SQL Server の管理についてください。

+ [パフォーマンスの監視とチューニング](../../relational-databases/performance/monitor-and-tune-for-performance.md)

+ [リソース ガバナー](../../relational-databases/resource-governor/resource-governor.md)

+ [リソース ガバナーの概要](https://technet.microsoft.com/library/bb895232.aspx)

+ [R Services のリソース管理](resource-governance-for-r-services.md)

+ [R のリソース プールを作成する方法](how-to-create-a-resource-pool-for-r.md)

+ [リソース ガバナーの構成の例](https://blog.sqlauthority.com/2012/06/04/sql-server-simple-example-to-configure-resource-governor-introduction-to-resource-governor/)

### <a name="tools"></a>ツール

+ [DISKSPD ストレージ ロード ジェネレーター/パフォーマンス テスト ツール](https://github.com/microsoft/diskspd)

+ [FSUtil ユーティリティ リファレンス](https://technet.microsoft.com/library/cc753059.aspx)


## <a name="other-articles-in-this-series"></a>このシリーズの他の資料

[パフォーマンス – R のチューニングの概要](sql-server-r-services-performance-tuning.md)

[R - SQL Server の構成のパフォーマンスの調整](sql-server-configuration-r-services.md)

[R の R のパフォーマンスの調整コードとデータの最適化](r-and-data-optimization-r-services.md)

[パフォーマンスのチューニングのケース スタディ結果](performance-case-study-r-services.md)
