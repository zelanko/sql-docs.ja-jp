---
title: "C から SQL へ: 時間 |Microsoft ドキュメント"
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
- data conversions from C to SQL types [ODBC], time
- time data type [ODBC]
- converting data from c to SQL types [ODBC], time
ms.assetid: a8da43c9-d9a5-45e5-bd9a-1dd633db2ee0
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6f1a59c15d2ebf1866d4543fa89662888154d4da
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="c-to-sql-time"></a>C から SQL へ: 時刻
時刻の ODBC C データ型の識別子です。  
  
 SQL_C_TYPE_TIME  
  
 次の表は、ODBC SQL データ型が time C データを変換することがありますを示します。 列とテーブルの用語の詳細については、次を参照してください。[に変換するデータを C から SQL データ型を](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)です。  
  
|SQL 型の識別子|テスト|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|列のバイト長 > = 8<br /><br /> 列のバイトの長さ < 8<br /><br /> データの値が有効な時刻|n/a<br /><br /> 22001<br /><br /> 22008|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|列の文字の長さ > = 8<br /><br /> 列の長さ < 8 を文字します。<br /><br /> データの値が有効な時刻|n/a<br /><br /> 22001<br /><br /> 22008|  
|SQL_TYPE_TIME|データの値が有効な時刻<br /><br /> データの値が有効な時刻|n/a<br /><br /> 22007|  
|SQL_TYPE_TIMESTAMP|データの値が有効な時刻 [a]<br /><br /> データの値が有効な時刻|n/a<br /><br /> 22007|  
  
 [a] のタイムスタンプの部分が、現在の日付およびタイムスタンプの部分が 0 に設定されている秒の小数部に設定されている日付です。  
  
 SQL_C_TYPE_TIME 構造で有効な値については、次を参照してください。 [C データ型](../../../odbc/reference/appendixes/c-data-types.md)、前述の「します。  
  
 C 時のデータが文字 SQL データに変換されると、結果の文字データは、"*hh*:*mm*:*ss*"の形式です。  
  
 ドライバーは、C データ型であり、データ バッファーのサイズが時間 C データ型のサイズであると見なされますの時刻からデータを変換するときに、長さ/インジケーターの値を無視します。 長さ/インジケーター値に渡されます、 *StrLen_or_Ind*引数**SQLPutData**とで指定したバッファー内の*StrLen_or_IndPtr* で引数**SQLBindParameter**です。 データ バッファーを指定した、 *DataPtr*引数**SQLPutData**と*ParameterValuePtr*引数**SQLBindParameter**.

