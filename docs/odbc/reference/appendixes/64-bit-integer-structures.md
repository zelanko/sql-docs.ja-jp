---
title: 64 ビット整数の構造体 |Microsoft ドキュメント
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
- C data types [ODBC], 64-bit integer structures
- data types [ODBC], C data types
- 64-bit integer structures [ODBC]
ms.assetid: ac80c798-d9b2-4430-85ed-bd2461db0ac7
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e9f397923b652bf889dae70e14c39e2f3a8865c7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32905327"
---
# <a name="64-bit-integer-structures"></a>64 ビット整数の構造体
Microsoft C コンパイラで SQL_C_SBIGINT、SQL_C_UBIGINT データ型識別子の C 型は、_int64 です。 Microsoft® C コンパイラよりもその他のコンパイラを使用する場合は、C 型が異なる可能性があります。 コンパイラは、ネイティブ 64 ビット整数値をサポートする場合ドライバーまたはアプリケーションは ODBCINT64 ネイティブの 64 ビット整数型であることを定義する必要があります。 コンパイラで 64 ビット整数がネイティブにサポートしない場合、アプリケーションまたはドライバーはこのデータへのアクセスを使用していることを確認する次の構造体を定義できます。  
  
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
  
 これらの構造体は、64 ビット整数が 8 バイト境界に配置するため、8 バイト境界に揃える必要があります。
