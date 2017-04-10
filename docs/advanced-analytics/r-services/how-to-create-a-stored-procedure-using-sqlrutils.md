---
title: "sqlrutils を使用してストアド プロシージャを作成する方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "R"
ms.assetid: 5ba99b49-481e-4b30-967a-a429b855b1bd
caps.latest.revision: 10
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 10
---
# sqlrutils を使用してストアド プロシージャを作成する方法
このトピックでは、T-SQL ストアド プロシージャとして実行する R コードを変換するための手順について説明します。 考えられる最良の結果を得るために、コードを少し変更し、すべての入力をパラメーター化できるようにする必要がある場合があります。

## <a name="step-1-format-your-r-script"></a>手順 1. R スクリプトの書式を設定する

1. 1 つの関数にすべてのコードをラップします。

   これは、関数で使用されるすべての変数を関数内に定義する必要があるか、入力パラメーターとして定義する必要があることを意味します。 このトピックの[サンプル コード](#samples)を参照してください。

## <a name="step-2-standardize-the-inputs-and-outputs"></a>手順 2. 入力と出力を標準化する

関数の入力パラメーターは SQL ストアド プロシージャの入力パラメーターになるため、次の種類の要件に従う必要があります。
- 入力パラメーターで使用できるデータ フレームは最大で 1 つです。
- データ フレーム内のオブジェクトと、関数の他のすべての入力パラメーターは、次の R データ型でなければなりません。
    - POSIXct
    - numeric
    - character
    - 整数 (integer)
    - logical
    - raw

- 入力の種類が上記の種類でない場合は、シリアル化し、*raw* として関数に渡す必要があります。 その場合、関数に入力を逆シリアル化するコードを含める必要もあります。

関数は次のいずれかを出力できます。

- サポートされているデータ型を含むデータ フレーム。 データ フレームのすべてのオブジェクトでは、サポートされているデータ型のいずれかを使用する必要があります。
- 最大で 1 つのデータ フレームを含む名前付きリスト。 リストのすべてのメンバーでは、サポートされるデータ型のいずれかを使用する必要があります。 
- NULL (関数が結果を返さない場合)

## <a name="step-3-make-calls-to-the-sqlrutils-package-to-generate-the-stored-procedure"></a>手順 3. ストアド プロシージャを生成するために sqlrutils パッケージを呼び出す

R コードがクリーンアップされ、1 つの関数として呼び出せるようになったら、**sqlrutils** の関数を使用して、ストアド プロシージャにコードを変換するプロセスを開始できます。

パラメーターのデータ型に応じて、さまざまな関数を使用して、データをキャプチャし、パラメーター オブジェクトを作成します。

1. 関数で入力パラメーターを使用する場合は、パラメーターごとに以下のオブジェクトのいずれかを作成します。 
    - 入力パラメーターがデータ フレームである場合は、`setInputData` を使用します。
    - 他のすべての入力パラメーターについては、`setInputParameter` を使用します。

2. 関数でリストが出力された場合は、オブジェクトを作成し、以下のようにリストの必要なデータを処理します。 
    - リスト内の変数がデータ フレームである場合は、`setOutputData` を使用します。
    - リストの他のすべてのメンバーについては、`setOutputParameter` を使用します。
    - 関数でデータ フレームが直接出力された場合は、最初にリストにラップせずに、この手順を省略できます。 
    - 関数で NULL が返された場合は、この手順を省略します。

3. すべての入力と出力のパラメーターの準備ができたら、`StoredProcedure` コンストラクターを呼び出して、R 関数を含むストアド プロシージャを生成します。
4. データベースにストアド プロシージャをすぐに登録する場合は、`registerStoredProcedure` を使用します。

## <a name="step-4-execute-the-stored-procedure"></a>手順 4. ストアド プロシージャを実行する

1. SQL Server からではなく、R コードからストアド プロシージャを実行する際に、ストアド プロシージャで入力が必要な場合には、関数を実行する前にその入力パラメーターを設定する必要があります。 
    - 入力パラメーター オブジェクトのリストを取得するには、`getInputParameters` を呼び出します。
    - `$query` を定義するか、入力パラメーターごとに `$value` を設定します。 

2. `executeStoredProcedure` を使用して、設定した入力パラメーター オブジェクトのリストを渡し、R 開発環境からストアド プロシージャを実行します。

## <a name="a-name-samplesaexamples-prepare-your-code"></a><a name = "samples"></a>例: コードを準備する 

この例では、R コードはデータベースから読み取り、データでいくつかの変換を行い、別のデータベースに保存します。 この単純な例は、R コードを並べ替え、ストアド プロシージャの変換のためにより単純なインターフェイスを提供する方法を示すためのものです。

**書式設定前の作業**


```R
sqlConnFrom <- "Driver={ODBC Driver 13 for SQL Server};Server=MyServer01;Database=AirlineSrc;Trusted_Connection=Yes;"
  
sqlConnTo <- "Driver={ODBC Driver 13 for SQL Server};Server=MyServer01;Database=AirlineTest;Trusted_Connection=Yes;"
  
sqlQueryAirline <- "SELECT TOP 10000 ArrDelay, CRSDepTime, DayOfWeek FROM [AirlineDemoSmall]"
  
dsSqlFrom <- RxSqlServerData(sqlQuery = sqlQueryAirline, connectionString = sqlConnFrom)
  
dsSqlTo <- RxSqlServerData(table = "cleanData", connectionString = sqlConnTo)
  
xFunc <- function(data) {
    data$CRSDepHour <- as.integer(trunc(data$CRSDepTime))
    return(data)
    }
  
xVars <- c("CRSDepTime")
  
sqlCompute <- RxInSqlServer(numTasks = 4, connectionString = sqlConnTo)
  
rxOpen(dsSqlFrom)
rxOpen(dsSqlTo)
  
if (rxSqlServerTableExists("cleanData", connectionString = sqlConnTo))   {
    rxSqlServerDropTable("cleanData")}
  
rxDataStep(inData = dsSqlFrom, 
     outFile = dsSqlTo,
     transformFunc = xFunc,
     transformVars = xVars,
     overwrite = TRUE)
```
*RxSqlServerData* を呼び出すのではなく、ODBC 接続を使用する場合は、データベースで操作を実行する前に、*rxOpen* を使用して接続を開く必要があることに注意してください。



**書式設定後の作業**

書式を再設定したバージョンで、最初の行で関数名を定義します。

元の R ソリューションからの他のすべてのコードは、その関数の一部になります。 

```R
myetl1function <- function() { 
   sqlConnFrom <- "Driver={ODBC Driver 13 for SQL Server};Server=MyServer01;Database=Airline01;Trusted_Connection=Yes;"
   sqlConnTo <- "Driver={ODBC Driver 13 for SQL Server};Server=MyServer02;Database=Airline02;Trusted_Connection=Yes;"
    
   sqlQueryAirline <- "SELECT TOP 10000 ArrDelay, CRSDepTime, DayOfWeek FROM [AirlineDemoSmall]"

   dsSqlFrom <- RxSqlServerData(sqlQuery = sqlQueryAirline, connectionString = sqlConnFrom)
  
   dsSqlTo <- RxSqlServerData(table = "cleanData", connectionString = sqlConnTo)
  
   xFunc <- function(data) {
     data$CRSDepHour <- as.integer(trunc(data$CRSDepTime))
     return(data)}
  
   xVars <- c("CRSDepTime")
  
   sqlCompute <- RxInSqlServer(numTasks = 4, connectionString = sqlConnTo)
  
   if (rxSqlServerTableExists("cleanData", connectionString = sqlConnTo)) {rxSqlServerDropTable("cleanData")}
  
   rxDataStep(inData = dsSqlFrom, 
        outFile = dsSqlTo,
        transformFunc = xFunc,
        transformVars = xVars,
        overwrite = TRUE)
   return(NULL)
}
```
コードの一部として明示的に ODBC 接続を開く必要はありませんが、**sqlrutils** を使用するには引き続き ODBC 接続が必要になります。 


## <a name="see-also"></a>参照

[sqlrutils を使用するストアド プロシージャの生成](../../advanced-analytics/r-services/generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md)

