---
title: "日付、時刻、およびタイムスタンプのリテラル |Microsoft ドキュメント"
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
- escape sequences [ODBC], literals
ms.assetid: 2b42a52a-6353-494c-a179-3a7533cd729f
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2af859a38f288507ad87564cfbbfffa2b8f6ecf8
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="date-time-and-timestamp-literals"></a>日付、時刻、およびタイムスタンプのリテラル
日付、時刻、およびタイムスタンプのリテラルのエスケープ シーケンスは、します。  
  
 **{***-型* **'** *値* **'}**   
  
 ここで*リテラル型*次の表に示す、値のいずれか。  
  
|*リテラル型*|意味|書式設定*値*|  
|---------------------|-------------|-----------------------|  
|**d**|日付|*yyyy*-*mm*-*dd*|  
|**t**|時間 *|*hh*:*mm*:*ss*[1]|  
|**ts**|Timestamp|*yyyy*-*mm*-*dd* *hh*:*mm*:*ss*[.*f.*] [1]|  
  
 [時間またはタイムスタンプ間隔 (秒) コンポーネントを含むリテラルの中で小数点の右側にある数字の 1] の番号は SQL_DESC_PRECISION 記述子フィールドに含まれる秒の有効桁数に依存します。 (詳細については、次を参照してください[SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)。)。  
  
 日付、時刻、およびタイムスタンプ エスケープ シーケンスの詳細については、次を参照してください。[日付、時刻、およびタイムスタンプ エスケープ シーケンス](../../../odbc/reference/appendixes/date-time-and-timestamp-escape-sequences.md)付録 c: SQL の文法でします。  
  
 たとえば、次の SQL ステートメントの両方の Orders テーブルの販売注文 1023 の開いている日付を更新します。 最初のステートメントでは、エスケープ シーケンスの構文を使用します。 2 番目のステートメントでは、日付列の Oracle Rdb ネイティブ構文を使用して、相互運用可能ではありません。  
  
```  
UPDATE Orders SET OpenDate={d '1995-01-15'} WHERE OrderID=1023  
UPDATE Orders SET OpenDate='15-Jan-1995' WHERE OrderID=1023  
```  
  
 日付、時刻、またはタイムスタンプのリテラルのエスケープ シーケンスは、日付、時刻、またはタイムスタンプ パラメーターにバインドされている文字変数にも配置できます。 たとえば、次のコードは文字変数にバインドされている日付のパラメーターを使用して、更新、Orders テーブルの販売注文 1023 の開いている日付。  
  
```  
SQLCHAR      OpenDate[56]; // The size of a date literal is 55.  
SQLINTEGER   OpenDateLenOrInd = SQL_NTS;  
  
// Bind the parameter.  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_TYPE_DATE, 0, 0,  
                  OpenDate, sizeof(OpenDate), &OpenDateLenOrInd);  
  
// Place the date in the OpenDate variable. In addition to the escape  
// sequence shown, it would also be possible to use either of the  
// strings "{d '1995-01-15'}" and "15-Jan-1995", although the latter  
// is data source-specific.  
strcpy_s( (char*) OpenDate, _countof(OpenDate), "{d '1995-01-15'}");  
  
// Execute the statement.  
SQLExecDirect(hstmt, "UPDATE Orders SET OpenDate=? WHERE OrderID = 1023", SQL_NTS);  
```  
  
 ただし、パラメーターにバインドして、日付構造体に直接効率的です。  
  
```  
SQL_DATE_STRUCT   OpenDate;  
SQLINTEGER        OpenDateInd = 0;  
  
// Bind the parameter.  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_TYPE_DATE, SQL_TYPE_DATE, 0, 0,  
                  &OpenDate, 0, &OpenDateLen);  
  
// Place the date in the dsOpenDate structure.  
OpenDate.year = 1995;  
OpenDate.month = 1;  
OpenDate.day = 15;  
  
// Execute the statement.  
SQLExecDirect(hstmt, "UPDATE Employee SET OpenDate=? WHERE OrderID = 1023", SQL_NTS);  
```  
  
 アプリケーションが呼び出す、ドライバーが日付、時刻、またはタイムスタンプのリテラルの ODBC エスケープ シーケンスをサポートするかどうかを確認、 **SQLGetTypeInfo**です。 データ ソースは、日付、時刻、またはタイムスタンプのデータ型をサポートする場合、対応するエスケープ シーケンスもサポートする必要があります。  
  
 データ ソースには、ANSI sql-92 仕様で定義されているとは異なります ODBC エスケープ シーケンスは、日付、時刻、またはタイムスタンプのリテラルの日付時刻リテラルもサポートできます。 データ ソースが ANSI リテラルをサポートするかどうかを決定するには、アプリケーションが呼び出す**SQLGetInfo** SQL_ANSI_SQL_DATETIME_LITERALS オプションを使用します。  
  
 アプリケーションが呼び出す、ドライバーが間隔のリテラルの ODBC エスケープ シーケンスをサポートするかどうかを確認、 **SQLGetTypeInfo**です。 データ ソースは、datetime interval データ型をサポートする場合、対応するエスケープ シーケンスもサポートする必要があります。  
  
 データ ソースには、ANSI sql-92 仕様で定義されている datetime 間隔リテラルの ODBC エスケープ シーケンスは、異なる日付時刻リテラルもサポートできます。 データ ソースが ANSI リテラルをサポートするかどうかを決定するには、アプリケーションが呼び出す**SQLGetInfo** SQL_ANSI_SQL_DATETIME_LITERALS オプションを使用します。

