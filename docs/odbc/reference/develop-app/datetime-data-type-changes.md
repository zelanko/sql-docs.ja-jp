---
title: 日時データ型の変更 |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4f186047dd31aa2c4b66ec1ce73c8cb9fae31c04
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304645"
---
# <a name="datetime-data-type-changes"></a>datetime データ型の変更
ODBC *3.x*では、日付、時刻、およびタイムスタンプの SQL データ型の識別子が、SQL_DATE、SQL_TIME、および SQL_TIMESTAMP (ヘッダー ファイルに **#define**のインスタンスが 9、10、および 11) から SQL_TYPE_DATE、SQL_TYPE_TIME、および SQL_TYPE_TIMESTAMP (ヘッダー ファイルの 91、92、および 93 の **#define**のインスタンス) にそれぞれ変更されています。 対応する C 型の識別子は、SQL_C_DATE、SQL_C_TIME、およびSQL_C_TIMESTAMPからSQL_C_TYPE_DATE、SQL_C_TYPE_TIME、およびSQL_C_TYPE_TIMESTAMPにそれぞれ変更されました。  
  
 ODBC *3.x*の SQL の日付時刻データ型に対して返される列サイズと小数点以下の桁数は、ODBC *2.x*で返される精度と小数点以下の桁数と同じです。 これらの値は、SQL_DESC_PRECISIONおよびSQL_DESC_SCALE記述子フィールドの値とは異なります。 (詳細については、「[列サイズ、10 進数、オクテットの長さの転送、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)」を参照してください。  
  
 これらの変更は **、SQLDescribeCol** **、SQLDescribe パラム**、および**SQLCol 属性**に影響を与えます。**、****および SQL バインドパラメーター**、および**SQLGet データを実行します**。および**SQLColumns** **、SQLGetTypeInfo** **、SQL プロシージャ列****、SQL 統計**、および**SQL 特殊列 。**  
  
 次の表は、ODBC *3.x*ドライバー マネージャーが **、SQLBindCol**および**SQLGetData**の*TargetType*引数、または**SQLBindParameter**の*値*型引数に入力された日付、時刻、およびタイムスタンプ C のデータ型のマッピングを実行する方法を示しています。  
  
|データ型<br /><br /> コードが入力されました|*2.x*アプリに<br /><br /> *2.x*ドライバ|*2.x*アプリに<br /><br /> *3.x*ドライバ|*3.x*アプリに<br /><br /> *2.x*ドライバ|*3.x*アプリに<br /><br /> *3.x*ドライバ|  
|--------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|  
|SQL_C_DATE (9)|マッピングなし|SQL_C_TYPE_DATE (91)|マッピングなし[1]|SQL_C_TYPE_DATE (91)|  
|SQL_C_TYPE_DATE (91)|エラー (DM から)|エラー (DM から)|SQL_C_DATE (9)|マッピングなし[2]|  
|SQL_C_TIME (10)|マッピングなし|SQL_C_TYPE_TIME (92)|マッピングなし[1]|SQL_C_TYPE_TIME (92)|  
|SQL_C_TYPE_TIME (92)|エラー (DM から)|エラー (DM から)|SQL_C_TIME (10)|マッピングなし[2]|  
|SQL_C_TIMESTAMP (11)|マッピングなし|SQL_C_TYPE_TIMESTAMP (93)|マッピングなし[1]|SQL_C_TYPE_TIMESTAMP (93)|  
|SQL_C_TYPE_TIMESTAMP (93)|エラー (DM から)|エラー (DM から)|SQL_C_TIMESTAMP (11)|マッピングなし[2]|  
  
 [1] この結果、ODBC *2.x*ドライバを使用する ODBC *3.x*アプリケーションは、カタログ関数によって返される結果セットに返される日付、時刻、またはタイムスタンプ コードを使用できます。  
  
 [2] この結果、ODBC *3.x*ドライバを使用する ODBC *3.x*アプリケーションは、カタログ関数によって返される結果セットに返される日付、時刻、またはタイムスタンプ コードを使用できます。  
  
 次の表は、ODBC *3.x*ドライバー マネージャーが **、SQLBindParameter**の*パラメーター型*引数または**SQLGetTypeInfo**の*データ型*引数に入力された日付、時刻、およびタイムスタンプの SQL データ型のマッピングを実行する方法を示しています。  
  
|データ型<br /><br /> コードが入力されました|*2.x*アプリに<br /><br /> *2.x*ドライバ|*2.x*アプリに<br /><br /> *3.x*ドライバ|*3.x*アプリに<br /><br /> *2.x*ドライバ|*3.x*アプリに<br /><br /> *3.x*ドライバ|  
|--------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|  
|SQL_DATE (9)|マッピングなし|SQL_TYPE_DATE (91)|マッピングなし[1]|SQL_TYPE_DATE (91)|  
|SQL_TYPE_DATE (91)|エラー (DM から)|エラー (DM から)|SQL_DATE (9)|マッピングなし[2]|  
|SQL_TIME (10)|マッピングなし|SQL_TYPE_TIME (92)|マッピングなし[1]|SQL_TYPE_TIME (92)|  
|SQL_TYPE_TIME (92)|エラー (DM から)|エラー (DM から)|SQL_TIME (10)|マッピングなし[2]|  
|SQL_TIMESTAMP (11)|マッピングなし|SQL_TYPE_TIMESTAMP (93)|マッピングなし[1]|SQL_TYPE_TIMESTAMP (93)|  
|SQL_TYPE_TIMESTAMP (93)|エラー (DM から)|エラー (DM から)|SQL_TIMESTAMP (11)|マッピングなし[2]|  
  
 [1] この結果、ODBC *2.x*ドライバを使用する ODBC *3.x*アプリケーションは、カタログ関数によって返される結果セットに返される日付、時刻、またはタイムスタンプ コードを使用できます。  
  
 [2] この結果、ODBC *3.x*ドライバを使用する ODBC *3.x*アプリケーションは、カタログ関数によって返される結果セットに返される日付、時刻、またはタイムスタンプ コードを使用できます。
