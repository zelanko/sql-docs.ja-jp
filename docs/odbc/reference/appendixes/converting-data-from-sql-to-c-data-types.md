---
title: SQL から C データ型へのデータの変換 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1a10730cb3910c55679c264583801cd57c83bfc3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284752"
---
# <a name="converting-data-from-sql-to-c-data-types"></a>SQL から C データ型へのデータ変換
アプリケーションが呼び出すとき**SQLFetch、** **SQLフェッチScroll**、または**SQLGetData**を使用すると、ドライバーはデータ ソースからデータを取得します。 必要に応じて、ドライバーが取得したデータ型から **、SQLBindCol**または**SQLGetData**の*引数の TargetType*で指定されたデータ型にデータを変換します。 最後に **、SQLBindCol**または**SQLGetData** (および ARD のSQL_DESC_DATA_PTR フィールド) の*引数*によって指される場所にデータを格納します。  
  
 次の表は、ODBC SQL データ型から ODBC C データ型への変換を示しています。 塗りつぶされた円は、SQL データ型 *(TargetType*の値がSQL_C_DEFAULTの場合にデータが変換される C データ型) の既定の変換を示します。 中空の円は、サポートされている変換を示します。  
  
 ODBC *2.x*ドライバーを使用する ODBC *3.x*アプリケーションでは、ドライバー固有のデータ型からの変換がサポートされない場合があります。  
  
 変換されたデータの形式は、Windows ®国の設定の影響を受けません。  
  
 次のセクションの表では、ドライバーまたはデータ ソースがデータ ソースから取得したデータをどのように変換するかを説明します。ドライバーは、サポートする ODBC SQL データ型からすべての ODBC C データ型への変換をサポートする必要があります。 特定の ODBC SQL データ型の場合、テーブルの最初の列には **、SQLBindCol**および**SQLGetData**の*TargetType*引数の有効な入力値が一覧表示されます。 2 番目の列には、多くの場合 **、SQLBindCol**または**SQLGetData**で指定された*BufferLength*引数を使用して、データを変換できるかどうかを判断するためにドライバーが実行する、テストの結果が一覧表示されます。 結果ごとに、3 番目と 4 番目の列には *、TargetValuePtr*で指定されたバッファーに格納された値と、ドライバーがデータを変換しようとした後に**SQLBindCol**または**SQLGetData**で指定された引数を*StrLen_or_IndPtr*します。 (StrLen_or_IndPtr*StrLen_or_IndPtr*引数は ARD のSQL_DESC_OCTET_LENGTH_PTRフィールドに対応します。最後の列には、SQL フェッチ、SQL**フェッチスクロール**、または**SQLGetData**によって各結果に対して返される**SQLSTATE**が一覧表示されます。  
  
 **SQLBindCol**または**SQLGetData**の*TargetType*引数に、指定された ODBC SQL データ型のテーブルに表示されていない ODBC C データ型の識別子が含まれている場合は **、SQLFetch** **、SQLFetchScroll、** または**SQLGetData**が SQLSTATE 07006 (制限されたデータ型属性違反) を返します。 *引数に*、ドライバー固有の SQL データ型から ODBC C データ型への変換を指定する識別子が含まれている場合、この変換は、ドライバー **、SQLFetch、SQLFetchScroll、** または**SQLGetData**によってサポートされていません SQLSTATE HYC00 (省略可能な機能が実装されていません)。 **SQLFetchScroll**  
  
 この値はテーブルに表示されませんが、SQL データ値が NULL の場合、ドライバーは*StrLen_or_IndPtr*引数で指定されたバッファーにSQL_NULL_DATAを返します。 データを取得するために複数の呼び出しが行われる場合の*StrLen_or_IndPtr*の使用の詳細については[、SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)関数の説明を参照してください。 SQL データが文字 C データに変換される場合\**、StrLen_or_IndPtr*に返される文字カウントには、ヌル終了バイトは含まれません。 *ターゲット値Ptr*が NULL ポインターの場合 **、SQLState** HY009 (NULL ポインターの無効な使用) を返します。**では、** 列のバインドが解除されます。  
  
 テーブルでは、次の用語と規約が使用されます。  
  
-   **データのバイト長**は、 **TargetValuePtr*で返される C データのバイト数です。 文字列データの場合、NULL 終端文字のスペースは含まれません。  
  
-   **文字バイト長**は、データを文字形式で表示するために必要なバイト数の合計です。 これは[、表示サイズ](../../../odbc/reference/appendixes/display-size.md)の場合は、文字バイトの長さがバイト単位である点を除き、各 C データ型に対して定義されています。  
  
-   *斜体の単語は、関数の*引数または SQL 文法の要素を表します。 文法要素の構文については、「[付録 C : SQL 文法](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md)」を参照してください。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [SQL から C へ: 文字](../../../odbc/reference/appendixes/sql-to-c-character.md)  
  
-   [SQL から C へ: 数値](../../../odbc/reference/appendixes/sql-to-c-numeric.md)  
  
-   [SQL から C へ: bit](../../../odbc/reference/appendixes/sql-to-c-bit.md)  
  
-   [SQL から C へ: Binary](../../../odbc/reference/appendixes/sql-to-c-binary.md)  
  
-   [SQL から C へ: Date](../../../odbc/reference/appendixes/sql-to-c-date.md)  
  
-   [SQL から C へ: GUID](../../../odbc/reference/appendixes/sql-to-c-guid.md)  
  
-   [SQL から C へ: Time](../../../odbc/reference/appendixes/sql-to-c-time.md)  
  
-   [SQL から C へ: Timestamp](../../../odbc/reference/appendixes/sql-to-c-timestamp.md)  
  
-   [SQL から C へ: 年月の間隔](../../../odbc/reference/appendixes/sql-to-c-year-month-intervals.md)  
  
-   [SQL から C へ: 日付と時刻の間隔](../../../odbc/reference/appendixes/sql-to-c-day-time-intervals.md)  
  
-   [SQL から C へのデータ変換の例](../../../odbc/reference/appendixes/sql-to-c-data-conversion-examples.md)
