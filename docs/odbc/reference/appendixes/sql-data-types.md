---
title: SQL データ型 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL data types [ODBC]
- SQL data types [ODBC], about SQL data types
- data types [ODBC], SQL data types
ms.assetid: 1b22f985-f5e4-4779-87eb-e43329a442b1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3cc91213533aa39f30be1bc838cc014c20e70884
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305006"
---
# <a name="sql-data-types"></a>SQL データ型
各 DBMS は、独自の SQL 型を定義します。 各 ODBC ドライバは、関連する DBMS によって定義されている SQL データ型のみを公開します。 ドライバーが DBMS SQL 型を ODBC 定義の SQL 型識別子にマップする方法、およびドライバーが DBMS SQL 型を独自のドライバー固有の SQL 型識別子にマップする方法に関する情報は、 **SQLGetTypeInfo**を呼び出して返されます。 ドライバーは、SQLCol 属性、SQLColumns **、SQLDescribeCol、SQLDescribeParam、SQL****プロシージャ列**、および**SQLSpecialColumns****SQLDescribeParam**の呼び出しを通じて列とパラメーターのデータ型を記述するときにも SQL データ型を返します。 **SQLColAttribute** **SQLColumns**  
  
> [!NOTE]  
>  SQL データ型は、実装記述子のSQL_DESC_CONCISE_TYPE、SQL_DESC_TYPE、およびSQL_DESC_DATETIME_INTERVAL_CODEフィールドに含まれています。 SQL データ・タイプの特性は、実装記述子のSQL_DESC_PRECISION、SQL_DESC_SCALE、SQL_DESC_LENGTH、およびSQL_DESC_OCTET_LENGTHのフィールドに含まれています。 詳細については、後[の「データ型識別子と記述子](../../../odbc/reference/appendixes/data-type-identifiers-and-descriptors.md)」を参照してください。  
  
 特定のドライバーとデータ ソースは、必ずしもこの付録で定義されているすべての SQL データ型をサポートしていません。 ドライバーの SQL データ型のサポートは、ドライバーが準拠する SQL-92 のレベルによって異なります。 ドライバーでサポートされている SQL-92 文法のレベルを決定するには、アプリケーションは、SQL_SQL_CONFORMANCE情報の種類を使用して**SQLGetInfo**を呼び出します。 さらに、特定のドライバーとデータ ソースは、追加のドライバー固有の SQL データ型をサポートする可能性があります。 ドライバーがサポートするデータ型を確認するには、アプリケーションは**SQLGetTypeInfo**を呼び出します。 ドライバー固有の SQL データ型については、ドライバーのドキュメントを参照してください。 特定のデータ ソースのデータ型については、そのデータ ソースのドキュメントを参照してください。  
  
> [!IMPORTANT]  
>  この付録全体の表はガイドラインにすぎず、通常使用される名前、範囲、および SQL データ型の制限を示しています。 特定のデータ ソースでは、一部のデータ型のみをサポートしている場合があり、サポートされているデータ型の特性は、一覧のものとは異なる場合があります。  
  
 次の表は、すべての SQL データ型の有効な SQL 型識別子を示しています。 この表には、SQL-92 の対応するデータ・タイプの名前と説明もリストされています (存在する場合)。  
  
