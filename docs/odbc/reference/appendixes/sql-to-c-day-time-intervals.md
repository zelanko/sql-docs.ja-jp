---
title: 'SQL から C: 日の間隔 |マイクロソフトドキュメント'
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to C types [ODBC], day-time intervals
- day-time intervals [ODBC]
- data conversions from SQL to C types [ODBC], day-time intervals
- intervals [ODBC], converting
ms.assetid: 8ea84d69-2292-4128-89a0-f184f68abb98
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1318da5285ba2384dd23e4c235e698aa72c7658e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296472"
---
# <a name="sql-to-c-day-time-intervals"></a>SQL から C へ: 日付と時刻の間隔

日時間間隔 ODBC SQL データ型の識別子は次のとおりです。

- SQL_INTERVAL_DAY
- SQL_INTERVAL_DAY_TO_MINUTE
- SQL_INTERVAL_HOUR
- SQL_INTERVAL_DAY_TO_SECOND
- SQL_INTERVAL_MINUTE
- SQL_INTERVAL_HOUR_TO_MINUTE
- SQL_INTERVAL_SECOND
- SQL_INTERVAL_HOUR_TO_SECOND
- SQL_INTERVAL_DAY_TO_HOUR
- SQL_INTERVAL_MINUTE_TO_SECOND

次の表は、SQL データを変換できる日時間間隔の ODBC C データ型を示しています。 表の列と用語の説明については[、SQL から C データ型へのデータの変換を参照してください](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)。

|C 型識別子|テスト|**ターゲット値Ptr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|すべての日中 C インターバル・タイプ|末尾のフィールド部分が切り捨てられていない<br /><br /> 末尾のフィールド部分が切り捨てられました<br /><br /> ターゲットの先行精度は、ソースからのデータを保持するのに十分な大きさではありません|Data<br /><br /> 切り捨てられたデータ<br /><br /> 未定義。|データの長さ<br /><br /> データの長さ<br /><br /> 未定義。|該当なし<br /><br /> 01S07<br /><br /> 22015|  
|SQL_C_STINYINT [b] SQL_C_UTINYINT [b] SQL_C_USHORT[b] SQL_C_SHORT[b] SQL_C_SLONG [b] SQL_C_ULONG[b] SQL_C_NUMERIC[b] SQL_C_BIGINT[b]|間隔の精度は単一のフィールドであり、データは切り捨てられずに変換されました<br /><br /> 間隔の精度は単一フィールドであり、小数部は切り捨てられています<br /><br /> 間隔の精度は単一フィールドであり、全体が切り捨てられました<br /><br /> 間隔の精度が単一フィールドではありませんでした|Data<br /><br /> 切り捨てられたデータ<br /><br /> 切り捨てられたデータ<br /><br /> 未定義。|C データ型のサイズ<br /><br /> データの長さ<br /><br /> データの長さ<br /><br /> C データ型のサイズ|該当なし<br /><br /> 01S07<br /><br /> 22003<br /><br /> 07006|  
|SQL_C_BINARY|データ長のバイト長<=*バッファ長*<br /><br /> データのバイト長 >*バッファ長*|Data<br /><br /> 未定義。|データの長さ<br /><br /> 未定義。|該当なし<br /><br /> 22003|  
|SQL_C_CHAR|バッファー長<文字バイト*長*<br /><br /> (小数部ではなく) バッファ*長*<整数の桁数<br /><br /> 整数の数 (小数部ではなく) >= *BufferLength*|Data<br /><br /> 切り捨てられたデータ<br /><br /> 未定義。|C データ型のサイズ<br /><br /> C データ型のサイズ<br /><br /> 未定義。|該当なし<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|文字長<*バッファー長*<br /><br /> (小数部ではなく) バッファ*長*<整数の桁数<br /><br /> 整数の数 (小数部ではなく) >= *BufferLength*|Data<br /><br /> 切り捨てられたデータ<br /><br /> 未定義。|C データ型のサイズ<br /><br /> C データ型のサイズ<br /><br /> 未定義。|該当なし<br /><br /> 01004<br /><br /> 22003|  
  
 [a] 日時間間隔 SQL タイプは、任意の日時間間隔 C 型に変換できます。  
  
 [b] 間隔の精度が単一フィールド (DAY、hour、minute、または SECOND のいずれか) の場合、間隔 SQL 型は任意の正確な数値 (SQL_C_STINYINT、SQL_C_UTINYINT、SQL_C_USHORT、SQL_C_SHORT、SQL_C_SLONG、SQL_C_ULONG、または SQL_C_NUMERIC) に変換できます。  
  
間隔 SQL 型の既定の変換は、対応する C 間隔データ型です。 次に、アプリケーションは、初期化されたSQL_INTERVAL_STRUCT構造体を指すように列またはパラメーターをバインドします (または、SQL_DESC_DATA_PTR フィールドを設定して、SQL_INTERVAL_STRUCT構造体を指します (または **、sqlGetData**の呼び出しで*引数 TargetValuePtr*としてSQL_INTERVAL_STRUCT構造体へのポインターを渡します)。  
  
次の例では、SQL_INTERVAL_DAY_TO_MINUTE型の列からSQL_INTERVAL_STRUCT構造にデータを転送して、DAY_TO_HOUR間隔で戻ってくる方法を示します。  

```cpp
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
