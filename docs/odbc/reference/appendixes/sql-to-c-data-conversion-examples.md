---
title: SQL から C へのデータ変換の例 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data conversions from SQL to C types [ODBC], examples
- converting data from SQL to C types [ODBC], examples
ms.assetid: 0190c76c-7f9b-42f4-be9d-cef7284840fd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 96b10dd93c807aaa49a7e10e198f789fb47ccdeb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296652"
---
# <a name="sql-to-c-data-conversion-examples"></a>SQL から C へのデータ変換の例

次の表に示す例は、ドライバーが SQL データを C データに変換する方法を示しています。  
  
|SQL 型<br /><br /> identifier|SQL data<br /><br /> value|C 型<br /><br /> identifier|バッファー<br /><br /> length|**ターゲット値Ptr*|SQLSTATE|  
|-----------------------------|------------------------|---------------------------|-----------------------|------------------------|--------------|  
|SQL_CHAR|abcdef|SQL_C_CHAR|7|abcdef\0[a]|該当なし|  
|SQL_CHAR|abcdef|SQL_C_CHAR|6|abcde\0[a]|01004|  
|SQL_DECIMAL|1234.56|SQL_C_CHAR|8|1234.56\0[a]|該当なし|  
|SQL_DECIMAL|1234.56|SQL_C_CHAR|5|1234\0[a]|01004|  
|SQL_DECIMAL|1234.56|SQL_C_CHAR|4|----|22003|  
|SQL_DECIMAL|1234.56|SQL_C_FLOAT|無視|1234.56|該当なし|  
|SQL_DECIMAL|1234.56|SQL_C_SSHORT|無視|1234|01S07|  
|SQL_DECIMAL|1234.56|SQL_C_STINYINT|無視|----|22003|  
|SQL_DOUBLE|1.2345678|SQL_C_DOUBLE|無視|1.2345678|該当なし|  
|SQL_DOUBLE|1.2345678|SQL_C_FLOAT|無視|1.234567|該当なし|  
|SQL_DOUBLE|1.2345678|SQL_C_STINYINT|無視|1|該当なし|  
|SQL_TYPE_DATE|1992-12-31|SQL_C_CHAR|11|1992-12-31\0[a]|該当なし|  
|SQL_TYPE_DATE|1992-12-31|SQL_C_CHAR|10|-----|22003|  
|SQL_TYPE_DATE|1992-12-31|SQL_C_TIMESTAMP|無視|1992,12,31, 0,0,0,0[b]|該当なし|  
|SQL_TYPE_TIMESTAMP|1992-12-31 23:45:55.12|SQL_C_CHAR|23|1992-12-31 23:45:55.12\0[a]|該当なし|  
|SQL_TYPE_TIMESTAMP|1992-12-31 23:45:55.12|SQL_C_CHAR|22|1992-12-31 23:45:55.1\0[a]|01004|  
|SQL_TYPE_TIMESTAMP|1992-12-31 23:45:55.12|SQL_C_CHAR|18|----|22003|  
  
 [a] "\0" は、null 終了バイトを表します。 ドライバーは常に null 終端SQL_C_CHARデータです。  
  
 [b] このリストの数字は、TIMESTAMP_STRUCT構造のフィールドに格納されている数値です。
