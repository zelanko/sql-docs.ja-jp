---
title: データ バッファーの長さ |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data buffers [ODBC], length
- buffers [ODBC], data
- length of data buffers [ODBC]
- buffers [ODBC], length
ms.assetid: 7288d143-f9e5-4f90-9b31-2549df79c109
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b40fb1b58a10ddd5db371869584b4d29f2110855
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32910207"
---
# <a name="data-buffer-length"></a>データ バッファーの長さ
アプリケーションでは、データ バッファーのバイトの長さを行い、という名前の引数でドライバーに*BufferLength*または類似した名前です。 たとえば、呼び出しでは、次に**SQLBindCol**、アプリケーションの長さを指定する、 *ValuePtr*バッファー (**sizeof (***ValuePtr***)**):  
  
```  
SQLCHAR      ValuePtr[50];  
SQLINTEGER   ValueLenOrInd;  
SQLBindCol(hstmt, 1, SQL_C_CHAR, ValuePtr, sizeof(ValuePtr), &ValueLenOrInd);  
```  
  
 ドライバーは、出力文字列引数を持つ任意の関数のバッファー長の引数で、文字の数ではなくバイト単位の数を常に返します。  
  
 データ バッファーの長さが出力バッファーにのみ必要ドライバーは、バッファーの末尾を越えて書き込みを避けるためにそれらを使用します。 ただし、バッファーに文字またはバイナリ データなどの可変長データが含まれている場合にのみ、ドライバーは、データ バッファーの長さを確認します。 バッファーには、整数や日付構造体などの固定長データが含まれている場合、ドライバーはデータ バッファーの長さを無視し、バッファーにデータを保持するのに十分な大きさが前提としていますつまり、固定長のデータを切り捨てますことはありません。 したがって、固定長のデータを十分な大きさのバッファーを割り当て、アプリケーションにとって重要です。  
  
 以外のデータの切り捨てが文字列を出力するときに発生 (のカーソル名が返されるなど**SQLGetCursorName**)、バッファー長の引数で返される長さは、可能な最大文字数。  
  
 データ バッファーの長さは、ドライバーがこれらのバッファーに書き込まれませんため入力バッファーの必要はありません。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [長さ/インジケーター値を使用します。](../../../odbc/reference/develop-app/using-length-and-indicator-values.md)  
  
-   [データの長さ、バッファー長、および切り捨て](../../../odbc/reference/develop-app/data-length-buffer-length-and-truncation.md)  
  
-   [文字データと C 文字列](../../../odbc/reference/develop-app/character-data-and-c-strings.md)
