---
title: ステートメントの実行 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], executing
ms.assetid: e5f0d2ee-0453-4faf-b007-12978dd300a1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c3ce09809c896a4d1d9333da00367f972655f96b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305743"
---
# <a name="executing-a-statement"></a>ステートメントの実行
ステートメントを実行する方法は、データベース エンジンによってコンパイル (準備) されるタイミングと、定義するユーザーに応じて、次の 4 とおりの方法があります。  
  
-   **直接実行**アプリケーションは SQL ステートメントを定義します。 これは、1 つのステップで実行時に準備され、実行されます。  
  
-   **準備実行**アプリケーションは SQL ステートメントを定義します。 これは、別々のステップで実行時に準備され、実行されます。 ステートメントは、1 回だけ準備して複数回実行できます。  
  
-   **手順**アプリケーションは、開発時に 1 つ以上の SQL ステートメントを定義およびコンパイルし、これらのステートメントをプロシージャーとしてデータ・ソースに保管することができます。 プロシージャは、実行時に 1 回以上実行されます。 アプリケーションは、カタログ関数を使用して、使用可能なストアド プロシージャを列挙できます。  
  
-   **カタログ関数**ドライバーのライターは、定義済みの結果セットを返す関数を作成します。 通常、この関数は、事前定義された SQL ステートメントを送信するか、またはこの目的のために作成されたプロシージャーを呼び出します。 この関数は、実行時に 1 回以上実行されます。  
  
 特定のステートメント (ステートメント ハンドルで識別される) は、何回でも実行できます。 ステートメントは、さまざまな異なる SQL ステートメントを使用して実行することも、同じ SQL ステートメントを使用して繰り返し実行することもできます。 たとえば、次のコードでは、同じステートメント ハンドル (*hstmt1*) を使用して、Sales データベースのテーブルを取得および表示します。 次に、このハンドルを再利用して、ユーザーが選択したテーブルの列を取得します。  
  
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
  
 次のコードは、テーブルから行を削除する同じステートメントを繰り返し実行するために、単一のハンドルを使用する方法を示しています。  
  
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
  
 多くのドライバーでは、ステートメントの割り当ては負荷の高い作業であるため、通常、この方法で同じステートメントを再利用する方が、既存のステートメントを解放して新しいステートメントを割り当てるよりも効率的です。 ステートメントに結果セットを作成するアプリケーションは、ステートメントを再実行する前に、結果セットの上にカーソルをクローズするように注意する必要があります。詳細については、「[カーソルを閉じる」を](../../../odbc/reference/develop-app/closing-the-cursor.md)参照してください。  
  
 ステートメントを再利用すると、一度にアクティブにできるステートメントの数の一部のドライバーの制限を回避するアプリケーションを強制します。 "active" の正確な定義はドライバ固有ですが、多くの場合、準備または実行されたステートメントを参照し、結果が得られることもあります。 例えば **、INSERT**ステートメントが準備された後、通常はアクティブであると見なされます。**SELECT**ステートメントが実行され、カーソルがオープンした後、通常はアクティブであると見なされます。CREATE **TABLE**ステートメントが実行された後は、通常はアクティブとは見なされません。  
  
 アプリケーションは **、SQLGetInfo**をSQL_MAX_CONCURRENT_ACTIVITIES オプションで呼び出すことによって、1 つの接続でアクティブにできるステートメントの数を一度に決定します。 アプリケーションは、データ ソースへの複数の接続を開くことで、この制限を超えるアクティブ ステートメントを使用できます。ただし、接続は負荷が高くなる可能性があるため、パフォーマンスへの影響を考慮する必要があります。  
  
 アプリケーションは、SQL_ATTR_QUERY_TIMEOUTステートメント属性を使用してステートメントを実行するために割り当てられる時間を制限できます。 データ・ソースが結果セットを戻す前にタイムアウト期間が満了すると、SQL ステートメントを実行する関数は SQLSTATE HYT00 (タイムアウト時間が経過した) を戻します。 既定では、タイムアウトはありません。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [直接実行](../../../odbc/reference/develop-app/direct-execution-odbc.md)  
  
-   [準備実行](../../../odbc/reference/develop-app/prepared-execution-odbc.md)  
  
-   [手順](../../../odbc/reference/develop-app/procedures-odbc.md)  
  
-   [SQL ステートメントのバッチ](../../../odbc/reference/develop-app/batches-of-sql-statements.md)  
  
-   [カタログ関数の実行](../../../odbc/reference/develop-app/executing-catalog-functions.md)
