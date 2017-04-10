---
title: "rxDataStep を使用した新しい SQL Server テーブルの作成 (データ サイエンスの詳細) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
ms.assetid: 98cead96-6de7-4edf-98b9-a1efb09297b9
caps.latest.revision: 19
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
---
# rxDataStep を使用した新しい SQL Server テーブルの作成 (データ サイエンスの詳細)
このレッスンでは、インメモリ データ フレーム、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンテキスト、およびローカル ファイルの間でデータを移動する方法を学習します。  
  
> [!NOTE]  
> このレッスンでは、別のデータセットを使用します。 航空便遅延データセットは、機械学習実験に広く使用されている公開データセットです。 R を始めたばかりの場合、このデータセットをテスト用に利用すると便利です。このデータセットは [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して公開された [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] の多様な製品サンプルに使用されています。 この例に必要なデータ ファイルは、その他の製品サンプルと同じディレクトリにあります。  
  
## ローカル データから SQL Server テーブルを作成する  
このチュートリアルの最初のレッスンでは、*RxTextData* 関数を使用してデータをテキスト ファイルから R にインポートし、*RxDataStep* 関数を使用してデータを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に移動しました。  
  
このレッスンでは、別のアプローチを使用して、[XDF 形式](https://en.wikipedia.org/wiki/Extensible_Data_Format)で保存したファイルからデータを取得します。 XDF 形式は、高次元データ用に開発された XML 標準です。 XDF は、R インターフェイスを使用したバイナリ ファイル形式です。行と列の処理と分析を最適化しています。  XDF 形式は、データの移動や、分析に有用なデータのサブセットを格納するために使用できます。
  
XDF ファイルを使用するデータに簡単な変換を実行した後に、変換後のデータを新しい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルに保存します。  
  
> [!NOTE]  
> この手順には、DDL の権限が必要です。  
  
1.  計算コンテキストをローカル ワークステーションに設定します。  
  
    ```R  
    rxSetComputeContext("local")   
    ```  
  
2.  *RxXdfData* 関数を使用して新しいデータ ソース オブジェクトを定義します。 XDF データ ソースの場合、データ ファイルのパスを指定するだけで済みます。  テキスト変数を使用してファイルのパスを指定できますが、ここでは、*rxGetOption* 関数から返されるディレクトリにサンプル データ ファイル (AirlineDemoSmall.xdf) が存在するので、便利なショートカットを使用できます。
  
    ```R  
    xdfAirDemo <- RxXdfData(file.path(rxGetOption("sampleDataDir"),  "AirlineDemoSmall.xdf"))   
    ```  
  
  
3.  インメモリ データに対して *rxGetVarInfo* を呼び出して、データセットの概要を表示します。  
  
    ```R  
    rxGetVarInfo(xdfAirDemo)    
    ```  
  
**[結果]**  
  
*Var 1: ArrDelay, Type: integer, Low/High: (-86, 1490)*   
*Var 2: CRSDepTime, Type: numeric, Storage: float32, Low/High: (0.0167, 23.9833)*   
*Var 3: DayOfWeek 7 factor levels: Monday Tuesday Wednesday Thursday Friday Saturday Sunday*  

> [!NOTE]
> 
> ご覧のように、データを XDF ファイルに読み込むために他の関数を呼び出す必要がなく、データに対して *rxGetVarInfo* をすぐに呼び出すことができます。 これは、XDF が RevoScaleR の既定の中間格納方法だからです。 XDF ファイルの詳細については、「[ScaleR Getting Started Guide](https://msdn.microsoft.com/microsoft-r/scaler-user-guide-data-transform#using-the-data-step-to-create-an-xdf-file-from-a-data-frame)」 (ScaleR ファースト ステップ ガイド) を参照してください。 
  
4.  ここで、このデータを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルに配置し、_DayOfWeek_ を値 1 ～ 7 の整数として格納します。  
  
    そのために、まず SQL Server データ ソースを定義します。  
  
    ```R  
    sqlServerAirDemo <- RxSqlServerData(table = "AirDemoSmallTest", connectionString = sqlConnString)   
    ```  
  
5.  同じ名前のテーブルが存在しないか確認し、存在する場合はそのテーブルを削除します。  
  
    ```R  
    if (rxSqlServerTableExists("AirDemoSmallTest",  connectionString = sqlConnString))  rxSqlServerDropTable("AirDemoSmallTest",  connectionString = sqlConnString)    
    ```  
  
6.  テーブルを作成し、`rxDataStep` を使用してデータを読み込みます。  
  
    ```R  
    rxDataStep(inData = xdfAirDemo, outFile = sqlServerAirDemo,    
            transforms = list( DayOfWeek = as.integer(DayOfWeek),   
            rowNum = .rxStartRow : (.rxStartRow + .rxNumRows - 1) ),   
            overwrite = TRUE )    
    ```  
  
7.  コンピューティング コンテキストを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューターに戻します。  
  
    ```R  
    rxSetComputeContext(sqlCompute)  
    ```  
  
8.  単純な SQL ステートメントを使用して、データのサブセットを定義します。  
  
    ```R    
    SqlServerAirDemo <- RxSqlServerData(  
        sqlQuery = "SELECT * FROM AirDemoSmallTest",      
        connectionString = sqlConnString,   
        rowsPerRead = 50000,      
        colInfo = list(DayOfWeek = list(type = "factor",  levels = as.character(1:7))))    
    ```  
  
9. *rxSummary* を呼び出して、クエリ内のデータの概要を確認します。  
  
    ```R  
    rxSummary(~., data = sqlServerAirDemo)   
    ```  
  
## 次の手順  
[rxDataStep を使用してチャンク分析を実行する (データ サイエンスの詳細情報)](../../advanced-analytics/r-services/perform-chunking-analysis-using-rxdatastep-data-science-deep-dive.md)  
  
## 前の手順  
[rxImport を使用してメモリにデータを読み込む (データ サイエンス詳細情報)](../../advanced-analytics/r-services/load-data-into-memory-using-rximport-data-science-deep-dive.md)  
  
## 参照  
[データ サイエンスの詳細: RevoScaleR パッケージの使用](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md)  
  
  
  
