---
title: RxExecBy - SQL Server Machine Learning Services を使用して複数のモデルを作成します。
description: RevoScaleR ライブラリから rxExecBy 関数を使用して、SQL Server に格納されているマシンのデータに対して複数のミニ モデルを作成します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 246f786243a95598f899034b3e0c67481d4082e5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62641832"
---
# <a name="creating-multiple-models-using-rxexecby"></a>rxExecBy を使用して複数のモデルを作成する
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

**RxExecBy** revoscaler 関数は、複数の関連モデルの並列処理をサポートしています。 大規模なモデルが複数のようなエンティティからデータに基づくいずれかのトレーニングではなく、データ サイエンティストはすぐに多数の関連モデルを作成、単一のエンティティに固有のデータを使用して各します。 

たとえば、デバイスの障害の監視はさまざまな種類の機器のデータをキャプチャします。 RxExecBy を使用すると、入力として 1 つの大規模なデータセットを提供、デバイスの種類など、データセット、層化する列を指定および、個々 のデバイスの複数のモデルを作成することができます。

このユース ケースと呼ばれるされて[「pleasingly 並列」](https://en.wikipedia.org/wiki/Embarrassingly_parallel)のため同時処理の構成要素に大きい複雑な問題を中断します。

このアプローチの一般的なアプリケーションには、個々 の世帯スマート メーターの予測の別の製品ラインの収益予測を作成またはの個々 の銀行の支店に合わせたローン承認モデルの作成が含まれます。

## <a name="how-rxexec-works"></a>RxExec のしくみ

Revoscaler rxExecBy 関数は、大量並列の小さなデータ セットの数が多い処理に適しています。

1. R コードの一部として rxExecBy 関数を呼び出し、順序付けられていないデータのデータセットを渡すとします。
2. パーティションをデータがグループ化して並べ替えを指定します。
3. 変換またはデータの各パーティションに適用される関数をモデル化を定義します。
4. 関数を実行すると、環境内でサポートされている場合、データのクエリが並列で処理されます。 さらに、モデリングまたは変換タスクが個々 のコア間で分散し、並列で実行します。 サポートされているコンピューティング コンテキストとして、RxSpark と RxInSQLServer 3 つの操作が含まれます。
5. 複数の結果が返されます。

## <a name="rxexecby-syntax-and-examples"></a>rxExecBy 構文と例

**rxExecBy**は 4 つの入力をパーティション分割するデータセットまたはデータ ソース オブジェクトをされている入力の 1 つに、指定した**キー**列。 関数は、パーティションごとに出力を返します。 出力の形式は、引数として渡される関数に依存します。 たとえば、rxLinMod などのモデリング関数を渡す場合は、データセットのパーティションごとに個別のトレーニング済みモデルを返すことができます。

### <a name="supported-functions"></a>サポートされる関数

モデリング: `rxLinMod`、 `rxLogit`、 `rxGlm`、 `rxDtree`

スコア付け: `rxPredict`、

変換または分析: `rxCovCor`

## <a name="example"></a>例

次の例では、航空会社のデータセットは [DayOfWeek] 列でパーティション分割を使用して複数のモデルを作成する方法を示します。 ユーザー定義関数、 `delayFunc`、呼び出し元 rxExecBy によって各パーティションに適用されます。 関数は、月曜日、火曜日の別のモデルを作成します。 など。

```sql
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

エラーが発生した場合`varsToPartition is invalid`、キー列または列の名前が正しく入力されているかどうかを確認します。 R 言語は大文字小文字を区別します。

この例は、SQL Server の最適化されていないとすることが多くの場合のパフォーマンス向上 SQL データのグループを使用しています。 ただし、rxExecBy を使用して、ジョブを作成できます並列 r

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


