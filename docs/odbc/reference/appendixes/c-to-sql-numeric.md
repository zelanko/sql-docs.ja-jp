---
title: "C から SQL へ: Numeric |Microsoft ドキュメント"
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
- numeric data type [ODBC], converting
- data conversions from C to SQL types [ODBC], numeric
- converting data from c to SQL types [ODBC], numeric
ms.assetid: af4095ff-06c3-4b04-83bf-19f9ee098dc2
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2cbdbbd3da828d5a995dbd9bff9c6b95aed1420a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="c-to-sql-numeric"></a>C から SQL へ: 数値
数値の ODBC C データ型の識別子は次のとおりです。  
  
 SQL_C_STINYINT  
  
 SQL_C_SLONG  
  
 SQL_C_UTINYINT  
  
 SQL_C_ULONG  
  
 SQL_C_TINYINT  
  
 SQL_C_LONG  
  
 SQL_C_SSHORT  
  
 SQL_C_FLOAT  
  
 SQL_C_USHORT  
  
 SQL_C_DOUBLE  
  
 SQL_C_SHORT  
  
 SQL_C_NUMERIC  
  
 SQL_C_SBIGINT  
  
 SQL_C_UBIGINT  
  
 次の表は、ODBC SQL データ型の数値の C データを変換することがありますを示します。 列とテーブルの用語の詳細については、次を参照してください。[に変換するデータを C から SQL データ型を](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)です。  
  
|SQL 型の識別子|テスト|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|数字の数 < バイト長の列を =<br /><br /> 数字の数 > 列のバイト長|n/a<br /><br /> 22001|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|文字の数 < 列の文字の長さを =<br /><br /> 文字の数 > 列の文字の長さ|n/a<br /><br /> 22001|  
|SQL_DECIMAL [b]<br /><br /> SQL_NUMERIC [b]<br /><br /> SQL_TINYINT [b]<br /><br /> SQL_SMALLINT [b]<br /><br /> SQL_INTEGER [b]<br /><br /> SQL_BIGINT [b]|データが切り詰めなしの変換または使用すると桁の小数部の切り捨て<br /><br /> データ全体の桁数の切り捨てと変換|n/a<br /><br /> 22003|  
|SQL_REAL<br /><br /> SQL_FLOAT<br /><br /> SQL_DOUBLE|データが数の変換先のデータ型の範囲内<br /><br /> データが数の変換先のデータ型の範囲外です。|n/a<br /><br /> 22003|  
|SQL_BIT|データが 0 または 1 です。<br /><br /> データが 0 より大きく、2、未満と 1 に等しくないです。<br /><br /> データがより小さい 0 より大きいまたは 2 に等しい|n/a<br /><br /> 22001<br /><br /> 22003|  
|SQL_INTERVAL_YEAR [a]<br /><br /> SQL_INTERVAL_MONTH [a]<br /><br /> SQL_INTERVAL_DAY [a]<br /><br /> SQL_INTERVAL_HOUR [a]<br /><br /> SQL_INTERVAL_MINUTE [a]<br /><br /> SQL_INTERVAL_SECOND [a]|データは切り捨てられません。<br /><br /> データが切り捨てられました。|n/a<br /><br /> 22015|  
  
 [a] (SQL_C_STINYINT、SQL_C_UTINYINT、SQL_C_SSHORT、SQL_C_USHORT、SQL_C_SLONG、SQL_C_ULONG、または SQL_C_NUMERIC) 真数値データ型に対してのみこれらの変換がサポートされます。 概数データ型 (SQL_C_FLOAT または SQL_C_DOUBLE) に対してはサポートされません。 真数 C データ型は、間隔の期間の有効桁数が 1 つのフィールドではありません SQL 型に変換できません。  
  
 [b]"n/a"場合は、ドライバーが必要に応じてを返す SQL_SUCCESS_WITH_INFO と 01S07 小数部の切り捨てがある場合にです。  
  
 ドライバーは、数値の C データ型からデータを変換するときに長さ/インジケーター値を無視し、データ バッファーのサイズが数値の C データ型のサイズであると見なされます。 長さ/インジケーター値に渡されます、 *StrLen_or_Ind*引数**SQLPutData**とで指定したバッファー内の*StrLen_or_IndPtr* で引数**SQLBindParameter**です。 データ バッファーを指定した、 *DataPtr*引数**SQLPutData**と*ParameterValuePtr*引数**SQLBindParameter**.

