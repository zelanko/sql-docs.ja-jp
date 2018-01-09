---
title: "SQL Server と XDF ファイル (SQL と R deep dive) 間でデータを移動 |Microsoft ドキュメント"
ms.custom: 
ms.date: 12/14/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to:
- SQL Server 2016
- SQL Server 2017
dev_langs: R
ms.assetid: 40887cb3-ffbb-4769-9f54-c006d7f4798c
caps.latest.revision: "17"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 10be63f32a197134e4979dc976dd84919fde9e1f
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="move-data-between-sql-server-and-xdf-file-sql-and-r-deep-dive"></a>SQL Server と XDF ファイル (SQL と R deep dive) 間でデータを移動します。

この記事の内容を使用する方法について、データ サイエンス Deep Dive のチュートリアルの一部である[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) SQL Server とします。

このステップでは、ファイルを使用して、XDF リモートとローカルの計算コンテキスト間でデータを転送するについて説明します。 XDF ファイルにデータを格納するには、データの変換を実行することができます。

ファイルにデータを使用する、新しいを作成したら、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブル。 関数は、 [rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep)データ フレームと .xdf ファイルの変換を行い、データへの変換を適用することができます。
  
## <a name="create-a-sql-server-table-from-an-xdf-file"></a>XDF ファイルから SQL Server テーブルを作成します。

この演習では、データを使用するクレジット_カード詐欺もう一度です。 このシナリオでは、カリフォルニア、オレゴン、ワシントンの各州のユーザーに対して追加の分析を実行するように求められています。 詳細にするには、効率的なことが決まっているをローカル コンピューターにこれらの状態のデータを格納して、変数の性別、カード会員、状態、および分散のみを使用します。

1. 再利用、`stateAbb`を含めるには、し、新しい変数に書き込んだりレベルを識別するために以前作成した変数`statesToKeep`です。
  
    ```R
    statesToKeep <- sapply(c("CA", "OR", "WA"), grep, stateAbb)
    statesToKeep
    ```
    **結果**
    
    CA|スイッチまたは|WA
    ----|----|----
    5|38|48
    
2. SQL Server から経由で移行するデータの定義を使用して、[!INCLUDE[tsql](../../includes/tsql-md.md)]クエリ。  この変数を使用して後で、*末尾*引数**rxImport**です。
  
    ```R
    importQuery <- paste("SELECT gender,cardholder,balance,state FROM",  sqlFraudTable,  "WHERE (state = 5 OR state = 38 OR state = 48)")
    ```
  
    クエリにライン フィードやタブなどの隠し文字がないことを確認します。
  
3. 次に、R. 内のデータを操作するときに使用する列を定義します。たとえば、小さいデータ セットに、する必要が 3 つだけの要素レベルでは、クエリのみの 3 つの状態のデータを返すため。  適用、`statesToKeep`に含める、適切なレベルを識別する変数。
  
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
    
    [RxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdata)関数はローカル XDF ファイルに任意のサポートされているデータ ソースからデータをインポートすることができます。 データに対して多くのさまざまな分析を行うには、同じクエリを何度も実行しないようにするときに、データのローカル コピーを使用すると便利です。

5. 引数として以前に定義された変数を渡すことによって、データ ソース オブジェクトを作成**RxSqlServerData**です。
  
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
  
    `localDs`によって返されるオブジェクト、 **rxImport**関数は、軽量**RxXdfData**データ ソース オブジェクトを表す、`ccFraud.xdf`データ ファイルがローカル ディスクに保存します。
  
7. XDF ファイルで [rxGetVarInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarinfoxdf) を呼び出し、データ スキーマが同じであることを確認します。
  
    ```R
    rxGetVarInfo(data = localDS)
    ```

    **結果**
    
    *rxGetVarInfo(data = localDS)*

    *Var 1: gender, Type: factor, no factor levels available*

    *Var 2: cardholder, Type: factor, no factor levels available*

    *Var 3: balance, Type: integer, Low/High: (0, 22463)*

    *Var 4: state, Type: factor, no factor levels available*
  
8. これでさまざまな R 関数を呼び出して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 上のソース データの場合と同じように、`localDs` オブジェクトを分析できます。 たとえば、性別に基づいて要約する可能性があります。
  
    ```R
    rxSummary(~gender + cardholder + balance + state, data = localDS)
    ```

コンピューティング コンテキストの使用と各種データ ソースの操作を習得したので、何かおもしろいことを試してみましょう。 [次へ] および最後のレッスンでは、リモート サーバーでカスタム R 関数を実行する単純なシミュレーションを作成します。

## <a name="next-step"></a>次の手順

[簡単なシミュレーションを作成する](../../advanced-analytics/tutorials/deepdive-create-a-simple-simulation.md)

## <a name="previous-step"></a>前の手順

[ローカル計算コンテキストでデータを分析する](../../advanced-analytics/tutorials/deepdive-analyze-data-in-local-compute-context.md)



