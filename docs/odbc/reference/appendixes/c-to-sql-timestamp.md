---
title: 'C から SQL: タイムスタンプ |マイクロソフトドキュメント'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data conversions from C to SQL types [ODBC], timestamp
- timestamp data type [ODBC]
- converting data from c to SQL types [ODBC], timestamp
ms.assetid: 0e08bfff-68f9-4648-9558-09b57fea08ad
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3102e5043527a1aa9463980c9dd546839cb92f37
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283752"
---
# <a name="c-to-sql-timestamp"></a>C から SQL へ: Timestamp
タイムスタンプ ODBC C データ型の識別子は次のとおりです。  
  
 SQL_C_TYPE_TIMESTAMP  
  
 次の表は、タイムスタンプ C データの変換先となる ODBC SQL データ型を示しています。 表の列と用語の説明については、データを[C から SQL データ型に変換する](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)を参照してください。  
  
|SQL タイプ識別子|テスト|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|列バイト長>= 文字バイト長<br /><br /> 19 <= 列バイト長<文字バイト長<br /><br /> 列バイト長 < 19<br /><br /> データ値が有効なタイムスタンプではありません|該当なし<br /><br /> 22001<br /><br /> 22001<br /><br /> 22008|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|列文字の長さ >= データの文字長<br /><br /> 19 <= 列の文字長<データの文字長<br /><br /> 列の文字長 < 19<br /><br /> データ値が有効なタイムスタンプではありません|該当なし<br /><br /> 22001<br /><br /> 22001<br /><br /> 22008|  
|SQL_TYPE_DATE|時間フィールドがゼロ<br /><br /> 時間フィールドが 0 以外の場合<br /><br /> データ値に有効な日付が含まれていません|該当なし<br /><br /> 22008<br /><br /> 22007|  
|SQL_TYPE_TIME|秒の小数部フィールドはゼロです[a]<br /><br /> 秒の小数部フィールドは 0 以外です。[a]<br /><br /> データ値に有効な時刻が含まれていません|該当なし<br /><br /> 22008<br /><br /> 22007|  
|SQL_TYPE_TIMESTAMP|秒の小数フィールドは切り捨てられない<br /><br /> 秒の小数フィールドは切り捨てられます<br /><br /> データ値が有効なタイムスタンプではありません|該当なし<br /><br /> 22008<br /><br /> 22007|  
  
 [a] タイムスタンプ構造体の日付フィールドは無視されます。  
  
 SQL_C_TIMESTAMP構造体で有効な値については、この付録の[「C データ型](../../../odbc/reference/appendixes/c-data-types.md)」を参照してください。  
  
 タイムスタンプCデータが文字SQLデータに変換されると、結果の文字データは "*yyyy*-*mm*-*dd* *hh*:*mm*:*ss*.*f..*[]形式。  
  
 ドライバーは、タイムスタンプ C データ型からデータを変換するときに長さ/インジケーター値を無視し、データ バッファーのサイズは、タイムスタンプ C データ型のサイズであると仮定します。 長さ/インジケーター値は **、SQLPutData**の*StrLen_or_Ind*引数と **、SQLBindParameter**の*StrLen_or_IndPtr*引数で指定されたバッファーに渡されます。 データ バッファーは **、SQLPutData**の*引数*と**SQLBindParameter**の*引数で指定*します。
