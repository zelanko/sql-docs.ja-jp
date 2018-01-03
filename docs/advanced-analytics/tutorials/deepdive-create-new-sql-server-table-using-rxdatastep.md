---
title: "RxDataStep (SQL と R deep dive) を使用して SQL Server テーブルを新規作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 12/14/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to:
- SQL Server 2016
- SQL Server 2017
dev_langs: R
ms.assetid: 98cead96-6de7-4edf-98b9-a1efb09297b9
caps.latest.revision: "19"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 5a414c590f72a1b1cfef9a3dbd8082a500592140
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2017
---
# <a name="create-new-sql-server-table-using-rxdatastep-sql-and-r-deep-dive"></a>RxDataStep (SQL と R deep dive) を使用して新しい SQL Server テーブルを作成します。

この記事の内容を使用する方法について、データ サイエンス Deep Dive のチュートリアルの一部である[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) SQL Server とします。

このレッスンでは、メモリ内のデータ フレームの間でデータを移動する方法を学習、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンテキスト、およびローカル ファイルです。

> [!NOTE]
> このレッスンでは、別のデータセットを使用します。 Airline 遅延データセットは、機械学習の実験に広く使用されているパブリック データセットです。 この例で使用されるデータ ファイルは、他の製品サンプルと同じディレクトリで使用できます。

## <a name="create-sql-server-table-from-local-data"></a>ローカル データから SQL Server テーブルを作成します。

このチュートリアルの前半で使用して、 **RxTextData**テキスト ファイルから R にデータをインポートする関数を使用して、 **RxDataStep**関数にデータを移動する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。

このレッスンでは、別のアプローチとで保存されたファイルからデータを使用して、 [XDF 形式](https://en.wikipedia.org/wiki/Extensible_Data_Format)です。 XDF ファイルを使用してデータの一部の軽量な変換を行うと、後に、新しい変換されたデータを保存する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブル。

**XDF とは何ですか。**

XDF 形式は、高次元データ用に開発された XML 標準とは、ネイティブのファイル形式をによって使用[Machine Learning サーバー](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-xdf)です。 XDF は、R インターフェイスを使用したバイナリ ファイル形式です。行と列の処理と分析を最適化しています。  XDF 形式は、データの移動や、分析に有用なデータのサブセットを格納するために使用できます。

1. 計算コンテキストをローカル ワークステーションに設定します。 **この手順では、DDL のアクセス許可が必要です。**

  
    ```R
    rxSetComputeContext("local")
    ```
  
2. **RxXdfData** 関数を使用して新しいデータ ソース オブジェクトを定義します。 XDF データ ソースを定義するのには、データ ファイルへのパスを指定します。  

    テキストの変数を使用して、ファイルへのパスを指定できます。 ただし、ここを使用する、便利なショートカット、 **rxGetOption**機能、サンプル データ ディレクトリからファイル (AirlineDemoSmall.xdf) を取得します。
  
    ```R
    xdfAirDemo <- RxXdfData(file.path(rxGetOption("sampleDataDir"),  "AirlineDemoSmall.xdf"))
    ```

3. インメモリ データに対して [rxGetVarInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarinfoxdf) を呼び出して、データセットの概要を表示します。
  
    ```R
    rxGetVarInfo(xdfAirDemo)
    ```

**結果**

*Var 1: ArrDelay, Type: integer, Low/High: (-86, 1490)*

*Var 2: CRSDepTime, Type: numeric, Storage: float32, Low/High: (0.0167, 23.9833)*

*Var 3: DayOfWeek 7 factor levels: Monday Tuesday Wednesday Thursday Friday Saturday Sunday*

> [!NOTE]
> 
> ご覧のように、データを XDF ファイルに読み込むために他の関数を呼び出す必要がなく、データに対して **rxGetVarInfo** をすぐに呼び出すことができます。 これは、XDF が RevoScaleR の既定の中間格納方法だからです。 XDF ファイルに加えて、 **rxGetVarInfo**関数では、複数のソースの種類をサポートします。
  
4. このデータに設定する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブルを格納する_DayOfWeek_ 7 ~ 1 の値で、整数として。
  
    そのために、まず SQL Server データ ソースを定義します。
  
    ```R
    sqlServerAirDemo <- RxSqlServerData(table = "AirDemoSmallTest", connectionString = sqlConnString)
    ```
  
5. 同じ名前のテーブルが既に存在しないか確認し、存在する場合はそのテーブルを削除します。
  
    ```R
    if (rxSqlServerTableExists("AirDemoSmallTest",  connectionString = sqlConnString))  rxSqlServerDropTable("AirDemoSmallTest",  connectionString = sqlConnString)
    ```
  
6. テーブルを作成し、 **rxDataStep**の多様な製品サンプルに使用されています。 この関数は、2 つのデータは既にデータ ソースを定義し、途中のデータを変換できる必要に応じてを移動します。
  
    ```R
    rxDataStep(inData = xdfAirDemo, outFile = sqlServerAirDemo,
            transforms = list( DayOfWeek = as.integer(DayOfWeek),
            rowNum = .rxStartRow : (.rxStartRow + .rxNumRows - 1) ),
            overwrite = TRUE )
    ```
  
    これは非常に大きなテーブル、次のような最終的な状態メッセージを表示するを待ってため: *Rows Read: 200000、合計行が処理: 600000*です。
     
7. コンピューティング コンテキストを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューターに戻します。

    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
8. 単純な SQL クエリを新しいテーブルで使用して、新しい SQL Server データ ソースを作成します。 この定義の要素のレベルを追加する、 *DayOfWeek*  列を使用して、 *colInfo*に渡す引数**RxSqlServerData**です。
  
    ```R
    SqlServerAirDemo <- RxSqlServerData(
        sqlQuery = "SELECT * FROM AirDemoSmallTest",
        connectionString = sqlConnString,
        rowsPerRead = 50000,
        colInfo = list(DayOfWeek = list(type = "factor",  levels = as.character(1:7))))
    ```
  
9. 呼び出す**rxSummary**クエリ内のデータの概要を確認します。
  
    ```R
    rxSummary(~., data = sqlServerAirDemo)
    ```

## <a name="next-step"></a>次の手順

[rxDataStep を使用したチャンク分析の実行](../../advanced-analytics/tutorials/deepdive-perform-chunking-analysis-using-rxdatastep.md)

## <a name="previous-step"></a>前の手順

[rxImport を使用してメモリにデータを読み込む](../../advanced-analytics/tutorials/deepdive-load-data-into-memory-using-rximport.md)
