---
title: 'C から SQL へ: バイナリ |Microsoft Docs'
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 76c2e4673d9b561aeb5af3e61e1e4dc8532195d6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47849130"
---
# <a name="c-to-sql-binary"></a>C から SQL へ: バイナリ
バイナリの ODBC C データ型の識別子です。  
  
 SQL_C_BINARY  
  
 次の表は、ODBC SQL データ型が C のバイナリ データを変換する可能性がありますを示します。 列とテーブルの用語の詳細については、次を参照してください。 [C から SQL データ型への変換データ](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)します。  
  
|SQL 型識別子|テスト|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|データのバイト長 < = バイト長の列<br /><br /> データのバイト長 > バイト長の列|n/a<br /><br /> 22001|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|データの長さを文字 < = 列の文字の長さ<br /><br /> データの文字長 > 列の文字の長さ|n/a<br /><br /> 22001|  
|SQL_DECIMAL<br /><br /> SQL_NUMERIC<br /><br /> SQL_TINYINT<br /><br /> SQL_SMALLINT<br /><br /> SQL_INTEGER<br /><br /> SQL_BIGINT<br /><br /> SQL_REAL<br /><br /> SQL_FLOAT<br /><br /> SQL_DOUBLE<br /><br /> SQL_BIT SQL_TYPE_DATE<br /><br /> SQL_TYPE_TIME<br /><br /> SQL_TYPE_TIMESTAMP|データのバイト長の SQL データの長さを =<br /><br /> データ <> SQL データの長さのバイト長|n/a<br /><br /> 22003|  
|SQL_BINARY<br /><br /> SQL_VARBINARY<br /><br /> SQL_LONGVARBINARY|データの長さ < = 列の長さ<br /><br /> データの長さ > 列の長さ|n/a<br /><br /> 22001|
