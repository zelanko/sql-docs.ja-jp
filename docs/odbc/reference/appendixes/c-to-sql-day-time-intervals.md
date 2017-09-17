---
title: "C から SQL へ: 1 日間隔で |Microsoft ドキュメント"
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
- day-time intervals [ODBC]
- data conversions from C to SQL types [ODBC], day-time intervals
- converting data from c to SQL types [ODBC], day-time intervals
- intervals [ODBC], converting
ms.assetid: f9ee1ddb-dec7-4f78-b6e2-5ba34e7d6f59
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 61c271a9de10bbc43db116f576b0c34589f899f3
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="c-to-sql-day-time-intervals"></a>C から SQL へ: 1 日間隔で
1 日の時間間隔の ODBC C データ型の識別子は次のとおりです。  
  
 SQL_C_INTERVAL_DAY  
  
 SQL_C_INTERVAL_HOUR  
  
 SQL_C_INTERVAL_MINUTE  
  
 SQL_C_INTERVAL_SECOND  
  
 SQL_C_INTERVAL_DAY_TO_HOUR  
  
 SQL_C_INTERVAL_DAY_TO_MINUTE  
  
 SQL_C_INTERVAL_DAY_TO_SECOND  
  
 SQL_C_INTERVAL_HOUR_TO_MINUTE  
  
 SQL_C_INTERVAL_HOUR_TO_SECOND  
  
 SQL_C_INTERVAL_MINUTE_TO_SECOND  
  
 次の表は、ODBC SQL データ型の C データの間隔を変換することがありますを示します。 列とテーブルの用語の詳細については、次を参照してください。[に変換するデータを C から SQL データ型を](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)です。  
  
|SQL 型の識別子|テスト|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR [a]<br /><br /> [A] SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR [a]|列のバイト長 > 文字バイトの長さを =<br /><br /> 列のバイト長 < 文字バイト長 [a]<br /><br /> データ値はリテラルの有効な間隔ではありません。|n/a<br /><br /> 22001<br /><br /> 22015|  
|[A] の SQL_WCHAR<br /><br /> SQL_WVARCHAR [a]<br /><br /> [A] SQL_WLONGVARCHAR|列の文字の長さ > データの文字の長さを =<br /><br /> 列の文字の長さ < [a] のデータの長さを文字<br /><br /> データ値はリテラルの有効な間隔ではありません。|n/a<br /><br /> 22001<br /><br /> 22015|  
|SQL_TINYINT [b]<br /><br /> SQL_SMALLINT [b] SQL_INTEGER [b]<br /><br /> SQL_BIGINT [b] SQL_NUMERIC [b]<br /><br /> SQL_DECIMAL [b]|単一フィールド間隔の変換は、全体の桁数の切り捨てを実行できませんでした。<br /><br /> 変換の結果が全体の桁数の切り捨て|n/a<br /><br /> 22003|  
|SQL_INTERVAL_DAY<br /><br /> SQL_INTERVAL_HOUR<br /><br /> SQL_INTERVAL_MINUTE<br /><br /> SQL_INTERVAL_SECOND<br /><br /> SQL_INTERVAL_DAY_TO_HOUR<br /><br /> SQL_INTERVAL_DAY_TO_MINUTE<br /><br /> SQL_INTERVAL_DAY_TO_SECOND<br /><br /> SQL_INTERVAL_HOUR_TO_MINUTE<br /><br /> SQL_INTERVAL_HOUR_TO_SECOND<br /><br /> SQL_INTERVAL_MINUTE_TO_SECOND|データ値がすべてのフィールドが切り詰めなしに変換されました<br /><br /> 変換中にデータ値の 1 つまたは複数のフィールドが切り詰められました|n/a<br /><br /> 22015|  
  
 [a] のすべての C interval データ型は、文字データ型に変換できます。  
  
 [b] 間隔構造体の型のフィールドが、間隔が 1 つのフィールド (SQL_DAY、SQL_HOUR、SQL_MINUTE、または SQL_SECOND) になるようの場合、間隔 C 型は、正確な numeric (SQL_TINYINT、SQL_SMALLINT、SQL_INTEGER、SQL_BIGINT に変換できます。、SQL_DECIMAL、または SQL_NUMERIC)。  
  
 C の間隔の種類の既定の変換は、対応する日の期間、SQL 型にです。  
  
 ドライバーは、間隔 C データ型からデータを変換するときに長さ/インジケーター値を無視し、データ バッファーのサイズが間隔 C データ型のサイズであると見なされます。 長さ/インジケーター値に渡されます、 *StrLen_or_Ind*引数**SQLPutData**とで指定したバッファー内の*StrLen_or_IndPtr* で引数**SQLBindParameter**です。 データ バッファーを指定した、 *DataPtr*引数**SQLPutData**と*ParameterValuePtr*引数**SQLBindParameter**.  
  
 次の例では、データベース列に SQL_INTERVAL_STRUCT 構造体に格納されている間隔 C データを送信する方法を示します。 間隔の構造体には、DAY_TO_SECOND 間隔; が含まれています。SQL_INTERVAL_DAY_TO_MINUTE の種類のデータベース列に保存されます。  
  
```  
SQL_INTERVAL_STRUCT is;  
SQLINTEGER cbValue;  
  
// Initialize the interval struct to contain the DAY_TO_SECOND  
// interval "154 days, 22 hours, 44 minutes, and 10 seconds"  
is.intval.day_second.day      = 154;  
is.intval.day_second.hour     = 22;  
is.intval.day_second.minute   = 44;  
is.intval.day_second.second   = 10;  
is.interval_sign              = SQL_FALSE;  
  
// Bind the dynamic parameter  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_INTERVAL_DAY_TO_SECOND,  
                  SQL_INTERVAL_DAY_TO_MINUTE, 0, 0, &is,  
                  sizeof(SQL_INTERVAL_STRUCT), &cbValue);  
  
// Execute an insert statement; "interval_column" is a column  
// whose data type is SQL_INTERVAL_DAY_TO_MINUTE.  
SQLExecDirect(hstmt,"INSERT INTO table(interval_column) VALUES (?)",SQL_NTS);  
```