|SQL タイプ識別子[1]|一般的な SQL データ<br /><br /> タイプ[2]|一般的なタイプの説明|  
|------------------------------|------------------------------------|------------------------------|  
|SQL_CHAR|CHAR(*n*)|固定文字列長*n*の文字ストリング。|  
|SQL_VARCHAR|ヴァルチャー(*n*)|最大文字列長*n*の可変長文字ストリング。|  
|SQL_LONGVARCHAR|LONG VARCHAR|可変長文字データ。 最大長はデータ ソースに依存します。[9]|  
|SQL_WCHAR|WCHAR(*n*)|固定文字列長*n*のユニコード文字ストリング|  
|SQL_WVARCHAR|ヴァルチャー(*n)*|最大文字列長*n*の Unicode 可変長文字ストリング|  
|SQL_WLONGVARCHAR|ロングヴァルチャー|Unicode 可変長文字データ。 最大長はデータ ソースに依存します。|  
|SQL_DECIMAL|10 進数(*p*,*s*)|符号付き、正確な数値、少なくとも*p*とスケール*の精度を*持つ数値。 (最大精度はドライバー定義です。(1 <= *p* <= 15;*s* <= *p*)。[4]|  
|SQL_NUMERIC|数値(*p*,*s*)|符号付き、正確な、精度*p*とスケール*s* (1 <= *p* <= 15;*s* <= *p*)。[4]|  
|SQL_SMALLINT|SMALLINT|精度 5 と位取り 0 の正確な数値 (符号付き: -32,768 <= *n* <= 32,767、符号なし: 0 <= *n* <= 65,535)[3]。|  
|SQL_INTEGER|INTEGER|精度 10 と位取り 0 の正確な数値 (符号付き: -2[31] <= *n* <= 2[31] - 1、符号なし: 0 <= *n* <= 2[32] - 1)[3]。|  
|SQL_REAL|real|符号付き、近似値、2 進精度 24 の数値 (ゼロまたは絶対値 10[-38] から 10[38])。|  
|SQL_FLOAT|フロート(*p*)|符号付き、近似値、数値の数値 (2 進精度が少なくとも*p)。* (最大精度はドライバー定義です。[5]|  
|SQL_DOUBLE|DOUBLE PRECISION|符号付き、近似値、2 進精度 53 の数値 (ゼロまたは絶対値 10[-308] から 10[308])。|  
|SQL_BIT|BIT|単一ビットのバイナリ データ。[8]|  
|SQL_TINYINT|TINYINT|精度 3 と位取り 0 の正確な数値 (符号付き: -128 <= *n* <= 127、符号なし: 0 <= *n* <= 255)[3]。|  
|SQL_BIGINT|bigint|精度 19 (符号付き) または 20 (符号なし) と位取り 0 (符号付き: -2[63] <= *n* <= 2[63] - 1、符号なし: 0 <= *n* <= 2[64] - 1[3],[9]。|  
|SQL_BINARY|バイナリー(*n*)|固定長*n*のバイナリ データ。[9]|  
|SQL_VARBINARY|VARBINARY(*n*)|最大長*n*の可変長バイナリー・データ。 最大値はユーザーによって設定されます。[9]|  
|SQL_LONGVARBINARY|ロング・ヴァーバイナリ|可変長バイナリ データ。 最大長はデータ ソースに依存します。[9]|  
|SQL_TYPE_DATE[6]|DATE|グレゴリオ暦の規則に従って、年、月、および日のフィールド。 ([グレゴリオ暦の制約](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md)については、この付録の「 」を参照してください)。|  
|SQL_TYPE_TIME[6]|時間(*p)*|時間 00 ~ 23 の有効な値、00 ~ 59 の分の有効値、および 00 ~ 61 の秒の有効値を持つ時間、分、秒の各フィールド。 精度*p は*秒精度を示します。|  
|SQL_TYPE_TIMESTAMP[6]|タイムスタンプ(*p*)|年、月、日、時、分、および 2 番目のフィールドで、DATE および TIME データ・タイプに対して定義された有効な値。|  
|SQL_TYPE_UTCDATETIME|UTC 日付時刻|年、月、日、時、分、秒、utc 時間、および utc 分のフィールド。 utchour と utcminute フィールドには、1/10 マイクロ秒の精度があります。|  
|SQL_TYPE_UTCTIME|UTC時刻|時間、分、秒、utchour、および utcminute フィールド。 utchour と utcminute フィールドには、1/10 マイクロ秒の精度があります。|  
|SQL_INTERVAL_MONTH[7]|間隔月(*p)*|2 つの日付間の月数。*p*は、間隔の先行精度です。|  
|SQL_INTERVAL_YEAR[7]|区間年(*p)*|2 つの日付間の年数。*p*は、間隔の先行精度です。|  
|SQL_INTERVAL_YEAR_TO_MONTH[7]|間隔年 *(p)* から月|2 つの日付間の年と月の数。*p*は、間隔の先行精度です。|  
|SQL_INTERVAL_DAY[7]|間隔日(*p*)|2 つの日付間の日数。*p*は、間隔の先行精度です。|  
|SQL_INTERVAL_HOUR[7]|間隔時間(*p*)|2 つの日付/時刻の間の時間数。*p*は、間隔の先行精度です。|  
|SQL_INTERVAL_MINUTE[7]|間隔分(*p*)|2 つの日付/時刻の間の分数。*p*は、間隔の先行精度です。|  
|SQL_INTERVAL_SECOND[7]|間隔秒(*p*,*q)*|2 つの日付/時刻の間の秒数。*p*は、インターバルの先行精度 *、q*は間隔秒精度です。|  
|SQL_INTERVAL_DAY_TO_HOUR[7]|間隔日 *(p)* から時間|2 つの日付/時刻の間の日数/時間数。*p*は、間隔の先行精度です。|  
|SQL_INTERVAL_DAY_TO_MINUTE[7]|間隔日 *(p)~* 分|2 つの日付/時刻の間の日数/時間/分数。*p*は、間隔の先行精度です。|  
|SQL_INTERVAL_DAY_TO_SECOND[7]|間隔日(*p*) から秒まで(*q*)|2 つの日付/時刻の間の日数/時間/分/秒数。*p*は、インターバルの先行精度 *、q*は間隔秒精度です。|  
|SQL_INTERVAL_HOUR_TO_MINUTE[7]|間隔時間 *(p)~* 分|2 つの日付/時刻の間の時間/分数。*p*は、間隔の先行精度です。|  
|SQL_INTERVAL_HOUR_TO_SECOND[7]|間隔時間 *(p)* から秒 *(q)*|2 つの日付/時刻の間の時間/分/秒数。*p*は、インターバルの先行精度 *、q*は間隔秒精度です。|  
|SQL_INTERVAL_MINUTE_TO_SECOND[7]|間隔分(*p*) から秒まで(*q*)|2 つの日付/時刻の間の分/秒の数。*p*は、インターバルの先行精度 *、q*は間隔秒精度です。|  
|SQL_GUID|GUID|固定長 GUID。|  
  
 [1] これは **、SQLGetTypeInfo**の呼び出しによってDATA_TYPE列に返される値です。  
  
 [2] これは **、SQLGetTypeInfo**の呼び出しによって名前列と CREATE PARAMS 列に返される値です。 NAME 列は CHAR-などの指定を戻し、CREATE PARAMS 列は精度、位取り、長さなどの作成パラメーターのコンマ区切りリストを戻します。  
  
 [3] アプリケーションは **、SQLGetTypeInfo**または**SQLColAttribute**を使用して、特定のデータ型または結果セット内の特定の列が符号なしかどうかを判断します。  
  
 [4] SQL_DECIMALデータ型とSQL_NUMERICデータ型は精度のみが異なります。 DECIMAL(*p*,*s*) の精度は、実装で定義された 10 進精度で *、p*以上であるのに対し、NUMERIC(*p*,*s*) の精度は*p*と正確に等しくなります。  
  
 [5] 実装によっては、SQL_FLOATの精度は 24 または 53 のいずれかになります: 24 の場合、SQL_FLOATデータ型はSQL_REALと同じです。53 の場合、SQL_FLOATデータ型はSQL_DOUBLEと同じになります。  
  
 ODBC *3.x*では、SQL の日付、時刻、およびタイムスタンプの各データ型が、それぞれSQL_TYPE_DATE、SQL_TYPE_TIME、およびSQL_TYPE_TIMESTAMP。ODBC *2.x*では、データ型はSQL_DATE、SQL_TIME、およびSQL_TIMESTAMP。  
  
 間隔 SQL データ型の詳細については、この付録の「[間隔データ型」](../../../odbc/reference/appendixes/interval-data-types.md)セクションを参照してください。  
  
 SQL_BITデータ型の特性は、SQL-92 の BIT 型とは異なります。  
  
 [9] このデータ型には、SQL-92 に対応するデータ型がありません。  
  
 このセクションでは、次の例を示します。  
  
-   [SQLGetTypeInfo 結果セットの例](../../../odbc/reference/appendixes/example-sqlgettypeinfo-result-set.md)
