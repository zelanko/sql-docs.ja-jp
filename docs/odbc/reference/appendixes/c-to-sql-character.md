---
title: 'C から SQL: 文字 |マイクロソフトドキュメント'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- character data type [ODBC]
- data conversions from C to SQL types [ODBC], character
- converting data from c to SQL types [ODBC], character
ms.assetid: be66188a-ebdb-4c9e-af72-c379886766fa
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: acde0d2a79492607185d56d3082797c79a100fa2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292033"
---
# <a name="c-to-sql-character"></a>C から SQL へ: 文字
文字 ODBC C データ型の識別子は次のとおりです。  
  
 SQL_C_CHAR  
  
 SQL_C_WCHAR  
  
 次の表は、C 文字データの変換先となる ODBC SQL データ型を示しています。 表の列と用語の説明については、データを[C から SQL データ型に変換する](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)を参照してください。  
  
> [!NOTE]  
>  文字 C のデータを Unicode SQL データに変換する場合、Unicode データの長さは偶数でなければなりません。  
  
|SQL タイプ識別子|テスト|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|データ<のバイト長 = 列の長さ。<br /><br /> データのバイト長>列の長さです。|該当なし<br /><br /> 22001|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|データの文字数<= 列の長さ。<br /><br /> データの文字長>列の長さです。|該当なし<br /><br /> 22001|  
|SQL_DECIMAL<br /><br /> SQL_NUMERIC<br /><br /> SQL_TINYINT<br /><br /> SQL_SMALLINT<br /><br /> SQL_INTEGERSQL_BIGINT|切り捨てなしで変換されたデータ<br /><br /> 小数部の桁の切り捨てで変換されたデータ[e]<br /><br /> データの変換は(小数部ではなく)全体の損失をもたらす[e]<br /><br /> データ値が*数値リテラル*ではありません|該当なし<br /><br /> 22001<br /><br /> 22001<br /><br /> 22018|  
|SQL_REAL<br /><br /> SQL_FLOAT<br /><br /> SQL_DOUBLE|データが、数値の変換先のデータ型の範囲内にある<br /><br /> データが、数値の変換先のデータ型の範囲外です。<br /><br /> データ値が*数値リテラル*ではありません|該当なし<br /><br /> 22003<br /><br /> 22018|  
|SQL_BIT|データは 0 または 1 です<br /><br /> データが 0 より大きく、2 より小さく、1 に等しくない<br /><br /> データが 0 未満か 2 以上です<br /><br /> データが*数値リテラル*ではありません|該当なし<br /><br /> 22001<br /><br /> 22003<br /><br /> 22018|  
|SQL_BINARY<br /><br /> SQL_VARBINARY<br /><br /> SQL_LONGVARBINARY|(データのバイト長) / 2 <= 列バイト長<br /><br /> (データのバイト長) / 2 >列バイト長<br /><br /> データ値が 16 進値ではありません|該当なし<br /><br /> 22001<br /><br /> 22018|  
|SQL_TYPE_DATE|データ値は有効な*ODBC 日付リテラルです*<br /><br /> データ値は有効な*ODBC タイムスタンプ リテラルです*。時間部分がゼロ<br /><br /> データ値は有効な*ODBC タイムスタンプ リテラルです*。時間部分はゼロ以外の値です[a]<br /><br /> データ値が有効な*ODBC 日付リテラル*または*ODBC タイムスタンプ リテラルではありません。*|該当なし<br /><br /> 該当なし<br /><br /> 22008<br /><br /> 22018|  
|SQL_TYPE_TIME|データ値は有効な*ODBC 時リテラルです。*<br /><br /> データ値は有効な*ODBC タイムスタンプ リテラルです*。小数秒部分はゼロ[b]<br /><br /> データ値は有効な*ODBC タイムスタンプ リテラルです*。小数秒部分がゼロ以外の[b]<br /><br /> データ値が有効な*ODBC 時刻リテラル*または*ODBC タイムスタンプ リテラルではありません。*|該当なし<br /><br /> 該当なし<br /><br /> 22008<br /><br /> 22018|  
|SQL_TYPE_TIMESTAMP|データ値は有効な*ODBC タイムスタンプ リテラルです*。小数秒部分が切り捨てられていない<br /><br /> データ値は有効な*ODBC タイムスタンプ リテラルです*。小数秒部分が切り捨てられる<br /><br /> データ値が有効な*ODBC 日付リテラル*[c] です<br /><br /> データ値は有効な*ODBC 時リテラル*[d] です<br /><br /> データ値が有効な*ODBC 日付リテラル* *、ODBC 時刻リテラル*、または*ODBC タイムスタンプ リテラルではありません。*|該当なし<br /><br /> 22008<br /><br /> 該当なし<br /><br /> 該当なし<br /><br /> 22018|  
|すべての SQL インターバル・タイプ|データ値は有効な*間隔値*です。切り捨ては行われません<br /><br /> データ値は有効な*間隔値*です。フィールドの 1 つの値が切り捨てられます<br /><br /> データ値が有効な間隔リテラルではありません|該当なし<br /><br /> 22015<br /><br /> 22018|  
  
 [a] タイムスタンプの時間部分が切り捨てられます。  
  
 [b] タイムスタンプの日付部分は無視されます。  
  
 [c] タイムスタンプの時間部分がゼロに設定されている。  
  
 [d] タイムスタンプの日付部分が現在の日付に設定されます。  
  
 [e] ドライバー/データ ソースは、変換を実行する前に、文字列全体を受信するまで (文字データが**SQLPutData**への呼び出しによって分割されて送信された場合でも) 効果的に待機します。  
  
 文字 C データを数値、日付、時刻、またはタイム・スタンプの SQL データに変換する場合、先行ブランクと末尾ブランクは無視されます。  
  
 文字 C データがバイナリ SQL データに変換されると、2 バイトの文字データが 1 バイト (8 ビット) のバイナリ データに変換されます。 文字データの 2 バイトは、16 進数形式の数値を表します。 たとえば、"01" はバイナリ 00000001 に変換され、"FF" はバイナリ 11111111 に変換されます。  
  
 ドライバーは常に 16 進数のペアを個々のバイトに変換し、null 終了バイトを無視します。 このため、文字列の長さが奇数の場合、文字列の最後のバイト (NULL 終了バイトがある場合は除く) は変換されません。  
  
> [!NOTE]  
>  アプリケーション開発者は、文字 C データをバイナリ SQL データ型にバインドすることはお勧めしません。 この変換は、通常、非効率的で低速です。
