---
title: RxImport (SQL と R deep dive) を使用しているメモリにデータを読み込む |Microsoft ドキュメント
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: ea5a977f1504a245e270a93a876ac617d8aa6852
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="load-data-into-memory-using-rximport-sql-and-r-deep-dive"></a>RxImport (SQL と R deep dive) を使用してメモリにデータの読み込み
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事の内容を使用する方法について、データ サイエンス Deep Dive のチュートリアルの一部である[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) SQL Server とします。

[RxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rximport)セッション メモリのデータ フレームやディスク上の XDF ファイルには、データ ソースからデータを移動する関数を使用できます。 移動先としてファイルを指定しない場合、データはデータ フレームとしてメモリに格納されます。

この手順でデータを取得する方法を学びます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、しを使用して、 **rxImport**ローカル ファイルに関心のあるデータを格納する関数。 この方法を利用すると、データベースに対して再クエリすることなく、ローカルの計算コンテキストでデータを繰り返し分析できます。

## <a name="extract-a-subset-of-data-from-sql-server-to-local-memory"></a>SQL Server からローカル メモリにデータのサブセットを抽出します。

さらに詳しく危険度の高いユーザーのみを確認すると判断しました。 ソース テーブルに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は大きい危険度の高い顧客だけに関する情報を取得するためです。 そのデータは、ローカル ワークステーションのメモリ内のデータ フレームを読み込みます。

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

3. 関数を呼び出す[rxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rximport)データ フレームにローカルの R セッションでデータを読み取る。

    ```R
    highRisk <- rxImport(sqlServerProbDS)
    ```

    操作が成功した場合は、次のようなステータス メッセージが表示されます:"Rows Read: 35、合計行の処理済み: 35、チャンク時間の合計: 0.036 秒"

4. 危険度の高いの観測値は、メモリ内のデータ フレームには、これで、データ フレームを操作するのにさまざまな R 関数を使用できます。 たとえば、顧客の order by、リスクのスコアでき、最高のリスクとなる顧客の一覧を印刷できます。

    ```R
    orderedHighRisk <- highRisk[order(-highRisk$ccFraudProb),]
    row.names(orderedHighRisk) <- NULL
    head(orderedHighRisk)
    ```

**結果**

*ccFraudLogitScore   state gender cardholder balance numTrans numIntlTrans creditLine ccFraudProb1*

*9.786345    SD   Male  Principal   23456       25            5 75   0.99994382*

*9.433040    FL Female  Principal   20629       24           28 75   0.99992003*

*8.556785    NY Female  Principal   19064       82           53 43   0.99980784*

*8.188668    AZ Female  Principal   19948       29            0 75   0.99972235*

*7.551699    NY Female  Principal   11051       95            0 75   0.99947516*

*7.335080    NV   Male  Principal   21566        4            6  75   0.9993482*

## <a name="more-about-rximport"></a>rxImport の詳細

**rxImport** は、データの移動だけでなく、読み取りプロセスでデータを変換する場合にも使用できます。 たとえば、幅が固定された列の文字数を指定する、変数の説明を指定する、要素列のレベルを設定する、さらにはインポート後に使用する新しいレベルを作成することもできます。

**RxImport**関数は、インポート処理中に、列を変数名を割り当てますを使用して新しい変数の名前を指定することができます、 *colInfo*パラメーター、または、を使用してデータの種類の変更*colClasses*パラメーター。

*transforms* パラメーターで追加の操作を指定すると、読み取り対象の各データ群に対して基本的な処理を実行できます。

## <a name="next-step"></a>次の手順

[rxDataStep を使用した新しい SQL Server テーブルの作成](../../advanced-analytics/tutorials/deepdive-create-new-sql-server-table-using-rxdatastep.md)

## <a name="previous-step"></a>前の手順

[R を使用したデータの変換](../../advanced-analytics/tutorials/deepdive-transform-data-using-r.md)

