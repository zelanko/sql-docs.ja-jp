---
title: "パフォーマンスのケース スタディ (R Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/10/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0e902312-ad9c-480d-b82f-b871cd1052d9
caps.latest.revision: 8
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 6
---
# パフォーマンスのケース スタディ (R Services)

前のセクションでは、」の説明の効果を示すためには、航空会社のデータ セットからテーブルを使用するテストは実行されています。 

## テストとデータの例

各テーブルの行を 10 M を使用して、6 つのテーブルがあります。

| テーブル名 | Description |
| ---------- | ----------- |
| _航空会社_ | データを変換元および xdf を使用してファイルから *rxDataStep*します。 |
| _airlineWithIntCol_ | *DayOfWeek* 文字列ではなく整数に変換します。 また、追加、 *rowNum* 列です。 |
| _airlineWithIndex_ | 同じデータ、 *airlineWithIntCol* テーブルが 1 つのクラスター化インデックスを使用して、 *rowNum* 列です。 |
| _airlineWithPageComp_ | 同じデータ、 *airlineWithIndex* テーブルが、ページの圧縮を有効になっているとします。 また 2 つの列を追加 *CRSDepHour* と *遅れて*, から計算される *CRSDepTime* と *ArrDelay*します。 |
| _airlineWithRowComp_ | 同じデータ、 *airlineWithIndex* テーブルが行の圧縮を有効にします。 また 2 つの列を追加 *CRSDepHour* と *遅れて* から計算される *CRSDepTime* と *ArrDelay*します。 
| _airlineColumnar_ | 1 つのクラスター化インデックス付き列のストアです。 このテーブルには、クリーンアップを csv からのデータ ファイル。 |

このセクションで、だけでなく、テストに使用されるサンプル データへのリンクで説明するテストの実行に使用するスクリプトについては、「 [https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/PerfTuning](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/PerfTuning)します。

各テストの実行が 6 回の最初の実行 (実行、コールド) 時刻は削除されました。 不定期の外れ値を許容するには、残りの 5 つの実行時間の上限がも削除されます。 各テストの平均経過時間のランタイムを計算する残りの 4 つの実行の平均値が取得されました。 各テストの前に、R のガベージ コレクションが発生しました。 値 *rowsPerRead* 500000 に各テストが設定されました。

## データのサイズを圧縮し、列ストア テーブルを使用する場合

データのサイズを小さく圧縮と列のテーブルを使用した結果を次に示します。

| テーブル名 | 行数 | 予約済み。 | Data | index_size | 未使用 | % (予約済み) |
| ---------- | ---- | -------- | ---- | ---------- | ------ | ------------------- |
| airlineWithIndex | 10000000 | 2978816 KB | 2972160 KB | 6128 KB | 528 KB | 0 |
| airlineWithPageComp | 10000000 | 625784 KB | 623744 KB | 1352 KB | 688 KB | 79% |
| airlineWithRowComp | 10000000 | 1262520 KB | 1258880 KB | 2552 KB | 1088 KB | 58% |
| airlineColumnar | 9999999 | 201992 KB | 201624 KB | n/a | 368 KB | 93% |

## Vs の整数を使用しています。数式内の文字列

この実験で `rxLinMod` 航空会社のテーブルで使用されました (場所 *DayOfWeek* 文字列) と *airlineWithIndex* (ここで *DayOfWeek* 整数)。 最初のケースの `colInfo` 因子レベルを指定するために使用された (`Monday`, 、`Tuesday`, ...)。 2 番目の `colInfo` が指定されていません。 どちらの場合も、同次数式が使用されていました。 使用される数式は `ArrDelay ~ CRSDepTime + DayOfWeek`です。 次の結果には、整数と文字列を使用する利点は、明確に示しています。

| テーブル名 | テストの名前 | 平均時間 |
| ---------- | --------- | ------------ |
| 航空会社 | FactorCol | 10.72 |
| airlineWithIntCol | IntCol | 3.4475 |

## 圧縮を使用します。

この実験で `rxLinMod` で使用されていた、 *airlineWithIndex*, 、*airlineWithPageComp*, 、および *airlineWithRowComp* テーブルです。 同じ式およびクエリは、すべてのテーブルで使用しました。 

| テーブル名 | テストの名前 | numTasks | 平均時間 |
| ---------- | --------- | -------- | ------------ |
| airlineWithIndex | NoCompression | 1 | 5.6775 |
| &nbsp; | &nbsp; | 4 | 5.1775 |
| airlineWithPageComp | PageCompression | 1 | 6.7875 |
| &nbsp; | &nbsp; | 4 | 5.3225 |
| airlineWithRowComp | RowCompression | 1 | 6.1325 |
| &nbsp; | &nbsp; | 4 | 5.2375 |

