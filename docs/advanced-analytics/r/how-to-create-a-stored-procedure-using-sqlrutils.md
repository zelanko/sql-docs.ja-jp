---
title: Sqlrutils - SQL Server Machine Learning Services を使用してストアド プロシージャを作成する方法
description: SQL Server で R 言語のコードをストアド プロシージャに引数として渡すことができる 1 つの関数にバンドルするのに sqlrutils R パッケージを使用します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 014fb8344a0b2cf93dc7f375fffc717663f53a46
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62641844"
---
# <a name="create-a-stored-pprocedure-using-sqlrutils"></a>Sqlrutils を使用してストアド pProcedure を作成します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、T-SQL ストアド プロシージャとして実行する R コードを変換するための手順について説明します。 考えられる最良の結果を得るために、コードを少し変更し、すべての入力をパラメーター化できるようにする必要がある場合があります。

## <a name="bkmk_rewrite"></a>手順 1. R スクリプトを書き直してください。

最適な結果、1 つの関数としてカプセル化する R コードを書き直す必要があります。

関数によって使用されるすべての変数は、関数内で定義する必要がありますか、入力パラメーターとして定義する必要があります。 参照してください、[サンプル コード](#samples)この記事では。

また、R 関数の入力パラメーターになるため、SQL の入力パラメーターはストアド プロシージャ、入力と出力が次の種類の要件に準拠していることを確認する必要があります。

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

内の関数を使用する R コードを使用すると、クリーンアップされて、1 つの関数として呼び出すことができます、 **sqlrutils**パッケージは、入力と出力で実際に構築するコンス トラクターに渡すことができるフォームを準備する、ストアド プロシージャです。

**sqlrutils**入力データ スキーマと型を定義し、出力データのスキーマと型を定義する関数を提供します。 必要な出力の種類に R オブジェクトを変換する関数も含まれています。 コードでのデータ型によって、必要なオブジェクトを作成するための複数の関数呼び出しを行うことがあります。

### <a name="inputs"></a>入力

関数が、入力を受け取る場合、それぞれの入力は、次の関数を呼び出します。

- `setInputData` 入力がデータ フレームの場合
- `setInputParameter` 他のすべての入力の種類に対して

引数として渡すは後で R オブジェクトを作成するときに、各関数の呼び出しを行うと、 `StoredProcedure`、完全なストアド プロシージャを作成します。

### <a name="outputs"></a>出力

**sqlrutils** R に変換するオブジェクトの SQL Server で必要な data.frame にリストのような複数の関数を提供します。
関数でデータ フレームが直接出力された場合は、最初にリストにラップせずに、この手順を省略できます。
手順を省略できます変換この場合は NULL を返します。

ときに、リストへの変換や、リストから特定の項目を取得するは、これらの関数から選択します。

- `setOutputData` 一覧から取得する変数がデータ フレームである場合
- `setOutputParameter` リストの他のすべてのメンバー

引数として渡すは後で R オブジェクトを作成するときに、各関数の呼び出しを行うと、 `StoredProcedure`、完全なストアド プロシージャを作成します。

## <a name="step-3-generate-the-stored-procedure"></a>手順 3. ストアド プロシージャを生成します。

すべての入力と出力パラメーターは、準備が整ったらへの呼び出しを行い、`StoredProcedure`コンス トラクター。

**使用方法**

`StoredProcedure (func, spName, ..., filePath = NULL ,dbName = NULL, connectionString = NULL, batchSeparator = "GO")`

仮定という名前のストアド プロシージャを作成することを示すために、 **sp_rsample**これらのパラメーターを使用します。

- 既存の関数を使用して**foosql**します。 関数が R 関数の既存のコードに基づいて**foo**、」の説明に従って、要件に準拠するように関数を書き直して、[ここ](#bkmk_rewrite)、名前付きとして更新された機能と**foosql**します。
- データ フレームを使用して**queryinput**入力として
- R 変数名では、データ フレームを出力として生成**sqloutput**
- 内のファイルとして T-SQL コードを作成する、`C:\Temp`フォルダー、後で SQL Server Management Studio を使用してこれを実行できるように

```R
StoredProcedure (foosql, sp_rsample, queryinput, sqloutput, filePath = "C:\\Temp")
```

> [!NOTE]
> ファイル システムにファイルを作成するためには、データベース接続を定義する引数を省略できます。

関数の出力は、SQL Server 2016 の (R Services が必要) または (R を使用した Machine Learning サービスが必要)、SQL Server 2017 のインスタンスで実行できる T-SQL ストアド プロシージャです。 

その他の例では、呼び出すことによって、パッケージのヘルプを参照してください。 `help(StoredProcedure)` 、R 環境から。

## <a name="step-4-register-and-run-the-stored-procedure"></a>手順 4. 登録およびストアド プロシージャの実行

ストアド プロシージャを実行することが 2 つの方法はあります。

- SQL Server 2016 または SQL Server 2017 のインスタンスへの接続をサポートする任意のクライアントから、T-SQL を使用します。
- R 環境から

どちらの方法では、ストアド プロシージャを使用するデータベースでストアド プロシージャを登録することが必要です。

### <a name="register-the-stored-procedure"></a>ストアド プロシージャを登録します。

R を使用するストアド プロシージャを登録することができますか、T-SQL で CREATE PROCEDURE ステートメントを実行することができます。

- T-SQL を使用します。  T-SQL で快適な場合は、SQl Server Management Studio (または SQL DDL コマンドを実行できるその他のクライアント) を開く準備でコードを使用して CREATE PROCEDURE ステートメントを実行して、`StoredProcedure`関数。
- R を使用まだ、R 環境では中を使用して、`registerStoredProcedure`関数**sqlrutils**データベースでストアド プロシージャを登録します。

  たとえば、ストアド プロシージャを登録することが**sp_rsample**インスタンスおよびデータベースで定義されている*sqlConnStr*、R 呼び出しによって。

  ```R
  registerStoredProcedure(sp_rsample, sqlConnStr)
  ```


> [!IMPORTANT]
> かどうかを使用する R または SQL に関係なくを新しいデータベース オブジェクトを作成するアクセス許可を持つアカウントを使用してステートメントを実行する必要があります。

### <a name="run-using-sql"></a>SQL を使用して実行します。

ストアド プロシージャが作成された後、T-SQL をサポートする任意のクライアントを使用して SQL database への接続を開くし、ストアド プロシージャに必要なパラメーター値を渡します。

### <a name="run-using-r"></a>R を使用して実行します。

SQL Server からではなく、R コードからストアド プロシージャを実行する場合は、いくつか追加の準備が必要です。 たとえば、ストアド プロシージャは、入力値を必要とする場合、関数を選択して、実行することができますし、R コードでストアド プロシージャにそれらのオブジェクトを渡す前にその入力パラメーターを設定する必要があります。

準備された SQL ストアド プロシージャを呼び出すことの全体的なプロセスは次のとおりです。

1. 入力パラメーター オブジェクトのリストを取得するには、 `getInputParameters` を呼び出します。
2. `$query` を定義するか、入力パラメーターごとに `$value` を設定します。
3. `executeStoredProcedure` を使用して、設定した入力パラメーター オブジェクトのリストを渡し、R 開発環境からストアド プロシージャを実行します。

## <a name = "samples"></a>例

この例では前に、と後のバージョンの R スクリプトの中で、SQL Server データベースからデータを取得し、データ、いくつかの変換の実行、別のデータベースに保存します。

この簡単な例は、ストアド プロシージャに変換するが簡単に R コードを並べ替え方法をデモンストレーションにのみ使用されます。

### <a name="before-code-preparation"></a>コードの準備をする前に


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


### <a name="after-code-preparation"></a>コードの準備

更新されたバージョンでは、最初の行は、関数名を定義します。 元の R ソリューションから他のすべてのコードでは、その関数の一部になります。

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

[sqlrutils (SQL)](ref-r-sqlrutils.md)


