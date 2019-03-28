---
title: SQL Server R Services - 結果とリソース - SQL Server Machine Learning Services のパフォーマンス
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 4b71afb8f373eed4f49bc2cf0ea1c6086b6f121d
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58510759"
---
# <a name="performance-for-r-services-results-and-resources"></a>R Services のパフォーマンス: 結果とリソース
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、4 番目と R Services のパフォーマンスの最適化を説明するシリーズの最後。 この記事では、メソッド、発見、およびさまざまな最適化の方法をテストする 2 つのケース スタディの結論をまとめたものです。

2 つのケース スタディでは、異なる目標がありました。

+ 特定の最適化手法の影響を測定する最初のケース スタディ、R Services 開発チームによって検索
+ 2 つ目のケース スタディ、データ サイエンティスト チームによって、特定の大量のスコア付けのシナリオに最適な最適化を判断する複数の方法で実験します。

このトピックでは、最初のケース スタディの詳細な結果を使用します。 2 番目のケース スタディの概要には、全体的な結果がについて説明します。 このトピックの最後には、すべてのスクリプトとサンプル データ、および元の作成者によって使用されるリソースへのリンクを示します。

## <a name="performance-case-study-airline-dataset"></a>パフォーマンスのケース スタディ:航空会社のデータセット

SQL Server R Services 開発チームがこのケース スタディは、さまざまな最適化の効果をテストします。 RxLogit を 1 つのモデルが作成され、スコア付け、航空会社のデータ セットで実行します。 最適化は、トレーニングと個々 の影響を評価するプロセスをスコア付け中に適用されました。

- Github:[サンプル データとスクリプト](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/PerfTuning)SQL Server の最適化の調査

### <a name="test-methods"></a>テスト メソッド

1. 航空会社のデータセットには、10 M 行の 1 つのテーブルで構成されます。 ダウンロードしたし、SQL Server に一括が読み込まれます。
2. テーブルの 6 つのコピーが行われました。
3. さまざまな変更は、ページの圧縮、インデックス、列指向データ ストアなど、行の圧縮などの SQL Server 機能をテストする、テーブルのコピーに適用されました。
4. 前に、と各最適化が適用された後、パフォーマンスが測定されました。

| テーブル名| 説明|
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
4. 各テストでは、6 回を実行します。 最初の実行 (「コールド ラン」) の時間が削除されました。 不定期の外れ値を許可する、**最大**残りの 5 つの実行間における時間のも削除します。 それ以外の 4 回の実行の平均値から、各テストの平均実行時間を計算します。
5. 使用して、テストの実行、 *reportProgress*パラメーター (レポートのタイミングと進行状況を =) 値 3 を使用します。 各出力ファイルには、IO、遷移時間、およびコンピューティング時間で費やされた時間に関する情報が含まれています。 これらの時間はトラブルシューティングと診断に役立ちます。
6. コンソール出力は、出力ディレクトリ内のファイルにも指示されました。
7. テスト スクリプトは、実行時間の平均を計算するこれらのファイルで時間を処理します。

たとえば、次の結果は、1 つのテストから時刻を示します。 関心がある主な時間は、**合計読み取り時間** (IO 時間) と **遷移時間** (計算のプロセスを設定するオーバーヘッド) です。

**サンプルのタイミング**

