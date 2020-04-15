---
title: 'C から SQL: 時間 |マイクロソフトドキュメント'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data conversions from C to SQL types [ODBC], time
- time data type [ODBC]
- converting data from c to SQL types [ODBC], time
ms.assetid: a8da43c9-d9a5-45e5-bd9a-1dd633db2ee0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 264ce7751072b79163923f0c141542680f7b02bb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304764"
---
# <a name="c-to-sql-time"></a>C から SQL へ: Time
ODBC C データ型の時刻の識別子は次のとおりです。  
  
 SQL_C_TYPE_TIME  
  
 次の表は、時刻 C データを変換できる ODBC SQL データ型を示しています。 表の列と用語の説明については、データを[C から SQL データ型に変換する](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)を参照してください。  
  
|SQL タイプ識別子|テスト|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|列バイト長>= 8<br /><br /> 列バイト長 < 8<br /><br /> データ値が有効な時刻ではありません|該当なし<br /><br /> 22001<br /><br /> 22008|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|列の文字数 >= 8<br /><br /> 列の文字長< 8<br /><br /> データ値が有効な時刻ではありません|該当なし<br /><br /> 22001<br /><br /> 22008|  
|SQL_TYPE_TIME|データ値は有効な時刻です<br /><br /> データ値が有効な時刻ではありません|該当なし<br /><br /> 22007|  
|SQL_TYPE_TIMESTAMP|データ値は有効な時刻です[a]<br /><br /> データ値が有効な時刻ではありません|該当なし<br /><br /> 22007|  
  
 [a] タイムスタンプの日付部分は現在の日付に設定され、タイムスタンプの秒の小数部分はゼロに設定されます。  
  
 SQL_C_TYPE_TIME構造体で有効な値については、この付録の[「C データ型](../../../odbc/reference/appendixes/c-data-types.md)」を参照してください。  
  
 時刻 C のデータが文字 SQL データに変換されるとき、結果の文字データは "*hh*:*mm*:*ss*" 形式になります。  
  
 ドライバーは、時間 C データ型からデータを変換するときに長さ/インジケーター値を無視し、データ バッファーのサイズは、時間 C データ型のサイズであると仮定します。 長さ/インジケーター値は **、SQLPutData**の*StrLen_or_Ind*引数と **、SQLBindParameter**の*StrLen_or_IndPtr*引数で指定されたバッファーに渡されます。 データ バッファーは **、SQLPutData**の*引数*と**SQLBindParameter**の*引数で指定*します。
