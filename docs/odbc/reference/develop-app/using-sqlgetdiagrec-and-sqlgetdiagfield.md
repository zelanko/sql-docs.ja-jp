---
title: を使用して、およびフィールドを使用して |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], SqlGetDiagField
- SQLGetDiagField function [ODBC], and SQLGetDiagRec
- SQLGetDiagRec function [ODBC], and SQLGetDiagField
- diagnostic information [ODBC], SqlGetDiagRec
- retrieving diagnostic information [ODBC]
ms.assetid: 4f486bb1-fad8-4064-ac9d-61f2de85b68b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 69a17086253b40469b0ed98cb6f870f319f03f52
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306753"
---
# <a name="using-sqlgetdiagrec-and-sqlgetdiagfield"></a>SQLGetDiagRec および SQLGetDiagField の使用
アプリケーションは、診断情報を取得するために**SQLGetDiagRec**または**SQLGetDiagField**を呼び出します。 これらの関数は、環境、接続、ステートメント、または記述子ハンドルを受け入れ、そのハンドルを最後に使用した関数から診断を返します。 特定のハンドルに記録された診断は、そのハンドルを使用して新しい関数が呼び出されると破棄されます。 関数が複数の診断レコードを返した場合、アプリケーションはこれらの関数を複数回呼び出します。ステータス レコードの合計数は、SQL_DIAG_NUMBER オプションを指定してヘッダー レコード (レコード 0) の**SQLGetDiagField**を呼び出すことによって取得されます。  
  
 アプリケーションは **、SQLGetDiagField**を呼び出し、取得するフィールドを指定することによって、個々の診断フィールドを取得します。 特定の診断フィールドには、特定のタイプのハンドルに対して何の意味もありません。 診断フィールドとその意味の一覧については[、SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)関数の説明を参照してください。  
  
 アプリケーションは、SQLSTATE、ネイティブ エラー コード、および診断メッセージを 1 回の**呼び出**しで取得します。**ヘッダー**レコードから情報を取得するために使用することはできません。  
  
 たとえば、次のコードは、ユーザーに SQL ステートメントを要求して実行します。 診断情報が返された場合は **、SQLGetDiagField**を呼び出して状態レコードの数を取得し **、SQLSTATE、** ネイティブ エラー コード、および診断メッセージをそれらのレコードから取得します。  
  
```  
SQLCHAR       SqlState[6], SQLStmt[100], Msg[SQL_MAX_MESSAGE_LENGTH];  
SQLINTEGER    NativeError;  
SQLSMALLINT   i, MsgLen;  
SQLRETURN     rc1, rc2;  
SQLHSTMT      hstmt;  
  
// Prompt the user for an SQL statement.  
GetSQLStmt(SQLStmt);  
  
// Execute the SQL statement and return any errors or warnings.  
rc1 = SQLExecDirect(hstmt, SQLStmt, SQL_NTS);  
if ((rc1 == SQL_SUCCESS_WITH_INFO) || (rc1 == SQL_ERROR)) {
   SQLLEN numRecs = 0;
   SQLGetDiagField(SQL_HANDLE_STMT, hstmt, 0, SQL_DIAG_NUMBER, &numRecs, 0, 0);
   // Get the status records.
   i = 1;  
   while (i <= numRecs && (rc2 = SQLGetDiagRec(SQL_HANDLE_STMT, hstmt, i, SqlState, &NativeError,  
            Msg, sizeof(Msg), &MsgLen)) != SQL_NO_DATA) {  
      DisplayError(SqlState,NativeError,Msg,MsgLen);  
      i++;  
   }  
}  
  
if ((rc1 == SQL_SUCCESS) || (rc1 == SQL_SUCCESS_WITH_INFO)) {  
   // Process statement results, if any.  
}  
```
