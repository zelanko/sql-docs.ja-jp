---
title: "SQL Server と XDF ファイル間でデータを移動 |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/18/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
dev_langs: R
ms.assetid: 40887cb3-ffbb-4769-9f54-c006d7f4798c
caps.latest.revision: "17"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2579c75a4d99e04d5cae60870632c45b52a56cac
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="move-data-between-sql-server-and-xdf-file"></a>SQL Server と XDF ファイル間のデータの移動

両方のローカル データ ファイルにアクセス権があるローカル コンピューティング コンテキストを使用する場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (RxSqlServerData データ ソースとして定義されている) データベース。

ここでは、データの変換を実行できるように、データを取得し、ローカル コンピューター上のファイルにそれを保存する方法を学習します。 完了したら、するを使用して、データ ファイルを新規作成[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]rxDataStep を使用して、テーブルです。
  
## <a name="create-a-sql-server-table-from-an-xdf-file"></a>XDF ファイルから SQL Server テーブルを作成する

RxImport 関数では、ローカル XDF ファイルに任意のサポートされているデータ ソースからデータをインポートすることができます。 ローカル ファイルを使用することは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに格納されているデータに対して多くのさまざまな分析を実行し、同じクエリを何度も実行したくない場合に便利なことがあります。

この練習では、クレジット カードの不正使用データを再度使用します。 このシナリオでは、カリフォルニア、オレゴン、ワシントンの各州のユーザーに対して追加の分析を実行するように求められています。 効率向上のため、これらの州のデータだけをローカル コンピューターに格納し、性別、カード会員、州、および残高の変数を操作します。

1. 以前に作成した *stateAbb* ベクトルを再利用して、含めるレベルを特定し、新しい変数 *statesToKeep*をコンソールに出力します。
  
    ```R
    statesToKeep <- sapply(c("CA", "OR", "WA"), grep, stateAbb)
    statesToKeep
    ```
    **[結果]**
    
    CA|または|WA
    ----|----|----
    5|38|48
    
2. 次に、 [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリを使用し、SQL Server から引き渡すデータを定義します。  後で、この変数は *rxImport* の *inData*引数として使用します。
  
    ```R
    importQuery <- paste("SELECT gender,cardholder,balance,state FROM",  sqlFraudTable,  "WHERE (state = 5 OR state = 38 OR state = 48)")
    ```
  
    クエリにライン フィードやタブなどの隠し文字がないことを確認します。
  
3. 次に、R. 内のデータを操作するときに使用する列を定義しますたとえば、小さいデータ セットはのみの 3 つの状態のデータが返されますのでのみの 3 つの要素レベルが必要です。  *statesToKeep* 変数を再利用して、含める正しい水準を特定できます。
  
    ```R
    importColInfo <- list(
        gender = list( type = "factor",  levels = c("1", "2"), newLevels = c("Male", "Female")),
        cardholder = list(  type = "factor",  levels = c("1", "2"), newLevels = c("Principal", "Secondary")),
        state = list(   type = "factor",  levels = as.character(statesToKeep), newLevels = names(statesToKeep))
            )
    ```
  
4. コンピューティング コンテキストを設定**ローカル**ローカル コンピューター上で使用できるすべてのデータをするため、します。
  
    ```R
    rxSetComputeContext("local")
    ```
  
5. RxSqlServerData への引数として定義したすべての変数を渡すことによって、データ ソース オブジェクトを作成します。
  
    ```R
    sqlServerImportDS <- RxSqlServerData(
        connectionString = sqlConnString,
        sqlQuery = importQuery,
        colInfo = importColInfo)
    ```
  
6. 次に、 **rxImport**という名前のファイルにデータを書き込む`ccFraudSub.xdf`、現在の作業ディレクトリにします。
  
    ```R
    localDS <- rxImport(inData = sqlServerImportDS,
        outFile = "ccFraudSub.xdf",
        overwrite = TRUE)
    ```
  
    *LocalDs* rxImport 関数によって返されるオブジェクトは、ローカル ディスクに保存 ccFraud.xdf データ ファイルを表す軽量 RxXdfData データ ソース オブジェクト。
  
7. データのスキーマが同じであることを確認する XDF ファイル rxGetVarInfo を呼び出します。
  
    ```R
    rxGetVarInfo(data = localDS)
    ```

    **[結果]**
    
    *rxGetVarInfo(data = localDS)*

    *Var 1: gender, Type: factor, no factor levels available*

    *Var 2: cardholder, Type: factor, no factor levels available*

    *Var 3: balance, Type: integer, Low/High: (0, 22463)*

    *Var 4: state, Type: factor, no factor levels available*
  
8. これでさまざまな R 関数を呼び出して、 *上のソース データの場合と同じように、* localDs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オブジェクトを分析できます。 例:
  
    ```R
    rxSummary(~gender + cardholder + balance + state, data = localDS)
    ```

コンピューティング コンテキストの使用と各種データ ソースの操作を習得したので、何かおもしろいことを試してみましょう。 次の最後のレッスンでは、カスタム R 関数を使用して、それをリモート サーバーで実行し、簡単なシミュレーションを作成します。

## <a name="next-step"></a>次の手順

[単純なシミュレーションを作成します。](../../advanced-analytics/tutorials/deepdive-create-a-simple-simulation.md)

## <a name="previous-step"></a>前の手順

[ローカル コンピューティング コンテキストでのデータを分析します。](../../advanced-analytics/tutorials/deepdive-analyze-data-in-local-compute-context.md)



