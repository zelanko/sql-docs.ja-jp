---
title: 位置指定更新および削除ステートメント |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- positioned deletes [ODBC]
- data updates [ODBC], positioned update or delete
- positioned updates [ODBC]
- updating data [ODBC], positioned update or delete
ms.assetid: 0eafba50-02c7-46ca-a439-ef3307b935dc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6e5316bee7057b30eace326b3ca82b30b75741fb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282363"
---
# <a name="positioned-update-and-delete-statements"></a>位置指定の UPDATE および DELETE ステートメント
アプリケーションは、位置指定更新または削除ステートメントを使用して、結果セット内の現在の行を更新または削除できます。 位置指定更新および削除ステートメントは、一部のデータ ソースでサポートされますが、すべてのステートメントがサポートされているわけではありません。 データ ソースが位置指定更新および削除ステートメントをサポートしているかどうかを判断するために、アプリケーションは**SQLGetInfo**を呼び出して、SQL_DYNAMIC_CURSOR_ATTRIBUTES1、SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1、SQL_KEYSET_CURSOR_ATTRIBUTES1、またはSQL_STATIC_CURSOR_ATTRIBUTES1 *InfoType* (カーソルの種類に応じて) を呼び出します。 ODBC カーソル ライブラリは位置指定更新および削除ステートメントをシミュレートすることに注意してください。  
  
 位置指定更新ステートメントまたは位置指定更新ステートメントまたは削除ステートメントを使用するには、アプリケーションは**SELECT FOR UPDATE**ステートメントを使用して結果セットを作成する必要があります。 このステートメントの構文は次のとおりです。  
  
 **[** **すべての**&#124;**異なる**]*選択リストを選択します。*  
  
 **FROM** *テーブル参照リスト*  
  
 [**WHERE** *検索条件*]  
  
 [*列名*] の**更新のため****[ ,** *列名*].]  
  
 アプリケーションは、更新または削除する行にカーソルを移動します。 **SQLFetchScroll**を呼び出して、必要な行を含む行セットを取得し **、SQLSetPos**を呼び出して行セット カーソルをその行に配置することで、これを行うことができます。 アプリケーションは、結果セットで使用されているステートメントとは異なるステートメントで位置指定更新または削除ステートメントを実行します。 これらのステートメントの構文は次のとおりです。  
  
 **テーブル***名を*更新  
  
 **SET** *列識別子***=**{*式*&#124; **NULL**}  
  
 [**,***列識別子***=**{*式*&#124; **NULL**} .  
  
 **カーソル名の現在***cursor-name*  
  
 テーブル名**から削除***する-***現在の***カーソル名*  
  
 これらのステートメントにはカーソル名が必要であることに注意してください。 アプリケーションは、結果セットを作成するステートメントを実行する前に**SQLSetCursorName**でカーソル名を指定するか、またはカーソルの作成時にデータ ソースにカーソル名を自動的に生成させることができます。 後者の場合、アプリケーションは、位置指定された更新および削除ステートメントで**使用するために、SQLGetCursorName**を呼び出すことによって、このカーソル名を取得します。  
  
 たとえば、次のコードでは、ユーザーが顧客テーブルをスクロールして顧客レコードを削除したり、住所や電話番号を更新したりできます。 **SQLSetCursorName**を呼び出して、顧客の結果セットを作成する前にカーソル名を指定し、結果セットに*hstmtCust、* 位置指定更新ステートメントに*hstmtUpdate、* 位置指定削除ステートメントに*hstmtDelete*という 3 つのステートメント ハンドルを使用します。 コードは、位置指定更新ステートメントのパラメーターに個別の変数をバインドできますが、行セット バッファーを更新し、これらのバッファーの要素をバインドします。 これにより、行セット バッファーと更新されたデータの同期が維持されます。  
  
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
