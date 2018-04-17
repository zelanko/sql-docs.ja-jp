---
title: SQL から C データ型にデータを変換する |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data conversions from SQL to C types [ODBC]
- data conversions from SQL to C types [ODBC], about converting
- data types [ODBC], C data types
- data types [ODBC], converting data
- data types [ODBC], SQL data types
- SQL data types [ODBC], converting to C types
- converting data from SQL to c types [ODBC]
- converting data from SQL to c types [ODBC], about converting
- C data types [ODBC], converting from SQL types
ms.assetid: 029727f6-d3f0-499a-911c-bcaf9714e43b
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fe89608061d82cf54a16394e5ce1a8f901e23523
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="converting-data-from-sql-to-c-data-types"></a>SQL から C データ型にデータを変換します。
アプリケーションを呼び出すと**SQLFetch**、 **SQLFetchScroll**、または**SQLGetData**ドライバーは、データ ソースからデータを取得します。 かどうか、必要に応じて、データ変換から変換ドライバー取得することによって指定されたデータ型にデータ型、 *TargetType*引数**SQLBindCol**または**SQLGetData です。** 最後に、によって示される場所にデータを格納、 *TargetValuePtr*引数**SQLBindCol**または**SQLGetData** (および、ARD の SQL_DESC_DATA_PTR フィールド)。  
  
 次の表は、ODBC SQL からサポートされている変換にデータ型を ODBC C データ型を示します。 塗りつぶされた円は、SQL データ型の既定の変換を示します (する、データは変換されるときに C データ型の値*TargetType*は SQL_C_DEFAULT)。 中空の円では、サポートされている変換を示します。  
  
 ODBC 3*.x* ODBC 2 を使用するアプリケーション*。x*ドライバー、ドライバー固有のデータ型がサポートされていない可能性がありますから変換します。  
  
 変換後のデータの形式は Windows® 国設定の影響を受けません。  
  
 次のセクションでは、内のテーブルでは、ドライバーまたはデータ ソースがデータ ソースから取得されたデータに変換する方法について説明します。ドライバーは、サポートする ODBC SQL データ型からすべての ODBC C データ型への変換をサポートするために必要です。 テーブルの最初の列の特定の ODBC SQL データ型の有効な入力値を一覧表示、 *TargetType*引数**SQLBindCol**と**SQLGetData**です。 2 番目の列は、多くの場合を使用して、テストの結果を一覧表示、 *BufferLength*引数で指定された**SQLBindCol**または**SQLGetData**へのドライバーを実行します。データを変換できるかどうかを決定します。 3 番目と 4 番目の列の各結果で指定されたバッファーに配置された値を一覧表示、 *TargetValuePtr*と*StrLen_or_IndPtr*で指定された引数**SQLBindCol**または**SQLGetData**後、ドライバーは、データを変換しようとしています。 (、 *StrLen_or_IndPtr*引数は、ARD の SQL_DESC_OCTET_LENGTH_PTR フィールドに対応します)。最後の列の一覧の各結果によって返される SQLSTATE **SQLFetch**、 **SQLFetchScroll**、または**SQLGetData**です。  
  
 場合、 *TargetType*引数**SQLBindCol**または**SQLGetData**いない特定の ODBC SQL データ型の表に示す ODBC C データ型の識別子を含む**SQLFetch**、 **SQLFetchScroll**、または**SQLGetData** SQLSTATE 07006 が返されます (制限付きのデータ型の属性に違反)。 場合、 *TargetType*引数には、ドライバー固有の SQL データ型から ODBC C データ型への変換を指定する識別子が含まれ、ドライバーでは、この変換はサポートされていない**SQLFetch**、**SQLFetchScroll**、または**SQLGetData** SQLSTATE HYC00 を返します (省略可能な機能が実装されていません)。  
  
 テーブルに示されていませんが、ドライバーがで指定したバッファー内 SQL_NULL_DATA を返します、 *StrLen_or_IndPtr* SQL データ値は NULL にする場合に引数。 使用の詳細について*StrLen_or_IndPtr*の複数の呼び出しが行われるとデータを取得するを参照してください、 [SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)関数の説明。 SQL データが文字データに変換されると、文字数が返される\* *StrLen_or_IndPtr* null 終了バイトには含まれません。 場合*TargetValuePtr* null ポインターでは、 **SQLGetData** SQLSTATE HY009 を返します (null ポインターの使い方が正しくありません); で**SQLBindCol**、これは、列をバインド解除します。  
  
 次の用語と規則は、テーブルで使用されます。  
  
-   **データのバイト長**で返される使用可能な C データのバイト数は、**TargetValuePtr*アプリケーションに返される前に、データが切り捨てられますかどうかにかかわらず、します。 文字列データの場合は、これに null 終端文字のための領域は含まれません。  
  
-   **バイトの長さを文字**文字形式でデータを表示するために必要なバイト数の合計数です。 これは、セクションの C データ型ごとに定義されている[表示サイズ](../../../odbc/reference/appendixes/display-size.md)文字バイトの長さはバイト単位で表示サイズは文字にする点を除いて、します。  
  
-   単語*斜体*関数の引数または SQL の文法の要素を表します。 文法要素の構文を参照してください。[付録 c: SQL 文法](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md)です。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [SQL から C へ: 文字](../../../odbc/reference/appendixes/sql-to-c-character.md)  
  
-   [SQL から C へ: 数値](../../../odbc/reference/appendixes/sql-to-c-numeric.md)  
  
-   [SQL から C へ: ビット](../../../odbc/reference/appendixes/sql-to-c-bit.md)  
  
-   [SQL から C へ: バイナリ](../../../odbc/reference/appendixes/sql-to-c-binary.md)  
  
-   [SQL から C へ: 日付](../../../odbc/reference/appendixes/sql-to-c-date.md)  
  
-   [SQL から C へ: GUID](../../../odbc/reference/appendixes/sql-to-c-guid.md)  
  
-   [SQL から C へ: 時刻](../../../odbc/reference/appendixes/sql-to-c-time.md)  
  
-   [SQL から C へ: タイムスタンプ](../../../odbc/reference/appendixes/sql-to-c-timestamp.md)  
  
-   [SQL から C へ: 年月の間隔](../../../odbc/reference/appendixes/sql-to-c-year-month-intervals.md)  
  
-   [SQL から C へ: 日付と時刻の間隔](../../../odbc/reference/appendixes/sql-to-c-day-time-intervals.md)  
  
-   [SQL から C へのデータ変換の例](../../../odbc/reference/appendixes/sql-to-c-data-conversion-examples.md)
