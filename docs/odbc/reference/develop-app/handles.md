---
title: 処理 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- handles [ODBC]
- driver handles [ODBC]
- driver manager [ODBC], handles
- handles [ODBC], about handles
ms.assetid: f663101e-a4cc-402b-b9d7-84d5e975be71
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 830c4b653af74097c59c9aff9e073267792a84b7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="handles"></a>ハンドル
ハンドルは特定のアイテムを識別する、32 ビットの非透過の値ODBC では、この項目は、環境、接続、ステートメント、または記述子することができます。 アプリケーションを呼び出すと**SQLAllocHandle**では、ドライバー マネージャーまたはドライバーを指定した型の新しい項目を作成およびアプリケーションへのハンドルを返します。 後で、アプリケーションでは、ハンドルを使用して、ODBC 関数を呼び出すときに、そのアイテムを識別します。 ドライバー マネージャーとドライバーは、ハンドルを使用して、項目に関する情報を探します。  
  
 たとえば、次のコードが 2 つのステートメント ハンドルを使用して (*hstmtOrder*と*hstmtLine*) の売上の結果セットを作成する対象の注文と販売注文行番号、ステートメントを識別します。 これらのハンドルを使って後からデータをフェッチする resultset を識別します。  
  
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
  
 ハンドルは、作成しています。 ODBC コンポーネントに対してのみ意味つまり、ドライバー マネージャーのハンドルを解釈できるは、ドライバー マネージャーのみ、ドライバーのみが、独自のハンドルを解釈できます。  
  
 たとえば、前の例で、ドライバー ステートメントに関する情報を格納する構造体を割り当てるし、ステートメント ハンドルとしてこの構造体へのポインターを返します。 アプリケーションを呼び出すと**SQLPrepare**SQL ステートメントを渡すこと、および販売注文の行番号、ステートメントのハンドルを使用します。 ドライバーは、データ ソースに準備し、アクセス プラン識別子を返しますに SQL ステートメントを送信します。 ドライバーでは、ハンドルを使用して、この識別子を格納する構造体を検索します。  
  
 その後、アプリケーションを呼び出すとき**SQLExecute**を特定の販売注文の行番号の結果セットを生成するには、同じハンドルを渡します。 ドライバーでは、ハンドルを使用して、構造体からのアクセスのプラン id を取得します。 識別子を実行する計画を指示するデータ ソースに送信します。  
  
 ODBC ハンドルの 2 つのレベルには: ドライバー マネージャー ハンドルとドライバーのハンドル。 アプリケーションは、ドライバー マネージャーでこれらの関数を呼び出すために、ODBC 関数を呼び出すときに、ドライバー マネージャーのハンドルを使用します。 ドライバー マネージャーは、このハンドルを使用して、対応するドライバー ハンドルを取得して、ドライバーで関数を呼び出すときに、ドライバー ハンドルを使用します。 ドライバーとドライバー マネージャーのハンドルの使用方法の例は、次を参照してください。[接続プロセスでドライバー マネージャーの役割](../../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md)です。  
  
 ODBC アーキテクチャ; の成果物は、ハンドルの 2 つのレベルがあることほとんどの場合、アプリケーションまたはドライバーに関連はありません。 通常、これを行う必要はありませんがアプリケーションを呼び出してドライバーのハンドルを決定することは**SQLGetInfo**です。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [環境ハンドル](../../../odbc/reference/develop-app/environment-handles.md)  
  
-   [接続ハンドル](../../../odbc/reference/develop-app/connection-handles.md)  
  
-   [ステートメント ハンドル](../../../odbc/reference/develop-app/statement-handles.md)  
  
-   [記述子ハンドル](../../../odbc/reference/develop-app/descriptor-handles.md)  
  
-   [状態遷移](../../../odbc/reference/develop-app/state-transitions.md)
