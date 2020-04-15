---
title: 'C から SQL: バイナリ |マイクロソフトドキュメント'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- binary data type [ODBC]
- data conversions from C to SQL types [ODBC], binary
- binary data transfers [ODBC]
- converting data from c to SQL types [ODBC], binary
ms.assetid: 3e9083f3-357b-41aa-833c-2c8aac2226cd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 818de0086ce3996cc1f6194311d2a2bb80c9f564
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292118"
---
# <a name="c-to-sql-binary"></a>C から SQL へ: Binary
バイナリ ODBC C データ型の識別子は次のとおりです。  
  
 SQL_C_BINARY  
  
 次の表は、バイナリ C データの変換先となる ODBC SQL データ型を示しています。 表の列と用語の説明については、データを[C から SQL データ型に変換する](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)を参照してください。  
  
|SQL タイプ識別子|テスト|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|データのバイト長 <= 列バイト長<br /><br /> データのバイト長 > 列バイト長|該当なし<br /><br /> 22001|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|データ<の文字数 = 列文字の長さ<br /><br /> データの文字数 > 列文字長|該当なし<br /><br /> 22001|  
|SQL_DECIMAL<br /><br /> SQL_NUMERIC<br /><br /> SQL_TINYINT<br /><br /> SQL_SMALLINT<br /><br /> SQL_INTEGER<br /><br /> SQL_BIGINT<br /><br /> SQL_REAL<br /><br /> SQL_FLOAT<br /><br /> SQL_DOUBLE<br /><br /> SQL_BITSQL_TYPE_DATE<br /><br /> SQL_TYPE_TIME<br /><br /> SQL_TYPE_TIMESTAMP|データのバイト長 = SQL データ長<br /><br /> データのバイト長 <> SQL データ長|該当なし<br /><br /> 22003|  
|SQL_BINARY<br /><br /> SQL_VARBINARY<br /><br /> SQL_LONGVARBINARY|データ<の長さ = 列の長さ<br /><br /> データの長さ>列の長さ|該当なし<br /><br /> 22001|
