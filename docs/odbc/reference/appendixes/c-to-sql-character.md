---
title: "C から SQL へ: 文字 |Microsoft ドキュメント"
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
- character data type [ODBC]
- data conversions from C to SQL types [ODBC], character
- converting data from c to SQL types [ODBC], character
ms.assetid: be66188a-ebdb-4c9e-af72-c379886766fa
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e8d6ab676fc351afd7819c1fe60d59a58bfe7207
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="c-to-sql-character"></a>SQL を C: の文字
ODBC C データ型の文字の識別子は次のとおりです。  
  
 SQL_C_CHAR  
  
 SQL_C_WCHAR  
  
 次の表は、ODBC SQL データ型が C の文字データを変換することがありますを示します。 列とテーブルの用語の詳細については、次を参照してください。[に変換するデータを C から SQL データ型を](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)です。  
  
> [!NOTE]  
>  文字データが Unicode SQL データに変換されると、Unicode データの長さは偶数である必要があります。  
  
|SQL 型の識別子|テスト|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|データのバイト長 < 列の長さを = です。<br /><br /> データのバイト長 > 列の長さ。|n/a<br /><br /> 22001|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|データの文字長 < 列の長さを = です。<br /><br /> データの文字長 > 列の長さ。|n/a<br /><br /> 22001|  
|SQL_DECIMAL<br /><br /> SQL_NUMERIC<br /><br /> SQL_TINYINT<br /><br /> SQL_SMALLINT<br /><br /> SQL_INTEGER SQL_BIGINT|データを切り捨てることがなく変換<br /><br /> データ変換 [e] 桁の小数部の切り捨て<br /><br /> [E]\(ではなく小数部) の整数桁の数字が失われる結果のデータの変換<br /><br /> データの値が、*数値リテラル*|n/a<br /><br /> 22001<br /><br /> 22001<br /><br /> 22018|  
|SQL_REAL<br /><br /> SQL_FLOAT<br /><br /> SQL_DOUBLE|データが数の変換先のデータ型の範囲内<br /><br /> データが数の変換先のデータ型の範囲外です。<br /><br /> データの値が、*数値リテラル*|n/a<br /><br /> 22003<br /><br /> 22018|  
|SQL_BIT|データが 0 または 1 です。<br /><br /> データが 0 より大きく、2、未満と 1 に等しくないです。<br /><br /> データがより小さい 0 より大きいまたは 2 に等しい<br /><br /> データがない、*数値リテラル*|n/a<br /><br /> 22001<br /><br /> 22003<br /><br /> 22018|  
|SQL_BINARY<br /><br /> SQL_VARBINARY<br /><br /> SQL_LONGVARBINARY|(データのバイト長)/2 < バイト長の列を =<br /><br /> (データのバイト長)/2 > の列のバイト長<br /><br /> データ値は、16 進数の値ではありません。|n/a<br /><br /> 22001<br /><br /> 22018|  
|SQL_TYPE_DATE|データ値が有効な*ODBC 日付リテラル*<br /><br /> データ値が有効な*ODBC タイムスタンプ リテラル*; 時刻部分は 0<br /><br /> データ値が有効な*ODBC タイムスタンプ リテラル*; 時刻部分が 0 以外の値 [a]<br /><br /> データの値が有効な*ODBC 日付リテラル*または*ODBC タイムスタンプ リテラル*|n/a<br /><br /> n/a<br /><br /> 22008<br /><br /> 22018|  
|SQL_TYPE_TIME|データ値が有効な*ODBC 時刻リテラル*<br /><br /> データ値が有効な*ODBC タイムスタンプ リテラル*以外の場合は小数秒の部分ではゼロ [b]<br /><br /> データ値が有効な*ODBC タイムスタンプ リテラル*以外の場合は小数秒の部分は 0 以外の値 [b]<br /><br /> データの値が有効な*ODBC 時刻リテラル*または*ODBC タイムスタンプ リテラル*|n/a<br /><br /> n/a<br /><br /> 22008<br /><br /> 22018|  
|SQL_TYPE_TIMESTAMP|データ値が有効な*ODBC タイムスタンプ リテラル*以外の場合は小数秒の部分を切り捨てられません<br /><br /> データ値が有効な*ODBC タイムスタンプ リテラル*以外の場合は小数秒の部分を切り捨てる<br /><br /> データ値が有効な*ODBC 日付リテラル*[c]<br /><br /> データ値が有効な*ODBC 時刻リテラル*[d]<br /><br /> データの値が有効な*ODBC 日付リテラル*、 *ODBC 時刻リテラル*、または*ODBC タイムスタンプ リテラル*|n/a<br /><br /> 22008<br /><br /> n/a<br /><br /> n/a<br /><br /> 22018|  
|すべての SQL interval 型|データ値が有効な*間隔値*; 切り捨ては行われません<br /><br /> データ値が有効な*間隔値*; フィールドのいずれかの値が切り詰められています<br /><br /> データ値は、リテラルの有効な間隔ではありません。|n/a<br /><br /> 22015<br /><br /> 22018|  
  
 [a] のタイムスタンプの時刻部分が切り詰められています。  
  
 [b] タイムスタンプの場合は、の日付部分は無視されます。  
  
 [c]、タイムスタンプの時刻部分は、0 に設定されます。  
  
 [d]タイムスタンプの で、日付部分は、現在の日付に設定されます。  
  
 [e] [電子メール] で、ドライバー/データ ソースは、文字列全体が受信されるまでに効果的に待機する (文字データへの呼び出しによって個別に送信される場合でも**SQLPutData**) 変換を実行する前にします。  
  
 文字データは、数値、変換後の日付、時刻、または SQL のタイムスタンプ データには、先頭と末尾の空白は無視されます。  
  
 SQL データのバイナリを文字データが変換されると、各 2 バイトの文字データがバイナリ データの 1 バイト (8 ビット) に変換されます。 各 2 バイトの文字データは、16 進形式の数値を表します。 たとえば、「01」はバイナリ 00000001 に変換され、"FF"はバイナリ 11111111 に変換されます。  
  
 常に、ドライバーは、個々 のバイトの 16 進数のペアに変換し、null 終了バイトを無視します。 このため、文字の文字列の長さが奇数の場合、文字列 (存在する場合は、null 終了バイトを除く) の最後のバイトは変換されません。  
  
> [!NOTE]  
>  アプリケーション開発者は、文字データをバイナリ SQL データ型にバインドしないことお勧めします。 この変換は、非効率的で低速では通常です。

