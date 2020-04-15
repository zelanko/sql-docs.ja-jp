---
title: C から SQL へのデータ変換の例 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from c to SQL types [ODBC], examples
- data conversions from C to SQL types [ODBC], examples
ms.assetid: 9f390afc-d8b8-4286-b559-98b3b8781f3d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0e21654f183946675c63cee10a3c08754e1508f5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81291992"
---
# <a name="c-to-sql-data-conversion-examples"></a>C から SQL へのデータ変換の例
次の例は、ドライバーが C データを SQL データに変換する方法を示しています。  
  
|C 型識別子|C データ値|SQL 型<br /><br /> identifier|列<br /><br /> length|SQL data<br /><br /> value|SQLSTATE|  
|-----------------------|------------------|-----------------------------|-----------------------|------------------------|--------------|  
|SQL_C_CHAR|abcdef\0[a]|SQL_CHAR|6|abcdef|該当なし|  
|SQL_C_CHAR|abcdef\0[a]|SQL_CHAR|5|Abcde|22001|  
|SQL_C_CHAR|1234.56\0[a]|SQL_DECIMAL|8[b]|1234.56|該当なし|  
|SQL_C_CHAR|1234.56\0[a]|SQL_DECIMAL|7[b]|1234.5|22001|  
|SQL_C_CHAR|1234.56\0[a]|SQL_DECIMAL|4|----|22003|  
|SQL_C_FLOAT|1234.56|SQL_FLOAT|該当なし|1234.56|該当なし|  
|SQL_C_FLOAT|1234.56|SQL_INTEGER|該当なし|1234|22001|  
|SQL_C_FLOAT|1234.56|SQL_TINYINT|該当なし|----|22003|  
|SQL_C_TYPE_DATE|1992,12,31[c]|SQL_CHAR|10|1992-12-31|該当なし|  
|SQL_C_TYPE_DATE|1992,12,31[c]|SQL_CHAR|9|----|22003|  
|SQL_C_TYPE_DATE|1992,12,31[c]|SQL_TIMESTAMP|該当なし|1992-12-31 00:00:00.0|該当なし|  
|SQL_C_TYPE_TIMESTAMP|1992,12,31, 23,45,55, 12000000[d]|SQL_CHAR|22|1992-12-31 23:45:55.12|該当なし|  
|SQL_C_TYPE_TIMESTAMP|1992,12,31, 23,45,55, 12000000[d]|SQL_CHAR|21|1992-12-31 23:45:55.1|22001|  
|SQL_C_TYPE_TIMESTAMP|1992,12,31, 23,45,55, 12000000[d]|SQL_CHAR|18|----|22003|  
  
 [a] "\0" は、null 終了バイトを表します。 ヌル終了バイトは、データの長さがSQL_NTS場合にのみ必要です。  
  
 [b] 数字のバイトに加えて、符号には 1 バイト、小数点には別のバイトが必要です。  
  
 [c] このリストの数値は、SQL_DATE_STRUCT構造のフィールドに格納されている数値です。  
  
 [d] このリストの数値は、SQL_TIMESTAMP_STRUCT構造のフィールドに格納されている数値です。
