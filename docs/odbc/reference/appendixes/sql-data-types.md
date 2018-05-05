---
title: SQL データ型 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL data types [ODBC]
- SQL data types [ODBC], about SQL data types
- data types [ODBC], SQL data types
ms.assetid: 1b22f985-f5e4-4779-87eb-e43329a442b1
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ba122ccbc873603b434a8541fe44aee10a5104e0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sql-data-types"></a>SQL データ型
各 DBMS では、独自の SQL 型を定義します。 各 ODBC ドライバーでは、関連付けられた DBMS 定義 SQL データ型のみを公開します。 ODBC で定義された SQL 型識別子をドライバーがどのようにマップについて DBMS SQL 型し、を呼び出すことによって、ドライバーがドライバー固有の SQL 型識別子には独自に DBMS SQL 型をマップする方法が返されます**SQLGetTypeInfo**です。 ドライバーは、列とを呼び出すことでパラメーターのデータ型を記述するときにも、SQL データ型を返します**SQLColAttribute**、 **SQLColumns**、 **SQLDescribeCol**、**SQLDescribeParam**、 **SQLProcedureColumns**、および**SQLSpecialColumns**です。  
  
> [!NOTE]  
>  SQL データ型は、実装記述子の SQL_DESC_ CONCISE_TYPE、SQL_DESC_TYPE、および SQL_DESC_DATETIME_INTERVAL_CODE フィールドに格納されます。 SQL データ型の特性は、実装記述子の SQL_DESC_PRECISION、SQL_DESC_SCALE、SQL_DESC_LENGTH、および SQL_DESC_OCTET_LENGTH フィールドに格納されます。 詳細については、次を参照してください。[のデータ型識別子と記述子](../../../odbc/reference/appendixes/data-type-identifiers-and-descriptors.md)後の「します。  
  
 特定のドライバーとデータ ソースは、必ずしもこの付録で定義されているすべての SQL データ型をサポートできません。 SQL データ型に対するドライバーのサポートは、ドライバーに準拠している SQL 92 のレベルによって異なります。 ドライバーでサポートされている SQL 92 文法のレベルを決定するには、アプリケーションが呼び出す**SQLGetInfo** SQL_SQL_CONFORMANCE 情報の種類とします。 さらに、特定のドライバーとデータ ソースは、追加のドライバー固有の SQL データ型をサポートする場合があります。 サポートするデータ型、ドライバーを決定する、アプリケーションが呼び出す**SQLGetTypeInfo**です。 ドライバー固有の SQL データ型については、ドライバーのドキュメントを参照してください。 特定のデータ ソース内のデータ型については、そのデータ ソースのマニュアルを参照してください。  
  
