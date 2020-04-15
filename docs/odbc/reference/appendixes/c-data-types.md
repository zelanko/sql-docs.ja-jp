---
title: C データ型 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 07/12/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], C data types
- C data types [ODBC], about C data types
- C data types [ODBC]
- C buffers [ODBC]
ms.assetid: b681d260-3dbb-47df-a616-4910d727add7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 979bfe85e1e78b55718e1f12fdcfcc7583097bb4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292302"
---
# <a name="c-data-types"></a>C データ型
ODBC C データ型は、アプリケーションにデータを格納するために使用される C バッファーのデータ型を示します。  
  
 すべてのドライバーは、すべての C データ型をサポートする必要があります。 すべてのドライバーは、サポートする SQL 型を変換できるすべての C 型をサポートする必要があり、すべてのドライバーは少なくとも 1 文字の SQL 型をサポートするためです。 文字 SQL 型は、すべての C 型に変換したり、すべての C 型から変換できるため、すべてのドライバーがすべての C 型をサポートする必要があります。  
  
 C データ型は *、引数を*使用して**SQLBindCol**関数および**SQLGetData**関数で指定し、*値型*引数を持つ**SQLBindParameter**関数で指定します。 また **、SQLSetDescField**を呼び出して ARD または APD のSQL_DESC_CONCISE_TYPEフィールドを設定するか、または*型*引数 (および必要に応じて*SubType*引数) を指定して**SQLSetDescRec**を呼び出し、*記述子ハンドル*引数を ARD または APD のハンドルに設定して指定することもできます。  
  
 次の表は、C データ型の有効な型識別子を示しています。 また、各識別子に対応する ODBC C データ型と、このデータ型の定義も示します。  
  
|C 型識別子|ODBC C の型定義|C 型|  
|-----------------------|--------------------|------------|  
|SQL_C_CHAR|SQLCHAR *|unsigned char *|  
|SQL_C_WCHAR|SQLWCHAR *|wchar_t *|  
|SQL_C_SSHORT[j]|SQLSMALLINT|short int|  
|SQL_C_USHORT[j]|スモートフィント|unsigned short int|  
|SQL_C_SLONG[j]|SQLINTEGER|long int|  
|SQL_C_ULONG[j]|SQLUINTEGER|unsigned long int|  
|SQL_C_FLOAT|SQL リアル|float|  
|SQL_C_DOUBLE|SQLDOUBLE、SQL フロート|double|  
|SQL_C_BIT|SQLCHAR|unsigned char|  
|SQL_C_STINYINT[j]|SQLSCHAR|signed char|  
|SQL_C_UTINYINT[j]|SQLCHAR|unsigned char|  
|SQL_C_SBIGINT|SQLBIGINT|_int64[h]|  
|SQL_C_UBIGINT|SQLUビジント|符号なし_int64 [h]|  
|SQL_C_BINARY|SQLCHAR *|unsigned char *|  
|SQL_C_BOOKMARK[i]|ブックマーク|符号なし長整数 int[d]|  
|SQL_C_VARBOOKMARK|SQLCHAR *|unsigned char *|  
|すべての C インターバル・データ・タイプ|SQL_INTERVAL_STRUCT|この付録の[「C 間隔構造」](../../../odbc/reference/appendixes/c-interval-structure.md)セクションを参照してください。|  
  
 **C 型識別子**SQL_C_TYPE_DATE[c]  
  
 **ODBC C の型定義**SQL_DATE_STRUCT  
  
 **C 型**  
  
```  
struct tagDATE_STRUCT {  
   SQLSMALLINT year;  
   SQLUSMALLINT month;  
   SQLUSMALLINT day;    
} DATE_STRUCT;[a]  
```  
  
 **C 型識別子**SQL_C_TYPE_TIME[c]  
  
 **ODBC C の型定義**SQL_TIME_STRUCT  
  
 **C 型**  
  
```  
struct tagTIME_STRUCT {  
   SQLUSMALLINT hour;  
   SQLUSMALLINT minute;  
   SQLUSMALLINT second;  
} TIME_STRUCT;[a]  
```  
  
 **C 型識別子**SQL_C_TYPE_TIMESTAMP[c]  
  
 **ODBC C の型定義**SQL_TIMESTAMP_STRUCT  
  
 **C 型**  
  
```  
struct tagTIMESTAMP_STRUCT {  
   SQLSMALLINT year;  
   SQLUSMALLINT month;  
   SQLUSMALLINT day;  
   SQLUSMALLINT hour;  
   SQLUSMALLINT minute;  
   SQLUSMALLINT second;  
   SQLUINTEGER fraction;[b]   
} TIMESTAMP_STRUCT;[a]  
```  
  
 **C 型識別子**SQL_C_NUMERIC  
  
 **ODBC C の型定義**SQL_NUMERIC_STRUCT  
  
 **C 型**  
  
