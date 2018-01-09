---
title: "sqlrutils を使用してストアド プロシージャを作成する方法 | Microsoft Docs"
ms.custom: 
ms.date: 12/16/2016
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: R
ms.assetid: 5ba99b49-481e-4b30-967a-a429b855b1bd
caps.latest.revision: "10"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3e1223ded4b8ef7107a0a565b751b31d12ff6f3e
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="create-a-stored-procedure-using-sqlrutils"></a>ストアド プロシージャを使用して sqlrutils を作成します。

このトピックでは、T-SQL ストアド プロシージャとして実行する R コードを変換するための手順について説明します。 考えられる最良の結果を得るために、コードを少し変更し、すべての入力をパラメーター化できるようにする必要がある場合があります。

## <a name="bkmk_rewrite"></a>手順 1. R スクリプトを書き直してください。

最良の結果を R コードを 1 つの関数としてカプセル化することを書き直す必要があります。

関数によって使用されているすべての変数は、関数内で定義する必要がありますか、入力パラメーターとして定義する必要があります。 このトピックの [サンプル コード](#samples) を参照してください。

また、R 関数の入力パラメーターになるため、ストアド プロシージャを SQL の入力パラメーターを入力と出力が次の種類の要件に準拠していることを確認する必要があります。

### <a name="inputs"></a>入力

入力パラメーターで使用できるデータ フレームは最大で 1 つです。

データ フレーム内のオブジェクトと、関数の他のすべての入力パラメーターは、次の R データ型でなければなりません。
- POSIXct
- NUMERIC
- character
- 整数 (integer)
- logical
- raw

入力の種類が上記の種類でない場合は、シリアル化し、 *raw*として関数に渡す必要があります。 その場合、関数に入力を逆シリアル化するコードを含める必要もあります。

### <a name="outputs"></a>出力

関数は次のいずれかを出力できます。

- サポートされているデータ型を含むデータ フレーム。 データ フレームのすべてのオブジェクトでは、サポートされているデータ型のいずれかを使用する必要があります。
- 最大で 1 つのデータ フレームを含む名前付きリスト。 リストのすべてのメンバーでは、サポートされるデータ型のいずれかを使用する必要があります。
- NULL (関数が結果を返さない場合)

## <a name="step-2-generate-required-objects"></a>手順 2. 必要なオブジェクトを生成します。

内の関数を使用する R コードがクリーンアップされた、1 つの関数として呼び出すことが後に、 **sqlrutils**パッケージを入力と出力で実際に構築するコンス トラクターに渡すことができるフォームを準備するのにはストアド プロシージャです。

**sqlrutils**入力データのスキーマと型を定義し、出力データのスキーマと型を定義する関数を提供します。 必要な出力の種類に R オブジェクトを変換する関数も含まれています。 コードを使用してデータの種類に応じて、必要なオブジェクトを作成するための複数の関数呼び出しを行うことがあります。

### <a name="inputs"></a>入力

場合は、関数は、入力を受け取りますは、各入力には、次の関数を呼び出します。

- `setInputData`入力がデータ フレームの場合
- `setInputParameter`他のすべての入力の種類

引数として渡すは後で R オブジェクトを作成する各関数の呼び出しを行うと`StoredProcedure`、完全なストアド プロシージャを作成します。

### <a name="outputs"></a>出力

**sqlrutils** SQL Server で必要な data.frame をリストのような R に変換するオブジェクトに対して複数の関数を提供します。
関数でデータ フレームが直接出力された場合は、最初にリストにラップせずに、この手順を省略できます。
手順を省略できます変換この場合は NULL を返します。

ときに、リストへの変換や、リストから特定の項目を取得するは、これらの関数から選択します。

- `setOutputData`変数を一覧から取得するが、データ フレームの場合
- `setOutputParameter`一覧の他のすべてのメンバー

引数として渡すは後で R オブジェクトを作成する各関数の呼び出しを行うと`StoredProcedure`、完全なストアド プロシージャを作成します。

## <a name="step-3-generate-the-stored-procedure"></a>手順 3. ストアド プロシージャを生成します。

すべての入力呼び出し力パラメーターは、準備が整ったらへの呼び出しを行う、`StoredProcedure`コンス トラクターです。

**Usage**

`StoredProcedure (func, spName, ..., filePath = NULL ,dbName = NULL, connectionString = NULL, batchSeparator = "GO")`

仮定という名前のストアド プロシージャを作成することを示すために、 **sp_rsample**これらのパラメーターを使用します。

- 既存の関数を使用して**foosql**です。 関数が R 関数の既存のコードに基づいている**foo**、」の説明に従って、要件に準拠するように、関数の書き直しが[ここ](#bkmk_rewrite)、名前付きとして更新された機能と**foosql**です。
- データ フレームを使用して**queryinput**入力として
- R の変数名では、データ フレームを出力として生成**sqloutput**
- 内のファイルとして T-SQL コードを作成する、`C:\Temp`フォルダーで、後で SQL Server Management Studio を使用してこれを実行できるように

```R
StoredProcedure (foosql, sp_rsample, queryinput, sqloutput, filePath = "C:\\Temp")
```

> [!NOTE]
> ファイル システムに、ファイルを作成しているために、データベース接続の定義の引数を省略できます。

関数の出力は、SQL Server 2016 の (R Services が必要) または SQL Server 2017 年 (の R の Machine Learning のサービスが必要) のインスタンスで実行できる T-SQL ストアド プロシージャです。 

その他の例では、呼び出すことによって、パッケージのヘルプを参照してください。 `help(StoredProcedure)` R 環境からです。

## <a name="step-4-register-and-run-the-stored-procedure"></a>手順 4. 登録およびストアド プロシージャの実行

2 つの方法が、ストアド プロシージャを実行することができます。

- SQL Server 2016 または SQL Server 2017 インスタンスへの接続をサポートする任意のクライアントから、T-SQL を使用します。
- R 環境から

どちらの方法では、ストアド プロシージャは、ストアド プロシージャを使用するデータベースに登録する必要があります。

### <a name="register-the-stored-procedure"></a>ストアド プロシージャを登録します。

R を使用するストアド プロシージャを登録することができますか、T-SQL で CREATE PROCEDURE ステートメントを実行することができます。

- T-SQL を使用します。  T-SQL で快適な場合は、SQl Server Management Studio (または SQL DDL コマンドを実行できるその他のクライアント) を開く準備されるコードを使用して CREATE PROCEDURE ステートメントを実行して、`StoredProcedure`関数。
- 使用して r です。R 環境内でまだは、使用すること、`registerStoredProcedure`関数**sqlrutils**データベースとストアド プロシージャを登録します。

  たとえば、ストアド プロシージャを登録することが**sp_rsample**インスタンスおよびデータベースで定義されている*sqlConnStr*、この R 呼び出しを行って。

  ```R
  registerStoredProcedure(sp_rsample, sqlConnStr)
  ```


> [!IMPORTANT]
> かどうかを使用する R または SQL に関係なく、新しいデータベース オブジェクトを作成するアクセス許可を持つアカウントを使用してステートメントを実行してください。

### <a name="run-using-sql"></a>SQL を使用して実行します。

ストアド プロシージャが作成された後は、T-SQL をサポートする任意のクライアントを使用して、SQL データベースへの接続を開き、ストアド プロシージャで必要なすべてのパラメーターの値を渡します。

### <a name="run-using-r"></a>R を使用して実行します。

SQL Server からではなく、R コードからストアド プロシージャを実行する場合は、いくつか追加の準備が必要です。 たとえば、ストアド プロシージャは、入力値を必要とする場合、関数を選択して、実行することができますし、それらのオブジェクト、ストアド プロシージャに渡す、R コードで前に、これらの入力パラメーターを設定する必要があります。

準備された SQL ストアド プロシージャを呼び出すときの全体的なプロセスは次のとおりです。

1. 入力パラメーター オブジェクトのリストを取得するには、 `getInputParameters` を呼び出します。
2. `$query` を定義するか、入力パラメーターごとに `$value` を設定します。
3. `executeStoredProcedure` を使用して、設定した入力パラメーター オブジェクトのリストを渡し、R 開発環境からストアド プロシージャを実行します。

## <a name = "samples"></a>使用例

この例では前に、と後のバージョンの R スクリプトの SQL Server データベースからデータを取得し、データの一部の変換を実行し、別のデータベースに保存します。

この簡単な例については、ストアド プロシージャに変換するが簡単に R コードを変更する方法を示すためにのみ使用されます。

### <a name="before-code-preparation"></a>コードの準備の前に


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

> [!NOTE]
> 
> ODBC 接続を使用する場合の呼び出しではなく、 *RxSqlServerData*関数を使用して接続を開く必要があります*rxOpen*データベースでの操作を実行する前にします。


### <a name="after-code-preparation"></a>コードの準備の後

更新されたバージョンでは、最初の行は、関数名を定義します。 元の R ソリューションの他のすべてのコードでは、その関数の一部になります。

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

> [!NOTE]
> 
> コードの一部として明示的に ODBC 接続を開く必要はありませんが、 **sqlrutils**を使用するには引き続き ODBC 接続が必要になります。

## <a name="see-also"></a>参照

[sqlrutils を使用するストアド プロシージャの生成](../../advanced-analytics/r-services/generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md)


