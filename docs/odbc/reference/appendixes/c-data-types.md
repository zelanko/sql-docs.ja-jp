---
title: C データ型 |Microsoft ドキュメント
ms.custom: ''
ms.date: 07/12/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], C data types
- C data types [ODBC], about C data types
- C data types [ODBC]
- C buffers [ODBC]
ms.assetid: b681d260-3dbb-47df-a616-4910d727add7
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 288ca6cbd5553b963131d34b8e63640518f70ef4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="c-data-types"></a>C データ型
ODBC C データ型では、アプリケーションでデータの格納に使用される C バッファーのデータ型を示します。  
  
 すべてのドライバーは、すべての C データ型をサポートする必要があります。 これが必要なすべてのドライバーをサポートする SQL 型を変換できること、すべての C 型をサポートする必要があり、すべてのドライバーが少なくとも 1 つの文字 SQL 型をサポートします。 すべての C 型から文字 SQL 型を変換できるため、すべてのドライバーは、すべての C 型をサポートする必要があります。  
  
 C データ型がで指定された、 **SQLBindCol**と**SQLGetData**関数を関連付け、 *TargetType*引数および、 **SQLBindParameter**で機能、 *ValueType*引数。 呼び出して指定することも**SQLSetDescField** ARD または APD のまたは呼び出すことによって、SQL_DESC_CONCISE_TYPE フィールドを設定する**SQLSetDescRec**で、*型*引数 (および*サブタイプ*引数が必要な場合) および*DescriptorHandle*引数 ARD または APD のハンドルに設定します。  
  
 次の表は、C データ型の有効な型識別子を一覧表示します。 テーブルには、各識別子とこのデータ型の定義に対応する ODBC C データ型も一覧表示します。  
  
|C 型識別子|ODBC C の typedef|C 型|  
|-----------------------|--------------------|------------|  
|SQL_C_CHAR|SQLCHAR *|unsigned char *|  
|SQL_C_WCHAR|SQLWCHAR *|wchar_t *|  
|SQL_C_SSHORT [j]|SQLSMALLINT|short int|  
|SQL_C_USHORT [j]|SQLUSMALLINT|符号なし short int|  
|SQL_C_SLONG [j]|SQLINTEGER|long int|  
|SQL_C_ULONG [j]|SQLUINTEGER|符号なし long int|  
|SQL_C_FLOAT|SQLREAL|float|  
|SQL_C_DOUBLE|SQLDOUBLE、SQLFLOAT|double|  
|SQL_C_BIT|SQLCHAR|unsigned char|  
|SQL_C_STINYINT [j]|SQLSCHAR|符号付き文字|  
|SQL_C_UTINYINT [j]|SQLCHAR|unsigned char|  
|SQL_C_SBIGINT|SQLBIGINT|_int64 [h]|  
|SQL_C_UBIGINT|SQLUBIGINT|符号なし _int64 [h]|  
|SQL_C_BINARY|SQLCHAR *|unsigned char *|  
|SQL_C_BOOKMARK [i]|ブックマーク|符号なし long int [d]|  
|SQL_C_VARBOOKMARK|SQLCHAR *|unsigned char *|  
|すべての C interval データ型|SQL_INTERVAL_STRUCT|参照してください、 [C 間隔構造](../../../odbc/reference/appendixes/c-interval-structure.md)この付録の後半の「します。|  
  
 **C 型識別子**SQL_C_TYPE_DATE [c]  
  
 **ODBC C typedef** SQL_DATE_STRUCT  
  
 **C 型**  
  
```  
struct tagDATE_STRUCT {  
   SQLSMALLINT year;  
   SQLUSMALLINT month;  
   SQLUSMALLINT day;    
} DATE_STRUCT;[a]  
```  
  
 **C 型識別子**SQL_C_TYPE_TIME [c]  
  
 **ODBC C typedef** SQL_TIME_STRUCT  
  
 **C 型**  
  
```  
struct tagTIME_STRUCT {  
   SQLUSMALLINT hour;  
   SQLUSMALLINT minute;  
   SQLUSMALLINT second;  
} TIME_STRUCT;[a]  
```  
  
 **C 型識別子**SQL_C_TYPE_TIMESTAMP [c]  
  
 **ODBC C typedef** SQL_TIMESTAMP_STRUCT  
  
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
  
 **ODBC C typedef** SQL_NUMERIC_STRUCT  
  
 **C 型**  
  
