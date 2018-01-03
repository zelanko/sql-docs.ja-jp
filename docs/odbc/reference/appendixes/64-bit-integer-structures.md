---
title: "64 ビット整数の構造体 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- C data types [ODBC], 64-bit integer structures
- data types [ODBC], C data types
- 64-bit integer structures [ODBC]
ms.assetid: ac80c798-d9b2-4430-85ed-bd2461db0ac7
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 15176629e0154b59c1dfadd9d58f755eb2c423ed
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
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
