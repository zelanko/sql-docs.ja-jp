---
title: Datetime データ型 |Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1cb92afa9467717b8a589ddbcaee4ab8a5a529f6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68130091"
---
# <a name="datetime-data-types"></a>Datetime データ型
*ODBC 3.x では、日付*、時刻、およびタイムスタンプの SQL データ型の識別子が、SQL_DATE、SQL_TIME、および SQL_TIMESTAMP (ヘッダーファイル (9、10、および11の **#define**インスタンス) から SQL_TYPE_DATE、SQL_TYPE_TIME、および SQL_TYPE_TIMESTAMP (ヘッダーファイル91、92、93 **) に**それぞれ変更されました。 対応する C 型識別子が SQL_C_DATE、SQL_C_TIME、および SQL_C_TIMESTAMP からそれぞれ SQL_C_TYPE_DATE、SQL_C_TYPE_TIME、および SQL_C_TYPE_TIMESTAMP に変更され、 **#define**のインスタンスがそれに応じて変更されています。  
  
 *Odbc 3.x*の SQL datetime データ型に対して返される列サイズと10進桁数は、odbc 2.x で返される有効桁数および小数点以下桁数と*同じです。* これらの値は、SQL_DESC_PRECISION および SQL_DESC_SCALE の記述子フィールドの値とは異なります。 (詳細については、「付録 D: データ型」の「[列のサイズ、10進数、転送オクテットの長さ、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)」を参照してください)。  
  
 これらの変更は、 **SQLDescribeCol**、 **SQLDescribeParam**、および**sqlcolattributes**に影響します。**SQLBindCol**、 **SQLBindParameter**、および**SQLGetData**;および**Sqlcolumns**、 **SQLGetTypeInfo**、 **SQLProcedureColumns**、 **sqlcolumns**、および**sqlcolumns 列**。  
  
 ODBC 3.x ドライバーは、SQL_ATTR_ODBC_VERSION 環境属性の設定に従って、前の段落に記載されている関数呼び出しを処理*します。* **Sqlcolumns**、 **SQLGetTypeInfo**、 **SQLProcedureColumns**、 **sqlcolumns columns**、および**sqlcolumns**の場合、SQL_ATTR_ODBC_VERSION が SQL_OV_ODBC3 に設定されていると、関数は SQL_TYPE_TIMESTAMP フィールドに SQL_TYPE_DATE、SQL_TYPE_TIME、および DATA_TYPE を返します。 COLUMN_SIZE 列 ( **Sqlcolumns**、 **SQLGetTypeInfo**、 **SQLProcedureColumns**、および**sqlcolumns columns**によって返される結果セット) には、概数型のバイナリ有効桁数が含まれています。 ( **Sqlcolumns**、 **SQLGetTypeInfo**、および**SQLProcedureColumns**によって返される結果セット内の) NUM_PREC_RADIX 列には、2という値が含まれています。 SQL_ATTR_ODBC_VERSION が SQL_OV_ODBC2 に設定されている場合、関数は SQL_TIMESTAMP フィールドに SQL_DATE、SQL_TIME、および DATA_TYPE を返します。 COLUMN_SIZE 列には、概数型の小数点以下桁数と NUM_PREC_RADIX 列が含まれます。の値が10です。  
  
 **SQLGetTypeInfo**の呼び出しですべてのデータ型が要求された場合、関数によって返される結果セットには *、odbc 3.x*で定義されている SQL_TYPE_DATE、SQL_TYPE_TIME、および SQL_TYPE_TIMESTAMP と、odbc 2.x で定義されている SQL_DATE、SQL_TIME、および SQL_TIMESTAMP の両方が含ま*れます。*  
  
 ODBC *3. x* Driver Manager が日付のマッピングを実行する方法によって、時刻、およびタイムスタンプデータ型では、 **SQLBindCol**と**SQLGetData**の*TargetType*引数に入力された日付、時刻、およびタイムスタンプの C データ型については、91、92、および93の **#defines**のみを*認識し、* SQLBindParameter の**ValueType** **引数**を*認識*している必要があります。また、は、92 91 #defines**SQLBindParameter**の*ParameterType*引数または**SQLGetTypeInfo**の*DataType*引数。 詳細については、「 [Datetime データ型の変更](../../../odbc/reference/develop-app/datetime-data-type-changes.md)」を参照してください。
