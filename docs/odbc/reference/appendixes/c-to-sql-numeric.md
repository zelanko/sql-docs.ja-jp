---
title: 'C から SQL: 数値 |マイクロソフトドキュメント'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- numeric data type [ODBC], converting
- data conversions from C to SQL types [ODBC], numeric
- converting data from c to SQL types [ODBC], numeric
ms.assetid: af4095ff-06c3-4b04-83bf-19f9ee098dc2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bbc0a994ef95f2deca29c8a4cbb06f3167b0433f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304733"
---
# <a name="c-to-sql-numeric"></a>C から SQL へ: 数値
数値 ODBC C データ型の識別子は次のとおりです。  
  
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
  
 次の表は、数値 C データの変換先となる ODBC SQL データ型を示しています。 表の列と用語の説明については、データを[C から SQL データ型に変換する](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)を参照してください。  
  
|SQL タイプ識別子|テスト|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|桁数 <= 列バイト長<br /><br /> 桁数 >列バイト長|該当なし<br /><br /> 22001|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|<文字数 = 列の文字数<br /><br /> 文字数 > 列の文字数|該当なし<br /><br /> 22001|  
|SQL_DECIMAL[b]<br /><br /> SQL_NUMERIC[b]<br /><br /> SQL_TINYINT[b]<br /><br /> SQL_SMALLINT[b]<br /><br /> SQL_INTEGER[b]<br /><br /> SQL_BIGINT[b]|切り捨てなしで、または小数部の桁数を切り捨てて変換されたデータ<br /><br /> 桁全体の切り捨てで変換されたデータ|該当なし<br /><br /> 22003|  
|SQL_REAL<br /><br /> SQL_FLOAT<br /><br /> SQL_DOUBLE|データが、数値の変換先のデータ型の範囲内にある<br /><br /> データが、数値の変換先のデータ型の範囲外です。|該当なし<br /><br /> 22003|  
|SQL_BIT|データは 0 または 1 です<br /><br /> データが 0 より大きく、2 より小さく、1 に等しくない<br /><br /> データが 0 未満か 2 以上です|該当なし<br /><br /> 22001<br /><br /> 22003|  
|SQL_INTERVAL_YEAR[a]<br /><br /> SQL_INTERVAL_MONTH[a]<br /><br /> SQL_INTERVAL_DAY[a]<br /><br /> SQL_INTERVAL_HOUR[a]<br /><br /> SQL_INTERVAL_MINUTE[a]<br /><br /> SQL_INTERVAL_SECOND[a]|切り捨てられていないデータ。<br /><br /> データが切り捨てられました。|該当なし<br /><br /> 22015|  
  
 [a] これらの変換は、正確な数値データ型 (SQL_C_STINYINT、SQL_C_UTINYINT、SQL_C_SSHORT、SQL_C_USHORT、SQL_C_SLONG、SQL_C_ULONG、またはSQL_C_NUMERIC) に対してのみサポートされます。 これらは、近似数値データ型 (SQL_C_FLOATまたはSQL_C_DOUBLE) ではサポートされません。 正確な数値 C データ型は、間隔精度が単一フィールドではない間隔 SQL 型に変換することはできません。  
  
 [b] "n/a" の場合、ドライバは、小数点以下の切り捨てがある場合に、オプションでSQL_SUCCESS_WITH_INFOと 01S07 を返す場合があります。  
  
 ドライバーは、数値 C データ型からデータを変換するときに長さ/インジケーター値を無視し、データ バッファーのサイズは数値 C データ型のサイズであると仮定します。 長さ/インジケーター値は **、SQLPutData**の*StrLen_or_Ind*引数と **、SQLBindParameter**の*StrLen_or_IndPtr*引数で指定されたバッファーに渡されます。 データ バッファーは **、SQLPutData**の*引数*と**SQLBindParameter**の*引数で指定*します。
