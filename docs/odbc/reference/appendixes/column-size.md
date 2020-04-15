---
title: 列サイズ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], column size
- size of data types [ODBC]
- SQL data types [ODBC], column characteristics
- column size of data types [ODBC]
ms.assetid: 541b83ab-b16d-4714-bcb2-3c3daa9a963b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 07b6151c723cb5e05189791100338e9e343c28aa
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306583"
---
# <a name="column-size"></a>列サイズ
数値データ型の列 (またはパラメーター) サイズは、列またはパラメーターのデータ型で使用される最大桁数、またはデータの精度として定義されます。 文字型の場合、これはデータの文字数の長さです。バイナリ データ型の場合、列サイズはデータの長さ (バイト単位) として定義されます。 時刻、タイム・スタンプ、およびすべての間隔データ・タイプの場合、これはこのデータの文字表現の文字数です。 次の表に、簡潔な SQL データ型ごとに定義されている列サイズを示します。  
  
|SQL タイプ識別子|列サイズ|  
|-------------------------|-----------------|  
|すべての文字タイプ[a],[b]|列またはパラメーターの定義済みまたは最大の列サイズ (SQL_DESC_LENGTH記述子フィールドに含まれる) 。 たとえば、CHAR(10) として定義された 1 バイト文字列の列サイズは 10 です。|  
|SQL_DECIMAL SQL_NUMERIC|定義された桁数。 例えば、NUMERIC(10,3) として定義された列の精度は 10 です。|  
|SQL_BIT[c]|1|  
|SQL_TINYINT[c]|3|  
|SQL_SMALLINT[c]|5|  
|SQL_INTEGER[c]|10|  
|SQL_BIGINT[c]|19 (署名されている場合) または 20 (署名されていない場合)|  
|SQL_REAL[c]|7|  
|SQL_FLOAT[c]|15|  
|SQL_DOUBLE[c]|15|  
|すべてのバイナリ型 [a],[b]|列またはパラメーターの定義された長さまたは最大長 (バイト単位)。 たとえば、BINARY(10) として定義された列の長さは 10 です。|  
|SQL_TYPE_DATE[c]|10 *(yyyy-mm-dd*形式の文字数)。|  
|SQL_TYPE_TIME[c]|8 *(hh-mm-ss*形式の文字数)、または 9 + *s* *(hh:mm:ss*[.fff..] 形式の文字数 *、s*は秒精度)。|  
|SQL_TYPE_TIMESTAMP|16 *(yyyy-mm-dd hh:mm*形式の文字数)<br /><br /> 19 *(yyyy-mm-dd* *hh:mm:ss*形式の文字数)<br /><br /> or<br /><br /> 20 + *s* *(yyyy-mm-dd hh:mm:ss*[.fff..] 形式の文字数 *(s*は秒精度)。|  
|SQL_INTERVAL_SECOND|p *p*は、インターバルの先行精度 *、s*は秒精度 *、p* *(s*=0 の場合) または*p*+*s*+1 *(s*が 0 の場合>) です。[d]|  
|SQL_INTERVAL_DAY_TO_SECOND|*p*は間隔を先行する精度 *、s*は秒精度、9+*p* *(s*=0 の場合) または 10+*p*+*s* *(s*が 0 の場合>) です。[d]|  
|SQL_INTERVAL_HOUR_TO_SECOND|*p*は間隔を先行する精度 *、s*は秒精度、6+*p* *(s*=0 の場合) または 7+*p*+*s* *(s*が>0 の場合) です。[d]|  
|SQL_INTERVAL_MINUTE_TO_SECOND|*p*は間隔を先行する精度 *、s*は秒精度、3+*p* *(s*=0 の場合) または 4+*p*+*s* *(s*が 0 の場合>) です。[d]|  
|SQL_INTERVAL_HOURSQL_INTERVAL_MINUTESQL_INTERVAL_MONTH SQL_INTERVAL_DAYSQL_INTERVAL_MONTHSQL_INTERVAL_YEAR|*p* *、p*は、間隔の先行精度です。[d]|  
|SQL_INTERVAL_YEAR_TO_MONTH SQL_INTERVAL_DAY_TO_HOUR|3 +*p* *、p*は間隔をリードする精度です。[d]|  
|SQL_INTERVAL_DAY_TO_MINUTE|6+*p* *、p*は間隔をリードする精度です。[d]|  
|SQL_INTERVAL_HOUR_TO_MINUTE|3 +*p* *、p*は間隔をリードする精度です。[d]|  
|SQL_GUID|36 *(aaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeee*の文字数)|  
  
 [a] ODBC 2.0 ドライバで**SQLSetParam**を呼び出す ODBC 1.0 アプリケーションの場合、ODBC 1.0 ドライバで**SQLBindParameter**を呼び出す ODBC 2.0 アプリケーションの場合\**、StrLen_or_IndPtr*がSQL_LONGVARCHARまたはSQL_LONGVARBINARY型に対してSQL_DATA_AT_EXECされる場合 *、ColumnSize は*送信されるデータの合計長に設定する必要があります。  
  
 [b] ドライバーが可変型の列またはパラメーターの長さを決定できない場合、SQL_NO_TOTAL返します。  
  
 [c] このデータ型では **、SQLBindParameter**の*ColumnSize*引数は無視されます。  
  
 [d] 間隔データ型の列の長さに関する一般的な規則については、この付録の前半の「[間隔データ型の長さ](../../../odbc/reference/appendixes/interval-data-type-length.md)」を参照してください。  
  
 列 (またはパラメーター) のサイズに対して戻される値が、1 つの記述子フィールドの値に対応していません。 値は、次の表に示すように、データの種類に応じて、SQL_DESC_PRECISIONまたはSQL_DESC_LENGTH フィールドのいずれかから取得できます。  
  
|SQL 型|対応する記述子フィールド<br /><br /> 列またはパラメーターのサイズ|  
|--------------|--------------------------------------------------------------------|  
|すべての文字とバイナリ型|LENGTH|  
|すべての数値型|PRECISION|  
|すべての日時と間隔の種類|LENGTH|  
|SQL_BIT|LENGTH|
