---
title: メッセージを生成するステートメントの処理 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- PRINT statement
- messages [ODBC], statements generating messages
- statements [ODBC], message generation
- errors [ODBC], statements generating messages
- SQL Server Native Client ODBC driver, errors
- STATISTICS IO option
- STATISTICS TIME option
- DBCC statements
- SQLExecute function
- RAISERROR statement
- SQLGetDiagRec function
- ODBC error handling, statements generating messages
- SQLExecDirect function
ms.assetid: 672ebdc5-7fa1-4ceb-8d52-fd25ef646654
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9820e202f5032423292c4306aa63b175bce550b6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304693"
---
# <a name="processing-statements-that-generate-messages"></a>メッセージを生成するステートメントの処理
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [!INCLUDE[tsql](../../includes/tsql-md.md)] SET ステートメントのオプション STATISTICS TIME と STATISTICS IO は、実行時間の長いクエリの診断に利用できる情報を取得する場合に使用します。 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、クエリ プランを分析するための SHOWPLAN オプションもサポートされています。 ODBC アプリケーションでは、次のステートメントを実行してこれらのオプションを設定できます。  
  
```  
SQLExecDirect(hstmt, "SET SHOWPLAN ON", SQL_NTS);  
SQLExecDirect(hstmt, "SET STATISTICS TIME ON", SQL_NTS90  
);  
SQLExecDirect(hstmt, "SET STATISTICS IO ON", SQL_NTS);  
```  
  
 統計時刻の設定またはプランの設定がオンの場合 **、SQLExecute**と**SQLExecDirect**はSQL_SUCCESS_WITH_INFOを返し、その時点で、アプリケーションは SQL_NO_DATA返すまで**SQLGetDiagRec**を呼び出すことによってプラン表示または統計 TIME 出力を取得できます。 SHOWPLAN データの各行は、次の形式で返されます。  
  
```  
szSqlState="01000", *pfNativeError=6223,  
szErrorMsg="[Microsoft][SQL Server Native Client][SQL Server]   
              Table Scan"  
```  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Version 7.0 では、SHOWPLAN オプションが SHOWPLAN_ALL オプションと SHOWPLAN_TEXT オプションに置き換えられました。これらの両方のオプションでは、一連のメッセージではなく、結果セットとして出力が返されます。  
  
 STATISTICS TIME の各行は、次の形式で返されます。  
  
```  
szSqlState="01000", *pfNativeError= 3613,  
szErrorMsg="[Microsoft][SQL Server Native Client][SQL Server]  
   SQL Server Parse and Compile Time: cpu time = 0 ms."  
```  
  
 SET STATISTICS IO の出力は、結果セットの最後に到達するまで使用できません。 統計 IO 出力を取得するには、アプリケーションは、SQLFetch または**SQLFetchScroll**がSQL_NO_DATAを返す時点で**SQLGetDiagRec**を呼び出します。 [SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md) STATISTICS IO の出力は、次の形式で返されます。  
  
```  
szSqlState="01000", *pfNativeError= 3615,  
szErrorMsg="[Microsoft][ SQL Server Native Client][SQL Server]  
   Table: testshow  scan count 1,  logical reads: 1,  
   physical reads: 0."  
```  
  
## <a name="using-dbcc-statements"></a>DBCC ステートメントの使用  
 DBCC ステートメントは、結果セットではなく、メッセージとしてデータを返します。 **SQLExecDirect**または**SQLExecute**はSQL_SUCCESS_WITH_INFOを返し、アプリケーションはSQL_NO_DATA返すまで**SQLGetDiagRec**を呼び出して出力を取得します。  
  
 たとえば、次のステートメントでは SQL_SUCCESS_WITH_INFO が返されます。  
  
```  
SQLExecDirect(hstmt, "DBCC CHECKTABLE(Authors)", SQL_NTS);  
```  
  
 呼び出しは次**を**返します。  
  
```  
szSqlState = "01000", *pfNativeError = 2536,  
szErrorMsg="[Microsoft][ SQL Server Native Client][SQL Server]  
   Checking authors"  
szSqlState = "01000", *pfNativeError = 2579,  
szErrorMsg="[Microsoft][ SQL Server Native Client][SQL Server]  
   The total number of data pages in this table is 1."  
szSqlState = "01000", *pfNativeError = 7929,  
szErrorMsg="[Microsoft][ SQL Server Native Client][SQL Server]  
   Table has 23 data rows."  
szSqlState = "01000", *pfNativeError = 2528  
szErrorMsg="[Microsoft][ SQL Server Native Client][SQL Server]  
   DBCC execution completed. If DBCC printed error messages,  
   see your System Administrator."  
```  
  
