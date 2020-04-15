---
title: 列サイズ、10 進数、転送オクテットの長さ、表示サイズ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- display size of data types [ODBC]
- data types [ODBC], column size
- transfer octet length of data types [ODBC]
- size of data types [ODBC]
- data types [ODBC], display size
- decimal digits of data types [ODBC]
- data types [ODBC], decimal digits
- SQL data types [ODBC], column characteristics
- column size of data types [ODBC]
- data types [ODBC], transfer octet length
ms.assetid: 723107a1-be08-4ea3-a8c0-b2c45d38d1aa
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 55b8e9dd305764a89601e9ffd5a337e42a8d8db3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306573"
---
# <a name="column-size-decimal-digits-transfer-octet-length-and-display-size---odbc"></a>列サイズ、10 進数、転送オクテットの長さ、および表示サイズ - ODBC
データ型は、列 (またはパラメーター) のサイズ、10 進数、長さ、および表示サイズによって特徴付けられます。 次の ODBC 関数は、SQL ステートメント内のパラメーター、またはデータ ソースの SQL データ型に対してこれらの属性を返します。 各 ODBC 関数は、次のように、これらの属性の異なるセットを返します。  
  
-   **SQLDescribeCol は**、列のサイズと、それが記述する列の 10 進数を返します。  
  
-   **SQLDescribeパラムは**、それが記述するパラメータのパラメータサイズと10進数を返します。 **SQLBindParameter SQL**ステートメント内のパラメーターのパラメーターのサイズと 10 進数を設定します。  
  
-   カタログ関数**SQLColumns** **、SQLProcedureColumns**、および**SQLGetTypeInfo**は、テーブル、結果セット、またはプロシージャ パラメーターとデータ ソース内のデータ型のカタログ属性の列の属性を返します。 **SQLColumns は**、指定されたテーブル (ベース テーブル、ビュー、システム テーブルなど) の列のサイズ、10 進数、および列の長さを返します。 **プロシージャ**内の列のサイズ、10 進数、および長さを返します。 **SQLGetTypeInfo は**、データ ソースの SQL データ型の最大列サイズと最小および最大 10 進数を返します。  
  
 列またはパラメーターのサイズに対してこれらの関数によって返される値は、ODBC 2 で定義されている "精度" に対応しています。*x .* ただし、値は、SQL_DESC_PRECISIONまたは他の記述子フィールドで返される値に必ずしも一致しません。 ODBC 2 で定義されている "スケール" に対応する 10 進数の数字についても同じことが言えます。*x .* これは、SQL_DESC_SCALEまたは他の記述子フィールドで返される値に必ずしも対応するわけではありませんが、データ型に応じて異なる記述子フィールドから取得されます。 詳細については、[列サイズ](../../../odbc/reference/appendixes/column-size.md)および[10 進数を参照してください](../../../odbc/reference/appendixes/decimal-digits.md)。  
  
 同様に、転送オクテット長の値はSQL_DESC_LENGTHから来るものではありません。 これらは、すべての文字型とバイナリ型の記述子のフィールドのSQL_DESC_OCTET_LENGTHから取得されます。 他の型のこの情報を保持する記述子フィールドはありません。  
  
 すべてのデータ型の表示サイズ値は、SQL_DESC_DISPLAY_SIZE単一の記述子フィールドの値に対応します。  
  
 記述子フィールドは、結果セットの特性を記述します。 記述子フィールドには、ステートメント実行前のデータに関する有効な値が含まれていません。 **一方、SQLColumns 、SQLProcedureColumns**、および**SQLGetTypeInfo**によって返される列サイズ、10 進数、および表示サイズの値は、データ ソースのカタログに存在するテーブル列やデータ型などのデータベース オブジェクトの特性を返します。 **SQLProcedureColumns** 同様に、結果セットでは **、SQLColAttribute は**列サイズ、10 進数、およびデータ ソースでの列の転送オクテットの長さを返します。これらの値は、SQL_DESC_PRECISION、SQL_DESC_SCALE、およびSQL_DESC_OCTET_LENGTH記述子フィールドの値と必ずしも同じではありません。  
  
 これらの記述子フィールドの詳細については、 [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)を参照してください。  
  
 関連トピック:  
  
-   [列サイズ](../../../odbc/reference/appendixes/column-size.md)  
-   [10 進数字](../../../odbc/reference/appendixes/decimal-digits.md)  
-   [転送オクテット長](../../../odbc/reference/appendixes/transfer-octet-length.md)  
-   [表示サイズ](../../../odbc/reference/appendixes/display-size.md)
