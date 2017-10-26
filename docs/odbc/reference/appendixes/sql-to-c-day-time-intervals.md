---
title: "SQL には、c: 1 日間隔で |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- converting data from SQL to C types [ODBC], day-time intervals
- day-time intervals [ODBC]
- data conversions from SQL to C types [ODBC], day-time intervals
- intervals [ODBC], converting
ms.assetid: 8ea84d69-2292-4128-89a0-f184f68abb98
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: cf87c74d4b2667daa032e814bae3655b83a46c31
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sql-to-c-day-time-intervals"></a>SQL から c: 1 日間隔でへ
1 日の時間間隔の ODBC SQL データ型の識別子は次のとおりです。  
  
 SQL_INTERVAL_DAY  
  
 SQL_INTERVAL_DAY_TO_MINUTE  
  
 SQL_INTERVAL_HOUR  
  
 SQL_INTERVAL_DAY_TO_SECOND  
  
 SQL_INTERVAL_MINUTE  
  
 SQL_INTERVAL_HOUR_TO_MINUTE  
  
 SQL_INTERVAL_SECOND  
  
 SQL_INTERVAL_HOUR_TO_SECOND  
  
 SQL_INTERVAL_DAY_TO_HOUR  
  
 SQL_INTERVAL_MINUTE_TO_SECOND  
  
 次の表は、ODBC C データ型の 1 日間隔 SQL データを変換することがありますを示します。 列とテーブルの用語の詳細については、次を参照してください。[に変換するデータを SQL から C データ型に](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)です。  
  
|C 型識別子|テスト|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|すべての時刻 C interval 型|末尾のフィールドの部分は切り捨てられません<br /><br /> 末尾のフィールド部分が切り捨てられます<br /><br /> ソースからデータを保持するために十分な大きさが先頭のターゲットの有効桁数です。|data<br /><br /> 切り捨てられたデータ<br /><br /> 未定義。|データの長さ<br /><br /> データの長さ<br /><br /> 未定義。|n/a<br /><br /> 01S07<br /><br /> 22015|  
|SQL_C_STINYINT [b] SQL_C_UTINYINT [b] SQL_C_USHORT [b] SQL_C_SHORT [b] SQL_C_SLONG [b] SQL_C_ULONG [b] SQL_C_NUMERIC [b] SQL_C_BIGINT [b]|間隔の有効桁数が 1 つのフィールドとデータを切り捨てることがなく変換されました<br /><br /> 間隔の有効桁数が 1 つのフィールドと小数部の切り捨て<br /><br /> 間隔の有効桁数が 1 つのフィールドおよび全体に切り捨てられました。<br /><br /> 間隔の有効桁数が 1 つのフィールド|data<br /><br /> 切り捨てられたデータ<br /><br /> 切り捨てられたデータ<br /><br /> 未定義。|C データ型のサイズ<br /><br /> データの長さ<br /><br /> データの長さ<br /><br /> C データ型のサイズ|n/a<br /><br /> 01S07<br /><br /> 22003<br /><br /> 07006|  
|SQL_C_BINARY|データのバイト長 < = *BufferLength*<br /><br /> データのバイト長 > *BufferLength*|data<br /><br /> 未定義。|データの長さ<br /><br /> 未定義。|n/a<br /><br /> 22003|  
|SQL_C_CHAR|バイトの長さを文字 < *BufferLength*<br /><br /> (ではなく小数部) 全体の数字の数 < *BufferLength*<br /><br /> (ではなく小数部) 全体の数字の数 > = *BufferLength*|data<br /><br /> 切り捨てられたデータ<br /><br /> 未定義。|C データ型のサイズ<br /><br /> C データ型のサイズ<br /><br /> 未定義。|n/a<br /><br /> 01004<br /><br /> 22003|  
_C_WCHAR|文字長 < *BufferLength*<br /><br /> (ではなく小数部) 全体の数字の数 < *BufferLength*<br /><br /> (ではなく小数部) 全体の数字の数 > = *BufferLength*|data<br /><br /> 切り捨てられたデータ<br /><br /> 未定義。|C データ型のサイズ<br /><br /> C データ型のサイズ<br /><br /> 未定義。|n/a<br /><br /> 01004<br /><br /> 22003|  
  
 [a] A 日の時間間隔の SQL 型は、任意の 1 日間隔 C 型に変換できます。  
  
 [b] 間隔精度が 1 つのフィールド (DAY、HOUR、MINUTE、または秒の 1 つ) の場合、SQL 型の間隔が、正確な numeric (SQL_C_STINYINT、SQL_C_UTINYINT、SQL_C_USHORT、SQL_C_SHORT、SQL_C_SLONG、SQL_C_ULONG、または SQL_C_NUMERIC) に変換できます。  
  
 間隔の SQL 型の既定の変換は、対応する C interval データ型です。 アプリケーション、列またはパラメーターをバインド (または、ARD の適切なレコードで、SQL_DESC_DATA_PTR フィールドを設定)、初期化された SQL_INTERVAL_STRUCT 構造体を指す (または、としてsql_INTERVAL_STRUCT構造体へのポインターを渡す*TargetValuePtr*への呼び出しで引数**SQLGetData**)。  
  
 次の例では、DAY_TO_HOUR 間隔として戻ってくるように SQL_INTERVAL_STRUCT 構造に SQL_INTERVAL_DAY_TO_MINUTE 型の列からデータを転送する方法を示します。  
  
```  
SQL_INTERVAL_STRUCT is;  
SQLINTEGER    cbValue;  
SQLUINTEGER   days, hours;  
  
// Execute a select statement; "interval_column" is a column  
// whose data type is SQL_INTERVAL_DAY_TO_MINUTE.  
SQLExecDirect(hstmt, "SELECT interval_column FROM table", SQL_NTS);  
  
// Bind  
SQLBindCol(hstmt, 1, SQL_C_INTERVAL_DAY_TO_MINUTE, &is, sizeof(SQL_INTERVAL_STRUCT), &cbValue);  
  
// Fetch  
SQLFetch(hstmt);  
  
// Process data  
days = is.intval.day_second.day;  
hours = is.intval.day_second.hour;  
```

