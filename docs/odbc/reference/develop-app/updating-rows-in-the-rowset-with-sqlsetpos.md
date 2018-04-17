---
title: SQLSetPos で行セット内の行を更新 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- updating data [ODBC], SQLSetPos
- data updates [ODBC], SQLSetPos
- SQLSetPos function [ODBC], updating rows
ms.assetid: d83a8c2a-5aa8-4f19-947c-79a817167ee1
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 868728a48781c03c6f1df7ec3d43108d989d5913
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="updating-rows-in-the-rowset-with-sqlsetpos"></a>SQLSetPos で行セット内の行を更新
更新操作**SQLSetPos**により、データ ソースのデータを使用してアプリケーションのバッファーでバインドされた各列 (長さ/インジケーター バッファー内の値が SQL_COLUMN_IGNORE の場合)、テーブルの 1 つまたは複数の選択した行を更新します。 バインドされていない列は更新されません。  
  
 行を更新する**SQLSetPos**アプリケーションは、次を実行します。  
  
1.  行セットのバッファーで新しいデータ値を配置します。 長い形式のデータを送信する方法について**SQLSetPos**を参照してください[長い形式のデータおよび SQLSetPos SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md)です。  
  
2.  必要に応じて、各列の長さ/インジケーター バッファーの値を設定します。 これは、バイナリのバッファー、および SQL_NULL_DATA を NULL に設定する列にバインドされた列のデータのバイト長文字列バッファーにバインドされている列のデータまたは SQL_NTS のバイト長です。  
  
3.  SQL_COLUMN_IGNORE に更新する列の長さ/インジケーター バッファーの値を設定します。 アプリケーションは、この手順をスキップし、既存のデータを再送信、この効率的ではありませんし、リスクが切り詰められました。 読み取られたときにデータ ソースに値を送信します。  
  
4.  呼び出し**SQLSetPos**で*操作*SQL_UPDATE に設定し、 *RowNumber*を更新する行の数に設定します。 場合*RowNumber*が 0 の行セット内のすべての行が更新されます場合、。  
  
 後に**SQLSetPos**が返される、現在の行が更新された行に設定します。  
  
 行セットのすべての行を更新するときに (*RowNumber*が 0 に等しい)、アプリケーションは、(、SQL_ATTR_ROW_OPERATION_PTR によって指さ行操作配列の対応する要素を設定して、特定の行の更新を無効にできますステートメント属性) SQL_ROW_IGNORE にします。 行操作配列は、(SQL_ATTR_ROW_STATUS_PTR ステートメント属性によって示される)、行の状態配列に要素のサイズと数に対応しています。 アプリケーションを正常にフェッチされた行セットから削除されていない結果セットの行のみを更新するには、行操作配列と、行セットをフェッチする関数から行の状態配列を使用して**SQLSetPos**.  
  
 更新プログラムとしてデータ ソースに送信されるすべての行でアプリケーション バッファーは有効な行データである必要があります。 フェッチによってアプリケーション バッファーが入力し、行の状態配列が維持されている場合は、これらの各の行位置でその値しないで SQL_ROW_DELETED、SQL_ROW_ERROR、または SQL_ROW_NOROW です。  
  
 たとえば、次のコードは、Customers テーブルをスクロールし、更新、削除、または新しい行を追加するユーザーを許可します。 新しいデータを呼び出す前に、行セットのバッファーに照らし合わせること**SQLSetPos**を更新または新しい行を追加します。 新しい行を保持するために、行セットのバッファーの末尾に余分な行が割り当てられています。これは既存のデータがバッファーに新しい行のデータを配置しているときに上書きすることを防ぎます。  
  
