---
title: RevoScaleR rxDataStep - SQL Server Machine Learning を使用したデータを変換します。
description: SQL Server で R 言語を使用してデータを変換する方法のチュートリアル。
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 8a339d52b04b297227e28833ea490f615ed268f9
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58510379"
---
# <a name="transform-data-using-r-sql-server-and-revoscaler-tutorial"></a>R (SQL Server と RevoScaleR チュートリアル) を使用してデータを変換します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

このレッスンの一部である、 [RevoScaleR チュートリアル](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)を使用する方法の[RevoScaleR 関数](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)と SQL Server。

このレッスンでについて説明します、 **RevoScaleR**分析のさまざまな段階でデータを変換する関数。

> [!div class="checklist"]
> * 使用**rxDataStep**作成し、データのサブセットを変換するには
> * 使用**rxImport**のインポート中に、XDF ファイルまたはメモリ内のデータ フレームとの間の転送中のデータを変換するには

データ移動専用ではありませんが、 **rxSummary**、 **rxCube**、 **rxLinMod**、 **rxLogit** の各関数もすべてデータ変換をサポートします。

## <a name="use-rxdatastep-to-transform-variables"></a>RxDataStep を使用して変数を変換するには

[rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) 関数は一度に 1 つのチャンクのデータを処理し、1 つのデータ ソースからデータを読み取って別のデータ ソースに書き込みます。 変換する列や読み込む変換などを指定できます。

この例を興味深いにするには、するのにには、データを変換するのに別の R パッケージから関数を使用してみましょう。 **boot** パッケージは "推奨" パッケージの 1 つであり、 **boot** は R のすべてのディストリビューションに含まれますが、起動時に自動的に読み込まれることはありません。 そのため、パッケージが既に利用できます、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスの R 統合用に構成します。

**ブート**関数を使用してパッケージを**inv.logit**、これは、ロジットの逆数を計算します。 つまり、 **inv.logit** 関数はロジットを [0,1] のスケールで確率に変換します。

> [!TIP] 
> このスケールの予測を取得するもう 1 つの方法としては、 *rxPredict* の元の呼び出しで **type** パラメーターを **response**に設定します。

1. テーブル用のデータを保持するためにデータ ソースを作成して開始`ccScoreOutput`します。
  
    ```R
    sqlOutScoreDS <- RxSqlServerData( table =  "ccScoreOutput",  connectionString = sqlConnString, rowsPerRead = sqlRowsPerRead )
    ```
  
2. テーブルのデータを保持するために別のデータ ソースを追加`ccScoreOutput2`します。
  
    ```R
    sqlOutScoreDS2 <- RxSqlServerData( table =  "ccScoreOutput2",  connectionString = sqlConnString, rowsPerRead = sqlRowsPerRead )
    ```
  
    新しいテーブルで、前のすべての変数を格納`ccScoreOutput`テーブルに加えて、新しく作成された変数。
  
3. 計算コンテキストを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに設定します。
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
4. 関数を使用して**rxSqlServerTableExists**を確認するかどうか、出力テーブル`ccScoreOutput2`; が存在して、そうである場合は、関数を使用して既に**rxSqlServerDropTable**テーブルを削除します。
  
    ```R
    if (rxSqlServerTableExists("ccScoreOutput2"))     rxSqlServerDropTable("ccScoreOutput2")
    ```
  
5. **rxDataStep** 関数を呼び出して、一覧で目的の変換を指定します。
  
    ```R
    rxDataStep(inData = sqlOutScoreDS,
        outFile = sqlOutScoreDS2,
        transforms = list(ccFraudProb = inv.logit(ccFraudLogitScore)),
        transformPackages = "boot",
        overwrite = TRUE)
    ```

    各列に適用される変換を定義するときは、変換の実行に必要な追加の R パッケージも指定できます。  実行できる変換の種類の詳細については、[RevoScaleR を使用してデータを変換およびサブセット方法](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-data-transform)を参照してください。
  
6. **rxGetVarInfo** を呼び出して、新しいデータ セットの変数の概要を表示します。
  
```R
rxGetVarInfo(sqlOutScoreDS2)
```

**結果**

```R
Var 1: ccFraudLogitScore, Type: numeric
Var 2: state, Type: character
Var 3: gender, Type: character
Var 4: cardholder, Type: character
Var 5: balance, Type: integer
Var 6: numTrans, Type: integer
Var 7: numIntlTrans, Type: integer
Var 8: creditLine, Type: integer
Var 9: ccFraudProb, Type: numeric
```

元のロジット スコアは保持されますが、新しい列の *ccFraudProb*が追加されており、ロジット スコアが 0 ～ 1 の値として表示されます。

因子変数が、テーブルに書き込まれた通知`ccScoreOutput2`文字データとして。 以降の解析で因子として使用するには、 *colInfo* パラメーターを使用してレベルを指定します。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [rxImport を使用してメモリにデータを読み込む](../../advanced-analytics/tutorials/deepdive-load-data-into-memory-using-rximport.md)