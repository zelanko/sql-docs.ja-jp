---
title: "ステートメントを実行する |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL statements [ODBC], executing
ms.assetid: e5f0d2ee-0453-4faf-b007-12978dd300a1
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8e3fdaf1a063951dcb06018858a905c5ee8651e9
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="executing-a-statement"></a>ステートメントを実行します。
4 つの方法で、データベース エンジンとそれを定義するには、(準備)、コンパイル時にに応じて、ステートメントを実行するにがあります。  
  
-   **実行を指示**アプリケーションは、SQL ステートメントを定義します。 準備され、1 つのステップで実行時に実行します。  
  
-   **準備実行**アプリケーションは、SQL ステートメントを定義します。 準備され、別の手順の実行時に実行します。 ステートメントを 1 回だけ準備し、複数回実行します。  
  
-   **プロシージャ**アプリケーションを定義およびコンパイル、または開発での複数の SQL ステートメントの時間し、プロシージャとして、データ ソースでこれらのステートメントを格納します。 プロシージャには、実行時に 1 つ以上の時間が実行されます。 アプリケーションでは、カタログ関数を使用して、使用できるストアド プロシージャを列挙できます。  
  
-   **カタログ関数**ドライバー ライターは、定義済みの結果セットを返す関数を作成します。 通常、この関数は、定義済みの SQL ステートメントを送信するか、この目的用に作成されたプロシージャを呼び出します。 関数は、実行時に 1 つまたは複数回実行されます。  
  
 特定のステートメント (そのステートメント ハンドルによって識別される) 可能性があります任意の回数実行します。 別の SQL ステートメントのさまざまなステートメントを実行することができますか、同じ SQL ステートメントを繰り返し実行することができます。 たとえば、次のコードが、同じステートメント ハンドルを使用して (*hstmt1*) を取得して、Sales データベースにテーブルを表示します。 次に、ユーザーによって選択されたテーブルで列を取得するには、このハンドルを再利用します。  
  
```  
SQLHSTMT    hstmt1;  
SQLCHAR *   Table;  
  
// Create a result set of all tables in the Sales database.  
SQLTables(hstmt1, "Sales", SQL_NTS, "sysadmin", SQL_NTS, NULL, 0, NULL, 0);  
  
// Fetch and display the table names; then close the cursor.  
// Code not shown.  
  
// Have the user select a particular table.  
SelectTable(Table);  
  
// Reuse hstmt1 to create a result set of all columns in Table.  
SQLColumns(hstmt1, "Sales", SQL_NTS, "sysadmin", SQL_NTS, Table, SQL_NTS, NULL, 0);  
  
// Fetch and display the column names in Table; then close the cursor.  
// Code not shown.  
```  
  
 次のコードでは、繰り返しステートメントを実行する、同じテーブルから行を削除する 1 つのハンドルを使用する方法を示しています。  
  
```  
SQLHSTMT      hstmt1;  
SQLUINTEGER   OrderID;  
SQLINTEGER    OrderIDInd = 0;  
  
// Prepare a statement to delete orders from the Orders table.  
SQLPrepare(hstmt1, "DELETE FROM Orders WHERE OrderID = ?", SQL_NTS);  
  
// Bind OrderID to the parameter for the OrderID column.  
SQLBindParameter(hstmt1, 1, SQL_PARAM_INPUT, SQL_C_ULONG, SQL_INTEGER, 5, 0,  
                  &OrderID, 0, &OrderIDInd);  
  
// Repeatedly execute hstmt1 with different values of OrderID.  
while ((OrderID = GetOrderID()) != 0) {  
   SQLExecute(hstmt1);  
}  
```  
  
 ドライバーの数、割り当てステートメントは高価なタスクでは、通常は既存のステートメントと割り当ての新たなを解放するよりも効率的ではこの方法で、同じステートメントを再利用されます。 ステートメントで結果セットを作成するアプリケーションは、ステートメントの前に設定の結果上にカーソルを閉じるように注意する必要があります。詳細については、次を参照してください。[カーソルを閉じる](../../../odbc/reference/develop-app/closing-the-cursor.md)です。  
  
 一部のドライバーを同時にアクティブにできるステートメントの数の制限を受けないようにアプリケーションを強制的もステートメントを再利用します。 「アクティブ」の正確な定義は、ドライバー固有ですが、多くの場合、準備または実行された任意のステートメントを参照して使用可能な結果がまだとします。 後など、**挿入**ステートメントが準備されて、一般を有効と見なされます後、**選択**ステートメントが実行されると、カーソルが開いたまま、通常と見なされます。アクティブです。後に、 **CREATE TABLE**ステートメントが実行される、一般的にアクティブにも考慮されません。  
  
 アプリケーションでは、呼び出すことによって、一度に 1 つの接続でアクティブにできる数のステートメントを決定**SQLGetInfo** SQL_MAX_CONCURRENT_ACTIVITIES オプションを使用します。 アプリケーションは、データ ソースに対して複数の接続を開くことによってこの制限よりも多くのアクティブなステートメントを使用できます。接続できるので負荷の高い、ただし、パフォーマンスに影響を考慮してください。  
  
 アプリケーションでは、SQL_ATTR_QUERY_TIMEOUT ステートメント属性を持つを実行するステートメントの時間を制限できます。 データ ソースが、結果セットを返す前に、タイムアウト期間が経過すると、SQL ステートメントを実行する関数は、SQLSTATE HYT00 を返します (タイムアウトになりました)。 既定では、タイムアウトはありません。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [直接実行](../../../odbc/reference/develop-app/direct-execution-odbc.md)  
  
-   [準備実行](../../../odbc/reference/develop-app/prepared-execution-odbc.md)  
  
-   [手順](../../../odbc/reference/develop-app/procedures-odbc.md)  
  
-   [SQL ステートメントのバッチ](../../../odbc/reference/develop-app/batches-of-sql-statements.md)  
  
-   [カタログ関数を実行します。](../../../odbc/reference/develop-app/executing-catalog-functions.md)