```  
struct tagSQL_NUMERIC_STRUCT {  
   SQLCHAR precision;  
   SQLSCHAR scale;  
   SQLCHAR sign[g];  
   SQLCHAR val[SQL_MAX_NUMERIC_LEN];[e], [f]   
} SQL_NUMERIC_STRUCT;  
```  
  
 **C 型識別子**SQL_C_GUID  
  
 **ODBC C typedef** SQLGUID  
  
 **C 型**  
  
```  
struct tagSQLGUID {  
   DWORD Data1;  
   WORD Data2;  
   WORD Data3;  
   BYTE Data4[8];  
} SQLGUID;[k]  
```  
  
 [a] 年、月、日、時、分、および datetime C データ型の 2 番目のフィールドの値は、グレゴリオ暦の制約に従っている必要があります。 (を参照してください[グレゴリオ暦の制約](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md)後の「します。)  
  
 [b] 小数フィールドの値は、10億分の 2 つ目と 0 ~ 999,999,999 (1 10億より小さい) の範囲の数です。 0.5 秒の小数フィールドの値の秒部分の 10,000 分の 1 の 500,000,000 は、たとえば、(1 ミリ秒) は、100万分の 1 秒あたりのための 1,000,000 (1 マイクロ秒) は 1,000 でありの 10億分の 1 秒 (1 ナノ秒) は 1 です。  
  
 [ODBC 2 の c]。*x*C の日付、時刻、および timestamp データ型は SQL_C_DATE、SQL_C_TIME、および SQL_C_TIMESTAMP です。  
  
 [d] ODBC 3 *.x* SQL_C_VARBOOKMARK、SQL_C_BOOKMARK いないアプリケーションを使用します。 ときに ODBC 3 *.x*アプリケーションが ODBC 2 *。x*ドライバー、ODBC 3 *.x*ドライバー マネージャーが SQL_C_VARBOOKMARK を SQL_C_BOOKMARK にマップされます。  
  
 [e] A 番号が格納されている、 *val*リトル エンディアン モード (、左端バイトが最下位バイト) でのスケーリングの整数として SQL_NUMERIC_STRUCT 構造体のフィールドです。 たとえば、4 の小数点以下桁数で数値 10.001 の底 10 は 100010 の整数にスケーリングされます。 これ 186AA 16 進形式であるため SQL_NUMERIC_STRUCT の値になります"AA 86 01 00 00.00"、SQL_MAX_NUMERIC_LEN によって定義されたバイト数で **#define**です。  
  
 詳細については**SQL_NUMERIC_STRUCT**を参照してください[HOWTO: SQL_NUMERIC_STRUCT で数値データの取得](retrieve-numeric-data-sql-numeric-struct-kb222831.md)です。  
  
 [SQL_C_NUMERIC データの f] で、有効桁数と小数点以下桁数のフィールドは、アプリケーションからの入力と出力をドライバーからアプリケーションが使われるを入力します。 ドライバーでは、数値の値を書き込む、SQL_NUMERIC_STRUCT に、独自のドライバー固有の既定の値として使用されます、*精度*フィールド、およびそのアプリケーション記述子 (の SQL_DESC_SCALE フィールドに、値が使用されます既定値は 0) の*スケール*フィールドです。 アプリケーションでは、アプリケーション記述子の SQL_DESC_PRECISION および SQL_DESC_SCALE フィールドを設定して、有効桁数と小数点以下桁数の独自の値を提供できます。  
  
 [g] 記号フィールドが 1 の場合は、正の値、負の場合は 0 です。  
  
 [h] _int64 を一部のコンパイラで提供されない可能性があります。  
  
 [ODBC 3 i] _SQL_C_BOOKMARK は廃止されて *.x*です。  
  
 [j] _SQL_C_SHORT、SQL_C_LONG、および SQL_C_TINYINT に置換された ODBC の符号付きと符号なしの型: SQL_C_SSHORT と SQL_C_USHORT、SQL_C_SLONG、SQL_C_ULONG、and SQL_C_STINYINT SQL_C_UTINYINT です。 ODBC 3 *.x* ODBC 2 で動作するドライバー *。x*アプリケーションは、そのため、呼び出されるときに、ドライバー マネージャーを使ってドライバーに渡します SQL_C_SHORT、SQL_C_LONG、および SQL_C_TINYINT、サポートする必要があります。  
  
 [k] SQL_C_GUID SQL_CHAR または SQL_WCHAR にのみ変換できます。  
  
 このセクションには、次のトピックが含まれています。  
  
-   [64 ビットの整数の構造](../../../odbc/reference/appendixes/64-bit-integer-structures.md)  
  
## <a name="see-also"></a>参照  
 [ODBC の C データ型](../../../odbc/reference/develop-app/c-data-types-in-odbc.md)
