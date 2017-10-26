---
title: "列のサイズ |Microsoft ドキュメント"
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
- data types [ODBC], column size
- size of data types [ODBC]
- SQL data types [ODBC], column characteristics
- column size of data types [ODBC]
ms.assetid: 541b83ab-b16d-4714-bcb2-3c3daa9a963b
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 13a50475602b7f71a7da33ebaaecb4c09eeaf534
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="column-size"></a>列のサイズ
数値データ型の列 (またはパラメーター) のサイズは、パラメーター、または列のデータ型またはデータの有効桁数によって使用される桁の数字の最大数として定義されます。 文字型の場合、これは、データの文字の長さバイナリ データ型の列のサイズは、データの長さ (バイト単位) として定義されます。 時刻、タイムスタンプ、およびすべての interval データ型の場合は、これはこのデータの文字表記の文字数です。 各簡潔な SQL データ型に対して定義されている列のサイズは、次の表に表示されます。  
  
|SQL 型の識別子|列のサイズ|  
|-------------------------|-----------------|  
|すべての文字の種類 [a] [b]。|列またはパラメーター (に記載されている SQL_DESC_LENGTH の記述子フィールド) の文字で定義されているまたは最大列サイズ。 たとえば、1 バイト文字の列の char (10) として定義されている列のサイズは 10 です。|  
|SQL_DECIMAL SQL_NUMERIC|定義されている桁数です。 たとえば、NUMERIC(10,3) として定義されている列の有効桁数には 10 です。|  
|SQL_BIT [c]|1|  
|SQL_TINYINT [c]|3|  
|SQL_SMALLINT [c]|5|  
|SQL_INTEGER [c]|10|  
|SQL_BIGINT [c]|19 (署名) の場合または 20 (符号なし) の場合|  
|SQL_REAL [c]|7|  
|[C] を使用できます。|15|  
|SQL_DOUBLE [c]|15|  
|すべてバイナリ型 [a] [b]。|未定義または最大長さ (バイト単位) の列またはパラメーター。 たとえば、binary (10) として定義されている列の長さは、10 です。|  
|SQL_TYPE_DATE [c]|10 (文字数、 *yyyy mm dd*形式)。|  
|SQL_TYPE_TIME [c]|8 (文字数、 *hh mm ss*形式)、または 9 + *s* (文字数、 *hh:mm:ss*[.fff.] 形式場所*の*秒の有効桁数です)。|  
|SQL_TYPE_TIMESTAMP|16 (文字数、 *- yyyy-mm-dd hh:mm*形式)<br /><br /> 19 (文字数、 *yyyy mm dd* *hh:mm:ss*形式)<br /><br /> または<br /><br /> 20 + *s* (文字数、 *- yyyy-mm-dd hh:mm:ss*[.fff.] 形式場所*s*秒の有効桁数です)。|  
|SQL_INTERVAL_SECOND|ここで*p*有効桁数を先頭間隔と*s*秒の有効桁数は、 *p* (場合*s*= 0) または*p* + *s*+1 (場合*s*> 0) です [。d]|  
|SQL_INTERVAL_DAY_TO_SECOND|ここで*p*有効桁数を先頭間隔と*s*秒の有効桁数、9 以降を*p* (場合*s*= 0) または 10 +*p*+ *s* (場合*s*> 0) です [。d]|  
|SQL_INTERVAL_HOUR_TO_SECOND|ここで*p*有効桁数を先頭間隔と*s*は秒の有効桁数、6 +*p* (場合*s*= 0) または 7 +*p* + *s* (場合*s*> 0) です [。d]|  
|SQL_INTERVAL_MINUTE_TO_SECOND|ここで*p*有効桁数を先頭間隔と*s*秒の有効桁数を 3 + が*p* (場合*s*= 0) または 4 +*p* + *s* (場合*s*> 0) です [。d]|  
|SQL_INTERVAL_YEAR SQL_INTERVAL_MONTH SQL_INTERVAL_DAY SQL_INTERVAL_HOUR SQL_INTERVAL_MINUTE|*p*ここで、 *p*有効桁数を先頭間隔です [。d]|  
|SQL_INTERVAL_YEAR_TO_MONTH SQL_INTERVAL_DAY_TO_HOUR|3 +*p*ここで、 *p*有効桁数を先頭間隔です [。d]|  
|SQL_INTERVAL_DAY_TO_MINUTE|6 +*p*ここで、 *p*有効桁数を先頭間隔です [。d]|  
|SQL_INTERVAL_HOUR_TO_MINUTE|3 +*p*ここで、 *p*有効桁数を先頭間隔です [。d]|  
|SQL_GUID|36 (文字数、 *aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee*形式)|  
  
 [a] の ODBC 1.0 アプリケーション通話**SQLSetParam** driver では、ODBC 2.0、および ODBC 2.0 アプリケーションの呼び出し元の**SQLBindParameter** driver では、ODBC 1.0、ときに\* *StrLen_or_IndPtr* SQL_LONGVARCHAR または SQL_LONGVARBINARY 型の場合は、SQL_DATA_AT_EXEC *ColumnSize*送信する、有効桁数いないこのテーブルで定義されているデータの長さの合計に設定する必要があります。  
  
 [b] 場合は、変数の型の列またはパラメーターの長さを判断できないのは、ドライバー、SQL_NO_TOTAL が返されます。  
  
 [c]、 *ColumnSize*の引数**SQLBindParameter**このデータ型は無視されます。  
  
 [d] interval データ型の列の長さに関する一般的な規則について[Interval データ型の長さ](../../../odbc/reference/appendixes/interval-data-type-length.md)、前述の「します。  
  
 列 (またはパラメーター) のサイズに対して返される値は、任意の 1 つの記述子フィールドの値に対応していません。 値は、次の表に示すように、SQL_DESC_PRECISION またはデータの種類に応じて、SQL_DESC_LENGTH フィールドのいずれかから取得できます。  
  
|SQL 型|対応する記述子フィールド<br /><br /> 列またはパラメーターのサイズ|  
|--------------|--------------------------------------------------------------------|  
|すべての文字とバイナリ型|LENGTH|  
|すべての数値型|PRECISION|  
|すべての日付時刻と間隔の種類|LENGTH|  
|SQL_BIT|LENGTH|

