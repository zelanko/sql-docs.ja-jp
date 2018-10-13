---
title: RxExecBy (SQL Server Machine Learning) を使用して複数のモデルを作成する |Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: b83abad65689e3e12310251d09199f5aa0e7c3cb
ms.sourcegitcommit: 0d6e4cafbb5d746e7d00fdacf8f3ce16f3023306
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/11/2018
ms.locfileid: "49085128"
---
# <a name="creating-multiple-models-using-rxexecby"></a>rxExecBy を使用して複数のモデルを作成する
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server 2017 CTP 2.0 には、新しい関数が含まれています。 **rxExecBy**、複数の関連モデルの並列処理をサポートします。 非常に大規模なモデルが複数のようなエンティティからデータに基づくいずれかのトレーニングではなく、データ サイエンティストは非常に高速、多くの関連モデルを作成、単一のエンティティに固有のデータを使用して各します。

たとえば、デバイスの障害を監視してさまざまな種類の機器のデータをキャプチャします。 RxExecBy を使用すると、入力として 1 つの大規模なデータセットを提供、デバイスの種類など、データセット、層化する列を指定および、個々 のデバイスの複数のモデルを作成することができます。

このプロセスがされていると呼ばれる「pleasingly 並列」の処理をタスクが、データ サイエンティストのやや面倒かせいぜい面倒でしたが、操作を高速かつ容易になりますがかかるため。

このアプローチの一般的なアプリケーションには、個々 の世帯スマート メーターの予測の別の製品ラインの収益予測を作成またはの個々 の銀行の支店に合わせたローン承認モデルの作成が含まれます。

## <a name="how-rxexec-works"></a>RxExec のしくみ

Revoscaler rxExecBy 関数は、大量並列の小さなデータ セットの数が多い処理に適しています。

1. R コードの一部として rxExecBy 関数を呼び出し、順序付けられていないデータのデータセットを渡すとします。
2. パーティションをデータがグループ化して並べ替えを指定します。
3. 変換またはデータの各パーティションに適用される関数をモデル化を定義します。
4. 関数を実行すると、環境内でサポートされている場合、データのクエリが並列で処理されます。 さらに、モデリングまたは変換タスクが個々 のコア間で分散し、並列で実行します。 サポートされているコンピューティング コンテキストとして、RxSpark と RxInSQLServer 3 つの操作が含まれます。
5. 複数の結果が返されます。

## <a name="rxexecby-syntax-and-examples"></a>rxExecBy 構文と例

**rxExecBy**は 4 つの入力をパーティション分割するデータセットまたはデータ ソース オブジェクトをされている入力の 1 つに、指定した**キー**列。 関数は、パーティションごとに出力を返します。 出力の形式は、引数として渡される関数によって異なります。、、、など rxLinMod などのモデリング関数を渡す場合は、データセットのパーティションごとに個別のトレーニング済みモデルを返すことができます。

### <a name="supported-functions"></a>サポートされる関数

モデリング: `rxLinMod`、 `rxLogit`、 `rxGlm`、 `rxDtree`

スコア付け: `rxPredict`、

変換または分析: `rxCovCor`

## <a name="example"></a>例

次の例では、航空会社のデータセットは [DayOfWeek] 列でパーティション分割を使用して複数のモデルを作成する方法を示します。 ユーザー定義関数、 `delayFunc`、呼び出し元 rxExecBy によって各パーティションに適用されます。 関数は、月曜日、火曜日の別のモデルを作成します。 など。

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

エラーが発生した場合`varsToPartition is invalid`、キー列または列の名前が正しく入力されているかどうかを確認します。 R 言語は大文字小文字を区別します。

SQL データのグループを使用してパフォーマンス向上のためこの例は、SQL Server の最適化されていないと、多くの場合の可能性があります。 ただし、rxExecBy を使用して、ジョブを作成できます並列 r

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


