---
title: 'SQL から C: 文字 |マイクロソフトドキュメント'
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to C types [ODBC], character
- character data type [ODBC]
- data conversions from SQL to C types [ODBC], character
ms.assetid: 7fdb7f38-b64d-48f2-bcb4-1ca96b2bbdb6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3486c0fcf5cefc39c4b85af814d7d3c1d609b4e3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296672"
---
# <a name="sql-to-c-character"></a>SQL から C へ: 文字

文字 ODBC SQL データ型の識別子は次のとおりです。

- SQL_CHAR
- SQL_VARCHAR
- SQL_LONGVARCHAR
- SQL_WCHAR
- SQL_WVARCHAR
- SQL_WLONGVARCHAR

次の表は、文字 SQL データの変換先となる ODBC C データ型を示しています。 表の列と用語の説明については[、SQL から C データ型へのデータの変換を参照してください](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)。  

|C 型識別子|テスト|ターゲット値Ptr|StrLen_or_IndPtr|SQLSTATE|
|:----------------|:---|:-------------|:---------------|:-------|
|SQL_C_CHAR|データのバイト長 <*バッファ長*<br /><br /> データ長のバイト長>=*バッファ長*|Data<br /><br /> 切り捨てられたデータ|データの長さ (バイト単位)<br /><br /> データの長さ (バイト単位)|該当なし<br /><br /> 01004|  
|SQL_C_WCHAR|データの文字数 <*バッファ長*<br /><br /> データ>の文字数 =*バッファ長*|Data<br /><br /> 切り捨てられたデータ|文字でのデータの長さ<br /><br /> 文字でのデータの長さ|該当なし<br /><br /> 01004|  
|SQL_C_ULONG SQL_C_LONG SQL_C_SLONG SQL_C_SHORT SQL_C_USHORT SQL_C_UBIGINT SQL_C_SBIGINT SQL_C_UTINYINTのSQL_C_ULONGSQL_C_NUMERICをSQL_C_SSHORTSQL_C_SSHORTSQL_C_TINYINTSQL_C_TINYINTSQL_C_TINYINTSQL_C_SSHORTSQL_C_STINYINTSQL_C_SSHORT|切り捨てなしで変換されたデータ[b]<br /><br /> 小数部の桁の切り捨てで変換されたデータ[a]<br /><br /> データの変換は(小数部とは対照的に)全体の損失をもたらす[a]<br /><br /> データは*数値リテラル*[b] ではありません|Data<br /><br /> 切り捨てられたデータ<br /><br /> 未定義。<br /><br /> 未定義。|C データ型のバイト数<br /><br /> C データ型のバイト数<br /><br /> 未定義。<br /><br /> 未定義。|該当なし<br /><br /> 01S07<br /><br /> 22003<br /><br /> 22018|  
|SQL_C_DOUBLESQL_C_FLOAT|データが、数値の変換先のデータ型の範囲内にある[a]<br /><br /> データが、数値の変換先のデータ型の範囲外である[a]。<br /><br /> データは*数値リテラル*[b] ではありません|Data<br /><br /> 未定義。<br /><br /> 未定義。|C データ型のサイズ<br /><br /> 未定義。<br /><br /> 未定義。|該当なし<br /><br /> 22003<br /><br /> 22018|  
|SQL_C_BIT|データは 0 または 1 です<br /><br /> データが 0 より大きく、2 より小さく、1 に等しくない<br /><br /> データが 0 未満か 2 以上です<br /><br /> データが*数値リテラル*ではありません|Data<br /><br /> 切り捨てられたデータ<br /><br /> 未定義。<br /><br /> 未定義。|1[b]<br /><br /> 1[b]<br /><br /> 未定義。<br /><br /> 未定義。|該当なし<br /><br /> 01S07<br /><br /> 22003<br /><br /> 22018|  
|SQL_C_BINARY|データ長のバイト長<=*バッファ長*<br /><br /> データのバイト長 >*バッファ長*|Data<br /><br /> 切り捨てられたデータ|データの長さ (バイト単位)<br /><br /> データの長さ|該当なし<br /><br /> 01004|  
|SQL_C_TYPE_DATE|データ値は有効な*日付値*です。[a]<br /><br /> データ値は有効な*タイムスタンプ値*です。時間部分はゼロです[a]<br /><br /> データ値は有効な*タイムスタンプ値*です。時間部分はゼロ以外の[a]、[c]<br /><br /> データ値が有効な*日付値*または*タイムスタンプ値*でない [a]|Data<br /><br /> Data<br /><br /> 切り捨てられたデータ<br /><br /> 未定義。|6[b]<br /><br /> 6[b]<br /><br /> 6[b]<br /><br /> 未定義。|該当なし<br /><br /> 該当なし<br /><br /> 01S07<br /><br /> 22018|  
|SQL_C_TYPE_TIME|データ値は有効な*時間値で、秒の小数部の値は 0*[a]<br /><br /> データ値は、有効な*タイムスタンプ値または有効な時間値*です。小数秒部分はゼロ[a]、[d]<br /><br /> データ値は有効な*タイムスタンプ値*です。小数秒部分はゼロ以外の[a]、[d]、[e]<br /><br /> データ値が有効な*時刻値*または*タイムスタンプ値*ではありません 。a|Data<br /><br /> Data<br /><br /> 切り捨てられたデータ<br /><br /> 未定義。|6[b]<br /><br /> 6[b]<br /><br /> 6[b]<br /><br /> 未定義。|該当なし<br /><br /> 該当なし<br /><br /> 01S07<br /><br /> 22018|  
|SQL_C_TYPE_TIMESTAMP|データ値は、有効な*タイムスタンプ値または有効な時間値*です。小数秒部分が切り捨てられていない[a]<br /><br /> データ値は、有効な*タイムスタンプ値または有効な時間値*です。小数秒部分が切り捨てられた[a]<br /><br /> データ値は有効な*日付値*です。[a]<br /><br /> データ値は有効な*時間値*です。[a]<br /><br /> データ値が有効な*日付値*、*時刻値*、または*タイムスタンプ値*[a] ではありません。|Data<br /><br /> 切り捨てられたデータ<br /><br /> データ[f]<br /><br /> データ[g]<br /><br /> 未定義。|16[b]<br /><br /> 16[b]<br /><br /> 16[b]<br /><br /> 16[b]<br /><br /> 未定義。|該当なし<br /><br /> 01S07<br /><br /> 該当なし<br /><br /> 該当なし<br /><br /> 22018|  
|すべての C インターバル・タイプ|データ値は有効な*間隔値*です。切り捨てなし<br /><br /> データ値は有効な*間隔値*です。1 つ以上の後続フィールドの切り捨て<br /><br /> データは有効な間隔です。先行フィールドの有意な精度が失われる<br /><br /> データ値が有効な間隔値ではありません|Data<br /><br /> 切り捨てられたデータ<br /><br /> 未定義。<br /><br /> 未定義。|データの長さ (バイト単位)<br /><br /> データの長さ (バイト単位)<br /><br /> 未定義。<br /><br /> 未定義。|該当なし<br /><br /> 01S07<br /><br /> 22015<br /><br /> 22018|  
|&nbsp;|&nbsp;|&nbsp;|&nbsp;|&nbsp;|

 [a] この変換では *、BufferLength*の値は無視されます。 ドライバーは、**ターゲット値Ptr*のサイズは、Cデータ型のサイズであると仮定します。  
  
 [b] これは、対応する C データ型のサイズです。  
  
 [c]*タイムスタンプ値*の時間部分が切り捨てられる。  
  
 [d]*タイムスタンプ値*の日付部分は無視されます。  
  
 [e] タイムスタンプの秒の小数部分が切り捨てられます。  
  
 [f] タイムスタンプ構造体の時間フィールドがゼロに設定されている。  
  
 [g] タイムスタンプ構造の日付フィールドは現在の日付に設定されます。  

**余分なスペース**

SQL 文字データが次のいずれかのタイプに変換される場合、先頭と末尾のスペースは無視されます。

- date
- numeric
- time
- timestamp
- 間隔 C データ
