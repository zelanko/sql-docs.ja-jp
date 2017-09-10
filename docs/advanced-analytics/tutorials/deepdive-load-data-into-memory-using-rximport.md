---
title: "RxImport を使用しているメモリにデータを読み込む |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/18/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
dev_langs:
- R
ms.assetid: 47a42e9a-05a0-4a50-871d-de73253cf070
caps.latest.revision: 14
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: bfea2db1797638da671cb59ffc4cd4954d145199
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="load-data-into-memory-using-rximport"></a>rxImport を使用してメモリにデータを読み込む

**rxImport** 関数を使用すると、データ ソースから R セッション メモリのデータ フレームに、またはディスク上の XDF ファイルにデータを移動できます。 移動先としてファイルを指定しない場合、データはデータ フレームとしてメモリに格納されます。

この手順でデータを取得する方法を学習[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、し、rxImport 関数を使用して、ローカル ファイルに関心のあるデータを格納します。 この方法を利用すると、データベースに対して再クエリすることなく、ローカルの計算コンテキストでデータを繰り返し分析できます。

## <a name="extract-a-subset-of-data-from-sql-server-to-local-memory"></a>SQL Server のデータのサブセットをローカル メモリに抽出する

高いリスクの個人のみを精査することになった場合を例に説明します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のソース テーブルはサイズが大きいので、高いリスク顧客に関する情報のみを取得し、ローカル ワークステーションのメモリのデータ フレームに読み込みます。

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

3. **rxImport** 関数を使用し、ローカル R セッションのデータ フレームにデータを実際に読み込みます。

    ```R
    highRisk <- rxImport(sqlServerProbDS)
    ```

    操作に成功した場合、「Rows Read: 35, Total Rows Processed: 35, Total Chunk Time: 0.036 seconds」というステータス メッセージが表示されるはずです。

4. メモリのデータ フレームに高いリスクの観察対象が格納されたので、多様な R 関数を使用してデータ フレームを操作できるようになりました。 たとえば、リスク スコアで顧客を並べ替え、高いリスクがあると考えられる顧客を印刷できます。

    ```R
    orderedHighRisk <- highRisk[order(-highRisk$ccFraudProb),]
    row.names(orderedHighRisk) <- NULL
    head(orderedHighRisk)
    ```

**[結果]**

*ccFraudLogitScore   state gender cardholder balance numTrans numIntlTrans creditLine ccFraudProb1*

*9.786345    SD   Male  Principal   23456       25            5 75   0.99994382*

*9.433040    FL Female  Principal   20629       24           28 75   0.99992003*

*8.556785    NY Female  Principal   19064       82           53 43   0.99980784*

*8.188668    AZ Female  Principal   19948       29            0 75   0.99972235*

*7.551699    NY Female  Principal   11051       95            0 75   0.99947516*

*7.335080    NV   Male  Principal   21566        4            6  75   0.9993482*

## <a name="more-about-rximport"></a>rxImport の詳細

読み取り、処理を行ってデータを変換するが、データを移動するだけでなく rxImport を使用することができます。 たとえば、幅が固定された列の文字数を指定する、変数の説明を指定する、要素列のレベルを設定する、さらにはインポート後に使用する新しいレベルを作成することもできます。

RxImport 関数は、インポート処理中に、列に変数名を割り当てますを使用して新しい変数の名前を指定することができます、 *colInfo*して、パラメーターを使用するデータ型を変更できます、 *colClasses*パラメーター。

*transforms* パラメーターで追加の操作を指定すると、読み取り対象の各データ群に対して基本的な処理を実行できます。

## <a name="next-step"></a>次の手順

[RxDataStep を使用して、新しい SQL Server のテーブルを作成します。](../../advanced-analytics/tutorials/deepdive-create-new-sql-server-table-using-rxdatastep.md)

## <a name="previous-step"></a>前の手順

[R を使用するデータを変換します。](../../advanced-analytics/tutorials/deepdive-transform-data-using-r.md)

## <a name="see-also"></a>参照

[機械学習のチュートリアル](../../advanced-analytics/tutorials/machine-learning-services-tutorials.md)


