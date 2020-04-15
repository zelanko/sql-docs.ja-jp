---
title: ユーザーが入力した SQL ステートメント |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- user-entered SQL statements [ODBC]
- SQL statements [ODBC], constructing
- SQL statements [ODBC], entered by user
ms.assetid: 109af162-93ba-425a-8fe5-49c7dc7cc784
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bf2f8cf36be392cb42a970fa2fb0b19c35daeb39
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301963"
---
# <a name="sql-statements-entered-by-the-user"></a>ユーザーが入力した SQL ステートメント
アドホック分析を実行するアプリケーションでは、一般に、ユーザーが SQL ステートメントを直接入力することもできます。 次に例を示します。  
  
```  
SQLCHAR *     Statement, SqlState[6], Msg[SQL_MAX_MESSAGE_LENGTH];  
SQLSMALLINT   i, MsgLen;  
SQLINTEGER    NativeError;  
SQLRETURN     rc1, rc2;  
  
// Prompt user for SQL statement.  
GetSQLStatement(Statement);  
  
// Execute the statement directly. Because it will be executed only once,  
// do not prepare it.  
rc1 = SQLExecDirect(hstmt, Statement, SQL_NTS);  
  
// Process any errors or returned information.  
if ((rc1 == SQL_ERROR) || rc1 == SQL_SUCCESS_WITH_INFO) {  
   i = 1;  
   while ((rc2 = SQLGetDiagRec(SQL_HANDLE_STMT, hstmt, i, SqlState, &NativeError,  
         Msg, sizeof(Msg), &MsgLen)) != SQL_NO_DATA) {  
      DisplayError(SqlState, NativeError, Msg, MsgLen);  
      i++;  
   }  
}  
```  
  
 この方法により、アプリケーションのコーディングが簡素化されます。アプリケーションは、ユーザーに依存して SQL ステートメントを作成し、データ ソースでステートメントの有効性を確認します。 SQL の複雑さを十分に公開するグラフィカル ユーザー インターフェイスを作成することは困難であるため、単にユーザーに SQL ステートメントテキストの入力を求める方が望ましい場合もあります。 ただし、この場合、ユーザーは SQL だけでなく、クエリ対象のデータ ソースのスキーマも知る必要があります。 アプリケーションによっては、グラフィカル ユーザー インターフェイスを備えており、ユーザーは基本的な SQL ステートメントを作成でき、ユーザーが変更できるテキスト インターフェイスも提供できます。
