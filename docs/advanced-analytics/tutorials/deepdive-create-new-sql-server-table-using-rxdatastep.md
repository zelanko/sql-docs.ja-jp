---
title: "RxDataStep を使用して、新しい SQL Server のテーブルを作成 |Microsoft ドキュメント"
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
ms.assetid: 98cead96-6de7-4edf-98b9-a1efb09297b9
caps.latest.revision: 19
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4a5a8aaa8df1df4d34216f9d55806ccf5594292a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-new-sql-server-table-using-rxdatastep"></a>rxDataStep を使用した新しい SQL Server テーブルの作成

このレッスンでは、インメモリ データ フレーム、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンテキスト、およびローカル ファイルの間でデータを移動する方法を学習します。

> [!NOTE]
> このレッスンでは、別のデータセットを使用します。 Airline 遅延データセットは、機械学習の実験に広く使用されているパブリック データセットです。 R を始めたばかりの場合、このデータセットをテスト用に利用すると便利です。このデータセットは [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] を使用して公開された [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]の多様な製品サンプルに使用されています。 この例に必要なデータ ファイルは、その他の製品サンプルと同じディレクトリにあります。

## <a name="create-sql-server-table-from-local-data"></a>ローカル データから SQL Server テーブルを作成する

このチュートリアルの最初の部分で使用して、 **RxTextData**テキスト ファイルから R にデータをインポートする関数を使用して、 **RxDataStep**関数にデータを移動する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。

このレッスンでは、別のアプローチを使用して、 [XDF 形式](https://en.wikipedia.org/wiki/Extensible_Data_Format)で保存したファイルからデータを取得します。 XDF 形式は、高次元データ用に開発された XML 標準です。 XDF は、R インターフェイスを使用したバイナリ ファイル形式です。行と列の処理と分析を最適化しています。  XDF 形式は、データの移動や、分析に有用なデータのサブセットを格納するために使用できます。

XDF ファイルを使用するデータに簡単な変換を実行した後に、変換後のデータを新しい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルに保存します。

> [!NOTE]
> この手順には、DDL の権限が必要です。

1. 計算コンテキストをローカル ワークステーションに設定します。
  
    ```R
    rxSetComputeContext("local")
    ```
  
2. **RxXdfData** 関数を使用して新しいデータ ソース オブジェクトを定義します。 XDF データ ソースの場合、データ ファイルのパスを指定するだけで済みます。  テキストの変数を使用して、ファイルへのパスを指定する可能性がありますが、ここでは、便利なショートカット サンプル データ ファイル (AirlineDemoSmall.xdf) が rxGetOption 関数によって返される、ディレクトリであるため。
  
    ```R
    xdfAirDemo <- RxXdfData(file.path(rxGetOption("sampleDataDir"),  "AirlineDemoSmall.xdf"))
    ```

3. データセットの概要を表示する、インメモリ データに対する rxGetVarInfo を呼び出します。
  
    ```R
    rxGetVarInfo(xdfAirDemo)
    ```

**[結果]**

*Var 1: ArrDelay, Type: integer, Low/High: (-86, 1490)*

*Var 2: CRSDepTime, Type: numeric, Storage: float32, Low/High: (0.0167, 23.9833)*

*Var 3: DayOfWeek 7 factor levels: Monday Tuesday Wednesday Thursday Friday Saturday Sunday*

> [!NOTE]
> 
> XDF ファイルに、データを読み込む、他の関数を呼び出す必要があるをでした rxGetVarInfo データにすぐに呼び出しに気付いたしますか。 これは、XDF が RevoScaleR の既定の中間格納方法だからです。 XDF ファイルの詳細については、次を参照してください。[作成、XDF](https://msdn.microsoft.com/microsoft-r/scaler-data-xdf)です。
  
4. ここで、このデータを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルに配置し、 _DayOfWeek_ を値 1 ～ 7 の整数として格納します。
  
    そのために、まず SQL Server データ ソースを定義します。
  
    ```R
    sqlServerAirDemo <- RxSqlServerData(table = "AirDemoSmallTest", connectionString = sqlConnString)
    ```
  
5. 同じ名前のテーブルが既に存在しないか確認し、存在する場合はそのテーブルを削除します。
  
    ```R
    if (rxSqlServerTableExists("AirDemoSmallTest",  connectionString = sqlConnString))  rxSqlServerDropTable("AirDemoSmallTest",  connectionString = sqlConnString)
    ```
  
6. テーブルを作成し、 **rxDataStep**の多様な製品サンプルに使用されています。 この関数は、既にデータ ソースを定義し、途中のデータを変換できる 2 つの間でデータを移動します。
  
    ```R
    rxDataStep(inData = xdfAirDemo, outFile = sqlServerAirDemo,
            transforms = list( DayOfWeek = as.integer(DayOfWeek),
            rowNum = .rxStartRow : (.rxStartRow + .rxNumRows - 1) ),
            overwrite = TRUE )
    ```
  
    これは大規模なテーブルのため、しばらくしてから最終的な状態に関する次のメッセージが表示されます。*読み取られた行: 200000、処理行数: 600000*。
     
7. コンピューティング コンテキストを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューターに戻します。

    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
8. 単純な SQL クエリを新しいテーブルで使用して、新しい SQL Server データ ソースを作成します。 この定義では、引数 *colInfo* を RxSqlServerData に使用して、*DayOfWeek* 列の因子レベルを追加します。
  
    ```R
    SqlServerAirDemo <- RxSqlServerData(
        sqlQuery = "SELECT * FROM AirDemoSmallTest",
        connectionString = sqlConnString,
        rowsPerRead = 50000,
        colInfo = list(DayOfWeek = list(type = "factor",  levels = as.character(1:7))))
    ```
  
9. クエリ内のデータの概要を確認するには、もう一度 rxSummary を呼び出します。
  
    ```R
    rxSummary(~., data = sqlServerAirDemo)
    ```

## <a name="next-step"></a>次の手順

[RxDataStep を使用して、チャンキング分析を実行します。](../../advanced-analytics/tutorials/deepdive-perform-chunking-analysis-using-rxdatastep.md)

## <a name="previous-step"></a>前の手順

[RxImport を使用しているメモリにデータを読み込む](../../advanced-analytics/tutorials/deepdive-load-data-into-memory-using-rximport.md)



