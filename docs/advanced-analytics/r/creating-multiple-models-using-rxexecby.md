---
title: "RxExecBy を使用して複数のモデルを作成する |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/18/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 55d194bf888defeebba64eeb4bb87ac04363cefb
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="creating-multiple-models-using-rxexecby"></a>RxExecBy を使用して複数のモデルを作成します。

SQL Server 2017 CTP 2.0 には、新しい関数が含まれています。 **rxExecBy**、複数の関連モデルの並列処理をサポートします。 電車いずれかのような複数のエンティティからのデータに基づいて、非常に大規模なモデルではなく、データ サイエンティストは非常に短時間、多くの関連モデルを作成、単一のエンティティに固有のデータを使用して各します。

たとえば、デバイスの障害を監視している機器のさまざまな種類のデータをキャプチャします。 RxExecBy を使用すると、入力として 1 つの大規模なデータセットを提供、デバイスの種類など、データセットを層化する列を指定でき、個々 のデバイスの複数のモデルのモデルを作成できます。

このプロセスがされていると呼ばれます"pleasingly parallel"処理が、データ サイエンティストをある程度煩雑または最善で面倒と高速で単純な操作を使用するタスクを受け取るためです。

この方法の一般的なアプリケーションには、個々 の世帯スマート メーターの予測、別の製品ラインの売上予測を作成する、または個々 の銀行の分岐に合わせたローンの承認モデルを作成するが含まれます。

## <a name="how-rxexec-works"></a>RxExec のしくみ

RevoScaleR で rxExecBy 関数は、小さなデータ セットの数が多いよりも処理を大量並列に適しています。

1. R コードの一部として、rxExecBy 関数を呼び出すし、順序付けられていないデータのデータセットを渡します。
2. データをグループ化され並べ替えられるパーティションを指定します。
3. 変換またはデータの各パーティションに適用される関数をモデリング定義します。
4. 関数が実行されると、環境内でサポートされる場合に、データ クエリが並列で処理されます。 さらに、モデリングまたは変換タスクが個別のコア間で分散し、並列で実行します。 サポートされているコンピューティング コンテキスト RxSpark と RxInSQLServer 3 つの操作が含まれます。
5. 複数の結果が返されます。

## <a name="rxexecby-syntax-and-examples"></a>rxExecBy 構文と例

**rxExecBy**は 4 つの入力がパーティション分割するデータセットまたはデータ ソース オブジェクトをされている入力の 1 つに、指定した**キー**列です。 この関数は、パーティションごとに出力を返します。 出力の形式は、引数として渡される関数によって決まります。、、、など rxLinMod などのモデリング機能を渡す場合は、データセットのパーティションごとに個別のトレーニング済みモデルを返すことができます。

### <a name="supported-functions"></a>サポートされる関数

モデリング: `rxLinMod`、 `rxLogit`、 `rxGlm`、`rxDtree`

スコア付け: `rxPredict`、

変換または分析:`rxCovCor`

## <a name="example"></a>例

次の例では、[DayOfWeek] 列にパーティション分割されている航空会社データセットを使用して複数のモデルを作成する方法を示します。 ユーザー定義関数、 `delayFunc`、呼び出し元 rxExecBy では各パーティションに適用します。 この関数は、月曜日、火曜日の異なるモデルを作成となります。

```SQL
EXEC sp_execute_external_script
@language = N'R'
, @script = N'
delayFunc <- function(key, data, params) { 
    df <- rxImport(inData = airlineData) 
    rxLinMod(ArrDelay ~ CRSDepTime, data = df) 
} 
OutputDataSet <- rxExecBy(airlineData, c("DayOfWeek"), delayFunc)
'
, @input_data_1 = N'select ArrDelay, DayOfWeek, CRSDepTime from AirlineDemoSmall]'
, @input_data_1_name = N'airlineData'

```

エラーが発生した場合`varsToPartition is invalid`、キー列または列の名前が正しく入力されているかどうかを確認します。 R 言語と小文字は区別されます。

SQL を使用してデータをグループ化、パフォーマンス向上のため for SQL Server では、次の例が最適化されていないと、多くの場合に可能性があります。 ただし、rxExecBy を使用すると、ジョブを作成できます並列 r です。 から

次の例は、計算コンテキストとして SQL Server を使用して、R でプロセスを示しています。

```R
sqlServerConnString <- "SERVER=hostname;DATABASE=TestDB;UID=DBUser;PWD=Password;"
inTable <- paste("airlinedemosmall")
sqlServerDataDS <- RxSqlServerData(table = inTable, connectionString = sqlServerConnString)

# user function
".Count" <- function(keys, data, params)
{
  myDF <- rxImport(inData = data)
  return (nrow(myDF))
}

# Set SQL Server compute context with level of parallelism = 2
sqlServerCC <- RxInSqlServer(connectionString = sqlServerConnString, numTasks = 4)
rxSetComputeContext(sqlServerCC)

# Execute rxExecBy in SQL Server compute context
sqlServerCCResults <- rxExecBy(inData = sqlServerDataDS, keys = c("DayOfWeek"), func = .Count)
```


