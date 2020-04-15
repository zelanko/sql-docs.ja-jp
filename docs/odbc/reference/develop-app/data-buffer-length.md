---
title: データ バッファの長さ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data buffers [ODBC], length
- buffers [ODBC], data
- length of data buffers [ODBC]
- buffers [ODBC], length
ms.assetid: 7288d143-f9e5-4f90-9b31-2549df79c109
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d4a4e9a739201d74cfc6c4f7c18e64b91e0fabe4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305263"
---
# <a name="data-buffer-length"></a>データ バッファーの長さ
アプリケーションは、引数*BufferLength*または類似の名前でドライバーにデータ バッファーのバイト長を渡します。 たとえば、次の**SQLBindCol**の呼び出しでは、アプリケーションは *、値のバッファー***の長***ValuePtr***** さを指定します。  
  
```  
SQLCHAR      ValuePtr[50];  
SQLINTEGER   ValueLenOrInd;  
SQLBindCol(hstmt, 1, SQL_C_CHAR, ValuePtr, sizeof(ValuePtr), &ValueLenOrInd);  
```  
  
 ドライバーは、出力文字列引数を持つ関数のバッファー長引数の文字数ではなく、バイト数を常に返します。  
  
 データ・バッファーの長さは出力バッファーにのみ必要です。ドライバーは、バッファーの末尾を過ぎて書き込みを回避するためにそれらを使用します。 ただし、ドライバーは、バッファーに文字やバイナリ データなどの可変長データが含まれている場合にのみ、データ バッファーの長さをチェックします。 バッファーに整数構造体や日付構造体などの固定長データが含まれている場合、ドライバーはデータ バッファーの長さを無視し、バッファーがデータを保持するのに十分な大きさであると想定します。つまり、固定長データは切り捨てることはありません。 したがって、アプリケーションは、固定長データ用に十分な大きさのバッファーを割り当てることが重要です。  
  
 非データ出力文字列の切り捨て **(SQLGetCursorName**に返されるカーソル名など) が発生した場合、バッファー長引数に返される長さは、可能な最大文字数です。  
  
 ドライバーがこれらのバッファーに書き込まないため、データ バッファーの長さは入力バッファーには必要ありません。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [長さ/インジケーター値の使用](../../../odbc/reference/develop-app/using-length-and-indicator-values.md)  
  
-   [データの長さ、バッファー長、および切り捨て](../../../odbc/reference/develop-app/data-length-buffer-length-and-truncation.md)  
  
-   [文字データと C 文字列](../../../odbc/reference/develop-app/character-data-and-c-strings.md)