その圧縮だけに注意してください (*numTasks* 1 に設定) がないと思われるこの例では、[ヘルプの IO 時間の低下、圧縮を処理するために CPU の増加を補正とします。 しかし、ときに、テストが並列実行を設定して *numTasks* から 4、平均時間が減少します。 大規模なデータセットの圧縮の効果がさらに顕著可能性があります。 圧縮は、実験は、データ セットには、効果の圧縮を決定に必要となる可能性がありますので、データ セットと、値に依存します。

## 変換関数を回避します。

この実験で `rxLinMod` airlineWithIndex テーブルと変換関数を使用せずに使用します。  

| テストの名前 | 平均時間 |
| --------- | ------------ |
| WithTransformation | 5.1675 |
| WithoutTransformation | 4.7 |

時間の改善があることに注意してください (それぞれの列が事前計算され、テーブルに保持されて) 変換関数を使用していない場合。 節約は、多くの複数の変換が存在し、データ セットが大きい (> 100 M) 場合に非常に大きいになります。

## 列ストアを使用します。

この実験で `rxLinMod` のすべての変換を使用せず、airlineWithIndex および airlineColumnar テーブルで使用されていた。 結果は、列のストアを行ストアより実行できることを示しています。 大きなデータ セット (> 100 M) のパフォーマンスに大きな違いがあります。  

| テーブル名 | テストの名前 |平均時間 |
| ---------- | --------- | ------------ |
| airlineWithIndex | 行ストア | 4.67 |
| airlineColumnar | ColStore | 4.555 |

## キューブ パラメーターの影響

この実験で `rxLinMod` 航空会社の表で使用場所 `DayOfWeek` 文字列として格納されます。 使用される数式は `ArrDelay ~ Origin:DayOfWeek + Month + DayofMonth + CRSDepTime`です。 結果を明確に示すを使用する `cube` パラメーターにより、パフォーマンスとします。 

| テストの名前 | キューブ パラメーター | numTasks | 平均時間 | 1 つの行の予測 (ArrDelay_Pred) |
| --------- | -------------- | -------- | ------------ | ------------------------------- |
| CubeArgEffect | `cube = F` | 1 | 91.0725 | 9.959204 |
| &nbsp; | &nbsp; | 4 | 44.09 | 9.959204 |
| &nbsp; | `cube = T` | 1 | 21.1125 | 9.959204 |
| &nbsp; | &nbsp; | 4 | 8.08 | 9.959204 |

## RxDTree の maxDepth の効果

この実験で `rxDTree` airlineColumnar テーブルで使用します。 いくつかの値が異なる *maxDepth* 実行時の複雑さに与える影響を示すために使用されました。 深さが多いほど、ノードの合計数が急激に増加し、経過時間が大幅に長くなります。 このテスト *numTasks* 4 に設定されました。

| テストの名前 | maxDepth | 平均時間 |
| --------- | -------- | ------------ |
| TreeDepthEffect | 1 | 10.1975 |
| &nbsp; | 2 | 13.2575 |
| &nbsp; | 4 | 19.27 |
| &nbsp; | 8 | 45.5775 |
| &nbsp; | 16 | 339.54 |

## 電源オプションの影響

この実験で `rxLinMod` Windows がバランスと高パフォーマンスの両方を電源オプションを設定中に、airlineWithIntCol テーブルで使用されました。 すべてのテストの *numTasks* 1 に設定されました。 テストでは、6 回実行され、バランス電源オプションを使用する場合は、結果の変動性を示すためには、両方の電源オプション] の下 2 回実行されました。 結果は、番号より一貫性のある、高いパフォーマンスの電源オプションの高速なことを示します。 

__高パフォーマンス__ 電源オプション。

| テストの名前 | [実行] # | 経過時間 | 平均時間 |
| --------- | ----- | ------------ | ------------ |
| IntCol | 1 | 3.57 (秒) | &nbsp; |
| &nbsp; | 2 | 3.45 (秒) | &nbsp; |
| &nbsp; | 3 | 3.45 (秒) | &nbsp; |
| &nbsp; | 4 | 3.55 (秒) | &nbsp; |
| &nbsp; | 5 | 3.55 (秒) | &nbsp; |
| &nbsp; | 6 | 3.45 (秒) | &nbsp; |
| &nbsp; | &nbsp; | &nbsp; | 3.475 |
| &nbsp; | 1 | 3.45 (秒) | &nbsp; |
| &nbsp; | 2 | 3.53 (秒) | &nbsp; |
| &nbsp; | 3 | 3.63 (秒) | &nbsp; |
| &nbsp; | 4 | 3.49 (秒) | &nbsp; |
| &nbsp; | 5 | 3.54 (秒) | &nbsp; |
| &nbsp; | 6 | 3.47 (秒) | &nbsp; |
| &nbsp; | &nbsp; | &nbsp; | 3.5075 |

