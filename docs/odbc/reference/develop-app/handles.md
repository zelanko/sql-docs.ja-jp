---
title: ハンドル |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- handles [ODBC]
- driver handles [ODBC]
- driver manager [ODBC], handles
- handles [ODBC], about handles
ms.assetid: f663101e-a4cc-402b-b9d7-84d5e975be71
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 713c2a71ec195b75d682b97239413e98d07b5861
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300212"
---
# <a name="handles"></a>ハンドル
ハンドルは不透明な 32 ビット値で、特定の項目を識別します。ODBC では、この項目は環境、接続、ステートメント、または記述子にすることができます。 アプリケーションが**SQLAllocHandle**を呼び出すと、ドライバー マネージャーまたはドライバーは、指定された種類の新しい項目を作成し、アプリケーションにハンドルを返します。 アプリケーションは、ODBC 関数を呼び出すときに、その項目を識別するために、後でハンドルを使用します。 ドライバー マネージャーとドライバーは、項目に関する情報を検索するハンドルを使用します。  
  
 たとえば、次のコードでは、2 つのステートメント ハンドル (*hstmtOrder*と*hstmtLine*) を使用して、販売注文と販売注文明細行番号の結果セットを作成するステートメントを識別します。 後でこれらのハンドルを使用して、データをフェッチする結果セットを識別します。  
  
```  
SQLHSTMT      hstmtOrder, hstmtLine; // Statement handles.  
SQLUINTEGER   OrderID;  
SQLINTEGER    OrderIDInd = 0;  
SQLRETURN     rc;  
  
// Prepare the statement that retrieves line number information.  
SQLPrepare(hstmtLine, "SELECT * FROM Lines WHERE OrderID = ?", SQL_NTS);  
  
// Bind OrderID to the parameter in the preceding statement.  
SQLBindParameter(hstmtLine, 1, SQL_PARAM_INPUT, SQL_C_ULONG, SQL_INTEGER, 5, 0,  
               &OrderID, 0, &OrderIDInd);  
  
// Bind the result sets for the Order table and the Lines table. Bind  
// OrderID to the OrderID column in the Orders table. When each row is  
// fetched, OrderID will contain the current order ID, which will then be  
// passed as a parameter to the statement tofetch line number  
// information. Code not shown.  
  
// Create a result set of sales orders.  
SQLExecDirect(hstmtOrder, "SELECT * FROM Orders", SQL_NTS);  
  
// Fetch and display the sales order data. Code to check if rc equals  
// SQL_ERROR or SQL_SUCCESS_WITH_INFO not shown.  
while ((rc = SQLFetch(hstmtOrder)) != SQL_NO_DATA) {  
   // Display the sales order data. Code not shown.  
  
   // Create a result set of line numbers for the current sales order.  
   SQLExecute(hstmtLine);  
  
   // Fetch and display the sales order line number data. Code to check  
   // if rc equals SQL_ERROR or SQL_SUCCESS_WITH_INFO not shown.  
   while ((rc = SQLFetch(hstmtLine)) != SQL_NO_DATA) {  
      // Display the sales order line number data. Code not shown.  
   }  
  
   // Close the sales order line number result set.  
   SQLCloseCursor(hstmtLine);  
}  
  
// Close the sales order result set.  
SQLCloseCursor(hstmtOrder);  
```  
  
 ハンドルは、ハンドルを作成した ODBC コンポーネントにのみ意味があります。つまり、ドライバー マネージャーのみがドライバー マネージャーのハンドルを解釈でき、ドライバーのみが独自のハンドルを解釈できます。  
  
 たとえば、前の例のドライバーは、ステートメントに関する情報を格納する構造体を割り当て、ステートメント ハンドルとしてこの構造体へのポインターを返します。 アプリケーションが**SQLPrepare**を呼び出すとき、SQL ステートメントと販売注文明細行番号に使用されるステートメントのハンドルが渡されます。 ドライバーは、SQL ステートメントをデータ ソースに送信し、データ ソースを準備し、アクセス プランの識別子を返します。 ドライバーは、この識別子を格納する構造体を見つけるためにハンドルを使用します。  
  
 その後、アプリケーションが**SQLExecute**を呼び出して、特定の販売注文の行番号の結果セットを生成すると、同じハンドルを渡します。 ドライバーは、構造体からアクセス プランの識別子を取得するハンドルを使用します。 識別子をデータ ソースに送信して、実行するプランを示します。  
  
 ODBC には、ドライバー マネージャーハンドルとドライバー ハンドルの 2 つのレベルがあります。 アプリケーションは、ドライバー マネージャーでこれらの関数を呼び出すため、ODBC 関数を呼び出すときにドライバー マネージャー ハンドルを使用します。 ドライバー マネージャーは、このハンドルを使用して、対応するドライバー ハンドルを検索し、ドライバーで関数を呼び出すときにドライバー ハンドルを使用します。 ドライバーとドライバー マネージャーのハンドルを使用する方法の例については、[接続プロセスでドライバー マネージャーの役割を](../../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md)参照してください。  
  
 ハンドルの 2 つのレベルがあることは、ODBC アーキテクチャの成果物です。ほとんどの場合、アプリケーションまたはドライバーには関係ありません。 通常、この操作を行う理由はありませんが、アプリケーションは**SQLGetInfo**を呼び出してドライバ ハンドルを決定できます。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [環境ハンドル](../../../odbc/reference/develop-app/environment-handles.md)  
  
-   [接続ハンドル](../../../odbc/reference/develop-app/connection-handles.md)  
  
-   [ステートメント ハンドル](../../../odbc/reference/develop-app/statement-handles.md)  
  
-   [記述子ハンドル](../../../odbc/reference/develop-app/descriptor-handles.md)  
  
-   [状態遷移](../../../odbc/reference/develop-app/state-transitions.md)
