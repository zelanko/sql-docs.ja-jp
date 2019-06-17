---
title: Datetime データ型の変更 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- time data type [ODBC]
- datetime data types [ODBC]
- date data type [ODBC]
- backward compatibility [ODBC], datetime data types
- timestamp data type [ODBC]
- compatibility [ODBC], datetime data types
ms.assetid: c38c79f9-8bb0-4633-ac86-542366c09a95
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a5a87a1cbfbdff5eb428e73d74cdd1199955d673
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63267697"
---
# <a name="datetime-data-type-changes"></a>datetime データ型の変更
ODBC 3。*x*、識別子を日付、時刻、および timestamp SQL データ型は、SQL_DATE、SQL_TIME、および SQL_TIMESTAMP から変更された (のインスタンスと **#define** 9、10、および 11 のヘッダー ファイルで)、SQL_TYPE_DATE にSQL_TYPE_TIME、および SQL_TYPE_TIMESTAMP (のインスタンスと **#define** 91、92、および 93 のヘッダー ファイルで)、それぞれします。 対応する C 型識別子から変更された SQL_C_DATE、SQL_C_TIME、および SQL_C_TIMESTAMP SQL_C_TYPE_DATE、SQL_C_TYPE_TIME、SQL_C_TYPE_TIMESTAMP では、それぞれします。  
  
 列のサイズと 10 進数字が ODBC 3 での SQL の datetime データ型に対して返されます。*x*は、ODBC 2 でそれらの有効桁数と小数点と同じ返されます *。x*します。 これらの値は、SQL_DESC_PRECISION および SQL_DESC_SCALE 記述子フィールドの値と異なります。 (詳細については、次を参照してください[列のサイズ、10 進数字、転送オクテット長、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)。)。  
  
 これらの変更に影響を与える**SQLDescribeCol**、 **SQLDescribeParam**、および**SQLColAttribute**;**SQLBindCol**、 **SQLBindParameter**、および**SQLGetData**; と**SQLColumns**、 **SQLGetTypeInfo**、 **SQLProcedureColumns**、 **SQLStatistics**、および**SQLSpecialColumns**します。  
  
 次の表では、ODBC 3 *.x*ドライバー マネージャーは、日付、時刻、およびタイムスタンプ C データ型の入力のマッピングを実行します、 *TargetType*の引数**SQLBindCol**と**SQLGetData**または、 *ValueType*の引数**SQLBindParameter**します。  
  
|データ型<br /><br /> 入力されたコード|2.*x*するアプリ<br /><br /> 2.*x*ドライバー|2.*x*するアプリ<br /><br /> 3.*x*ドライバー|3.*x*するアプリ<br /><br /> 2.*x*ドライバー|3.*x*するアプリ<br /><br /> 3.*x*ドライバー|  
|--------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|  
|SQL_C_DATE (9)|マッピングなし|SQL_C_TYPE_DATE (91)|[1] にマッピングなし|SQL_C_TYPE_DATE (91)|  
|SQL_C_TYPE_DATE (91)|(DM) からのエラー|(DM) からのエラー|SQL_C_DATE (9)|[2] にマッピングなし|  
|SQL_C_TIME (10)|マッピングなし|SQL_C_TYPE_TIME (92)|[1] にマッピングなし|SQL_C_TYPE_TIME (92)|  
|SQL_C_TYPE_TIME (92)|(DM) からのエラー|(DM) からのエラー|SQL_C_TIME (10)|[2] にマッピングなし|  
|SQL_C_TIMESTAMP (11)|マッピングなし|SQL_C_TYPE_TIMESTAMP (93)|[1] にマッピングなし|SQL_C_TYPE_TIMESTAMP (93)|  
|SQL_C_TYPE_TIMESTAMP (93)|(DM) からのエラー|(DM) からのエラー|SQL_C_TIMESTAMP (11)|[2] にマッピングなし|  
  
 [1] の結果としてこれで、ODBC 3。*x* ODBC 2 を使用するアプリケーション *。x*ドライバーは、カタログ関数によって返される結果セットに返される日付、時刻、またはタイムスタンプのコードを使用できます。  
  
 [2] の結果としてこれで、ODBC 3。*x*アプリケーションは、ODBC 3 の操作します *。x*ドライバーは、カタログ関数によって返される結果セットに返される日付、時刻、またはタイムスタンプのコードを使用できます。  
  
 次の表では、ODBC 3 *.x*ドライバー マネージャーに入力された日付、時刻、およびタイムスタンプ SQL データの型のマッピングを実行する、 *ParameterType*の引数**SQLBindParameter**または、 *DataType*の引数**SQLGetTypeInfo**します。  
  
|データ型<br /><br /> 入力されたコード|2.*x*するアプリ<br /><br /> 2.*x*ドライバー|2.*x*するアプリ<br /><br /> 3.*x*ドライバー|3.*x*するアプリ<br /><br /> 2.*x*ドライバー|3.*x*するアプリ<br /><br /> 3.*x*ドライバー|  
|--------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|  
|SQL_DATE (9)|マッピングなし|SQL_TYPE_DATE (91)|[1] にマッピングなし|SQL_TYPE_DATE (91)|  
|SQL_TYPE_DATE (91)|(DM) からのエラー|(DM) からのエラー|SQL_DATE (9)|[2] にマッピングなし|  
|SQL_TIME (10)|マッピングなし|SQL_TYPE_TIME (92)|[1] にマッピングなし|SQL_TYPE_TIME (92)|  
|SQL_TYPE_TIME (92)|(DM) からのエラー|(DM) からのエラー|SQL_TIME (10)|[2] にマッピングなし|  
|SQL_TIMESTAMP (11)|マッピングなし|SQL_TYPE_TIMESTAMP (93)|[1] にマッピングなし|SQL_TYPE_TIMESTAMP (93)|  
|SQL_TYPE_TIMESTAMP (93)|(DM) からのエラー|(DM) からのエラー|SQL_TIMESTAMP (11)|[2] にマッピングなし|  
  
 [1] の結果としてこれで、ODBC 3。*x* ODBC 2 を使用するアプリケーション *。x*ドライバーは、カタログ関数によって返される結果セットに返される日付、時刻、またはタイムスタンプのコードを使用できます。  
  
 [2] の結果としてこれで、ODBC 3。*x*アプリケーションは、ODBC 3 の操作します *。x*ドライバーは、カタログ関数によって返される結果セットに返される日付、時刻、またはタイムスタンプのコードを使用できます。
