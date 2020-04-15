---
title: 'C から SQL: 年と月の間隔 |マイクロソフトドキュメント'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from c to SQL types [ODBC], year-month intervals
- intervals [ODBC], converting
- year-month intervals [ODBC]
- data conversions from C to SQL types [ODBC], year-month intervals
ms.assetid: a0eb7b55-9db0-4375-9210-bddec4593880
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2ec7bfda0015883c8470dd453c7ae5de9bfd6cec
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306613"
---
# <a name="c-to-sql-year-month-intervals"></a>C から SQL へ: 年月の間隔
年と月の間隔 ODBC C データ型の識別子は次のとおりです。  
  
 SQL_C_INTERVAL_MONTH SQL_C_INTERVAL_YEAR SQL_C_INTERVAL_YEAR_TO_MONTH  
  
 次の表は、年と月の間隔 C データを変換できる ODBC SQL データ型を示しています。 表の列と用語の説明については、データを[C から SQL データ型に変換する](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)を参照してください。  
  
|SQL タイプ識別子|テスト|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR[a]<br /><br /> SQL_VARCHAR[a]<br /><br /> SQL_LONGVARCHAR[a]|列バイト長>= 文字バイト長<br /><br /> 列バイト長<文字バイト長[a]<br /><br /> データ値が有効な間隔リテラルではありません|該当なし<br /><br /> 22001<br /><br /> 22015|  
|SQL_WCHAR[a]<br /><br /> SQL_WVARCHAR[a]<br /><br /> SQL_WLONGVARCHAR[a]|列文字の長さ >= データの文字長<br /><br /> 列の文字長<データの文字長[a]<br /><br /> データ値が有効な間隔リテラルではありません|該当なし<br /><br /> 22001<br /><br /> 22015|  
|SQL_TINYINT[b]<br /><br /> SQL_SMALLINT[b]<br /><br /> SQL_INTEGER[b]<br /><br /> SQL_BIGINT[b]<br /><br /> SQL_NUMERIC[b]<br /><br /> SQL_DECIMAL[b]|単一フィールド間隔の変換では、桁全体の切り捨てが発生しませんでした。<br /><br /> 変換の結果、桁全体が切り捨てられた|該当なし<br /><br /> 22003|  
|SQL_INTERVAL_MONTH<br /><br /> SQL_INTERVAL_YEAR<br /><br /> SQL_INTERVAL_YEAR_TO_MONTH|データ値は、フィールドを切り捨てずに変換されました。<br /><br /> 変換中にデータ値の 1 つ以上のフィールドが切り捨てられました|該当なし<br /><br /> 22015|  
  
 [a] すべての C 間隔データ型は、文字データ型に変換できます。  
  
 [b] 間隔構造のタイプフィールドが単一のフィールド (SQL_YEARまたはSQL_MONTH) である場合、間隔 C 型は任意の正確な数値 (SQL_TINYINT、SQL_SMALLINT、SQL_INTEGER、SQL_BIGINT、SQL_DECIMAL、またはSQL_NUMERIC) に変換できます。  
  
 間隔 C 型の既定の変換は、対応する年月間隔 SQL 型です。  
  
 ドライバーは、間隔 C のデータ型からデータを変換するときに長さ/インジケーター値を無視し、データ バッファーのサイズは、間隔 C データ型のサイズであると仮定します。 長さ/インジケーター値は **、SQLPutData**の*StrLen_or_Ind*引数と **、SQLBindParameter**の*StrLen_or_IndPtr*引数で指定されたバッファーに渡されます。 データ バッファーは **、SQLPutData**の*引数*と**SQLBindParameter**の*引数で指定*します。
