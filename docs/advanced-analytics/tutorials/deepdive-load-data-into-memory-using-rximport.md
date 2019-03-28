---
title: RevoScaleR rxImport - SQL Server Machine Learning を使用してメモリにデータを読み込む
description: SQL Server で R 言語を使用してデータを読み込む方法のチュートリアル。
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 5fc29872795623bd0d9e72414a15add92591ec7d
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58513019"
---
# <a name="load-data-into-memory-using-rximport-sql-server-and-revoscaler-tutorial"></a>RxImport (SQL Server と RevoScaleR チュートリアル) を使用してメモリにデータを読み込む
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

このレッスンの一部である、 [RevoScaleR チュートリアル](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)を使用する方法の[RevoScaleR 関数](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)と SQL Server。

[RxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rximport)セッションのメモリ内のデータ フレームに、またはディスク上の XDF ファイルには、データ ソースからデータを移動する関数を使用できます。 移動先としてファイルを指定しない場合、データはデータ フレームとしてメモリに格納されます。

この手順でデータを取得する方法を学習します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、しを使用して、 **rxImport**ローカル ファイルに関心のあるデータを格納する関数。 この方法を利用すると、データベースに対して再クエリすることなく、ローカルの計算コンテキストでデータを繰り返し分析できます。

## <a name="extract-a-subset-of-data-from-sql-server-to-local-memory"></a>SQL Server からローカル メモリにデータのサブセットを抽出します。

さらに詳しく危険度の高い個人のみを確認すると判断しました。 ソース テーブル[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サイズが大きいので、危険度の高い顧客のみに関する情報を取得します。 そのデータは、ローカル ワークステーションのメモリ内のデータ フレームに読み込みます。

1. 計算コンテキストをローカル ワークステーションにリセットします。

    ```R
    rxSetComputeContext("local")
    ```

2. 新しい SQL Server データ ソース オブジェクトを作成し、 *sqlQuery* パラメーターに有効な SQL ステートメントを指定します。 この例では、リスク スコアが最上位になっている観察のサブセットが取得されます。 この方法なら、本当に必要なデータのみがローカル メモリに格納されます。

    ```R
    sqlServerProbDS \<- RxSqlServerData(
        sqlQuery = paste("SELECT * FROM ccScoreOutput2",
        "WHERE (ccFraudProb > .99)"),
        connectionString = sqlConnString)
    ```

3. 関数を呼び出す[rxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rximport)をローカルの R セッションでデータ フレームにデータを読み取る。

    ```R
    highRisk <- rxImport(sqlServerProbDS)
    ```

    操作が成功した場合は、次のようなステータス メッセージが表示されます。"の読み取り行数。処理された合計行は、35:35、チャンクの合計時間:0.036 seconds"

4. これで、危険度の高い観察では、インメモリ データ フレームには、データ フレームを操作するのにさまざまな R 関数を使用できます。 たとえば、リスク スコアで顧客を並べ替えおよび、高いリスクをもたらしている顧客の一覧を印刷できます。

    ```R
    orderedHighRisk <- highRisk[order(-highRisk$ccFraudProb),]
    row.names(orderedHighRisk) <- NULL
    head(orderedHighRisk)
    ```

**結果**

```R
ccFraudLogitScore   state gender cardholder balance numTrans numIntlTrans creditLine ccFraudProb1
9.786345    SD   Male  Principal   23456       25            5 75   0.99994382
9.433040    FL Female  Principal   20629       24           28 75   0.99992003
8.556785    NY Female  Principal   19064       82           53 43   0.99980784
8.188668    AZ Female  Principal   19948       29            0 75   0.99972235
7.551699    NY Female  Principal   11051       95            0 75   0.99947516
7.335080    NV   Male  Principal   21566        4            6  75   0.9993482
```

## <a name="more-about-rximport"></a>rxImport の詳細

**rxImport** は、データの移動だけでなく、読み取りプロセスでデータを変換する場合にも使用できます。 たとえば、幅が固定された列の文字数を指定する、変数の説明を指定する、要素列のレベルを設定する、さらにはインポート後に使用する新しいレベルを作成することもできます。

**RxImport**関数は、インポート プロセス中に、列を変数名を割り当てますを使用して新しい変数名を指定することができます、 *colInfo*パラメーター、または、を使用してデータ型を変更*colClasses*パラメーター。

*transforms* パラメーターで追加の操作を指定すると、読み取り対象の各データ群に対して基本的な処理を実行できます。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [rxDataStep を使用した新しい SQL Server テーブルの作成](../../advanced-analytics/tutorials/deepdive-move-data-between-sql-server-and-xdf-file.md)