```  
struct tagSQL_NUMERIC_STRUCT {  
   SQLCHAR precision;  
   SQLSCHAR scale;  
   SQLCHAR sign[g];  
   SQLCHAR val[SQL_MAX_NUMERIC_LEN];[e], [f]   
} SQL_NUMERIC_STRUCT;  
```  
  
 **C 型識別子**SQL_C_GUID  
  
 **ODBC C の型定義**Sqlguid  
  
 **C 型**  
  
```  
struct tagSQLGUID {  
   DWORD Data1;  
   WORD Data2;  
   WORD Data3;  
   BYTE Data4[8];  
} SQLGUID;[k]  
```  
  
 [a] 日付時刻 C データ型の年、月、日、時、分、および 2 番目のフィールドの値は、グレゴリオ暦の制約に準拠している必要があります。 ([グレゴリオ暦の制約](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md)については、この付録の「 グレゴリオ暦の制約 」を参照してください。  
  
 [b] 分数フィールドの値は 10 億分の 1 秒の数で、0 から 999,999,999 (10 億未満) の範囲です。 たとえば、半秒の分数フィールドの値は 500,000,000、1000 分の 1 秒 (1 ミリ秒) は 1,000,000、100 万分の 1 (1 マイクロ秒) は 1,000、10 億分の 1 秒 (1 ナノ秒) は 1 です。  
  
 [c] ODBC 2 で。*x*、C の日付、時刻、およびタイムスタンプのデータ型は、SQL_C_DATE、SQL_C_TIME、およびSQL_C_TIMESTAMPです。  
  
 [d] ODBC 3 *.x*アプリケーションでは、SQL_C_BOOKMARKではなく、SQL_C_VARBOOKMARKを使用する必要があります。 ODBC 3 *.x*アプリケーションが ODBC 2 で動作する場合。*x*ドライバー、ODBC 3 *.x*ドライバー マネージャーはSQL_C_BOOKMARKにSQL_C_VARBOOKMARKをマップします。  
  
 [e] 数値は、小さなエンディアン モード (左端のバイトが最下位バイト) で、スケールされた整数としてSQL_NUMERIC_STRUCT構造体の*val*フィールドに格納されます。 たとえば、スケールが 4 の数値 10.001 base 10 は、整数 100010 にスケールされます。 これは 16 進形式の 186AA であるため、SQL_NUMERIC_STRUCTの値は "AA 86 01 00 00 ..SQL_MAX_NUMERIC_LEN **#define**で定義されたバイト数を指定して、00" を指定します。  
  
 **SQL_NUMERIC_STRUCT**の詳細については、「 [HOWTO : SQL_NUMERIC_STRUCT を使用した数値データの取得](retrieve-numeric-data-sql-numeric-struct-kb222831.md)」を参照してください。  
  
 [f] SQL_C_NUMERICデータ型の精度と小数点以下桁数のフィールドは、アプリケーションからの入力と、ドライバーからアプリケーションへの出力に使用されます。 ドライバーは、SQL_NUMERIC_STRUCTに数値を書き込むとき、*精度*フィールドの値として独自のドライバー固有の既定値を使用し、*スケール*フィールドのアプリケーション記述子 (既定は 0) のSQL_DESC_SCALE フィールドの値を使用します。 アプリケーションは、アプリケーション記述子のSQL_DESC_PRECISIONフィールドおよびSQL_DESC_SCALEフィールドを設定することにより、精度とスケールに関する独自の値を提供できます。  
  
 [g] 符号フィールドは正の場合は 1、負の場合は 0 です。  
  
 [h] _int64は、一部のコンパイラでは提供されない場合があります。  
  
 [i] _SQL_C_BOOKMARK ODBC 3 *.x*では非推奨になりました。  
  
 [j] _SQL_C_SHORT、SQL_C_LONG、およびSQL_C_TINYINTは、ODBC で符号付きおよび符号なしの型 (SQL_C_SSHORTとSQL_C_USHORT、SQL_C_SLONGとSQL_C_ULONG、SQL_C_STINYINTとSQL_C_UTINYINT) に置き換えられました。 ODBC 2 で動作する ODBC 3 *.x*ドライバー。*x*アプリケーションは、呼び出されたときに、ドライバー マネージャーがドライバーに渡すため、SQL_C_SHORT、SQL_C_LONG、およびSQL_C_TINYINTをサポートする必要があります。  
  
 [k] SQL_C_GUIDはSQL_CHARまたはSQL_WCHARにのみ変換できます。  
  
 このセクションでは、次のトピックについて説明します。  
  
-   [64 ビットの整数の構造](../../../odbc/reference/appendixes/64-bit-integer-structures.md)  
  
## <a name="see-also"></a>参照  
 [ODBC の C データ型](../../../odbc/reference/develop-app/c-data-types-in-odbc.md)