## <a name="using-print-and-raiserror-statements"></a>PRINT ステートメントと RAISERROR ステートメントの使用  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]印刷ステートメントと RAISERROR ステートメントも **、SQLGetDiagRec**を呼び出してデータを返します。 PRINT ステートメントは、SQL ステートメントの実行をSQL_SUCCESS_WITH_INFOを返し、その後の**SQLGetDiagRec**の呼び出しは、01000 の*SQLState*を返します。 重大度が 10 以下の RAISERROR の動作は PRINT と同様です。 重大度が 11 以上の RAISERROR は、実行をSQL_ERRORを返し、その後**の SQLGetDiagRec**の呼び出しは*SQLState* 42000 を返します。 たとえば、次のステートメントでは SQL_SUCCESS_WITH_INFO が返されます。  
  
```  
SQLExecDirect (hstmt, "PRINT  'Some message' ", SQL_NTS);  
```  
  
 呼び出し**は次を**返します。  
  
```  
szSQLState = "01000", *pfNative Error = 0,  
szErrorMsg= "[Microsoft] [SQL Server Native Client][SQL Server]  
   Some message"  
```  
  
 次のステートメントからは、SQL_SUCCESS_WITH_INFO が返されます。  
  
```  
SQLExecDirect (hstmt, "RAISERROR ('Sample error 1.', 10, -1)",  
   SQL_NTS)  
```  
  
 呼び出し**は次を**返します。  
  
```  
szSQLState = "01000", *pfNative Error = 50000,  
szErrorMsg= "[Microsoft] [SQL Server Native Client][SQL Server]  
   Sample error 1."  
```  
  
 次のステートメントからは、SQL_ERROR が返されます。  
  
```  
SQLExecDirect (hstmt, "RAISERROR ('Sample error 2.', 11, -1)", SQL_NTS)  
```  
  
 呼び出し**は次を**返します。  
  
```  
szSQLState = "42000", *pfNative Error = 50000,  
szErrorMsg= "[Microsoft] [SQL Server Native Client][SQL Server]  
   Sample error 2."  
```  
  
 PRINT または RAISERROR ステートメントからの出力が結果セットに含まれている場合は **、SQLGetDiagRec**を呼び出すタイミングが重要です。 PRINT または RAISERROR 出力を取得するための**SQLGetDiagRec**の呼び出しは、SQL_ERRORまたはSQL_SUCCESS_WITH_INFOを受け取るステートメントの直後に行う必要があります。 この操作は、上記の例のように、1 つの SQL ステートメントのみを実行するときは容易に実行できます。 このような場合 **、SQLExecDirect**または**SQLExecute**の呼び出しはSQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返し **、SQLGetDiagRec**を呼び出すことができます。 SQL ステートメントのバッチの出力を処理するループをコーディングするとき、または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ストアド プロシージャを実行するときは、1 つの SQL ステートメントのみを実行するときほど簡単ではありません。  
  
 この場合、バッチまたはストアド プロシージャで実行される SELECT ステートメントごとに、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から結果セットが返されます。 バッチまたはプロシージャに PRINT ステートメントまたは RAISERROR ステートメントが含まれている場合、これらのステートメントの出力は SELECT ステートメントの結果セットと交互に返されます。 バッチまたはプロシージャの最初のステートメントが PRINT または RAISERROR である場合 **、SQLExecute**または**SQLExecDirect**はSQL_SUCCESS_WITH_INFOまたはSQL_ERRORを返し、アプリケーションは印刷または RAISERROR 情報を取得するためにSQL_NO_DATA戻るまで**SQLGetDiagRec**を呼び出す必要があります。  
  
 PRINT ステートメントまたは RAISERROR ステートメントが SQL ステートメント (SELECT ステートメントなど) の後に来る場合、エラーを含む結果セットに[SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md)が配置されるときに、PRINT または RAISERROR 情報が返されます。 **メッセージの**重大度に応じてSQL_SUCCESS_WITH_INFOまたはSQL_ERRORが返されます。 メッセージは、SQL_NO_DATAを返すまで**SQLGetDiagRec**を呼び出すことによって取得されます。  
  
## <a name="see-also"></a>参照  
 [エラーとメッセージの処理](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
