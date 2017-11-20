---
title: "Datetime データ型の変更 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- time data type [ODBC]
- datetime data types [ODBC]
- date data type [ODBC]
- backward compatibility [ODBC], datetime data types
- timestamp data type [ODBC]
- compatibility [ODBC], datetime data types
ms.assetid: c38c79f9-8bb0-4633-ac86-542366c09a95
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b09a6daa19b7a8b22ac5f4b3147e6cefde6ffc60
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="datetime-data-type-changes"></a>Datetime データ型の変更
ODBC 3 です。*x*、識別子、日付、時刻、および timestamp SQL データ型は SQL_DATE、SQL_TIME、および SQL_TIMESTAMP から変更された (のインスタンスと**#define** 9、10、および 11 のヘッダー ファイルで)、SQL_TYPE_DATE にSQL_TYPE_TIME、および SQL_TYPE_TIMESTAMP (のインスタンスと**#define** 91、92、および 93 のヘッダー ファイルで)、それぞれします。 対応する C 型識別子から変更された SQL_C_DATE、SQL_C_TIME、および SQL_C_TIMESTAMP SQL_C_TYPE_DATE、SQL_C_TYPE_TIME、SQL_C_TYPE_TIMESTAMP、それぞれします。  
  
 列のサイズと ODBC 3 での SQL の datetime データ型に対して返される小数点以下桁数です。*x* ODBC 2 でそれらに対して返される有効桁数と小数点以下桁数と同じです*。x*です。 これらの値は、SQL_DESC_PRECISION および SQL_DESC_SCALE 記述子フィールドの値と異なります。 (詳細については、次を参照してください[列のサイズ、小数点以下桁数、転送オクテット長さ、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)。)。  
  
 これらの変更に影響を与える**SQLDescribeCol**、 **SQLDescribeParam**、および**SQLColAttribute**です。**SQLBindCol**、 **SQLBindParameter**、および**SQLGetData**; と**SQLColumns**、 **SQLGetTypeInfo**、 **SQLProcedureColumns**、 **SQLStatistics**、および**SQLSpecialColumns**です。  
  
 次の表にどのように ODBC 3*.x*ドライバー マネージャーが、日付、時刻、およびタイムスタンプ C データ型の入力のマッピングを実行、 *TargetType*の引数**SQLBindCol**と**SQLGetData**または、 *ValueType*の引数**SQLBindParameter**です。  
  
|データ型<br /><br /> 入力されたコード|2.*x*するアプリ<br /><br /> 2.*x*ドライバー|2.*x*するアプリ<br /><br /> 3.*x*ドライバー|3.*x*するアプリ<br /><br /> 2.*x*ドライバー|3.*x*するアプリ<br /><br /> 3.*x*ドライバー|  
|--------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|  
|SQL_C_DATE (9)|マッピングなし|SQL_C_TYPE_DATE (91)|マッピングなし [1]|SQL_C_TYPE_DATE (91)|  
|SQL_C_TYPE_DATE (91)|(DM) からのエラー|(DM) からのエラー|SQL_C_DATE (9)|[2] をマッピングなし|  
|SQL_C_TIME (10)|マッピングなし|SQL_C_TYPE_TIME (92)|マッピングなし [1]|SQL_C_TYPE_TIME (92)|  
|SQL_C_TYPE_TIME (92)|(DM) からのエラー|(DM) からのエラー|SQL_C_TIME (10)|[2] をマッピングなし|  
|SQL_C_TIMESTAMP (11)|マッピングなし|SQL_C_TYPE_TIMESTAMP (93)|マッピングなし [1]|SQL_C_TYPE_TIMESTAMP (93)|  
|SQL_C_TYPE_TIMESTAMP (93)|(DM) からのエラー|(DM) からのエラー|SQL_C_TIMESTAMP (11)|[2] をマッピングなし|  
  
 [1] の結果としてこの、ODBC 3。*x* ODBC 2 を使用するアプリケーション*。x*ドライバーは、カタログ関数によって返される結果セットに返される日付、時刻、またはタイムスタンプのコードを使用できます。  
  
 [2] の結果としてこの、ODBC 3。*x* ODBC 3 を使用するアプリケーション*。x*ドライバーは、カタログ関数によって返される結果セットに返される日付、時刻、またはタイムスタンプのコードを使用できます。  
  
 次の表にどのように ODBC 3*.x*ドライバー マネージャーに入力された日付、時刻、およびタイムスタンプ SQL データの型のマッピングを実行する、 *ParameterType*の引数**SQLBindParameter**または、 *DataType*の引数**SQLGetTypeInfo**です。  
  
|データ型<br /><br /> 入力されたコード|2.*x*するアプリ<br /><br /> 2.*x*ドライバー|2.*x*するアプリ<br /><br /> 3.*x*ドライバー|3.*x*するアプリ<br /><br /> 2.*x*ドライバー|3.*x*するアプリ<br /><br /> 3.*x*ドライバー|  
|--------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|  
|SQL_DATE (9)|マッピングなし|SQL_TYPE_DATE (91)|マッピングなし [1]|SQL_TYPE_DATE (91)|  
|SQL_TYPE_DATE (91)|(DM) からのエラー|(DM) からのエラー|SQL_DATE (9)|[2] をマッピングなし|  
|SQL_TIME (10)|マッピングなし|SQL_TYPE_TIME (92)|マッピングなし [1]|SQL_TYPE_TIME (92)|  
|SQL_TYPE_TIME (92)|(DM) からのエラー|(DM) からのエラー|SQL_TIME (10)|[2] をマッピングなし|  
|SQL_TIMESTAMP (11)|マッピングなし|SQL_TYPE_TIMESTAMP (93)|マッピングなし [1]|SQL_TYPE_TIMESTAMP (93)|  
|SQL_TYPE_TIMESTAMP (93)|(DM) からのエラー|(DM) からのエラー|SQL_TIMESTAMP (11)|[2] をマッピングなし|  
  
 [1] の結果としてこの、ODBC 3。*x* ODBC 2 を使用するアプリケーション*。x*ドライバーは、カタログ関数によって返される結果セットに返される日付、時刻、またはタイムスタンプのコードを使用できます。  
  
 [2] の結果としてこの、ODBC 3。*x* ODBC 3 を使用するアプリケーション*。x*ドライバーは、カタログ関数によって返される結果セットに返される日付、時刻、またはタイムスタンプのコードを使用できます。

