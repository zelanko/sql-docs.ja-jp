---
title: 明示的なデータ型変換関数 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- explicit data type conversion functions [ODBC]
- data type conversion functions [ODBC]
- functions [ODBC], explicit data type conversion functions
ms.assetid: d5789450-b668-4753-96c8-6789e955e7ed
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2de8a8cb6177e9210e8d48c0ce097d13c9a276fd
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306993"
---
# <a name="explicit-data-type-conversion-function"></a>データ型の明示的な変換用関数
SQL データ型定義の観点から、明示的なデータ型変換が指定されます。  
  
 明示的なデータ型変換関数の ODBC 構文では、変換は制限されません。 あるデータ型から別のデータ型への特定の変換の有効性は、各ドライバー固有の実装によって決定されます。 ドライバーは、ODBC 構文をネイティブ構文に変換すると、ODBC 構文では有効ですが、データ ソースでサポートされていない変換を拒否します。 ODBC 関数**SQLGetInfo**変換オプション (SQL_CONVERT_BIGINT、SQL_CONVERT_BINARY、SQL_CONVERT_INTERVAL_YEAR_MONTHなど) を使用すると、データ ソースでサポートされている変換について問い合わせることができます。  
  
 **CONVERT**関数の形式は次のとおりです。  
  
 **変換(** _value_exp_, _data_type_**)**  
  
 この関数は、指定された*data_typedata_type*に変換*data_type**value_exp*で指定された値を返します。  
  
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
  
 明示的なデータ型変換関数の ODBC 構文では、変換形式の指定はサポートされていません。 明示的な形式の仕様が基になるデータ ソースでサポートされている場合、ドライバーは既定値を指定するか、形式の仕様を実装する必要があります。  
  
 引数*value_exp*は、列名、別のスカラー関数の結果、または数値リテラルまたは文字列リテラルです。 次に例を示します。  
  
```  
{ fn CONVERT( { fn CURDATE() }, SQL_CHAR ) }  
```  
  
 CURDATE スカラー関数の出力を文字列に変換します。  
  
 ODBC では、データ型がスカラー関数からの戻り値に対して必須ではないため (関数はデータ ソース固有の場合が多いため)、アプリケーションは可能な限り CONVERT スカラー関数を使用してデータ型変換を強制する必要があります。  
  
 次の 2 つの例は **、CONVERT**関数の使用方法を示しています。 これらの例では、タイプ・SQL_SMALLINTの EMPNO 列とタイプ・SQL_CHARの EMPNAME 列を持つ、EMPLOYEES という表が存在することを前提としています。  
  
 アプリケーションが次の SQL ステートメントを指定する場合。  
  
```  
SELECT EMPNO FROM EMPLOYEES WHERE {fn CONVERT(EMPNO,SQL_CHAR)} LIKE '1%'  
```  
  
-   ORACLE 用のドライバーは、SQL ステートメントを次のように変換します。  
  
    ```  
    SELECT EMPNO FROM EMPLOYEES WHERE to_char(EMPNO) LIKE '1%'  
    ```  
  
-   SQL Server のドライバーは、SQL ステートメントを次のように変換します。  
  
    ```  
    SELECT EMPNO FROM EMPLOYEES WHERE convert(char,EMPNO) LIKE '1%'  
    ```  
  
 アプリケーションが次の SQL ステートメントを指定する場合。  
  
```  
SELECT {fn ABS(EMPNO)}, {fn CONVERT(EMPNAME,SQL_SMALLINT)}  
   FROM EMPLOYEES WHERE EMPNO <> 0  
```  
  
-   ORACLE 用のドライバーは、SQL ステートメントを次のように変換します。  
  
    ```  
    SELECT abs(EMPNO), to_number(EMPNAME) FROM EMPLOYEES WHERE EMPNO <> 0  
    ```  
  
-   SQL Server のドライバーは、SQL ステートメントを次のように変換します。  
  
    ```  
    SELECT abs(EMPNO), convert(smallint, EMPNAME) FROM EMPLOYEES  
       WHERE EMPNO <> 0  
    ```  
  
-   Ingres のドライバーは、SQL ステートメントを次のように変換します。  
  
    ```  
    SELECT abs(EMPNO), int2(EMPNAME) FROM EMPLOYEES WHERE EMPNO <> 0  
    ```
