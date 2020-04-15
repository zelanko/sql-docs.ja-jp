---
title: リテラル接頭辞と接尾辞 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], literal prefixes and suffixes
- literals [ODBC], prefixes and suffixes
ms.assetid: 29f468f2-f557-4a92-b31d-569c63cc6272
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d52ca54c329353e3d9dc67ca35d89b2d28cedf74
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287984"
---
# <a name="literal-prefixes-and-suffixes"></a>リテラル プレフィックスおよびサフィックス
SQL ステートメントでは、*リテラル*は実際のデータ値の文字表現です。 例えば、次のステートメントでは、ABC、FFFF、および 10 はリテラルです。  
  
```  
SELECT CharCol, BinaryCol, IntegerCol FROM MyTable  
   WHERE CharCol = 'ABC' AND BinaryCol = 0xFFFF AND IntegerCol = 10  
```  
  
 一部のデータ型のリテラルには、特別なプレフィックスとサフィックスが必要です。 前の例では、文字リテラル (ABC) は、プレフィックスとサフィックスの両方として単一引用符 (') を必要とし、バイナリ リテラル (FFFF) はプレフィックスとして 0x 文字を必要とし、整数リテラル (10) はプレフィックスまたはサフィックスを必要としません。  
  
 日付、時刻、およびタイムスタンプを除くすべてのデータ型に対して、相互運用可能なアプリケーションでは、LITERAL_PREFIXで返される値を使用し **、SQLGetTypeInfo**によって作成された結果セットの列LITERAL_SUFFIXする必要があります。 日付、時刻、タイムスタンプ、および日時間隔リテラルの場合、相互運用可能なアプリケーションでは、前のセクションで説明したエスケープ シーケンスを使用する必要があります。
