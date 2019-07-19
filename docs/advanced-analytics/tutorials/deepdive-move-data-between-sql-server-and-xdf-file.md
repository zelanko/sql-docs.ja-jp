---
title: SQL Server と RevoScaleR - SQL Server Machine Learning を使用して、XDF ファイル間でデータを移動します。
description: SQL Server で XDF と R 言語を使用してデータを移行する方法に関するチュートリアル。
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: f5800f315ee09328908b612c18faf6c77a7ac13c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962212"
---
# <a name="move-data-between-sql-server-and-xdf-file-sql-server-and-revoscaler-tutorial"></a>SQL Server と XDF ファイル (SQL Server と RevoScaleR チュートリアル) の間でデータを移動します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

このレッスンの一部である、 [RevoScaleR チュートリアル](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)を使用する方法の[RevoScaleR 関数](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)と SQL Server。

この手順では、XDF ファイルを使用して、リモートとローカル計算コンテキストの間でデータを転送するについて説明します。 XDF ファイルにデータを格納するデータの変換を実行することができます。

新たに作成するファイルにデータを使用する設定が完了したら、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブル。 関数は、 [rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep)データに変換を適用することができ、データ フレームと .xdf ファイル間の変換を実行します。
  
## <a name="create-a-sql-server-table-from-an-xdf-file"></a>XDF ファイルから SQL Server テーブルを作成します。

この演習では、データを使用するクレジット_カード詐欺もう一度です。 このシナリオでは、カリフォルニア、オレゴン、ワシントンの各州のユーザーに対して追加の分析を実行するように求められています。 詳細、効率的なを決めたら、ローカル コンピューターでこれらの状態のデータを格納し、変数の性別、カード所有者、状態、および分散のみを使用します。

1. 再利用、`stateAbb`を含めるには、し、新しい変数に書き込むレベルを識別するために以前作成した変数`statesToKeep`します。
  
    ```R
    statesToKeep <- sapply(c("CA", "OR", "WA"), grep, stateAbb)
    statesToKeep
    ```
    **結果**
    
    CA|スイッチまたは|WA
    ----|----|----
    5|38|48
    
2. SQL Server から提供するデータの定義を使用して、[!INCLUDE[tsql](../../includes/tsql-md.md)]クエリ。  この変数を使用して後で、 *inData*引数**rxImport**します。
  
    ```R
    importQuery <- paste("SELECT gender,cardholder,balance,state FROM",  sqlFraudTable,  "WHERE (state = 5 OR state = 38 OR state = 48)")
    ```
  
    クエリにライン フィードやタブなどの隠し文字がないことを確認します。
  
3. 次に、R でデータを扱うときに使用する列を定義します。たとえば、データ セットが小さいはクエリのみの 3 つの状態のデータを返すため、3 つだけの因子レベルが必要。  適用、`statesToKeep`に含める正しい水準を識別する変数。
  
    ```R
    importColInfo <- list(
        gender = list( type = "factor",  levels = c("1", "2"), newLevels = c("Male", "Female")),
        cardholder = list(  type = "factor",  levels = c("1", "2"), newLevels = c("Principal", "Secondary")),
        state = list(   type = "factor",  levels = as.character(statesToKeep), newLevels = names(statesToKeep))
            )
    ```
  
4. コンピューティング コンテキストを設定**ローカル**使用可能なすべてのデータをローカル コンピューターにするためです。
  
    ```R
    rxSetComputeContext("local")
    ```
    
    [RxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdata)関数はローカル XDF ファイルに任意のサポートされているデータ ソースからデータをインポートすることができます。 データに対して多くのさまざまな分析を実行するが、同じクエリを繰り返し実行されないようにする場合に、データのローカル コピーを使用すると便利です。

5. 引数として以前に定義された変数を渡すことによって、データ ソース オブジェクトを作成する**RxSqlServerData**します。
  
    ```R
    sqlServerImportDS <- RxSqlServerData(
        connectionString = sqlConnString,
        sqlQuery = importQuery,
        colInfo = importColInfo)
    ```
  
6. 呼び出す**rxImport**という名前のファイルにデータを書き込む`ccFraudSub.xdf`、現在の作業ディレクトリにします。
  
    ```R
    localDS <- rxImport(inData = sqlServerImportDS,
        outFile = "ccFraudSub.xdf",
        overwrite = TRUE)
    ```
  
    `localDs`によって返されるオブジェクト、 **rxImport**関数は、軽量**RxXdfData**データ ソース オブジェクトを表す、`ccFraud.xdf`データ ファイルをローカル ディスクに保存します。
  
7. XDF ファイルで [rxGetVarInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarinfoxdf) を呼び出し、データ スキーマが同じであることを確認します。
  
    ```R
    rxGetVarInfo(data = localDS)
    ```

    **結果**
    
    ```R
    rxGetVarInfo(data = localDS)
    Var 1: gender, Type: factor, no factor levels available
    Var 2: cardholder, Type: factor, no factor levels available
    Var 3: balance, Type: integer, Low/High: (0, 22463)
    Var 4: state, Type: factor, no factor levels available
    ```

8. 分析するさまざまな R 関数を呼び出すようになりましたことができます、 **localDs**オブジェクト、SQL Server のソース データの場合と同様です。 たとえば、性別による集約する可能性があります。
  
    ```R
    rxSummary(~gender + cardholder + balance + state, data = localDS)
    ```

## <a name="next-steps"></a>次の手順

このレッスンで、マルチパートのチュートリアル シリーズの最後に**RevoScaleR**と SQL Server。 独自のデータとプロジェクトの要件を進めるための基盤を提供、さまざまなデータ関連およびコンピューティング概念が導入されました。

知識を深める**RevoScaleR**、できなかった可能性があります、演習を通じてステップに R のチュートリアルの一覧を返すことができます。 また、一般的なタスクに関する情報のコンテンツの表に、ハウツー記事を確認します。

> [!div class="nextstepaction"]
> [SQL Server の R チュートリアル](sql-server-r-tutorials.md)