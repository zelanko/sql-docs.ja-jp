---
title: "列のサイズ、十進数、転送のオクテットの長さ、サイズを表示します |。Microsoft ドキュメント"
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
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 19f505751d63f07dbd5eb2d1d53b9c191307e9b2
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="column-size-decimal-digits-transfer-octet-length-and-display-size---odbc"></a>列のサイズ、10 進数字は、オクテットの長さを転送し、ODBC のサイズを表示
データ型は、その列 (またはパラメーター) のサイズ、小数点以下桁数、長さ、によって特徴付けられ、サイズを表示します。 次の ODBC 関数では、データ ソースでこれらの属性は、SQL ステートメント内のパラメーターや、SQL データ型を返します。 各 ODBC 関数では、次のように、これらの属性の別のセットを返します。  
  
-   **SQLDescribeCol**列について説明する列のサイズおよび小数点以下桁数を返します。  
  
-   **SQLDescribeParam**パラメーターについて説明しますが、パラメーターのサイズおよび小数点以下の桁を返します。 **SQLBindParameter** SQL ステートメントにパラメーターのサイズおよび小数点以下桁数のパラメーターを設定します。  
  
-   カタログ関数**SQLColumns**、 **SQLProcedureColumns**、および**SQLGetTypeInfo**テーブル、結果セット、またはプロシージャのパラメーターの列の属性を返すとデータ ソース内のデータ型のカタログの属性です。 **SQLColumns** (など、ベース テーブル、ビュー、またはシステム テーブル) の指定したテーブルに列のサイズ、10 進数字、および列の長さを返します。 **SQLProcedureColumns**プロシージャで列のサイズ、10 進数字、および列の長さを返します。 **SQLGetTypeInfo**データ ソース内の列の最大サイズと最小値と最大の 10 進、SQL データ型を返します。  
  
 列のこれらの関数によって返される値またはパラメーターのサイズは"precision"として ODBC 2 で定義されているに対応します。*x*です。 ただし、値は必ずしも対応しません SQL_DESC_PRECISION またはその他の任意の 1 つの記述子フィールドで返される値。 同じ機能は、"scale"として ODBC 2 で定義されているに対応する 10 進数字の場合は true です。*x*です。 必ずしも対応しません SQL_DESC_SCALE またはその他の 1 つ記述子フィールドで返される値が、データ型に応じて異なる記述子フィールドから取得します。 詳細については、次を参照してください。[列サイズ](../../../odbc/reference/appendixes/column-size.md)と[小数点以下桁数](../../../odbc/reference/appendixes/decimal-digits.md)です。  
  
 同様に、転送のオクテットの長さの値にならない SQL_DESC_LENGTH からです。 すべての文字とバイナリ型記述子のフィールドの SQL_DESC_OCTET_LENGTH から取得します。 その他の種類には、この情報を保持する記述子フィールドはありません。  
  
 すべてのデータ型の表示サイズの値は、SQL_DESC_DISPLAY_SIZE、1 つの記述子フィールドの値に対応します。  
  
 記述子フィールドは、結果セットの特性を記述します。 記述子フィールドには、ステートメントの実行前にデータの有効な値はありません。 列の値のサイズ、10 進数字とから返されるサイズを表示**SQLColumns**、 **SQLProcedureColumns**、および**SQLGetTypeInfo**、互いに戻り、渡すデータ ソースのカタログ内に存在するテーブルの列とデータ型などのデータベース オブジェクトの特性。 同様に、その結果セットで**SQLColAttribute**列のサイズ、10 進数字、およびデータ ソースの列の転送のオクテットの長さを返しますこれらの値は必ずしも SQL_DESC_PRECISION、sql _ の値と同じDESC_SCALE、および SQL_DESC_OCTET_LENGTH 記述子フィールドです。  
  
 これらの記述子フィールドの詳細については、次を参照してください。 [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)です。  
  
 関連項目:   
  
-   [列のサイズ](../../../odbc/reference/appendixes/column-size.md)  
-   [小数点以下桁数](../../../odbc/reference/appendixes/decimal-digits.md)  
-   [転送のオクテットの長さ](../../../odbc/reference/appendixes/transfer-octet-length.md)  
-   [表示サイズ](../../../odbc/reference/appendixes/display-size.md)
