---
title: 64 ビット整数構造 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- C data types [ODBC], 64-bit integer structures
- data types [ODBC], C data types
- 64-bit integer structures [ODBC]
ms.assetid: ac80c798-d9b2-4430-85ed-bd2461db0ac7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1ecbe4dae4c1bd21ac3d542ee0d9b18169df0116
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307513"
---
# <a name="64-bit-integer-structures"></a>64 ビットの整数の構造
Microsoft C コンパイラのSQL_C_SBIGINTおよびSQL_C_UBIGINTデータ型識別子の C 型は_int64。 Microsoft® C コンパイラ以外のコンパイラを使用する場合、C 型が異なる場合があります。 コンパイラがネイティブで 64 ビット整数をサポートする場合、ドライバーまたはアプリケーションは、ネイティブ 64 ビット整数型に ODBCINT64 を定義する必要があります。 コンパイラがネイティブで 64 ビット整数をサポートしていない場合、アプリケーションまたはドライバーは、このデータにアクセスできることを確認する次の構造体を定義できます。  
  
```  
typedef struct{  
SQLUINTEGER dwLowWord;  
SQLUINTEGER dwHighWord;  
} SQLUBIGINT  
  
typedef struct{  
SQLUINTEGER dwLowWord;  
SQLINTEGER sdwHighWord;  
} SQLBIGINT  
```  
  
 64 ビット整数は 8 バイト境界に揃えられるため、これらの構造体は 8 バイト境界に揃える必要があります。
