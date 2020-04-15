---
title: 行セットの行を SQLSetPos で更新する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- updating data [ODBC], SQLSetPos
- data updates [ODBC], SQLSetPos
- SQLSetPos function [ODBC], updating rows
ms.assetid: d83a8c2a-5aa8-4f19-947c-79a817167ee1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4851d4ba741379fc188b2b88c895a378ef3bb80d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298972"
---
# <a name="updating-rows-in-the-rowset-with-sqlsetpos"></a>SQLSetPos による行セットの行の更新
**SQLSetPos**の更新操作では、データ ソースがテーブルの 1 つ以上の選択した行を更新します (長さ/インジケーター バッファーの値がSQL_COLUMN_IGNOREされていない限り、バインドされた各列のアプリケーション バッファー内のデータを使用します)。 バインドされていない列は更新されません。  
  
 **SQLSetPos**を使用して行を更新するには、アプリケーションは次の処理を行います。  
  
1.  新しいデータ値を行セット バッファーに配置します。 **SQLSetPos**を使用して長いデータを送信する方法の詳細については、「[長いデータと SQL セットポスおよび SQLBulk オペレーション](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md)」を参照してください。  
  
2.  必要に応じて、各列の長さ/インジケーター バッファーの値を設定します。 これは、文字列バッファーにバインドされた列のデータまたはSQL_NTSのバイト長、バイナリ バッファーにバインドされた列のデータのバイト長、および NULL に設定される列のSQL_NULL_DATAです。  
  
3.  SQL_COLUMN_IGNOREに更新されない列の長さ/インジケーター バッファーの値を設定します。 アプリケーションはこの手順をスキップして既存のデータを再送信できますが、これは非効率的であり、読み取り時に切り捨てられたデータ ソースに値を送信するリスクがあります。  
  
4.  *[操作*] を SQL_UPDATE に設定し、更新する行の番号に*設定された行番号を指定*して**SQLSetPos**を呼び出します。 *行番号*が 0 の場合、行セット内のすべての行が更新されます。  
  
 **SQLSetPos が**戻った後、現在の行は更新された行に設定されます。  
  
 行セットのすべての行を更新する場合 *(RowNumber*が 0)、アプリケーションは行操作配列の対応する要素 (SQL_ATTR_ROW_OPERATION_PTR ステートメント属性によって指す) をSQL_ROW_IGNORE に設定することで、特定の行の更新を無効にすることができます。 行操作配列は、要素のサイズと数に対応し、行の状態の配列 (SQL_ATTR_ROW_STATUS_PTR ステートメント属性で示されます) に対応します。 正常にフェッチされ、行セットから削除されていない結果セット内の行だけを更新するために、アプリケーションは行セットをフェッチした関数の行状態配列を**SQLSetPos**に行操作配列として使用します。  
  
 更新としてデータ ソースに送信されるすべての行に対して、アプリケーション バッファーに有効な行データが必要です。 アプリケーション・バッファーがフェッチによって満たされ、行状況配列が維持されている場合、これらの行位置のそれぞれの値を、SQL_ROW_DELETED、SQL_ROW_ERROR、またはSQL_ROW_NOROWにすることはできません。  
  
 たとえば、次のコードでは、ユーザーが Customers テーブルをスクロールして、新しい行を更新、削除、または追加できます。 新しいデータを行セット バッファーに配置してから **、SQLSetPos**を呼び出して新しい行を更新または追加します。 新しい行を保持するために、行セット バッファーの末尾に余分な行が割り当てられます。これにより、新しい行のデータがバッファーに入れられた場合に既存のデータが上書きされるのを防ぎます。  
  
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
