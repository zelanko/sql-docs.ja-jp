---
title: 'C から SQL: 日付 |マイクロソフトドキュメント'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- date data type [ODBC]
- converting data from c to SQL types [ODBC], date
- data conversions from C to SQL types [ODBC], date
ms.assetid: bea087d3-911f-418b-b483-d2b5b334da19
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fa3df8aaee03472076b3241cb9bb60e2a307e28b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298850"
---
# <a name="c-to-sql-date"></a>C から SQL へ: Date
日付 ODBC C データ型の識別子は次のとおりです。  
  
 SQL_C_TYPE_DATE  
  
 次の表は、日付 C データを変換できる ODBC SQL データ型を示しています。 表の列と用語の説明については、データを[C から SQL データ型に変換する](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)を参照してください。  
  
|SQL タイプ識別子|テスト|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|列バイト長>= 10<br /><br /> 列バイト長 < 10<br /><br /> データ値が有効な日付ではありません|該当なし<br /><br /> 22001<br /><br /> 22008|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|列の文字長>= 10<br /><br /> 列の文字長 < 10<br /><br /> データ値が有効な日付ではありません|該当なし<br /><br /> 22001<br /><br /> 22008|  
|SQL_TYPE_DATE|データ値が有効な日付です<br /><br /> データ値が有効な日付ではありません|該当なし<br /><br /> 22007|  
|SQL_TYPE_TIMESTAMP|データ値は有効な日付です。.a]<br /><br /> データ値が有効な日付ではありません|該当なし<br /><br /> 22007|  
  
 [a] タイムスタンプの時間部分がゼロに設定されている。  
  
 SQL_C_TYPE_DATE構造体で有効な値については、この付録の[「C データ型](../../../odbc/reference/appendixes/c-data-types.md)」を参照してください。  
  
 日付 C のデータが文字 SQL データに変換されると、結果の文字データは "*yyyy*-*mm*-*dd*" 形式になります。  
  
 ドライバは、日付 C のデータ型からデータを変換するときに長さ/インジケーター値を無視し、データ バッファーのサイズが日付 C データ型のサイズであると仮定します。 長さ/インジケーター値は **、SQLPutData**の*StrLen_or_Ind*引数と **、SQLBindParameter**の*StrLen_or_IndPtr*引数で指定されたバッファーに渡されます。 データ バッファーは **、SQLPutData**の*引数*と**SQLBindParameter**の*引数で指定*します。
