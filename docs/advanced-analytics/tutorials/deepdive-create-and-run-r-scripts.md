---
title: RevoScaleR のチュートリアル - SQL Server Machine Learning の概要統計情報を計算します。
description: SQL Server で R 言語を使用して概要統計情報の統計を計算する方法のチュートリアル。
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 883a4afa68571c18e6dcaffe96d12644f611f99a
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58510259"
---
# <a name="compute-summary-statistics-in-r-sql-server-and-revoscaler-tutorial"></a>R (SQL Server と RevoScaleR チュートリアル) で概要統計情報を計算します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

このレッスンの一部である、 [RevoScaleR チュートリアル](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)を使用する方法の[RevoScaleR 関数](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)と SQL Server。

この 1 つで高性能の R スクリプトを実行するのに、確立されているデータ ソースと前のレッスンで作成した計算コンテキストを使用します。 このレッスンでは、ローカルとリモート サーバーの計算コンテキストを使用して、次のタスク。

> [!div class="checklist"]
> * SQL Server 計算コンテキストを切り替える
> * リモート データ オブジェクトの概要統計情報を取得します。
> * ローカル サマリーを計算します。

前のレッスンを完了すると場合、これらのリモート コンピューティング コンテキストが必要: sqlCompute sqlComputeTrace とします。 使用するフォワードして、移動は sqlCompute とローカル コンピューティング コンテキスト以降のレッスンでします。

R IDE を使用するか、 **Rgui**このレッスンでは、R スクリプトを実行します。

## <a name="compute-summary-statistics-on-remote-data"></a>リモート データの概要統計情報を計算します。

リモートでの R コードを実行するには、リモート コンピューティング コンテキストを指定する必要があります。 後続のすべての計算実行、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で指定されたコンピューター、 *sqlCompute*パラメーター。

コンピューティング コンテキストは、変更するまでアクティブなままです。 ただし、R スクリプト*できません*リモート サーバー コンテキストで実行を自動的にローカルで実行します。

コンピューティング コンテキストの動作を確認するには、リモートの SQL Server で sqlFraudDS データ ソースの概要統計情報を生成します。 このデータ ソース オブジェクトを作成した[レッスン 2](deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md) RevoDeepDive データベース ccFraudSmall テーブルを表します。 

1. SqlCompute 前のレッスンで作成するには、コンピューティング コンテキストを切り替えます。
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```

2. 呼び出す、 [rxSummary](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsummary)関数し、数式や、データ ソースなどの必須の引数を渡すし、結果を変数に割り当てる`sumOut`します。
  
    ```R
    sumOut <- rxSummary(formula = ~gender + balance + numTrans + numIntlTrans + creditLine, data = sqlFraudDS)
    ```
  
    R 言語には、多くの集計関数が用意されていますが、 **rxSummary**で**RevoScaleR**などのさまざまなリモート コンピューティング コンテキストで実行をサポート[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 同様の機能については、[RevoScaleR を使用してデータを集計](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-data-summaries)を参照してください。
  
3. コンソールに sumOut の内容を印刷します。
  
    ```R
    sumOut
    ```
    > [!NOTE]
    > エラーが発生する場合は、実行が、コマンドを再試行する前に完了するまで数分を待機します。

**結果**

```R
Summary Statistics Results for: ~gender + balance + numTrans + numIntlTrans + creditLine
Data: sqlFraudDS (RxSqlServerData Data Source)
Number of valid observations: 10000

 Name  Mean    StdDev  Min Max ValidObs    MissingObs
 balance       4075.0318 3926.558714            0   25626 100000
 numTrans        29.1061   26.619923 0     100 10000    0           100000
 numIntlTrans     4.0868    8.726757 0      60 10000    0           100000
 creditLine       9.1856    9.870364 1      75 10000    0          100000
 
 Category Counts for gender
 Number of categories: 2
 Number of valid observations: 10000
 Number of missing observations: 0

 gender Counts
  Male   6154
  Female 3846
```

## <a name="create-a-local-summary"></a>ローカル サマリーを作成します。

1. すべての作業をローカルに行うように計算コンテキストを変更します。
  
    ```R
    rxSetComputeContext ("local")
    ```
  
2. SQL Server からデータを抽出するときに多くの場合、取得できますパフォーマンスを向上させる 1 回の読み取り、抽出された行の数を増やすことでメモリの増加のブロック サイズを確保できると仮定した場合します。 値を増やすには、次のコマンドを実行、 *rowsPerRead*データ ソースのパラメーター。 これまでは、 *rowsPerRead* の値は 5000 に設定されていました。
  
    ```R
    sqlServerDS1 <- RxSqlServerData(
       connectionString = sqlConnString,
       table = sqlFraudTable,
       colInfo = ccColInfo,
       rowsPerRead = 10000)
    ```

3. 呼び出す**rxSummary**新しいデータ ソース。
  
    ```R
    rxSummary(formula = ~gender + balance + numTrans + numIntlTrans + creditLine, data = sqlServerDS1)
    ```
  
   実際の結果は、 **コンピューターのコンテキストで** rxSummary [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行した場合と同じになるはずです。 ただし、処理は速くなる場合と遅くなる場合があります。 データは分析のためのローカル コンピューターに転送されるので、処理速度はデータベースへの接続に左右されます。

4. 以降のいくつかのレッスンのコンピューティング コンテキストをリモートにスイッチ_バックします。

    ```R
    rxSetComputeContext(sqlCompute)
    ```

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [R を使用して SQL Server のデータを表示する](../../advanced-analytics/tutorials/deepdive-visualize-sql-server-data-using-r.md)