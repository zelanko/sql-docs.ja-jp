---
title: 'SQL から C: 数値 |マイクロソフトドキュメント'
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data conversions from SQL to C types [ODBC], numeric
- numeric data type [ODBC], converting
- converting data from SQL to C types [ODBC], numeric
ms.assetid: 76f8b5d5-4bd0-4dcb-a90a-698340e0d36e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 36b24da4023a96b686742416b83bb5790e129278
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296412"
---
# <a name="sql-to-c-numeric"></a>SQL から C へ: 数値

数値 ODBC SQL データ型の識別子は次のとおりです。

- SQL_DECIMAL  
- SQL_BIGINT  
- SQL_NUMERIC  
- SQL_REAL  
- SQL_TINYINT  
- SQL_FLOAT  
- SQL_SMALLINT  
- SQL_DOUBLE SQL_INTEGER  

次の表は、数値 SQL データの変換先となる ODBC C データ型を示しています。 表の列と用語の説明については[、SQL から C データ型へのデータの変換を参照してください](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)。  

|C 型識別子|テスト|**ターゲット値Ptr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|バッファー長<文字バイト*長*<br /><br /> (小数部ではなく) バッファ*長*<整数の桁数<br /><br /> 整数の数 (小数部ではなく) >= *BufferLength*|Data<br /><br /> 切り捨てられたデータ<br /><br /> 未定義。|データの長さ (バイト単位)<br /><br /> データの長さ (バイト単位)<br /><br /> 未定義。|該当なし<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|文字長<*バッファー長*<br /><br /> (小数部ではなく) バッファ*長*<整数の桁数<br /><br /> 整数の数 (小数部ではなく) >= *BufferLength*|Data<br /><br /> 切り捨てられたデータ<br /><br /> 未定義。|文字でのデータの長さ<br /><br /> 文字でのデータの長さ<br /><br /> 未定義。|該当なし<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_STINYINT<br /><br /> SQL_C_UTINYINT<br /><br /> SQL_C_TINYINT<br /><br /> SQL_C_SBIGINT<br /><br /> SQL_C_UBIGINT<br /><br /> SQL_C_SSHORT<br /><br /> SQL_C_USHORT<br /><br /> SQL_C_SHORT<br /><br /> SQL_C_SLONG<br /><br /> SQL_C_ULONG<br /><br /> SQL_C_LONG<br /><br /> SQL_C_NUMERIC|切り捨てなしで変換されたデータ[a]<br /><br /> 小数部の桁の切り捨てで変換されたデータ[a]<br /><br /> データの変換は(小数部とは対照的に)全体の損失をもたらす[a]|Data<br /><br /> 切り捨てられたデータ<br /><br /> 未定義。|C データ型のサイズ<br /><br /> C データ型のサイズ<br /><br /> 未定義。|該当なし<br /><br /> 01S07<br /><br /> 22003|  
|SQL_C_FLOAT<br /><br /> SQL_C_DOUBLE|データが、数値の変換先のデータ型の範囲内にある[a]<br /><br /> データが、数値の変換先のデータ型の範囲外である[a]。|Data<br /><br /> 未定義。|C データ型のサイズ<br /><br /> 未定義。|該当なし<br /><br /> 22003|  
|SQL_C_BIT|データは 0 または 1[a]<br /><br /> データが 0 より大きく、2 より小さく、1[a] に等しくない<br /><br /> データが 0 未満か、2[a] 以上である|Data<br /><br /> 切り捨てられたデータ<br /><br /> 未定義。|1[b]<br /><br /> 1[b]<br /><br /> 未定義。|該当なし<br /><br /> 01S07<br /><br /> 22003|  
|SQL_C_BINARY|データ長のバイト長<=*バッファ長*<br /><br /> データのバイト長 >*バッファ長*|Data<br /><br /> 未定義。|データの長さ<br /><br /> 未定義。|該当なし<br /><br /> 22003|  
|SQL_C_INTERVAL_MONTH[c] SQL_C_INTERVAL_YEAR[c] SQL_C_INTERVAL_DAY[c] SQL_C_INTERVAL_HOUR[c] SQL_C_INTERVAL_MINUTE[c] SQL_C_INTERVAL_SECOND[c]|データが切り捨てられていない<br /><br /> 秒の小数部が切り捨てられる<br /><br /> 数値の全体部分が切り捨てられました|Data<br /><br /> 切り捨てられたデータ<br /><br /> 未定義。|データの長さ (バイト単位)<br /><br /> データの長さ (バイト単位)<br /><br /> 未定義。|該当なし<br /><br /> 01S07<br /><br /> 22015|  
|SQL_C_INTERVAL_DAY_TO_SECOND SQL_C_INTERVAL_DAY_TO_MINUTESQL_C_INTERVAL_DAY_TO_HOURSQL_C_INTERVAL_HOUR_TO_SECOND SQL_C_INTERVAL_HOUR_TO_MINUTESQL_C_INTERVAL_DAY_TO_SECONDSQL_C_INTERVAL_DAY_TO_HOURSQL_C_INTERVAL_YEAR_TO_MONTH|数値の全体部分が切り捨てられました|未定義。|未定義。|22015|  
  
 [a] この変換では *、BufferLength*の値は無視されます。 ドライバーは、**ターゲット値Ptr*のサイズは、Cデータ型のサイズであると仮定します。  
  
 [b] これは、対応する C データ型のサイズです。  
  
 [c] この変換は、正確な数値データ型 (SQL_DECIMAL、SQL_NUMERIC、SQL_TINYINT、SQL_SMALLINT、SQL_INTEGER、およびSQL_BIGINT) に対してのみサポートされます。 近似数値データ型 (SQL_REAL、SQL_FLOAT、またはSQL_DOUBLE) ではサポートされません。  