```text
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

ダウンロードして、R Services または RevoScaleR 関数問題のトラブルシューティングに役立つ、テスト スクリプトを変更することをお勧めします。

### <a name="test-results-all"></a>テスト結果 (すべて)

このセクションでは、各テストの結果の前後に比較します。

#### <a name="data-size-with-compression-and-a-columnar-table-store"></a>データのサイズを圧縮および単票形式テーブル ストアを使用

最初のテストでは、圧縮および単票形式データのサイズを縮小するテーブルの使用と比較します。

| テーブル名            | [行]     | 予約済み。   | データ       | index_size | 未使用  | 節約率 (予約済み) |
|-----------------------|----------|------------|------------|------------|---------|---------------------|
| *airlineWithIndex*    | 10000000 | 2978816 KB | 2972160 KB | 6128 KB    | 528 KB  | 0                   |
| *airlineWithPageComp* | 10000000 | 625784 KB  | 623744 KB  | 1352 KB    | 688 KB  | 79%                 |
| *airlineWithRowComp*  | 10000000 | 1262520 KB | 1258880 KB | 2552 KB    | 1088 KB | 58%                 |
| *airlineColumnar*     | 9999999  | 201992 KB  | 201624 KB  | n/a        | 368 KB  | 93%                 |

**結論**

最大データ サイズの削減は、ページの圧縮後に、列ストア インデックスを適用することによって実現されました。

#### <a name="effects-of-compression"></a>圧縮の影響

このテストでは、行の圧縮、ページの圧縮と圧縮はなしの利点を比較します。 使用して、モデルのトレーニングが`rxLinMod`3 つの異なるデータ テーブルからのデータにします。 すべてのテーブルで同じ式とクエリが使用されました。

| テーブル名            | テスト名       | numTasks | 平均時間 |
|-----------------------|-----------------|----------|--------------|
| *airlineWithIndex*    | NoCompression   | 1        | 5.6775       |
|                       | Nocompression です - 並列| 4        | 5.1775       |
| *airlineWithPageComp* | PageCompression | 1        | 6.7875       |
|                       | PageCompression - 並列 | 4        | 5.3225       |
| *airlineWithRowComp*  | RowCompression  | 1        | 6.1325       |
|                       | RowCompression - 並列  | 4        | 5.2375       |

**結論**

圧縮だけでは、ヘルプには見えません。 この例では、圧縮を処理するために CPU の増加は、IO 時間の低下を補正します。

ただし、*numTasks* を 4 に設定してテストを並列実行すると、平均時間が短縮されます。

データ セットの量が増えると、圧縮の効果はさらに顕著になる可能性があります。 圧縮はデータ セットと値によって変わるため、自らのデータ セットに圧縮が与える効果を判別するには実験することをお勧めします。

### <a name="effect-of-windows-power-plan-options"></a>Windows の電源プランのオプションの効果

この実験では、`rxLinMod` が *airlineWithIntCol* テーブルで使用されました。 Windows の電源プラン設定されたいずれかに**バランス**または**高性能**します。 すべてのテストで *numTasks* は 1 に設定されました。 テストは 6 回実行され、結果のばらつきを調査する両方の電源オプションで 2 回実行されました。

**高パフォーマンス**電源オプション。

| テスト名 | \#を実行します。 | 経過時間 | 平均時間 |
|-----------|--------|--------------|--------------|
| IntCol    | 1      | 3.57 秒 |              |
|           | 2      | 3.45 秒 |              |
|           | 3      | 3.45 秒 |              |
|           | 4      | 3.55 秒 |              |
|           | 5      | 3.55 秒 |              |
|           | 6      | 3.45 秒 |              |
|           |        |              | 3.475        |
|           | 1      | 3.45 秒 |              |
|           | 2      | 3.53 秒 |              |
|           | 3      | 3.63 秒 |              |
|           | 4      | 3.49 秒 |              |
|           | 5      | 3.54 秒 |              |
|           | 6      | 3.47 秒 |              |
|           |        |              | 3.5075       |

**[バランス]** 電源オプション:

| テスト名 | \#を実行します。 | 経過時間 | 平均時間 |
|-----------|--------|--------------|--------------|
| IntCol    | 1      | 3.89 秒 |              |
|           | 2      | 4.15 秒 |              |
|           | 3      | 3.77 秒 |              |
|           | 4      | 5 秒    |              |
|           | 5      | 3.92 秒 |              |
|           | 6      | 3.8 秒  |              |
|           |        |              | 3.91         |
|           | 1      | 3.82 秒 |              |
|           | 2      | 3.84 秒 |              |
|           | 3      | 3.86 秒 |              |
|           | 4      | 4.07 秒 |              |
|           | 5      | 4.86 秒 |              |
|           | 6      | 3.75 秒 |              |
|           |        |              | 3.88         |

**結論**

Windows を使用する場合、実行時間が一貫して速い**高性能**電源プラン。

#### <a name="using-integer-vs-strings-in-formulas"></a>数式での文字列と整数を使用します。

このテストでは、文字列の要素の一般的な問題を回避する R コードの変更の影響を評価します。 具体的には、モデルのトレーニングを使用して`rxLinMod`2 つのテーブルを使用して: 文字列として、最初の要素が格納されている。 2 番目のテーブルの要素が整数として格納されます。

+ *航空*テーブルでは、[DayOfWeek] 列に文字列が含まれています。 _ColInfo_要素レベル (月曜日、火曜日、...) を指定するパラメーターが使用されました

+  *AirlineWithIndex*テーブル [DayOfWeek] は整数です。 _ColInfo_パラメーターが指定されませんでした。

+ どちらの場合も、同じ式 `ArrDelay ~ CRSDepTime + DayOfWeek` が使用されました。

| テーブル名          | テスト名   | 平均時間 |
|---------------------|-------------|--------------|
| *航空会社*           | *FactorCol* | 10.72        |
| *airlineWithIntCol* | *IntCol*    | 3.4475       |

**結論**

明確な利点がある要因を文字列ではなく整数を使用する場合。

### <a name="avoiding-transformation-functions"></a>変換関数を回避します。

使用して、このテストでは、モデルがトレーニングされて`rxLinMod`が、2 つの実行、コードを変更します。

+ 最初の実行で、変換関数は、モデルの構築の一部として適用されました。 
+ 2 つ目の実行で、特徴の値が事前計算済みおり、利用可能できるように、変換関数は必要ありません。

| テスト名             | 平均時間 |
|-----------------------|--------------|
| WithTransformation    | 5.1675       |
| WithoutTransformation | 4.7          |

**結論**

短い場合にトレーニング時間**いない**変換関数を使用します。 つまり、モデルでは事前計算され、テーブルに保持されている列を使用するときにトレーニングが高速化します。

節約のあった多くの変換と、データ セットが大きい場合に大きいことが必要です (\> 100,000, 000)。

### <a name="using-columnar-store"></a>単票形式ストアを使用します。

このテストでは、列指向データ ストアおよびインデックスを使用してのパフォーマンスの利点を評価します。 使用して、同じモデルのトレーニングが`rxLinMod`とデータ変換はありません。

+ 最初の実行では、データ テーブルは、標準的な行ストアを使用します。
+ 2 つ目の実行では、列ストアが使用されました。

| テーブル名         | テスト名 | 平均時間 |
|--------------------|-----------|--------------|
| *airlineWithIndex* | RowStore  | 4.67         |
| *airlineColumnar*  | ColStore  | 4.555        |

**結論**

標準の行ストアよりも単票形式ストアのパフォーマンスお勧めします。 大規模なデータ セットのパフォーマンスに大きな違いを想定することができます (\> 100,000, 000)。

### <a name="effect-of-using-the-cube-parameter"></a>Cube パラメーターの使用

このテストの目的を決定するがかどうか、事前計算済みを使用するために RevoScaleR オプション**キューブ**パラメーターは、パフォーマンスを向上させることができます。 使用して、モデルのトレーニングが`rxLinMod`、次の数式を使用します。

```R
ArrDelay ~ Origin:DayOfWeek + Month + DayofMonth + CRSDepTime
```

表に、要因*DayOfWeek*を文字列として格納されます。

| テスト名     | Cube パラメーター | numTasks | 平均時間 | 単一行の予測 (ArrDelay_Pred) |
|---------------|----------------|----------|--------------|---------------------------------|
| CubeArgEffect | `cube = F`     | 1        | 91.0725      | 9.959204                        |
|               |                | 4        | 44.09        | 9.959204                        |
|               | `cube = T`     | 1        | 21.1125      | 9.959204                        |
|               |                | 4        | 8.08         | 9.959204                        |

**結論**

キューブ パラメーターの引数の使用には、明らかにパフォーマンスが向上します。

### <a name="effect-of-changing-maxdepth-for-rxdtree-models"></a>モデルの rxDTree の maxDepth の変更の影響

この実験では、`rxDTree`でモデルの作成に使用されたアルゴリズム、 *airlineColumnar*テーブル。 このテストでは *numTasks* は 4 に設定されました。 いくつかの値が異なる*maxDepth*をツリーの深さを変更すると、実行時にどのように影響する方法を示すために使用されました。

| テスト名       | maxDepth | 平均時間 |
|-----------------|----------|--------------|
| TreeDepthEffect | 1        | 10.1975      |
|                 | 2        | 13.2575      |
|                 | 4        | 19.27        |
|                 | 8        | 45.5775      |
|                 | 16       | 339.54       |

**結論**

ツリーの深さの増大に合わせて、ノードの合計数が指数関数的に増加します。 モデルを作成するための経過時間も大幅に向上します。

### <a name="prediction-on-a-stored-model"></a>格納されたモデルの予測

このテストの目的は、現在実行中のコードの一部として生成ではなく、SQL Server テーブルに保存されると、トレーニング済みモデルをスコア付けのパフォーマンスに与える影響を判断します。 スコア付け、格納されたモデルがデータベースから読み込まれ、メモリ (ローカル計算コンテキスト) で、1 行のデータ フレームを使用して予測を作成します。

テスト結果は、モデルを読み込むし、予測作成に要した時間と、モデルを保存する時間を表示します。

| テーブル名 | テスト名 | 平均時間 (モデルのトレーニング) | モデルの保存/読み込みの時間|
|------------|------------|------------|------------|
| airline    | SaveModel| 21.59| 2.08|
| airline    | LoadModelAndPredict | | 2.09 (予測する時間を含む) |

**結論**

テーブルからトレーニング済みモデルの読み込みは、予測を行うより高速の方法では明確にします。 モデルを作成して、同じスクリプトですべてのスコア付けを実行しないことをお勧めします。

## <a name="case-study-optimization-for-the-resume-matching-task"></a>ケース スタディ:Resume-一致するタスクの最適化

Microsoft データ サイエンスの専門家 Ke Huang、SQL Server での R コードのパフォーマンスをテストするためのヘルプ データ科学者は、スケーラブルな作成手順を実行して、再開-一致するモデルが開発されたエンタープライズ レベルのソリューションです。

### <a name="methods"></a>メソッド

RevoScaleR と MicrosoftML の両方のパッケージは、大規模なデータセットに関連する複雑な R ソリューションで予測モデルのトレーニングに使用されました。 SQL クエリと R コードは、すべてのテストでは同じでした。 SQL Server がインストールされている 1 つの Azure VM でテストを実施しました。 作成者と SQL Server によって提供される、次の最適化なしのスコア付けの時間と比較されます。

- インメモリ テーブル
- ssNoVersion
- [リソース ガバナー]

R スクリプトの実行にソフト NUMA の影響を評価するため、データ サイエンス チーム物理コア数 20 の Azure の仮想マシン、ソリューションのテスト。 これらの物理コアに、4 つのソフト NUMA ノードは各ノードには、5 つのコアが含まれているように、自動的に作成されました。

CPU の結合は、R ジョブへの影響を評価するための再開に一致するシナリオで適用されました。 4 つ**SQL のリソース プール**と 4 つ**外部リソース プール**作成された Cpu の同じセットの各ノードで使用することを確認する CPU 関係が指定されています。

各リソース プールは、ハードウェアの使用率を最適化するために、別のワークロード グループに割り当てられました。 理由は、ソフト NUMA、CPU アフィニティは、物理 NUMA ノードの物理メモリを分けることはできません。そのため、定義では同じ物理 NUMA ノードに基づいているすべてのソフト NUMA ノードする必要がありますを使用して、メモリの同じ OS のメモリ ブロックで。 つまり、メモリ、プロセッサのアフィニティはありません。

次のプロセスは、この構成の作成に使用しました。

1. SQL Server に既定で割り当てられたメモリの量を削減します。

2. 並列 R ジョブを実行するための 4 つの新しいプールを作成します。

3. 各ワークロード グループはリソース プールに関連付けられているように、4 つのワークロード グループを作成します。

4. 新しいワークロード グループの割り当てとリソース ガバナーを再起動します。

5. ユーザー定義分類子関数 (UDF) を割り当てる別のワークロード グループでさまざまなタスクを作成します。

6. 適切なワークロード グループの関数を使用してリソース ガバナーの構成を更新します。

### <a name="results"></a>[結果]

調査最高のパフォーマンスを再開一致に含まれていた構成は次のとおりです。

-   (SQL Server) 用の 4 つの内部リソース プール

-   (外部スクリプト ジョブ) の 4 つの外部リソース プール

-   各リソース プールが特定のワークロード グループに関連付けられました。

-   各リソース プールが異なる Cpu に割り当てられています。

-   (SQL Server) 用の最大の内部のメモリ使用率を 30% を =

-   R セッションで使用するメモリを最大 70% を =

再開-一致するモデルの場合は、外部スクリプトの使用状況が負荷の高いとが含まれていないその他のデータベース エンジン サービスが実行されています。 そのため、外部スクリプトに割り当てられたリソースはされたスクリプトのパフォーマンスの最適な構成証明が 70% に増加します。

この構成が、異なる値を使って試してみるに到着しました。 別のハードウェアまたは別のソリューションを使用する場合は、最適な構成が異なる可能性があります。 常に状況に合わせて最適な構成を検索する試してみる。

最適なソリューションで 1.1 100万行の (100 機能) を使用してデータが 20 core コンピューターに 8.5 秒以内に評価されます。 最適化は、スコア付けの時間の観点でのパフォーマンスを大幅に向上します。

結果もことを提案、**機能数**スコア付けの時間に大きな影響を与える必要があります。 改善より多くの機能は、予測モデルで使用されていたときよりも目立つでした。

このブログの記事と付随するチュートリアルの詳細については、確認することをお勧めします。

-   [SQL Server での machine learning の最適化のヒントとテクニック](https://azure.microsoft.com/blog/optimization-tips-and-tricks-on-azure-sql-server-for-machine-learning-services/)

多くのユーザーがある小規模の一時停止 (R または Python) ランタイムが初めて読み込まれるとメモします。 このため、これらのテスト」の説明に従って初回実行時刻は多くの場合、測定しますが、後で破棄されます。 後続のキャッシングと、最初のパフォーマンスの顕著な違いがあり、次に実行します。 オーバーヘッドがありますもいくつかデータが SQL Server と外部のランタイム間で移動すると SQL Server から直接読み込まれるのではなく、ネットワーク経由でデータが渡された場合に特に。

これらすべての理由からはこの最初の読み込み時間を短縮するための 1 つのソリューション タスクによってはパフォーマンスに与える影響が大幅に変化します。 単一行のバッチでのスコア付けのキャッシュの実行例そのため、一連のスコア付けの操作がはるかに高速と、モデルでも、R ランタイムが再度読み込まれます。 使用することも[ネイティブ スコアリング](../sql-native-scoring.md)R ランタイムを完全に読み込まれないようにします。

大規模なモデルでのトレーニングや、大きなバッチでスコア付け、オーバーヘッドが最小データ移動を回避またはストリーミングと並列処理の向上と比べてなる可能性があります。 これらの最近のブログと追加のパフォーマンス ガイダンスのサンプルを参照してください。

+ [SQL Server 2016 R Services を使用してローンの分類](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2016/09/27/loan-classification-using-sql-server-2016-r-services/)
+ [初期の顧客のエクスペリエンスと R Services](https://blogs.msdn.microsoft.com/sqlcat/2016/06/16/early-customer-experiences-with-sql-server-r-services/)
+ [R を使用して、1 秒あたり 100万トランザクションでの不正行為の検出](https://blog.revolutionanalytics.com/2016/09/fraud-detection.html/)

## <a name="resources"></a>リソース

次に、情報、ツール、およびこれらのテストの開発で使用されるスクリプトへのリンクを示します。

+ パフォーマンスのテスト スクリプトとデータへのリンク:[サンプル データと SQL Server の最適化の学習用のスクリプト](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/PerfTuning)

+ Resume-一致するソリューションを記述する情報の記事:[最適化ヒントとテクニックについては、SQL Server R Services](https://azure.microsoft.com/blog/optimization-tips-and-tricks-on-azure-sql-server-for-machine-learning-services/)

+ Resume-一致するソリューションの SQL の最適化で使用されるスクリプト:[GitHub リポジトリ](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/SQLOptimizationTips)

### <a name="learn-about-windows-server-management"></a>Windows server の管理について説明します

+ [64 ビット版 Windows 用の適切なページ ファイルのサイズを確認する方法](https://support.microsoft.com/kb/2860880)

+ [NUMA を理解します。](https://technet.microsoft.com/library/ms178144.aspx)

+ [SQL Server で NUMA をサポートする方法](https://technet.microsoft.com/library/ms180954.aspx)

+ [ソフト NUMA](https://docs.microsoft.com/sql/database-engine/configure-windows/soft-numa-sql-server)

### <a name="learn-about-sql-server-optimizations"></a>SQL Server の最適化について説明します

+ [インデックスの再編成と再構築](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md)

+ [メモリ最適化テーブルの概要](https://docs.microsoft.com/sql/relational-databases/in-memory-oltp/introduction-to-memory-optimized-tables)

+ 「[実証: インメモリ OLTP のパフォーマンスの向上](https://docs.microsoft.com/sql/relational-databases/in-memory-oltp/demonstration-performance-improvement-of-in-memory-oltp)

+ [データの圧縮](../../relational-databases/data-compression/data-compression.md)

+ [テーブルまたはインデックスの圧縮の有効化](../../relational-databases/data-compression/enable-compression-on-a-table-or-index.md)

+ [テーブルまたはインデックスの圧縮の無効化](../../relational-databases/data-compression/disable-compression-on-a-table-or-index.md)

### <a name="learn-about-managing-sql-server"></a>SQL Server の管理について説明します

+ [パフォーマンスの監視とチューニング](../../relational-databases/performance/monitor-and-tune-for-performance.md)

+ [リソース ガバナー](../../relational-databases/resource-governor/resource-governor.md)

+ [リソース ガバナーの概要](https://technet.microsoft.com/library/bb895232.aspx)

+ [R Services のリソース管理](resource-governance-for-r-services.md)

+ [R のリソース プールを作成する方法](how-to-create-a-resource-pool-for-r.md)

+ [リソース ガバナーの構成の例](https://blog.sqlauthority.com/2012/06/04/sql-server-simple-example-to-configure-resource-governor-introduction-to-resource-governor/)

### <a name="tools"></a>ツール

+ [DISKSPD ストレージ ロード ジェネレーター/パフォーマンス テスト ツール](https://github.com/microsoft/diskspd)

+ [FSUtil ユーティリティ リファレンス](https://technet.microsoft.com/library/cc753059.aspx)


## <a name="other-articles-in-this-series"></a>このシリーズの他の記事

[パフォーマンス チューニング - R の概要](sql-server-r-services-performance-tuning.md)

[R で SQL Server の構成のパフォーマンス チューニング](sql-server-configuration-r-services.md)

[R の R のパフォーマンス チューニング コードとデータの最適化](r-and-data-optimization-r-services.md)

[パフォーマンス チューニング - 結果のケース スタディ](performance-case-study-r-services.md)
