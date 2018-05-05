---
title: 明示的なデータ型変換関数 |Microsoft ドキュメント
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
- explicit data type conversion functions [ODBC]
- data type conversion functions [ODBC]
- functions [ODBC], explicit data type conversion functions
ms.assetid: d5789450-b668-4753-96c8-6789e955e7ed
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1c0326cb06ce772a66be464c176cba58c085d855
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="explicit-data-type-conversion-function"></a>明示的なデータ型変換関数
明示的なデータ型の変換は、SQL データ型の定義を使用して指定します。  
  
 明示的なデータ型変換関数の ODBC 構文では、変換は制限されません。 別のデータ型への 1 つのデータ型の特定の変換の有効性は、各ドライバー固有の実装によって決定されます。 ドライバーは、ネイティブの構文に ODBC 構文を変換として拒否される ODBC の構文では有効ですが、データ ソースでサポートされていない変換のします。 ODBC 関数**SQLGetInfo**オプション (SQL_CONVERT_BIGINT SQL_CONVERT_BINARY、SQL_CONVERT_INTERVAL_YEAR_MONTH、やなど) などが、データ ソースによってサポートされている変換に関する情報を取得する方法を提供する変換.  
  
 形式、**変換**関数は。  
  
 **変換 (** *value_exp*、 *data_type * * *)**  
  
 指定された値が返されます*value_exp*を指定された変換*data_type*ここで、 *data_type*は次のキーワードのいずれか。  
  
|||  
|-|-|  
|SQL_BIGINT|SQL_INTERVAL_HOUR_TO_MINUTE|  
|SQL_BINARY|SQL_INTERVAL_HOUR_TO_SECOND|  
|SQL_BIT|SQL_INTERVAL_MINUTE_TO_SECOND|  
|SQL_CHAR|SQL_LONGVARBINARY|  
|SQL_DECIMAL|SQL_LONGVARCHAR|  
|SQL_DOUBLE|SQL_NUMERIC|  
|SQL_FLOAT|SQL_REAL|  
|SQL_GUID|SQL_SMALLINT|  
|SQL_INTEGER|SQL_DATE|  
|SQL_INTERVAL_MONTH|SQL_TIME|  
|SQL_INTERVAL_YEAR|SQL_TIMESTAMP|  
|SQL_INTERVAL_YEAR_TO_MONTH|SQL_TINYINT|  
|SQL_INTERVAL_DAY|SQL_VARBINARY|  
|SQL_INTERVAL_HOUR|SQL_VARCHAR|  
|SQL_INTERVAL_MINUTE|SQL_WCHAR|  
|SQL_INTERVAL_SECOND|SQL_WLONGVARCHAR|  
|SQL_INTERVAL_DAY_TO_HOUR|SQL_WVARCHAR|  
|SQL_INTERVAL_DAY_TO_MINUTE||  
|SQL_INTERVAL_DAY_TO_SECOND||  
  
 ODBC 構文明示的なデータ型変換関数は、変換形式の仕様をサポートしていません。 明示的な形式の仕様が、基になるデータ ソースによってサポートされている場合、ドライバーは既定値を指定や、形式の仕様を実装する必要があります。  
  
 引数*value_exp*列名、または指定できます、別のスカラー関数、または数値の結果の文字列リテラルです。 以下に例を示します。  
  
```  
{ fn CONVERT( { fn CURDATE() }, SQL_CHAR ) }  
```  
  
 CURDATE スカラー関数の出力を文字の文字列に変換します。  
  
 ODBC がからの戻り値のデータ型を要求していないため、スカラー関数 (ため、関数は、データ ソース固有では多くの場合)、アプリケーションは、データ型の変換を強制的に可能な限り CONVERT のスカラー関数を使用する必要があります。  
  
 次の 2 つの例の例を示します、**変換**関数。 これらの例では、EMPNO 列 SQL_SMALLINT 型の列と SQL_CHAR 型の EMPNAME 列に、従業員をという名前のテーブルの存在があるとします。  
  
 場合は、アプリケーションは、次の SQL ステートメントを指定します。  
  
```  
SELECT EMPNO FROM EMPLOYEES WHERE {fn CONVERT(EMPNO,SQL_CHAR)} LIKE '1%'  
```  
  
-   ORACLE 用のドライバーでは、SQL ステートメントに変換します。  
  
    ```  
    SELECT EMPNO FROM EMPLOYEES WHERE to_char(EMPNO) LIKE '1%'  
    ```  
  
-   SQL Server 用のドライバーでは、SQL ステートメントを変換します。  
  
    ```  
    SELECT EMPNO FROM EMPLOYEES WHERE convert(char,EMPNO) LIKE '1%'  
    ```  
  
 場合は、アプリケーションは、次の SQL ステートメントを指定します。  
  
```  
SELECT {fn ABS(EMPNO)}, {fn CONVERT(EMPNAME,SQL_SMALLINT)}  
   FROM EMPLOYEES WHERE EMPNO <> 0  
```  
  
-   ORACLE 用のドライバーでは、SQL ステートメントに変換します。  
  
    ```  
    SELECT abs(EMPNO), to_number(EMPNAME) FROM EMPLOYEES WHERE EMPNO <> 0  
    ```  
  
-   SQL Server 用のドライバーでは、SQL ステートメントを変換します。  
  
    ```  
    SELECT abs(EMPNO), convert(smallint, EMPNAME) FROM EMPLOYEES  
       WHERE EMPNO <> 0  
    ```  
  
-   Ingres 用のドライバーでは、SQL ステートメントに変換します。  
  
    ```  
    SELECT abs(EMPNO), int2(EMPNAME) FROM EMPLOYEES WHERE EMPNO <> 0  
    ```