## <a name="sql_c_numeric-and-sqlsetdescfield"></a>SQL_C_NUMERICとSQLセットフィールド

 SQL_C_NUMERIC値を使用して手動バインディングを実行するには[、SQLSetDesc フィールド関数](../../../odbc/reference/syntax/sqlsetdescfield-function.md)が必要です。 (ODBC 3.0 で SQLSetDesc フィールドが追加されました。手動バインディングを実行するには、まず記述子ハンドルを取得する必要があります。  

```cpp
if (fCType == SQL_C_NUMERIC) {   
   // special processing required for NUMERIC to get right scale & precision  
   // Modify the fields in the implicit application parameter descriptor  
   SQLHDESC hdesc=NULL;  
  
   // Use SQL_ATTR_APP_ROW_DESC for calls to SQLBindCol()  
   // Use SQL_ATTR_APP_PARAM_DESC for calls to SQLBindParameter()  
   //  
   // retcode = SQLGetStmtAttr(hstmt, SQL_ATTR_APP_ROW_DESC, &hdesc, 0, NULL);  
   retcode = SQLGetStmtAttr(hstmt, SQL_ATTR_APP_PARAM_DESC, &hdesc, 0, NULL);  
   if (!ODBC_CALL_SUCCESS(retcode)) {  
      printf ("\nSQLGetStmtAttr failed");  
      i = 1;  
      sqlstate[7] = '\0';  
      while (SQLGetDiagRec(SQL_HANDLE_STMT, hstmt, i, sqlstate, &NativeError, wrkbuf, sizeof(wrkbuf), &len) != SQL_NO_DATA) {  
         printf("\niTestCase = %d Failed...Precision = %d, Scale = %d\nNativeError=%d, State=%s, \n  Message=%s",   
            iTestCase, Precision, Scale, NativeError, sqlstate, wrkbuf);  
         i++;  
      }  
      continue;  
   }  
   retcode = SQLSetDescField(hdesc, iCol, SQL_DESC_TYPE, (SQLPOINTER) SQL_C_NUMERIC, 0);  
   if (!ODBC_CALL_SUCCESS(retcode))  
      goto error;  
   retcode = SQLSetDescField(hdesc, iCol, SQL_DESC_PRECISION, (SQLPOINTER)num.precision, 0);  
   if (!ODBC_CALL_SUCCESS(retcode))  
      goto error;  
   retcode = SQLSetDescField(hdesc, iCol, SQL_DESC_SCALE, (SQLPOINTER)num.scale, 0);  
   if (!ODBC_CALL_SUCCESS(retcode))  
      goto error;  
   retcode = SQLSetDescField(hdesc, iCol, SQL_DESC_DATA_PTR, (SQLPOINTER) &(num), sizeof(num));  
```
