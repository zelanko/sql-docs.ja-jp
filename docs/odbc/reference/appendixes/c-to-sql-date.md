---
title: "C から SQL へ: 日付 |Microsoft ドキュメント"
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
- date data type [ODBC]
- converting data from c to SQL types [ODBC], date
- data conversions from C to SQL types [ODBC], date
ms.assetid: bea087d3-911f-418b-b483-d2b5b334da19
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e5806fe1dcdbabbc27e25c0387f2d06ea25f64ee
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="c-to-sql-date"></a>C から SQL へ: 日付
日付の ODBC C データ型の識別子です。  
  
 SQL_C_TYPE_DATE  
  
 次の表は、ODBC SQL データ型の C データの日付を変換する場合がありますを示します。 列とテーブルの用語の詳細については、次を参照してください。[に変換するデータを C から SQL データ型を](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)です。  
  
|SQL 型の識別子|テスト|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|列のバイト長 > 10 を =<br /><br /> 列のバイトの長さ < 10<br /><br /> データ値が有効な日付ではありません。|n/a<br /><br /> 22001<br /><br /> 22008|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|列の文字の長さ > 10 を =<br /><br /> 列の文字の長さ < 10<br /><br /> データ値が有効な日付ではありません。|n/a<br /><br /> 22001<br /><br /> 22008|  
|SQL_TYPE_DATE|データの値が有効な日付<br /><br /> データ値が有効な日付ではありません。|n/a<br /><br /> 22007|  
|SQL_TYPE_TIMESTAMP|データの値が有効な日付 [a]<br /><br /> データ値が有効な日付ではありません。|n/a<br /><br /> 22007|  
  
 [a] のタイムスタンプの時刻部分は 0 に設定します。  
  
 SQL_C_TYPE_DATE 構造で有効な値については、次を参照してください。 [C データ型](../../../odbc/reference/appendixes/c-data-types.md)、前述の「します。  
  
 C の日付データが文字 SQL データに変換されると、結果の文字データは、"*yyyy*-*mm*-*dd*"の形式です。  
  
 ドライバーは、日付 C データ型からデータを変換するときに長さ/インジケーター値を無視し、データ バッファーのサイズが、日付 C データ型のサイズであると見なされます。 長さ/インジケーター値に渡されます、 *StrLen_or_Ind*引数**SQLPutData**とで指定したバッファー内の*StrLen_or_IndPtr* で引数**SQLBindParameter**です。 データ バッファーを指定した、 *DataPtr*引数**SQLPutData**と*ParameterValuePtr*引数**SQLBindParameter**.

