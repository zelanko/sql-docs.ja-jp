---
title: カーソル用の SQL ステートメントの作成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-odbc-queries
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], statement construction
- ODBC applications, cursors
- SQL Server Native Client ODBC driver, statements
- statements [ODBC], constructing
- ODBC applications, statements
- statements [ODBC], cursors
ms.assetid: 134003fd-9c93-4f5c-a988-045990933b80
caps.latest.revision: 36
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 3c472fac6b4cf6f138fb75beeab8933c40e08993
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="constructing-sql-statements-for-cursors"></a>カーソル用の SQL ステートメントの作成
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、サーバー カーソルを使用して、ODBC 仕様で定義されたカーソル機能を実装します。 ODBC アプリケーションを使用してカーソル動作を制御する[SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)別のステートメント属性を設定します。 次に、属性とその既定値を示します。  
  
|属性|既定値|  
|---------------|-------------|  
|SQL_ATTR_CONCURRENCY|SQL_CONCUR_READ_ONLY|  
|SQL_ATTR_CURSOR_TYPE|SQL_CURSOR_FORWARD_ONLY|  
|SQL_ATTR_CURSOR_SCROLLABLE|SQL_NONSCROLLABLE|  
|SQL_ATTR_CURSOR_SENSITIVITY|SQL_UNSPECIFIED|  
|SQL_ATTR_ROW_ARRAY_SIZE|1|  
  
 これらのオプションが設定されている既定値には、SQL ステートメントの実行時に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーには、結果セットを実装する、サーバー カーソルは使用しません。 代わりに、既定の結果セットを使用します。 これらのオプションのいずれかが、SQL ステートメントの実行時に、既定値から変更された場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは結果セットを実装する、サーバー カーソルを使用しようとしています。  
  
 既定の結果セットは、すべての [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントをサポートします。 既定の結果セットを使用するときに実行できる SQL ステートメントの種類に制限はありません。  
  
 サーバー カーソルはすべての [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントをサポートしているわけではありません。 複数の結果セットを生成する SQL ステートメントはサポートされません。  
  
 次に示す種類のステートメントは、サーバー カーソルではサポートされません。  
  
-   バッチ  
  
     2 つ以上の個別の SQL SELECT ステートメントから構成される SQL ステートメント。次に例を示します。  
  
    ```  
    SELECT * FROM Authors; SELECT * FROM Titles  
    ```  
  
-   複数の SELECT ステートメントを含むストアド プロシージャ  
  
     複数の SELECT ステートメントを含むストアド プロシージャを実行する SQL ステートメント。 パラメーターまたは変数を設定する SELECT ステートメントも該当します。  
  
-   キーワード  
  
     キーワード FOR BROWSE または INTO を伴う SELECT ステートメント。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で、上記の条件のいずれかに該当する SQL ステートメントをサーバー カーソルを使用して実行した場合、サーバー カーソルは暗黙的に既定の結果セットに変換されます。 後に**SQLExecDirect**または**SQLExecute**属性の既定の設定に戻す設定は、カーソル、sql_success_with_info が返されます。  
  
 上記の分類に該当しない SQL ステートメントは、ステートメント属性の設定がどのようであっても実行できます。既定の結果セット、サーバー カーソルを問わず、どちらも正常に機能します。  
  
## <a name="errors"></a>エラー  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 以降のバージョンで複数の結果セットが生成されるステートメントを実行すると、SQL_SUCCESS_WITH INFO および次のメッセージが生成されます。  
  
```  
SqlState: 01S02"  
pfNative: 0  
szErrorMsgString: "[Microsoft][SQL Server Native Client][SQL Server]  
               Cursor type changed."  
```  
  
 このメッセージを受信する ODBC アプリケーションから呼び出せる[SQLGetStmtAttr](../../relational-databases/native-client-odbc-api/sqlgetstmtattr.md)に現在のカーソル設定を確認します。  
  
 サーバー カーソルを使用しているときに、複数の SELECT ステートメントから構成されるプロシージャを実行すると、次のエラーが発生します。  
  
```  
SqlState: 42000  
pfNative: 16937  
szErrorMsgString: [Microsoft][SQL Server Native Client][SQL Server]  
               A server cursor is not allowed on a stored procedure  
               with more than one SELECT statement in it. Use a  
               default result set or client cursor.  
```  
  
 サーバー カーソルを使用しているときに、複数の SELECT ステートメントから構成されるバッチを実行すると、次のエラーが発生します。  
  
```  
SqlState: 42000  
pfNative: 16938  
szErrorMsgString: [Microsoft][SQL Server Native Client][SQL Server]  
               sp_cursoropen. The statement parameter can only  
               be a single SELECT statement or a single stored   
               procedure.  
```  
  
 ODBC アプリケーションで上記のエラーが発生した場合、カーソルのすべてのステートメント属性を既定値に戻してからステートメントを実行する必要があります。  
  
## <a name="see-also"></a>参照  
 [クエリを実行する&#40;ODBC&#41;](../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  
