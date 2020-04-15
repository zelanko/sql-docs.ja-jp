---
title: 長さとインジケータの値を使用する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data buffers [ODBC], length
- length/indicator buffers [ODBC]
- length of data buffers [ODBC]
- buffers [ODBC], length
ms.assetid: 849792f1-cb1e-4bc2-b568-c0aff0b66199
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a0c878c9038b26aa996ed206c6b8adfe8d6c21e5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306763"
---
# <a name="using-length-and-indicator-values"></a>長さとインジケーターの値の使用
長さ/インジケーター・バッファーは、データ・バッファー内のデータのバイト長または SQL_NULL_DATA などの特殊標識 (データが NULL であることを示す) を渡すために使用されます。 使用される関数に応じて、長さ/標識バッファーは SQLINTEGER または SQLSMALLINT として定義されます。 したがって、それを記述するためには単一の引数が必要です。 データ バッファーが非遅延入力バッファーの場合、この引数にはデータ自体のバイト長または標識値が含まれます。 StrLen_or_Ind*または同様*の名前の名前が付けられます。 たとえば、次のコードは、データの完全なバッファーを渡すために**SQLPutData**を呼び出します。バイト長 (*ValueLen*) は、データ バッファー (*ValuePtr*) が入力バッファーであるため、直接渡されます。  
  
```  
SQLCHAR      ValuePtr[50];  
SQLINTEGER   ValueLen;  
  
// Call local function to place data in ValuePtr. In ValueLen, return the  
// number of bytes of data placed in ValuePtr. If there is not enough  
// data, this will be less than 50.  
FillBuffer(ValuePtr, sizeof(ValuePtr), &ValueLen);  
  
// Call SQLPutData to send the data to the driver.  
SQLPutData(hstmt, ValuePtr, ValueLen);  
```  
  
 データ・バッファーが据え置き入力バッファー、非据え置き出力バッファー、または出力バッファーである場合、引数には長さ/インジケーター・バッファーのアドレスが入ります。 これは、多くの場合 *、StrLen_or_IndPtr*または同様の名前の名前です。 たとえば、次のコードは、データの完全なバッファーを取得する**SQLGetData**を呼び出します。バイト長は、対応するデータ バッファー (*ValuePtr*) が非遅延出力バッファーであるため、アドレスが**SQLGetData**に渡される長さ/インジケーター バッファー (*ValueLenOrInd*) のアプリケーションに返されます。  
  
```  
SQLCHAR      ValuePtr[50];  
SQLINTEGER   ValueLenOrInd;  
SQLGetData(hstmt, 1, SQL_C_CHAR, ValuePtr, sizeof(ValuePtr), &ValueLenOrInd);  
```  
  
 特に禁止されていない限り、長さ/標識バッファー引数は 0 (非遅延入力の場合) またはヌル・ポインター (出力または据え置き入力の場合) にすることができます。 入力バッファーの場合、ドライバーはデータのバイト長を無視します。 これは可変長データを渡すときにエラーを返しますが、長さも標識値も必要ないため、非 null、固定長データを渡すときに一般的です。 出力バッファーの場合、ドライバーはデータまたはインジケーター値のバイト長を返しません。 これは、ドライバーによって返されるデータが NULL であるが、長さも標識値も必要ないため、固定長、null 非許容データを取得する場合に一般的なエラーです。  
  
 遅延データ バッファーのアドレスがドライバーに渡される場合と同様に、遅延長/インジケーター バッファーのアドレスは、バッファーがバインド解除されるまで有効な状態を維持する必要があります。  
  
 以下の長さは、長さ/インジケーター値として有効です。  
  
-   *n* *、n*は 0 >。  
  
-   0.  
  
-   SQL_NTS。 対応するデータ バッファー内のドライバーに送信される文字列は null で終了します。これは、C プログラマがバイト長を計算せずに文字列を渡す場合に便利な方法です。 この値は、アプリケーションがドライバーにデータを送信する場合にのみ有効です。 ドライバーは、アプリケーションにデータを返すとき、常にデータの実際のバイト長を返します。  
  
 以下の値は、長さ/インジケーター値として有効です。 SQL_NULL_DATAはSQL_DESC_INDICATOR_PTR記述子フィールドに格納されます。その他の値はすべてSQL_DESC_OCTET_LENGTH_PTR記述子フィールドに格納されます。  
  
-   SQL_NULL_DATA。 データは NULL データ値であり、対応するデータ バッファーの値は無視されます。 この値は、ドライバーに送信またはドライバーから取得される SQL データに対してのみ有効です。  
  
-   SQL_DATA_AT_EXEC。 データ バッファーにデータが含まれていません。 代わりに、ステートメントが実行されたとき、または**SQLBulkOperations**または**SQLSetPos**が呼び出されたときに、データが**SQLPutData**と共に送信されます。 この値は、ドライバーに送信される SQL データに対してのみ有効です。 詳細については[、「SQL バインドパラメーター](../../../odbc/reference/syntax/sqlbindparameter-function.md) [、SQL バルクオペレーション](../../../odbc/reference/syntax/sqlbulkoperations-function.md)、および[SQL セットポス](../../../odbc/reference/syntax/sqlsetpos-function.md)」を参照してください。  
  
-   SQL_LEN_DATA_AT_EXEC(*長さ*) マクロの結果。 この値はSQL_DATA_AT_EXECに似ています。 詳細については、「[長いデータの送信](../../../odbc/reference/develop-app/sending-long-data.md)」を参照してください。  
  
-   SQL_NO_TOTAL。 ドライバーは、出力バッファーに返すためにまだ使用可能な長いデータのバイト数を決定できません。 この値は、ドライバーから取得した SQL データに対してのみ有効です。  
  
-   SQL_DEFAULT_PARAM。 プロシージャでは、対応するデータ バッファーの値ではなく、プロシージャ内の入力パラメーターの既定値を使用します。  
  
-   SQL_COLUMN_IGNORE。 **データ バッファー内の**値を無視する操作または**SQL セットポス**。 **SQLBulk オペレーション**または**SQLSetPos**の呼び出しによってデータ行を更新する場合、列の値は変更されません。 **SQLBulkOperations**の呼び出しによって新しいデータ行を挿入する場合、列の値は既定値に設定されます。