> [!IMPORTANT]  
>  この付録の内容全体でのテーブルは、唯一のガイドラインと通常使用される表示名、範囲、および SQL データ型の制限は。 指定したデータ ソースは、表示されているデータ型の一部のみをサポート可能性があり、」の一覧から、サポートされているデータ型の特性が異なることができます。  
  
 次の表は、すべての SQL データ型の有効な SQL 型識別子を一覧表示します。 (存在する場合に、名前と説明、sql-92 から対応するデータ型の表も示します。  
  
|SQL 型識別子 [1]|一般的な SQL データ<br /><br /> [2] の種類|一般的な種類の説明|  
|------------------------------|------------------------------------|------------------------------|  
|SQL_CHAR|CHAR (*n*)|文字の固定文字列の長さの文字列*n*です。|  
|SQL_VARCHAR|VARCHAR (*n*)|文字列の最大長を持つ可変長文字の文字列*n*です。|  
|SQL_LONGVARCHAR|LONG VARCHAR|可変長文字データ。 最大長は、データ ソースに依存します。[9]|  
|SQL_WCHAR|WCHAR (*n*)|固定文字列長の Unicode 文字の文字列*n*|  
|SQL_WVARCHAR|VARWCHAR (*n*)|文字列の最大長を持つ可変長文字の文字列を Unicode *n*|  
|SQL_WLONGVARCHAR|LONGWVARCHAR|Unicode の可変長の文字データです。 最大長はデータ ソースに依存しますです。|  
|SQL_DECIMAL|10 進数 (*p*、*s*)|符号付き、正確な数値の有効桁数を持つには、少なくとも*p*有効桁数と小数点*s。* (最大有効桁数はドライバーで定義されます。)(1 < = *p* < = 15 です。*s* <= *p*) です [。4]|  
|SQL_NUMERIC|数値 (*p*、*s*)|符号付き、正確な数値有効桁数を持つ*p*有効桁数と小数点*s* (1 < = *p* < = 15 です。*s* <= *p*) です [。4]|  
|SQL_SMALLINT|SMALLINT|固定精度が 5 で数値および 0 をスケール (署名: –32,768 < = *n* < 符号なし、32,767 を =: 0 < = *n* < 65,535 を =) [3]。|  
_INTEGER|INTEGER|固定精度が 10 で数値および 0 のスケール (署名: – 2 [31] < = *n* < = 2 [31] – 1、符号なし: 0 < = *n* < = 2 [32] – 1) [3]。|  
|SQL_REAL|REAL|署名済み、バイナリ有効桁数 24 を持つ概数の数値の値 (0 または絶対値 10 [–38] 10[38]) にします。|  
|SQL_FLOAT|FLOAT (*p*)|署名済み、バイナリ有効桁数の概数の数値の値には、少なくとも*p*です。 (最大有効桁数はドライバーで定義されます。)[5]|  
|SQL_DOUBLE|DOUBLE PRECISION|署名済み、バイナリ有効桁数が 53 概数の数値の値 (0 または絶対値 10 [– 308] 10[308]) にします。|  
|SQL_BIT|BIT|1 つのビットのバイナリ データ。[8]|  
|SQL_TINYINT|TINYINT|固定精度が 3 で数値および 0 のスケール (署名: – 128 < = *n* < = 127 文字で、符号なし: 0 < = *n* < = 255) [3]。|  
_BIGINT|bigint|正確な数値有効桁数 19 (署名) の場合または 20 (符号なし) の場合、0 を拡張 (署名: – 2 [63] < = *n* < = 2 [63] – の符号なし、1: 0 < = *n* < = 2 [64] – 1) [3]、[9] です。|  
|SQL_BINARY|バイナリ (*n*)|固定長のバイナリ データ*n*[。9]|  
|SQL_VARBINARY|VARBINARY (*n*)|最大長の可変長のバイナリ データ*n*です。 最大値は、ユーザーによって設定されます。[9]|  
|SQL_LONGVARBINARY|長い VARBINARY|可変長バイナリ データ。 最大長は、データ ソースに依存します。[9]|  
|SQL_TYPE_DATE [6]|[DATE]|年、月、および日のフィールド、グレゴリオ暦の規則に準拠します。 (を参照してください[グレゴリオ暦の制約](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md)、後の「します。)|  
|SQL_TYPE_TIME [6]|時間 (*p*)|時間、分、および 00 ~ 59 の分を 00 ~ 23 の有効な値の時間の有効な値と 00 に 61 の秒の有効な値で、2 番目のフィールドです。 有効桁数*p*秒の有効桁数を示します。|  
|SQL_TYPE_TIMESTAMP [6]|タイムスタンプ (*p*)|年、月、日、時、分、および日付と時刻のデータ型に対して定義されていると有効な値を持つ、2 番目のフィールドです。|  
_TYPE_UTCDATETIME|UTCDATETIME のフィールド|年、月、日、時、分、秒、utchour、および utcminute フィールドです。 Utchour と utcminute フィールドでは、1/10 マイクロ秒の有効桁数があります。|  
|SQL_TYPE_UTCTIME|UTCTIME|時間、分、秒、utchour、および utcminute フィールドです。 Utchour と utcminute フィールドは、1/10 マイクロ秒の有効桁数を含める.|  
|SQL_INTERVAL_MONTH [7]|INTERVAL MONTH (*p*)|2 つの日付の月の数*p*有効桁数を先頭間隔です。|  
|SQL_INTERVAL_YEAR [7]|INTERVAL YEAR (*p*)|2 つの日付の年の数*p*有効桁数を先頭間隔です。|  
|SQL_INTERVAL_YEAR_TO_MONTH [7]|INTERVAL YEAR (*p*) の月に|年と 2 つの日付の月の数*p*有効桁数を先頭間隔です。|  
|SQL_INTERVAL_DAY [7]|間隔の日 (*p*)|2 つの日付間の日数*p*有効桁数を先頭間隔です。|  
|SQL_INTERVAL_HOUR [7]|間隔の時間 (*p*)|2 つの間の時間数の日付/時刻です。*p*有効桁数を先頭間隔です。|  
|SQL_INTERVAL_MINUTE [7]|間隔分 (*p*)|2 つの間隔を分単位の数の日付/時刻です。*p*有効桁数を先頭間隔です。|  
|SQL_INTERVAL_SECOND [7]|間隔 2 番目 (*p*、*q*)|2 つの間の秒数日付/時刻です。*p*有効桁数を先頭間隔と*q*間隔 (秒) の有効桁数です。|  
_INTERVAL_DAY_TO_HOUR [7]|間隔の日 (*p*) 1 時間|2 つの間の日数/時間数の日付/時刻です。*p*有効桁数を先頭間隔です。|  
|SQL_INTERVAL_DAY_TO_MINUTE [7]|間隔の日 (*p*) 分|日数/時間/間隔 (分) 2 つの日付/時刻です。*p*有効桁数を先頭間隔です。|  
|SQL_INTERVAL_DAY_TO_SECOND [7]|間隔の日 (*p*) 2 番目 (*q*)|日数/時間/分/秒数 2 つの日付/時刻です。*p*有効桁数を先頭間隔と*q*間隔 (秒) の有効桁数です。|  
|SQL_INTERVAL_HOUR_TO_MINUTE [7]|間隔の時間 (*p*) 分|2 つの分単位の時間数日付/時刻です。*p*有効桁数を先頭間隔です。|  
|SQL_INTERVAL_HOUR_TO_SECOND [7]|間隔の時間 (*p*) 2 番目 (*q*)|2 つの時間、分/秒の数の日付/時刻です。*p*有効桁数を先頭間隔と*q*間隔 (秒) の有効桁数です。|  
_INTERVAL_MINUTE_TO_SECOND [7]|INTERVAL MINUTE (*p*) 2 番目 (*q*)|2 つ分/秒数日付/時刻です。*p*有効桁数を先頭間隔と*q*間隔 (秒) の有効桁数です。|  
|SQL_GUID|GUID|固定長の GUID。|  
  
 [呼び出しでは、DATA_TYPE 列に返される値は 1] この**SQLGetTypeInfo**です。  
  
 [2] これは、名前とパラメーターの作成の列への呼び出しによって返される値**SQLGetTypeInfo**です。 [名前] 列での表記を返します — たとえば、CHAR — 作成 PARAMS 列は、作成パラメーターの有効桁数、小数点以下桁数、長さなどのコンマ区切りの一覧を返しますがします。  
  
 [3]、アプリケーションを使用して**SQLGetTypeInfo**または**SQLColAttribute**かどうかを特定のデータ型または特定の列を結果セットにない署名します。  
  
 [4] SQL_DECIMAL と SQL_NUMERIC のデータ型の違いのみの有効桁数です。 10 進数の有効桁数 (*p*、*s*) は、実装で定義された小数点以下有効桁数である以下*p*であるのに対し、数値の有効桁数 (*p*、*s*) とまったく同じ*p*です。  
  
 [24 または 53 5]、実装に繰り返し使用できますの有効桁数ができますは、使用できますのデータ型が、SQL_REAL; と同じになる場合 24 は、。53 の場合、使用できますのデータ型は SQL_DOUBLE と同じです。  
  
 [6] ODBC 3 *.x*、SQL の日付、時刻、および timestamp データ型は SQL_TYPE_DATE、SQL_TYPE_TIME、および SQL_TYPE_TIMESTAMP、ODBC 2 にそれぞれ;.*x*データ型は、SQL_DATE、SQL_TIME、および SQL_TIMESTAMP です。  
  
 [7] interval SQL データ型の詳細についてを参照してください、 [Interval データ型](../../../odbc/reference/appendixes/interval-data-types.md)この付録の後半の「します。  
  
 [8] で、SQL_BIT データ型は BIT 型とは異なる特性、sql-92 でします。  
  
 [SQL 92 では、9] このデータ型の対応するデータ型はありません。  
  
 このセクションでは、次の例を示します。  
  
-   [SQLGetTypeInfo 結果セットの例](../../../odbc/reference/appendixes/example-sqlgettypeinfo-result-set.md)