__分散__ 電源オプション。

| テストの名前 | [実行] # | 経過時間 | 平均時間 |
| --------- | ----- | ------------ | ------------ |
| IntCol | 1 | 3.89 (秒) | &nbsp; |
| &nbsp; | 2 | 4.15 (秒) | &nbsp; |
| &nbsp; | 3 | 3.77 (秒) | &nbsp; |
| &nbsp; | 4 | 5 秒 | &nbsp; |
| &nbsp; | 5 | 3.92 (秒) | &nbsp; |
| &nbsp; | 6 | 3.8 (秒) | &nbsp; |
| &nbsp; | &nbsp; | &nbsp; | 3.91 |
| &nbsp; | 1 | 3.82 (秒) | &nbsp; |
| &nbsp; | 2 | 3.84 (秒) | &nbsp; |
| &nbsp; | 3 | 3.86 (秒) | &nbsp; |
| &nbsp; | 4 | 4.07 (秒) | &nbsp; |
| &nbsp; | 5 | 4.86 (秒) | &nbsp; |
| &nbsp; | 6 | 3.75 秒 | &nbsp; |
| &nbsp; | &nbsp; | &nbsp; | 3.88 |

## 保存されたモデルを使用して予測

この実験では、モデルが作成され、データベースに格納します。 [保存されたモデルは、データベースとメモリ (ローカル計算コンテキスト) 内の 1 つの行のデータ フレームを使用して作成した予測から読み込まれます。 トレーニング、保存、およびモデルを読み込むおよび予測にかかる時間を次に示します。 これは、予測を行う高速な方法では明確にします。 テストの結果は、モデルを保存するときと、モデルの読み込みや予測にかかる時間を表示します。 

| テーブル名 | テストの名前 | (モデルのトレーニング) にかかる平均時間 | モデルの保存と読み込みを行う時間 |
| ---------- | --------- | ----- | ----- |
| 航空会社 | SaveModel | 21.59 | 2.08 | 
| &nbsp; | LoadModelAndPredict | &nbsp; |  2.09 (を予測する時間を含む) |


## パフォーマンスのトラブルシューティング

このセクションで使用されるテストを使用してそれぞれの実行用の出力ファイルを生成する、 *reportProgress* は値を持つテストに渡されるパラメーター `3`します。 コンソール出力が出力ディレクトリにあるファイルに出力します。 出力ファイルには、IO、切り替え効果時間およびコンピューティング時間で費やされた時間に関する情報が含まれています。 このような場合は、トラブルシューティングと診断に役立ちます。 テスト スクリプトでは、その時間帯の実行にかかる平均時間を考案するさまざまな実行を処理します。 これらのテスト スクリプトと手法にも役立ちます問題解決時の rx 分析関数を使用する場合に、 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]です。 たとえば、次に示します実行のサンプルの時刻。 関心のある主なタイミングは (IO 時間) の読み取りの合計時間 (オーバーヘッドの計算プロセスを設定する) を移行します。

    Running IntCol Test. Using airlineWithIntCol table.  
        run  1  took  3.66  seconds  
        run  2  took  3.44  seconds  
        run  3  took  3.44  seconds  
        run  4  took  3.44  seconds  
        run  5  took  3.45  seconds  
        run  6  took  3.75  seconds  

    Average Time:  3.4425  
                    metric   time    pct 
    1           Total time 3.4425 100.00 
    2 Overall compute time 2.8512  82.82 
    3      Total read time 2.5378  73.72 
    4      Transition time 0.5913  17.18 
    5    Total non IO time 0.3134   9.10 
 
 ## 参照
 [SQL Server R サービス パフォーマンス チューニング ガイド](../../advanced-analytics/r-services/sql-server-r-services-performance-tuning.md)
 
 [R のサービスの SQL Server の構成](../../advanced-analytics/r-services/sql-server-configuration-r-services.md)
 
 [R とデータの最適化](../../advanced-analytics/r-services/r-and-data-optimization-r-services.md)