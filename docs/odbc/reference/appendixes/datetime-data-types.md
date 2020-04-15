---
title: 日時データ型 |マイクロソフトドキュメント
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
- data types [ODBC], date
- backward compatibility [ODBC], datetime data types
- timestamp data type [ODBC]
- data types [ODBC], timestamp
- data types [ODBC], backward compatibility
- compatibility [ODBC], datetime data types
- data types [ODBC], time
ms.assetid: 6b9363c9-04bf-4492-a210-7aa15dea4af8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 10626c4f0bf2e33c70322a0eb49af6c3e01e4303
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307063"
---
# <a name="datetime-data-types"></a>Datetime データ型
ODBC *3.x*では、日付、時刻、およびタイムスタンプの SQL データ型の識別子が、SQL_DATE、SQL_TIME、および SQL_TIMESTAMP (ヘッダー ファイルに **#define**のインスタンスが 9、10、および 11) から SQL_TYPE_DATE、SQL_TYPE_TIME、および SQL_TYPE_TIMESTAMP (ヘッダー ファイルの 91、92、および 93 の **#define**のインスタンス) にそれぞれ変更されています。 対応する C 型の識別子は、SQL_C_DATE、SQL_C_TIME、およびSQL_C_TIMESTAMPからSQL_C_TYPE_DATE、SQL_C_TYPE_TIME、およびSQL_C_TYPE_TIMESTAMPにそれぞれ変更され、それに応じて **#define**のインスタンスが変更されました。  
  
 ODBC *3.x*の SQL の日付時刻データ型に対して返される列サイズと小数点以下の桁数は、ODBC *2.x*で返される精度と小数点以下の桁数と同じです。 これらの値は、SQL_DESC_PRECISIONおよびSQL_DESC_SCALE記述子フィールドの値とは異なります。 (詳細については、「付録 D: データ型」の[「列サイズ、10 進数、転送オクテットの長さ、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)」を参照してください。  
  
 これらの変更は **、SQLDescribeCol** **、SQLDescribe パラム**、および**SQLCol 属性**に影響を与えます。**、****および SQL バインドパラメーター**、および**SQLGet データを実行します**。および**SQLColumns** **、SQLGetTypeInfo** **、SQL プロシージャ列****、SQL 統計**、および**SQL 特殊列 。**  
  
 ODBC *3.x*ドライバは、SQL_ATTR_ODBC_VERSION環境属性の設定に従って、前の段落に示した関数呼び出しを処理します。 **SQLColumns** **、SQLGetTypeInfo** **、SQLProcedureColumns** **、SQLSpecialColumns**、および**SQLStatistics**の場合、SQL_ATTR_ODBC_VERSIONがSQL_OV_ODBC3に設定されている場合、関数はDATA_TYPEフィールドにSQL_TYPE_DATE、SQL_TYPE_TIME、およびSQL_TYPE_TIMESTAMPを返します。 COLUMN_SIZE列 ( **SQLColumns**、 **SQLGetTypeInfo**、 **SQLProcedureColumns**、および**SQLSpecialColumns**によって返される結果セット内 ) には、概数値型のバイナリ精度が含まれています。 NUM_PREC_RADIX列 ( **SQLColumns**、 **SQLGetTypeInfo**、および**SQL プロシージャ列**によって返される結果セット内 ) には、2 の値が含まれています。 SQL_ATTR_ODBC_VERSIONが SQL_OV_ODBC2 に設定されている場合、DATA_TYPE フィールドにSQL_DATE、SQL_TIME、およびSQL_TIMESTAMPが返され、COLUMN_SIZE列には近似数値型の 10 進数が含まれ、NUM_PREC_RADIX列の値は 10 になります。  
  
 **SQLGetTypeInfo**の呼び出しですべてのデータ型が要求されると、関数によって返される結果セットには、ODBC *3.x*で定義されているSQL_TYPE_DATE、SQL_TYPE_TIME、およびSQL_TYPE_TIMESTAMP、および ODBC *2.x*で定義されているSQL_DATE、SQL_TIME、およびSQL_TIMESTAMPの両方が含まれます。  
  
 ODBC *3.x*ドライバ マネージャが日付、時刻のマッピングを実行する方法により、 タイムスタンプ データ型*DataType*の ODBC *3.x*ドライバは **、SQLBindCol**および**SQLGetData**の TargetType 引数または**SQLBindParameter**の**SQLBindParameter***ValueType*引数に入力された日付、*ValueType*時刻、およびタイムスタンプ C のデータ型に対して 91、92、および**タイムスタンプの**93 の **#defines**を認識するだけで、SQLBindDataType の*引数*に入力された日付、時刻、およびタイムスタンプの SQL データ型の **#defines**だけを認識する必要があります。 詳細については、「[日時データ型の変更](../../../odbc/reference/develop-app/datetime-data-type-changes.md)」を参照してください。
