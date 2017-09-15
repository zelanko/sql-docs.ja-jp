---
title: "SQL から c: の文字へ |Microsoft ドキュメント"
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
- converting data from SQL to C types [ODBC], character
- character data type [ODBC]
- data conversions from SQL to C types [ODBC], character
ms.assetid: 7fdb7f38-b64d-48f2-bcb4-1ca96b2bbdb6
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3ba39caca1a4ad37437f35918545ed54a5dd2266
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sql-to-c-character"></a>SQL には、c: の文字
文字の ODBC SQL データ型の識別子は次のとおりです。  
  
 SQL_CHAR  
  
 SQL_VARCHAR  
  
 SQL_LONGVARCHAR  
  
 SQL_WCHAR  
  
 SQL_WVARCHAR  
  
 SQL_WLONGVARCHAR  
  
 次の表は、ODBC C データ型が文字 SQL データを変換することがありますを示します。 列とテーブルの用語の詳細については、次を参照してください。[に変換するデータを SQL から C データ型に](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)です。  
  
|C 型識別子|テスト|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|データのバイト長 < *BufferLength*<br /><br /> データのバイト長 > = *BufferLength*|data<br /><br /> 切り捨てられたデータ|バイト単位でデータの長さ<br /><br /> バイト単位でデータの長さ|n/a<br /><br /> 01004|  
|SQL_C_WCHAR|データの文字長 < *BufferLength*<br /><br /> データの文字長 > = *BufferLength*|data<br /><br /> 切り捨てられたデータ|データの文字の長さ<br /><br /> データの文字の長さ|n/a<br /><br /> 01004|  
|SQL_C_STINYINT SQL_C_UTINYINT SQL_C_TINYINT SQL_C_SBIGINT SQL_C_UBIGINT SQL_C_SSHORT SQL_C_USHORT SQL_C_SHORT SQL_C_SLONG SQL_C_ULONG SQL_C_LONG SQL_C_NUMERIC|[B] を切り捨てることがなくデータが変換されます。<br /><br /> データ変換する小数部の桁数 [a] の切り捨て<br /><br /> データの変換とは、[a] ではなく小数部) の整数桁の消失<br /><br /> データがない、*数値リテラル*[b]。|data<br /><br /> 切り捨てられたデータ<br /><br /> 未定義。<br /><br /> 未定義。|C データ型のバイト数<br /><br /> C データ型のバイト数<br /><br /> 未定義。<br /><br /> 未定義。|n/a<br /><br /> 01S07<br /><br /> 22003<br /><br /> 22018|  
|SQL_C_FLOAT SQL_C_DOUBLE|データは、数の変換先のデータ型の範囲内で、[a]<br /><br /> データが数の変換先のデータ型の範囲外 [a]<br /><br /> データがない、*数値リテラル*[b]。|data<br /><br /> 未定義。<br /><br /> 未定義。|C データ型のサイズ<br /><br /> 未定義。<br /><br /> 未定義。|n/a<br /><br /> 22003<br /><br /> 22018|  
_C_BIT|データが 0 または 1 です。<br /><br /> データが 0 より大きく、2、未満と 1 に等しくないです。<br /><br /> データがより小さい 0 より大きいまたは 2 に等しい<br /><br /> データがない、*数値リテラル*|data<br /><br /> 切り捨てられたデータ<br /><br /> 未定義。<br /><br /> 未定義。|1 [b]<br /><br /> 1 [b]<br /><br /> 未定義。<br /><br /> 未定義。|n/a<br /><br /> 01S07<br /><br /> 22003<br /><br /> 22018|  
|SQL_C_BINARY|データのバイト長 < = *BufferLength*<br /><br /> データのバイト長 > *BufferLength*|data<br /><br /> 切り捨てられたデータ|バイト単位でデータの長さ<br /><br /> データの長さ|n/a<br /><br /> 01004|  
|SQL_C_TYPE_DATE|データ値が有効な*日付値*[a]<br /><br /> データ値が有効な*タイムスタンプ値*; 時刻部分は 0 を [a]<br /><br /> データ値が有効な*タイムスタンプ値*; 時刻部分が 0 以外の値 [a] [c]<br /><br /> データの値が有効な*日付値*または*タイムスタンプ値*[a]|data<br /><br /> data<br /><br /> 切り捨てられたデータ<br /><br /> 未定義。|6 [b]<br /><br /> 6 [b]<br /><br /> 6 [b]<br /><br /> 未定義。|n/a<br /><br /> n/a<br /><br /> 01S07<br /><br /> 22018|  
|SQL_C_TYPE_TIME|データ値が有効な*時刻値、および秒の小数部の値は 0*[a]<br /><br /> データ値が有効な*タイムスタンプ値または有効な時刻値*以外の小数部は 0、秒の部分を [a]、[d]<br /><br /> データ値が有効な*タイムスタンプ値*以外の場合は小数秒の部分が 0 でない [a]、[d] [e]<br /><br /> データの値が有効な*時刻値*または*タイムスタンプ値*[a]|data<br /><br /> data<br /><br /> 切り捨てられたデータ<br /><br /> 未定義。|6 [b]<br /><br /> 6 [b]<br /><br /> 6 [b]<br /><br /> 未定義。|n/a<br /><br /> n/a<br /><br /> 01S07<br /><br /> 22018|  
_C_TYPE_TIMESTAMP|データ値が有効な*タイムスタンプ値または有効な時刻値*小数部以外の秒部分の切り捨て [a]<br /><br /> データ値が有効な*タイムスタンプ値または有効な時刻値*以外の場合は小数秒の部分を切り捨てる [a]<br /><br /> データ値が有効な*日付値*[a]<br /><br /> データ値が有効な*時刻値*[a]<br /><br /> データの値が有効な*日付値*、*時刻値*、または*タイムスタンプ値*[a]|data<br /><br /> 切り捨てられたデータ<br /><br /> データ [f]<br /><br /> データ [g]<br /><br /> 未定義。|16 [b]<br /><br /> 16 [b]<br /><br /> 16 [b]<br /><br /> 16 [b]<br /><br /> 未定義。|n/a<br /><br /> 01S07<br /><br /> n/a<br /><br /> n/a<br /><br /> 22018|  
|すべての C interval 型|データ値が有効な*間隔値*; 損失はありません。<br /><br /> データ値が有効な*間隔値*; 1 つ以上の後続のフィールドの切り捨て<br /><br /> データが有効な間隔です。先頭のフィールドの大きな有効桁数が失われる<br /><br /> データの値が有効な間隔の値|data<br /><br /> 切り捨てられたデータ<br /><br /> 未定義。<br /><br /> 未定義。|バイト単位でデータの長さ<br /><br /> バイト単位でデータの長さ<br /><br /> 未定義。<br /><br /> 未定義。|n/a<br /><br /> 01S07<br /><br /> 22015<br /><br /> 22018|  
  
 [a] の値*BufferLength*この変換では無視されます。 ドライバーでのサイズ **TargetValuePtr* C データ型のサイズです。  
  
 [b] これは、対応する C データ型のサイズです。  
  
 [c] の時刻部分、*タイムスタンプ値*が切り詰められています。  
  
 [d] の日付部分、*タイムスタンプ値*は無視されます。  
  
 [電子メール] タイムスタンプの秒部分は切り捨てられます。  
  
 [f] で、時刻、タイムスタンプの構造体のフィールドは、0 に設定されます。  
  
 [タイムスタンプの構造体の場合は、g] で、日付フィールドは、現在の日付に設定されます。  
  
 SQL データの文字は数値に変換するときに、日付、時刻、タイムスタンプ、または C の間隔のデータ、先頭と末尾のスペースは無視されます。
