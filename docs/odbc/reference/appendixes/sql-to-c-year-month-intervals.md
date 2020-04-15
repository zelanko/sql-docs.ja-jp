---
title: 'SQL から C: 年と月の間隔 |マイクロソフトドキュメント'
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to c types [ODBC], about converting
- data conversions from SQL to C types [ODBC], year-month intervals
- intervals [ODBC], converting
- year-month intervals [ODBC]
ms.assetid: 1233634b-8214-420f-b872-3b2630105ba4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ba79a4d6165a43676634a6b79db56b88f5bcc234
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296392"
---
# <a name="sql-to-c-year-month-intervals"></a>SQL から C へ: 年月の間隔

年と月の間隔 ODBC SQL データ型の識別子は次のとおりです。

- SQL_INTERVAL_MONTH
- SQL_INTERVAL_YEAR
- SQL_INTERVAL_YEAR_TO_MONTH

次の表は、SQL データの変換先となる、年と月の間隔の ODBC C データ型を示しています。 表の列と用語の説明については[、SQL から C データ型へのデータの変換を参照してください](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)。  

|C 型識別子|テスト|ターゲット値Ptr|StrLen_or_IndPtr|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_INTERVAL_MONTH[a]<br /><br /> SQL_C_INTERVAL_YEAR[a]<br /><br /> SQL_C_INTERVAL_YEAR_TO_MONTH[a]|末尾のフィールド部分が切り捨てられていない<br /><br /> 末尾のフィールド部分が切り捨てられました<br /><br /> ターゲットの先行精度は、ソースからのデータを保持するのに十分な大きさではありません|Data<br /><br /> 切り捨てられたデータ<br /><br /> 未定義。|データの長さ (バイト単位)<br /><br /> データの長さ (バイト単位)<br /><br /> 未定義。|該当なし<br /><br /> 01S07<br /><br /> 22015|  
|SQL_C_STINYINT[b]<br /><br /> SQL_C_UTINYINT[b]<br /><br /> SQL_C_USHORT[b]<br /><br /> SQL_C_SHORT[b]<br /><br /> SQL_C_SLONG[b]<br /><br /> SQL_C_ULONG[b]<br /><br /> SQL_C_NUMERIC[b]<br /><br /> SQL_C_BIGINT[b]|間隔の精度は単一のフィールドであり、データは切り捨てられずに変換されました<br /><br /> 間隔の精度は単一フィールドであり、全体が切り捨てられました<br /><br /> 間隔の精度が単一フィールドではありませんでした|Data<br /><br /> 切り捨てられたデータ<br /><br /> 未定義。|C データ型のサイズ<br /><br /> データの長さ (バイト単位)<br /><br /> C データ型のサイズ|該当なし<br /><br /> 22003<br /><br /> 22015|  
|SQL_C_BINARY|データ長のバイト長<=*バッファ長*<br /><br /> データのバイト長 >*バッファ長*|Data<br /><br /> 未定義。|データの長さ (バイト単位)<br /><br /> 未定義。|該当なし<br /><br /> 22003|  
|SQL_C_CHAR|バッファー長<文字バイト*長*<br /><br /> (小数部ではなく) バッファ*長*<整数の桁数<br /><br /> 整数の数 (小数部ではなく) >= *BufferLength*|Data<br /><br /> 切り捨てられたデータ<br /><br /> 未定義。|C データ型のサイズ<br /><br /> C データ型のサイズ<br /><br /> 未定義。|該当なし<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|文字長<*バッファー長*<br /><br /> (小数部ではなく) バッファ*長*<整数の桁数<br /><br /> 整数の数 (小数部ではなく) >= *BufferLength*|Data<br /><br /> 切り捨てられたデータ<br /><br /> 未定義。|C データ型のサイズ<br /><br /> C データ型のサイズ<br /><br /> 未定義。|該当なし<br /><br /> 01004<br /><br /> 22003|  
  
 [a] 年と月の間隔の SQL 型は、任意の年月間隔 C 型に変換できます。  
  
 [b] 間隔の精度が単一フィールド (YEAR または MONTH の 1 つ) の場合、間隔 SQL タイプは任意の正確な数値 (SQL_C_STINYINT、SQL_C_UTINYINT、SQL_C_USHORT、SQL_C_SHORT、SQL_C_SLONG、SQL_C_ULONG、または SQL_C_NUMERIC に変換できます。  

## <a name="default-conversions"></a>既定の変換

間隔 SQL 型の既定の変換は、対応する C 間隔データ型です。 次に、アプリケーションは、初期化されたSQL_INTERVAL_STRUCT構造体を指すように列またはパラメーターをバインドします (または、SQL_DESC_DATA_PTR フィールドを設定して、SQL_INTERVAL_STRUCT構造体を指します (または **、sqlGetData**の呼び出しで*引数 TargetValuePtr*としてSQL_INTERVAL_STRUCT構造体へのポインターを渡します)。