```  
#define UPDATE_ROW   100  
#define DELETE_ROW   101  
#define ADD_ROW      102  
  
SQLUINTEGER    CustIDArray[11];  
SQLCHAR        NameArray[11][51], AddressArray[11][51],   
               PhoneArray[11][11];  
SQLINTEGER     CustIDIndArray[11], NameLenOrIndArray[11],   
               AddressLenOrIndArray[11],  
               PhoneLenOrIndArray[11];  
SQLUSMALLINT   RowStatusArray[10], Action, RowNum;  
SQLRETURN      rc;  
SQLHSTMT       hstmt;  
  
// Set the SQL_ATTR_ROW_BIND_TYPE statement attribute to use column-wise   
// binding. Declare the rowset size with the SQL_ATTR_ROW_ARRAY_SIZE   
// statement attribute. Set the SQL_ATTR_ROW_STATUS_PTR statement   
// attribute to point to the row status array.  
SQLSetStmtAttr(hstmt, SQL_ATTR_CURSOR_TYPE, SQL_CURSOR_KEYSET_DRIVEN, 0);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_BIND_TYPE, SQL_BIND_BY_COLUMN, 0);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, 10, 0);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, RowStatusArray, 0);  
  
// Bind arrays to the CustID, Name, Address, and Phone columns.  
SQLBindCol(hstmt, 1, SQL_C_ULONG, CustIDArray, 0, CustIDIndArray);  
SQLBindCol(hstmt, 2, SQL_C_CHAR, NameArray, sizeof(NameArray[0]), NameLenOrIndArray);  
SQLBindCol(hstmt, 3, SQL_C_CHAR, AddressArray, sizeof(AddressArray[0]),  
            AddressLenOrIndArray);  
SQLBindCol(hstmt, 4, SQL_C_CHAR, PhoneArray, sizeof(PhoneArray[0]),  
            PhoneLenOrIndArray);  
  
// Execute a statement to retrieve rows from the Customers table.  
SQLExecDirect(hstmt, "SELECT CustID, Name, Address, Phone FROM Customers", SQL_NTS);  
  
// Fetch and display the first 10 rows.  
rc = SQLFetchScroll(hstmt, SQL_FETCH_NEXT, 0);  
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
         SQLFetchScroll(hstmt, Action, RowNum);  
         DisplayData(CustIDArray, CustIDIndArray,  
                     NameArray, NameLenOrIndArray,  
                     AddressArray, AddressLenOrIndArray,  
                     PhoneArray, PhoneLenOrIndArray, RowStatusArray);  
         break;  
  
      case UPDATE_ROW:  
         // Place the new data in the rowset buffers and update the   
         // specified row.  
         GetNewData(&CustIDArray[RowNum - 1], &CustIDIndArray[RowNum - 1],  
                  NameArray[RowNum - 1], &NameLenOrIndArray[RowNum - 1],  
                  AddressArray[RowNum - 1], &AddressLenOrIndArray[RowNum - 1],  
                  PhoneArray[RowNum - 1], &PhoneLenOrIndArray[RowNum - 1]);  
         SQLSetPos(hstmt, RowNum, SQL_UPDATE, SQL_LOCK_NO_CHANGE);  
         break;  
  
      case DELETE_ROW:  
         // Delete the specified row.  
         SQLSetPos(hstmt, RowNum, SQL_DELETE, SQL_LOCK_NO_CHANGE);  
         break;  
  
      case ADD_ROW:  
         // Place the new data in the rowset buffers at index 10.   
         // This is an extra element for new rows so rowset data is   
         // not overwritten. Insert the new row. Row 11 corresponds   
         // to index 10.  
         GetNewData(&CustIDArray[10], &CustIDIndArray[10],  
                     NameArray[10], &NameLenOrIndArray[10],  
                     AddressArray[10], &AddressLenOrIndArray[10],  
                     PhoneArray[10], &PhoneLenOrIndArray[10]);  
         SQLSetPos(hstmt, 11, SQL_ADD, SQL_LOCK_NO_CHANGE);  
         break;  
   }  
}  
  
// Close the cursor.  
SQLCloseCursor(hstmt);  
```
