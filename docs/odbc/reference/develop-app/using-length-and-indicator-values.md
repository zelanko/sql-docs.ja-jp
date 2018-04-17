---
title: 長さのインジケーター値を使って |Microsoft ドキュメント
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
- data buffers [ODBC], length
- length/indicator buffers [ODBC]
- length of data buffers [ODBC]
- buffers [ODBC], length
ms.assetid: 849792f1-cb1e-4bc2-b568-c0aff0b66199
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5c3a817aa541d397a46ae75d09ed09ccbb550842
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="using-length-and-indicator-values"></a>長さとインジケーターの値を使用してください。
長さ/インジケーター バッファーを使用して、データ バッファーやデータが NULL であることを示す SQL_NULL_DATA などの特殊なインジケーター内のデータのバイトの長さを渡します。 使用されている、関数によっては、長さ/インジケーター バッファーは、SQLINTEGER または、SQLSMALLINT に定義されます。 そのため、それを記述する 1 つの引数が必要です。 データ バッファーが使用中として入力バッファーの場合は、この引数には、データ自体のバイトの長さまたはインジケーターの値が含まれます。 という名前が多くの場合、 *StrLen_or_Ind*または類似した名前です。 たとえば、次のコード呼び出し**SQLPutData**にバッファーを渡すデータの完全; バイトの長さ (*ValueLen*) あるために、直接渡すはデータ バッファー (*ValuePtr*) は入力バッファー。  
  
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
  
 データ バッファーが遅延の入力バッファー、使用中として出力バッファーまたは出力バッファーの場合は、引数には、長さ/インジケーター バッファーのアドレスが含まれています。 という名前が多くの場合、 *StrLen_or_IndPtr*または類似した名前です。 たとえば、次のコード呼び出し**SQLGetData**データでいっぱいバッファーを取得するバイトの長さが長さ/インジケーター バッファー内のアプリケーションに返されます (*ValueLenOrInd*)、アドレスを持つ渡される**SQLGetData**ため、対応するデータ バッファー (*ValuePtr*) は、使用中として出力バッファー。  
  
```  
SQLCHAR      ValuePtr[50];  
SQLINTEGER   ValueLenOrInd;  
SQLGetData(hstmt, 1, SQL_C_CHAR, ValuePtr, sizeof(ValuePtr), &ValueLenOrInd);  
```  
  
 具体的には禁止されている場合を除き、長さ/インジケーター バッファー引数が 0 にすることができます (場合は使用中として入力) または null ポインター (場合出力または遅延の入力)。 入力バッファーの場合、これが原因、データのバイト長を無視するドライバー。 これにより、可変長のデータを渡すときにエラーが返されますが、ため一般的では、null 以外の固定長のデータを渡すときに、長さもインジケーターの値が必要があります。 出力バッファーには原因データやインジケーター値のバイト長に返されないドライバーです。 これは、ドライバーによって返されるデータは NULL ですので一般的では、null 非許容の固定長のデータを取得するときに、長さもインジケーターの値が必要な場合のエラーです。  
  
 遅延データ バッファーのアドレスがドライバーに渡されたときと遅延の長さ/インジケーター バッファーのアドレス必要がありますされるまで有効なバッファーがバインドです。  
  
 長さまたはインジケーターの値として有効な次の長さです。  
  
-   *n*ここで、 *n* > 0 です。  
  
-   0.  
  
-   SQL_NTS です。 ドライバー対応するデータ バッファーに送信される文字列終端は null です。これは、文字列を渡す、バイトの長さを計算することがなく C プログラマのための便利な方法です。 この値は、アプリケーションがドライバーにデータを送信するときにのみです。 ドライバーは、アプリケーションにデータを返すときに常に、データの実際のバイトの長さを返します。  
  
 次の値は、長さ/インジケーターの値として有効です。 SQL_NULL_DATA フィールドに格納されて、SQL_DESC_INDICATOR_PTR 記述子です。その他のすべての値は、SQL_DESC_OCTET_LENGTH_PTR 記述子フィールドに格納されます。  
  
-   SQL_NULL_DATA です。 データは、NULL データ値、および対応するデータ バッファー内の値は無視されます。 この値は、SQL データに送信される、またはドライバーから取得に対してのみ有効です。  
  
-   SQL_DATA_AT_EXEC です。 データ バッファーにデータが含まれていません。 データを送信する代わりに、 **SQLPutData** 、ステートメントが実行されるとき、または**SQLBulkOperations**または**SQLSetPos**と呼びます。 この値は、ドライバーに送信される SQL データに対してのみ有効です。 詳細については、次を参照してください。 [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)、 [SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)、および[SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)です。  
  
-   結果の SQL_LEN_DATA_AT_EXEC (*長さ*) マクロです。 この値は、SQL_DATA_AT_EXEC に似ています。 詳細については、次を参照してください。[長い形式のデータを送信する](../../../odbc/reference/develop-app/sending-long-data.md)です。  
  
-   SQL_NO_TOTAL です。 ドライバーは、出力バッファーに戻るにはまだ使用できる長い形式のデータのバイト数を特定できません。 この値は、ドライバーから取得した SQL データに対してのみ有効です。  
  
-   SQL_DEFAULT_PARAM です。 プロシージャでは、対応するデータ バッファー内の値ではなくプロシージャの入力パラメーターの既定値を使用します。  
  
-   SQL_COLUMN_IGNORE です。 **SQLBulkOperations**または**SQLSetPos**が、データ バッファーに値を無視します。 呼び出しによってデータの行を更新するときに**SQLBulkOperations**または**SQLSetPos、**列の値は変更されません。 呼び出しによって新しいデータの行を挿入するときに**SQLBulkOperations**列の値が既定の設定にまたは、列には、null、既定値はありません。
