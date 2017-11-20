---
title: "Datetime データ型 |Microsoft ドキュメント"
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
- data types [ODBC], date
- backward compatibility [ODBC], datetime data types
- timestamp data type [ODBC]
- data types [ODBC], timestamp
- data types [ODBC], backward compatibility
- compatibility [ODBC], datetime data types
- data types [ODBC], time
ms.assetid: 6b9363c9-04bf-4492-a210-7aa15dea4af8
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 92ab5f52282fddf89c48bef73fa7817684ae3496
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="datetime-data-types"></a>Datetime データ型
ODBC 3*.x*、識別子、日付、時刻、および timestamp SQL データ型は SQL_DATE、SQL_TIME、および SQL_TIMESTAMP から変更された (のインスタンスと**#define** 9、10、および 11 のヘッダー ファイルで) に sql _TYPE_DATE、SQL_TYPE_TIME、および SQL_TYPE_TIMESTAMP (のインスタンスと**#define** 91、92、および 93 のヘッダー ファイルで)、それぞれします。 識別子から変更された SQL_C_DATE、SQL_C_TIME、および SQL_C_TIMESTAMP SQL_C_TYPE_DATE、SQL_C_TYPE_TIME、SQL_C_TYPE_TIMESTAMP、それぞれ、対応する C 型のインスタンスとインスタンス**#define**が変更されましたそれに従っています。  
  
 ODBC 3 での SQL の datetime データ型に対して返される列のサイズおよび小数点以下桁数*.x* ODBC 2 でそれらに対して返される有効桁数と小数点以下桁数と同じです*。x*です。 これらの値は、SQL_DESC_PRECISION および SQL_DESC_SCALE 記述子フィールドの値と異なります。 (詳細については、次を参照してください[列のサイズ、小数点以下桁数、転送オクテット長さ、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)付録 d: データ型にします。)。  
  
 これらの変更に影響を与える**SQLDescribeCol**、 **SQLDescribeParam**、および**SQLColAttributes**です。**SQLBindCol**、 **SQLBindParameter**、および**SQLGetData**; と**SQLColumns**、 **SQLGetTypeInfo**、 **SQLProcedureColumns**、 **SQLStatistics**、および**SQLSpecialColumns**です。  
  
 ODBC 3*.x*ドライバーがまた環境属性の設定に従って、前の段落に表示されている関数の呼び出しを処理します。 **SQLColumns**、 **SQLGetTypeInfo**、 **SQLProcedureColumns**、 **SQLSpecialColumns**、および**SQLStatistics**またに設定されている SQL_OV_ODBC3、関数の戻り値 SQL_TYPE_DATE、SQL_TYPE_TIME、および SQL_TYPE_TIMESTAMP DATA_TYPE フィールドの場合は、します。 COLUMN_SIZE 列 (によって返される結果セットに**SQLColumns**、 **SQLGetTypeInfo**、 **SQLProcedureColumns**、および**SQLSpecialColumns**)概数の数値型のバイナリ有効桁数が含まれています。 NUM_PREC_RADIX 列 (によって返される結果セットに**SQLColumns**、 **SQLGetTypeInfo**、および**SQLProcedureColumns**) 2 の値が含まれています。 またに設定されている SQL_OV_ODBC2、その関数は、戻り値の場合は SQL_DATE、SQL_TIME、および SQL_TIMESTAMP DATA_TYPE フィールドに場合、COLUMN_SIZE 列に概数の数値型と NUM_PREC_RADIX 列の小数点以下有効桁数が含まれます10 の値が含まれています。  
  
 呼び出しですべてのデータ型を要求するときに**SQLGetTypeInfo**、関数によって返される結果セットが格納されます両方 SQL_TYPE_DATE、SQL_TYPE_TIME、および SQL_TYPE_TIMESTAMP ODBC 3 で定義されている*.x*、SQL_DATE、SQL_TIME、および SQL_TIMESTAMP ODBC 2 で定義されています。*x*です。  
  
 方法により、ODBC 3*.x*ドライバー マネージャーが、日付、時刻、および timestamp データ型、ODBC 3 のマッピングを実行*.x*だけ必要なドライバーが認識**#defines** 91 の 92、および入力した日付、時刻、および timestamp C データ型の 93、 *TargetType*の引数**SQLBindCol**と**SQLGetData**または*ValueType*の引数**SQLBindParameter**、必要なだけが認識と**#defines** 91 92、93 の日付、時間、および timestamp SQL データ型が、で入力*ParameterType*の引数**SQLBindParameter**または*DataType*の引数**SQLGetTypeInfo**です。 詳細については、次を参照してください。 [Datetime データ型の変更](../../../odbc/reference/develop-app/datetime-data-type-changes.md)です。

