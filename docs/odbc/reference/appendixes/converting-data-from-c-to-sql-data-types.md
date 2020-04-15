---
title: データを C から SQL データ型に変換する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from c to SQL types [ODBC], about converting
- converting data from c to SQL types [ODBC]
- data conversions from C to SQL types [ODBC], about converting
- data types [ODBC], C data types
- data types [ODBC], converting data
- SQL data types [ODBC], converting from C types
- data types [ODBC], SQL data types
- data conversions from C to SQL types [ODBC]
- C data types [ODBC], converting to SQL types
ms.assetid: ee0afe78-b58f-4d34-ad9b-616bb23653bd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8fb707e77df7d793277d4a23146adc980eede6fd
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304661"
---
# <a name="converting-data-from-c-to-sql-data-types"></a>C から SQL データ型へのデータ変換
アプリケーションが**SQLExecute**または**SQLExecDirect**を呼び出すと、ドライバーは、アプリケーション内のストレージの場所から**SQLBindParameter**でバインドされたパラメーターのデータを取得します。 アプリケーションが**SQLSetPos**を呼び出すと、ドライバーは、更新のデータを取得するか **、SQLBindCol**でバインドされた列から操作を追加します。 実行時のデータ パラメーターの場合、アプリケーションは**SQLPutData**を使用してパラメーター データを送信します。 必要に応じて、ドライバーは **、SQLBindParameter**の*引数で指定*されたデータ型のデータ型から、データを変換します、 **SQLBindParameter**引数で*引数*で指定されたデータ型、データ ソースにデータを送信します。  
  
 次の表は、ODBC C データ型から ODBC SQL データ型への変換を示しています。 塗りつぶされた円は、SQL データ型の既定の変換を示します *(ValueType*またはSQL_DESC_CONCISE_TYPE記述子フィールドがSQL_C_DEFAULTされた場合にデータを変換する C データ型)。 中空の円は、サポートされている変換を示します。  
  
 変換されたデータの形式は、Windows ®国の設定の影響を受けません。  
  
 ![サポートされる ODBC C から SQL へのデータ型の変換](../../../odbc/reference/appendixes/media/apd1b.gif "apd1b")  
  
 次のセクションの表では、ドライバーまたはデータ ソースがデータ ソースに送信されるデータをどのように変換するかを説明します。ドライバーは、すべての ODBC C データ型からサポートする ODBC SQL データ型への変換をサポートする必要があります。 指定された ODBC C データ型の場合、テーブルの最初の列には **、SQLBindParameter**の*引数 ParameterType*の有効な入力値が一覧表示されます。 2 番目の列には、ドライバーがデータを変換できるかどうかを判断するために実行するテストの結果が一覧表示されます。 3 番目の列には、結果ごとに返される**SQLSTATE**が**SQLExecute**一覧表示されます**SQLBulkOperations****。** **SQLSetPos** データは、SQL_SUCCESSが返された場合にのみデータ ソースに送信されます。  
  
 引数*の引数は***、指定**された C データ型のテーブルに表示されていない ODBC SQL データ型の識別子が含**まれている場合は**、SQLState 07006 (制限されたデータ型の属性違反) を返します。 引数*ParameterType*ドライバー固有の識別子が含まれ、ドライバーは、特定の ODBC C データ型からそのドライバー固有の SQL データ型への変換をサポートしない場合**SQLBindParameter** SQLSTATE HYC00 (オプション機能が実装されていません) を返します。  
  
 **SQLBindParameter**で指定された*パラメーター値Ptr*引数と*StrLen_or_IndPtr*引数が両方ともヌル・ポインターである場合、その関数は SQLSTATE HY009 (ヌル・ポインターの無効な使用) を戻します。 この値は表に示されていませんが、アプリケーションは**SQLBindParameter**の*StrLen_or_IndPtr*引数によって指される長さ/標識バッファーの値、または**SQLPutData**の*StrLen_or_IndPtr*引数の値を設定して、NULL SQL データ値を指定SQL_NULL_DATAします。 (StrLen_or_IndPtr*StrLen_or_IndPtr*引数は、APD のSQL_DESC_OCTET_LENGTH_PTRフィールドに対応します。アプリケーションは、これらの値をSQL_NTSに\*設定して **、SQLPutData**の*ParameterValuePtr* \*または**SQLPutData**の*DataPtr* (APD のSQL_DESC_DATA_PTR フィールドによって指される) の値が NULL で終わる文字列であることを指定します。  
  
 テーブルでは、次の用語が使用されます。  
  
-   **データのバイト長**- データ ソースに送信される前にデータが切り捨てられるかどうかに関係なく、データ ソースに送信できる SQL データのバイト数。 文字列データの場合、これには NULL 終端文字用のスペースは含まれません。  
  
-   **列バイト長**- データ ソースでデータを格納するために必要なバイト数。  
  
-   **文字バイト長**- 文字形式でデータを表示するために必要な最大バイト数。 これは[、表示サイズ](../../../odbc/reference/appendixes/display-size.md)が文字単位である間、文字バイトの長さがバイト単位である場合を除き、 表示サイズ の各 SQL データ・タイプに対して定義されます。  
  
-   **桁数**- マイナス記号、小数点、指数 (必要な場合) を含む、数値を表すために使用する文字数。  
  
-   **の言葉**   
     ***斜体***- SQL 文法の要素。 文法要素の構文については、「[付録 C : SQL 文法](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md)」を参照してください。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [C から SQL へ: 文字](../../../odbc/reference/appendixes/c-to-sql-character.md)  
  
-   [C から SQL へ: 数値](../../../odbc/reference/appendixes/c-to-sql-numeric.md)  
  
-   [C から SQL へ: bit](../../../odbc/reference/appendixes/c-to-sql-bit.md)  
  
-   [C から SQL へ: Binary](../../../odbc/reference/appendixes/c-to-sql-binary.md)  
  
-   [C から SQL へ: Date](../../../odbc/reference/appendixes/c-to-sql-date.md)  
  
-   [C から SQL へ: GUID](../../../odbc/reference/appendixes/c-to-sql-guid.md)  
  
-   [C から SQL へ: Time](../../../odbc/reference/appendixes/c-to-sql-time.md)  
  
-   [C から SQL へ: Timestamp](../../../odbc/reference/appendixes/c-to-sql-timestamp.md)  
  
-   [C から SQL へ: 年月の間隔](../../../odbc/reference/appendixes/c-to-sql-year-month-intervals.md)  
  
-   [C から SQL へ: 日付と時刻の間隔](../../../odbc/reference/appendixes/c-to-sql-day-time-intervals.md)  
  
-   [C から SQL へのデータ変換の例](../../../odbc/reference/appendixes/c-to-sql-data-conversion-examples.md)
