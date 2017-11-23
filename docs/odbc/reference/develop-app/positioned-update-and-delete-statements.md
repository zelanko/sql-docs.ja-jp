---
title: "Update ステートメントと Delete ステートメントを配置 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- positioned deletes [ODBC]
- data updates [ODBC], positioned update or delete
- positioned updates [ODBC]
- updating data [ODBC], positioned update or delete
ms.assetid: 0eafba50-02c7-46ca-a439-ef3307b935dc
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a35d57aaa00f7f2406b779f987c4dd07e694f737
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="positioned-update-and-delete-statements"></a>位置指定更新ステートメントと Delete ステートメント
アプリケーションの更新または位置指定更新と結果セットの現在の行を削除またはステートメントを削除します。 Update および delete に配置されているステートメントは、それらのすべてではなく一部のデータ ソースでサポートされています。 アプリケーションが配置されているデータ ソースのサポートが update および delete ステートメントであるかどうかを決定するを呼び出す**SQLGetInfo** SQL_DYNAMIC_CURSOR_ATTRIBUTES1、SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1、SQL_KEYSET_CURSOR_ATTRIBUTES1、または SQL_STATIC_CURSOR_ATTRIBUTES1*情報の種類*(カーソルの種類) によって異なります。 ODBC カーソル ライブラリが位置指定更新をシミュレートおよび delete ステートメントことに注意してください。  
  
 位置指定更新を使用してまたは delete ステートメントは、アプリケーションを含む結果セットを作成する必要があります、**更新用に選択**ステートメントです。 このステートメントの構文です。  
  
 **選択**[**すべて**&#124; です。**DISTINCT**]*選択リスト*  
  
 **** *テーブル参照一覧*  
  
 [**場所***検索条件*]  
  
 **UPDATE OF の**[*列名*[**、** *列名*]...]  
  
 その後、アプリケーションは、更新または削除する行にカーソルを位置付けます。 これを行うこと**SQLFetchScroll**必要な行が含まれると、呼び出しには、行セットを取得する**SQLSetPos**にその行に行セットのカーソルを配置します。 その後、アプリケーションは、結果セットで使用されているステートメントよりも別のステートメントで位置指定の update または delete ステートメントを実行します。 これらのステートメントの構文です。  
  
 **更新***テーブル名*  
  
 **設定***列識別子*  **=**  {*式*&#124; です。**NULL**}  
  
 [**、** *列識別子*  **=**  {*式*&#124; です。**NULL**}].  
  
 **WHERE CURRENT OF** *カーソル名*  
  
 **DELETE FROM** *テーブル名* **WHERE CURRENT OF** *カーソル名*  
  
 これらのステートメントにカーソル名が必要なことに注意してください。 アプリケーションはいずれかでカーソル名を指定できます**SQLSetCursorName**設定またはデータ ソースを自動的にさせることができます、結果を作成するステートメントを実行する前に、カーソルが作成されるとき、カーソル名を生成します。 後者の場合、アプリケーションで呼び出すことで位置指定更新ステートメントと delete ステートメントで使用するためには、このカーソル名を取得**SQLGetCursorName**です。  
  
 たとえば、次のコードは、Customers テーブルをスクロールし、顧客レコードを削除またはのアドレスと電話番号を更新するユーザーを許可します。 呼び出す**SQLSetCursorName**顧客の結果セットを作成して、次の 3 つのステートメント ハンドルを使用する前に、カーソル名を指定する: *hstmtCust*によって結果セットの*hstmtUpdate*位置指定の update ステートメント、および*hstmtDelete*位置指定の delete ステートメント。 コードは、位置指定の update ステートメントのパラメーターに別々 の変数をバインドでした、ですが、行セットのバッファーを更新し、これらのバッファーの要素をバインドします。 これにより、更新されたデータと同期されている行セットのバッファーが保持されます。  
  
```  
#define POSITIONED_UPDATE 100  
#define POSITIONED_DELETE 101  
  
SQLUINTEGER    CustIDArray[10];  
SQLCHAR        NameArray[10][51], AddressArray[10][51],   
               PhoneArray[10][11];  
SQLINTEGER     CustIDIndArray[10], NameLenOrIndArray[10],   
               AddressLenOrIndArray[10],  
               PhoneLenOrIndArray[10];  
SQLUSMALLINT   RowStatusArray[10], Action, RowNum;  
SQLHSTMT       hstmtCust, hstmtUpdate, hstmtDelete;  
  
// Set the SQL_ATTR_BIND_TYPE statement attribute to use column-wise   
// binding. Declare the rowset size with the SQL_ATTR_ROW_ARRAY_SIZE   
// statement attribute. Set the SQL_ATTR_ROW_STATUS_PTR statement   
// attribute to point to the row status array.  
SQLSetStmtAttr(hstmtCust, SQL_ATTR_ROW_BIND_TYPE, SQL_BIND_BY_COLUMN, 0);  
SQLSetStmtAttr(hstmtCust, SQL_ATTR_ROW_ARRAY_SIZE, 10, 0);  
SQLSetStmtAttr(hstmtCust, SQL_ATTR_ROW_STATUS_PTR, RowStatusArray, 0);  
  
// Bind arrays to the CustID, Name, Address, and Phone columns.  
SQLBindCol(hstmtCust, 1, SQL_C_ULONG, CustIDArray, 0, CustIDIndArray);  
SQLBindCol(hstmtCust, 2, SQL_C_CHAR, NameArray, sizeof(NameArray[0]),  
            NameLenOrIndArray);  
SQLBindCol(hstmtCust, 3, SQL_C_CHAR, AddressArray, sizeof(AddressArray[0]),  
         AddressLenOrIndArray);  
SQLBindCol(hstmtCust, 4, SQL_C_CHAR, PhoneArray, sizeof(PhoneArray[0]),  
            PhoneLenOrIndArray);  
  
// Set the cursor name to Cust.  
SQLSetCursorName(hstmtCust, "Cust", SQL_NTS);  
  
// Prepare positioned update and delete statements.  
SQLPrepare(hstmtUpdate,  
   "UPDATE Customers SET Address = ?, Phone = ? WHERE CURRENT OF Cust",  
   SQL_NTS);  
SQLPrepare(hstmtDelete, "DELETE FROM Customers WHERE CURRENT OF Cust", SQL_NTS);  
  
// Execute a statement to retrieve rows from the Customers table.  
SQLExecDirect(hstmtCust,  
   "SELECT CustID, Name, Address, Phone FROM Customers FOR UPDATE OF Address, Phone",  
   SQL_NTS);  
  
// Fetch and display the first 10 rows.  
SQLFetchScroll(hstmtCust, SQL_FETCH_NEXT, 0);  
DisplayData(CustIDArray, CustIDIndArray, NameArray, NameLenOrIndArray, AddressArray,  
            AddressLenOrIndArray, PhoneArray, PhoneLenOrIndArray, RowStatusArray);  
  
// Call GetAction to get an action and a row number from the user.  
while (GetAction(&Action, &RowNum)) {  
   switch (Action) {  
  
      case SQL_FETCH_NEXT:  
      case SQL_FETCH_PRIOR:  
      case SQL_FETCH_FIRST:  
      case SQL_FETCH_LAST:  
      case SQL_FETCH_ABSOLUTE:  
      case SQL_FETCH_RELATIVE:  
         // Fetch and display the requested data.  
         SQLFetchScroll(hstmtCust, Action, RowNum);  
         DisplayData(CustIDArray, CustIDIndArray, NameArray, NameLenOrIndArray,  
                     AddressArray, AddressLenOrIndArray, PhoneArray,  
                     PhoneLenOrIndArray, RowStatusArray);  
         break;  
  
      case POSITIONED_UPDATE:  
         // Get the new data and place it in the rowset buffers.  
         GetNewData(AddressArray[RowNum - 1], &AddressLenOrIndArray[RowNum - 1],  
                     PhoneArray[RowNum - 1], &PhoneLenOrIndArray[RowNum - 1]);  
  
         // Bind the elements of the arrays at position RowNum-1 to the   
         // parameters of the positioned update statement.  
         SQLBindParameter(hstmtUpdate, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR,  
                           50, 0, AddressArray[RowNum - 1], sizeof(AddressArray[0]),  
                           &AddressLenOrIndArray[RowNum - 1]);  
         SQLBindParameter(hstmtUpdate, 2, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR,  
                           10, 0, PhoneArray[RowNum - 1], sizeof(PhoneArray[0]),  
                           &PhoneLenOrIndArray[RowNum - 1]);  
  
         // Position the rowset cursor. The rowset is 1-based.  
         SQLSetPos(hstmtCust, RowNum, SQL_POSITION, SQL_LOCK_NO_CHANGE);  
  
         // Execute the positioned update statement to update the row.  
         SQLExecute(hstmtUpdate);  
         break;  
  
      case POSITIONED_DELETE:  
         // Position the rowset cursor. The rowset is 1-based.  
         SQLSetPos(hstmtCust, RowNum, SQL_POSITION, SQL_LOCK_NO_CHANGE);  
  
         // Execute the positioned delete statement to delete the row.  
         SQLExecute(hstmtDelete);  
         break;  
   }  
}  
  
// Close the cursor.  
SQLCloseCursor(hstmtCust);  
```
